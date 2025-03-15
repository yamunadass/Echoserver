# Echoserver
Echo server and client using python socket

# AIM:

To develop a simple webserver to serve html programming pages.

## DESIGN STEPS:

### Step 1:

Design of echo server and client using python socket

### Step 2:

Implementation using Python code

### Step 3:

Testing the server and client 

## PROGRAM:

### Server code:
```python
import socket

HOST = "127.0.0.1"  # Standard loopback interface address (localhost)
PORT = 65432  # Port to listen on (non-privileged ports are > 1023)

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    try:
        s.bind((HOST, PORT))
    except Exception as e:
        print(f"Error binding to {HOST}:{PORT}: {e}")
        exit()
    
    s.listen()
    print(f"Listening on {HOST}:{PORT}...")

    try:
        conn, addr = s.accept()
    except Exception as e:
        print(f"Error accepting connection: {e}")
        exit()

    with conn:
        print(f"Connected by {addr}")
        while True:
            try:
                data = conn.recv(1024)
                if not data:
                    break
                conn.sendall(data)
            except Exception as e:
                print(f"Error receiving/sending data: {e}")
                exit()

```
### Client Code:
```python
import socket

HOST = "127.0.0.1"  # Server IP (localhost)
PORT = 65432  # Same port as the server

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))
    s.sendall(b"Hello, Server!")
    data = s.recv(1024)

print(f"Received from server: {data.decode()}")

```

## OUTPUT:
### Server side:
![Screenshot 2025-03-06 111725](https://github.com/user-attachments/assets/0a9d54be-7b7c-4862-95cd-036976ece649)


### Client side:
![Screenshot 2025-03-06 111755](https://github.com/user-attachments/assets/d95c39bd-97e1-4567-b7a5-af6108a748c1)


## RESULT:
The program is executed successfully.
