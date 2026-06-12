---
title: "OpenSSH help"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Ronfar on 2007-08-26
I'm having problems logging into my SSH server from outside of my LAN, it works fine when both computers are on the same line. When I try to connect from outside of it, it will wait for about 5 minutes then give me this message ssh: connect to host "my ip" port "my port": Connection timed out. Has anyone experience this problem before or have any solutions, I apperciate anyone taking the time to helping me out with this problem. Thanks!

---

### Post by sizzam on 2007-08-26
Is your firewall blocking access to the SSH port?   It uses port 22 by default.   In my router, I have to set up Port Forwarding to forward requests on port 22 to the IP of the machine that is running the SSH server.

---

### Post by Ronfar on 2007-08-26
So what your saying is that I would need to port forward from the connection that I am on right now? What if I am not able to configure the router because it is a hotspot then I just can't use my ssh server at home?

---

### Post by Jimmyfj on 2007-08-26
The computer from which you try to connect from the outside, is that a Windows or a Linux computer? Provided that port 22 in your firewall is open, and incoming traffic is redirected to the correct IP address things should work fine. Be sure that the client from which you try to connect also has port 22 opened, and has the OpenSSH-client is installed on it.

---

### Post by Ronfar on 2007-08-26
It's a Linux computer, the computer does have openssh client installed and the correct port open. Is it possible that the hotspot connection that I am on would have that port disabled and that is the reason why I can't connect? If so are there any ways I can check to see if this is true?

---

