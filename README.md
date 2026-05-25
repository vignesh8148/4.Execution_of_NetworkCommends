# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>
## PROGRAM

SERVER.PY:


```
import socket
from pythonping import ping

s = socket.socket()

s.bind(('localhost', 8000))
s.listen(1)

print("Server waiting for connection...")

c, addr = s.accept()
print("Connected with", addr)

while True:
    try:
        hostname = c.recv(1024).decode()

        if not hostname:
            break

        result = ping(hostname, verbose=False)
        c.send(str(result).encode())

    except Exception as e:
        print("Connection closed:", e)
        break

c.close()
s.close()

```
Client.py
```

import socket

c = socket.socket()

c.connect(('localhost', 8000))

while True:
    hostname = input("Enter hostname: ")

    c.send(hostname.encode())

    data = c.recv(4096).decode()

    print("Ping Result:")
    print(data)

c.close()
```


## Output
<img width="1243" height="367" alt="{2FDC7C98-09B2-422B-B8FA-BBAE681122A5}" src="https://github.com/user-attachments/assets/65778db4-e739-4779-b4ec-2f3fbb72eb1d" />


## Result
Thus Execution of Network commands Performed 
