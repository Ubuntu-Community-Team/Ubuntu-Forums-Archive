---
title: "Using NoMachine to connect to Ubuntu desktop with Windows"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by smithwk2 on 2008-01-11
When I try to connect to Unbuntu destop from Windows, I get "Connection refused" with the following details.

NX> 203 NXSSH running with pid: 4964
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host 192.168.1.14 port 22: Connection refused


Both machines are within my home network.  Thanks in advance for the help.

---

### Post by geirha on 2008-01-11
Have you installed openssh-server on the ubuntu-box? It's not installed by default.

---

### Post by smithwk2 on 2008-01-11
Thanks for the reply.  No I have not.  Could you point me to some documentation that would tell me how to install openssh-server?  Thanks again.

---

### Post by eolson on 2008-01-11
From the command line

   sudo apt-get install openssh-server

Then everything should work.

---

### Post by geirha on 2008-01-11
And if you prefer the GUI, then choose System -> Administration -> Synaptic package manager from the gnome-panel. Then search for openssh-server and install.

---

### Post by smithwk2 on 2008-01-11
That did it!!!  Thanks a bunch.  Have a great weekend!!!

---

### Post by smithwk2 on 2008-01-11
After making the above changes, it worked for a few times and now it gets all the way to connecting to the desktop and I  get "NX" in the setup box and the following is the last line in the detail information:

NX> 280 Exiting on signal: 15

Thanks again in advance.

---

### Post by smithwk2 on 2008-01-12
Disregard my previous post.  I am not sure how, but I got it to work.  Thanks.

---

### Post by exactopposite on 2008-01-12
The instructions in this post worked great for me.

[http://ubuntuforums.org/showthread.php?t=493983](http://ubuntuforums.org/showthread.php?t=493983)

---

