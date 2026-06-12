---
title: "Question about PuTTY, SSH, and TOP"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by lakefire on 2005-06-08
Hey guys, I currently have 3 systems, two ubuntu's and one winXP (my main computer).  I have them setup though VPN and can view the desktop via tightvncviewer (on my windows machine).  However, this software seems unstable and crashes the server on the linux side on occasion.

Unfortunately for me, I only have 2 monitors (well, I actually have 3 with 2 connected to my windows machine, but that's besides the point) and incase my VPN connection crashes on my 3rd box, I want to be able to restart the server through PuTTY.

OK, I have gotten SSH up and running and I am aware that I need to go into "top" to handle my current processes.  My question is what is the correct command to restart a process and do you know the name of the process for the VPN server?

THanks in advance!

---

### Post by Jussi Kukkonen on 2005-06-09
[QUOTE=lakefire]
OK, I have gotten SSH up and running and I am aware that I need to go into "top" to handle my current processes.  My question is what is the correct command to restart a process and do you know the name of the process for the VPN server?

THanks in advance![/QUOTE]

I'm guessing you're running xvnc. It's been a while, so take this with a grain of salt... I think the running server is called *xvnc*, but it is started with *vncserver*-wrapper.

You could test that by running
```
ps aux | grep vnc
```
while your server is running. It should find an instance of xvnc. If it does, kill it (for testing purposes):
```
vncserver -kill *:display*
```
will probably do the trick. Try *vncserver -kill :1* if you don't know the display number. You could also find the config file *vncservers* somewhere in your system (*locate vncservers* will find it), and see what number your username has.

Then start the server with 
```
vncserver *options*
```
Try it without any options, or find the startup file in /etc/init.d/ (probably named xvnc or vncserver) and see what options it uses.

---

