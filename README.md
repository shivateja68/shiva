# shiva
from flask import Flask
import os
from datetime import datetime
import subprocess

app = Flask(_name_)

@app.route('/htop')
def htop():
    full_name = "Your Full Name"
    username = os.getlogin()  # System username
    server_time = datetime.now().strftime('%Y-%m-%d %H:%M:%S IST')  # IST time
    top_output = subprocess.check_output(['top', '-b', '-n', '1']).decode('utf-8')  # 'top' command output

    response = f"<h1>Name: {full_name}</h1>"
    response += f"<p>Username: {username}</p>"
    response += f"<p>Server Time in IST: {server_time}</p>"
    response += f"<pre>{top_output}</pre>"

    return response

if _name_ == '_main_':
    app.run(host='0.0.0.0', port=8080)
