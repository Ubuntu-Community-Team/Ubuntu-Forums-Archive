---
title: "SSH using PuTTY"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by lupgop on 2008-01-10
I recently installed SSH
sudo apt-get install openssh-server

forwarded port 22 to the server.

now im at work , i run PuTTY
put in the IP tick SSH and click Open

a terminal window open - but just sits there ???  green square top right corner - not flashing ; few minutes later  info box pops up saying
Putty Fatal Error
Network error: Connection timed out

any idea what could cause this ???   would it be blocked via work ??? telnet works ???

---

### Post by shad0w_walker on 2008-01-10
Have you forwarded the port on your router at home?

---

### Post by Borbus on 2008-01-10
It is quite possible that your work has blocked port 22. Can you connect to the server on any other ports? Port 80 would be a good test.

---

### Post by lupgop on 2008-01-10
i have forwarded port 22 to the server on my router at home.
i can see the index page on the machine - that is via port 80 ? is this what you mean ?

---

### Post by tigerplug on 2008-01-10
Try to Telnet and see what happens?

---

### Post by AndyCooll on 2008-01-10
> **lupgop said:**
> i have forwarded port 22 to the server on my router at home.
i can see the index page on the machine - that is via port 80 ? is this what you mean ?

If you have forwarded port 22 to your server at home then it is highly likely that your work has blocked port 22, hence the reason why you get a blank screen.

What has been suggested is that you change your SSH settings and set it use port 80. This port is less likely to be blocked by your works firewall as it is the one used for most Internet traffic.

:cool:

---

### Post by lupgop on 2008-01-10
gottcha - do i need to make changes on the SSH server (at home) or just SSH to my IP using port 80.

---

### Post by ByteJuggler on 2008-01-10
> **lupgop said:**
> any idea what could cause this ???   would it be blocked via work ??? telnet works ???

Its very unlikely that port 22 would be opened for access for you to use at your workplace to the general internet. Probably your web access is also routed via an (http/web) proxy server, which is why that works.  Everything else is probably locked down.

Edit: You would probably need to speak to your networking people if you seriously want to use SSH from your machine, so they can open/make an allowance in the corporate firewall.  

There are other web based options, Webmin for example, although that also doesn't normally run on port 80.  (But probably can be made to do that, and will work with your browser, via your corporate proxy server.)

---

### Post by lupgop on 2008-01-10
tried this but still just get a blank window with a green square cursor not flashing ??

---

### Post by lupgop on 2008-01-10
i can telnet to my shell account ???? that works.

---

### Post by ByteJuggler on 2008-01-10
> **lupgop said:**
> i can telnet to my shell account ???? that works.

Telnet actually works?  Hmmm then your work network is set up strangely, IMHO... You can use telnet, but be aware that every command you issue over telnet is trasmitted over the internet in plain text, including when you log on, so your password could conceivably be captured by someone sniffing the traffic between your PC and your server.  (This is precisely why you want to use SSH, and why most places disable Telnet and enable SSH.  If you work actually allows Telnet, they it stands to reason they should want to also use/support SSH and eventually get away from Telnet...)

---

### Post by Clickbg on 2008-01-10
Just do:

nano /etc/ssh/sshd*

Find the line - #Port 22 and replace it with Port 2200 (just an example) Do no use port 80, thats the port for HTTPD. Use ports above 1024. After that just write:

/etc/init.d/sshd restart

---

### Post by ByteJuggler on 2008-01-10
> **Clickbg said:**
> Just do:

nano /etc/ssh/sshd*

Find the line - #Port 22 and replace it with Port 2200 (just an example) Do no use port 80, thats the port for HTTPD. Use ports above 1024. After that just write:

/etc/init.d/sshd restart

Actually -- if Telnet works from your work, then you could always stop the telnet service, and run SSH on it (port 23) instead, after which putty should work! (Using telnet port 23 of course!)

---

