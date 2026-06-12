---
title: "Understanding SSH tunnels"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-06-28
Hello everyone!

Here is the scenario: 
-> My ISP blocks all access to my machine on ports lesser than 1024. 
-> I want to install a FTP server, so that I can access it while I am travelling elsewhere. 

Here are my options
-> Install a SSH server, make it listen on a port greater than 1024 by editing /etc/ssh/sshd_config. Works fine.
-> Install FTP server (ex: proftpd) and edit /etc/proftpd.conf to make it listen on a port greater than 1024.  Fine too. 

However, the above 2 are not what I want. I want to understand how tunnels work. What I have in mind is this
-> Let FTP server listen on port 22. 
-> Create a SSH tunnel from port 8600 to port 22 within the local machine. 

Is that possible? Can somebody explain how to do it? I know it sounds silly and that there are other ways to get what I want, but I really want to try a tunnel. Is is possible to create a tunnel between 2 ports on the same machine? Do I need a root account? ... -- Thanks, Hari

---

### Post by harisund on 2006-06-29
Any ideas anyone?

---

### Post by Footer on 2006-06-29
I'm not sure why you'd need a tunnel (i.e. secure connection) between ports on the *same * machine?

Are you using a router by chance?  Why not just forward port 8600 to port 22 on your local machine?

---

### Post by harisund on 2006-06-29
Hmmm... you are right. You see, I want to know whether a tunnel can be created between 2 ports on the same machine, especially if one of the ports is lesser than 1000 (previliged, need root access, but no root in Ubuntu, won't work with sudo). I know I can forward port 8600 to 22 and all that stuff, but my question is with the tunnel on the same machine. 

Has anybody tried that out?

---

