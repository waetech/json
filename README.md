# json
This project is about loading a JSON file into a web page.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Ajax 2 - Local JSON</title>
</head>
<body>
    <button id="btnUser">Get User</button>
    <button id="btnUser2">Get Users</button>
    <br><br>
    <h1>User</h1>
    <div id="user"></div>
    <h1>Users</h1>
    <div id="users"></div>

    <script>
    document.getElementById('btnUser').addEventListener('click', loadUser);
    document.getElementById('btnUser2').addEventListener('click', loadUsers);

    function loadUser(){
        var xhr = new XMLHttpRequest();
        xhr.open('GET','user.json', true);

        xhr.onload = function(){
            if(this.status === 200){
                //console.log(this.responseText);
                var user = JSON.parse(this.responseText);
                //console.log(user.name);

                

                var output = '';
                
                
                    output += '<ul>' +
                '<li>ID: '+user.id+'</li>' +
                '<li>Name: '+user.name+ '</li>'+
                '<li>Email: '+user.email+ '</li>'+
                '</ul>';
                
                
                document.getElementById('user').innerHTML = output;
                }else if (this.status === 404){
                    document.getElementById('user').innerHTML = 'Error 404 Not found';
                }else if (this.status === 400){
                    document.getElementById('user').innerHTML = 'Error 400 Bad Request';
                }else if (this.status === 403){
                    document.getElementById('user').innerHTML = 'Error 403 Forbidden';
                }                  

                }
            xhr.onerror = function(){
                console.log(this.responseText);
            }
            xhr.send();
        }

        function loadUsers(){
        var xhr = new XMLHttpRequest();
        xhr.open('GET','users.json', true);

        xhr.onload = function(){
            if(this.status === 200){
                //console.log(this.responseText);
                var users = JSON.parse(this.responseText);
                //console.log(user.name);

                

                var output = '';
  
            for(var i in users){
                output += '<ul>' +
                '<li>ID: '+users[i].id+ '</li>'+
                '<li>Name: '+users[i].name+ '</li>'+
                '<li>Email: '+users[i].email+ '</li>'+
                '</ul>';
            }
                
                document.getElementById('users').innerHTML = output;
                }else if (this.status === 404){
                    document.getElementById('users').innerHTML = 'Error 404 Not found';
                }else if (this.status === 400){
                    document.getElementById('users').innerHTML = 'Error 400 Bad Request';
                }else if (this.status === 403){
                    document.getElementById('users').innerHTML = 'Error 403 Forbidden';
                }                  

                }
            xhr.onerror = function(){
                console.log(this.responseText);
            }

            xhr.send();
        }

                
        
    
    
    </script>
</body>
</html>
