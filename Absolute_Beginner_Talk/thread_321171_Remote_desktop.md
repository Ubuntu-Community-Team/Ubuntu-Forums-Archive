---
title: "Remote desktop"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by DrMega on 2006-12-18
Hi all.

I'm trying to get some sort of remote desktop going between my two Ubuntu machines. One machine is connected to the TV only (no monitor) so it is horrible to read text on it, so for admin jobs, I want to remote onto it. I've read the article at....

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_configure_remote_desktop_.28not_secure.29]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_configure_remote_desktop_.28not_secure.29")

...and as far as I can tell I've done everything it said. However when I run the VNC viewer, It won't work. Here's what I got in the terminal. Any ideas?

~$ vncviewer 192.168.0.142
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused

---

### Post by hyper_ch on 2006-12-18
I have on mine, as vncserver, krfb... it's a kde program but runs fine on xubuntu...
you can then connect to it with any vnc client I think...

---

### Post by greyhill on 2006-12-18
If you can ssh into the box connected to your TV, we can try to set it up the old-fashioned way.

1. ssh in
2. sudo apt-get install tightvncserver
3. tightvncviewer
4. enter a password
5. end your ssh session
6. now try to connect

Or it could be a firewall problem, of course.  Have you set up firestarter or anything like that?

---

### Post by DrMega on 2006-12-18
> **greyhill said:**
> If you can ssh into the box connected to your TV, we can try to set it up the old-fashioned way.

1. ssh in
2. sudo apt-get install tightvncserver
3. tightvncviewer
4. enter a password
5. end your ssh session
6. now try to connect

Or it could be a firewall problem, of course.  Have you set up firestarter or anything like that?

Sorry, I'm new to linux. What's ssh? I haven't set up any firewall because I'd read that Ubuntu is secure by default.

---

### Post by edemark on 2006-12-19
ssh as far as i know is secure shell it is a way of connecting to remote machines. Actually the server part is not installed by default in any ubuntu system (at least i was only able to connect to my fedora machines but not from them to my ubuntu) so first you might want to install ssh server (ssh is really good you may even use graphical front ends is to say that you can run just your xfce4-panel on a remote machine)

actually i have the same problem that i cannot connect to my xubuntu machine via vnc so i am trying out what was sugested by greyhill.

so thanks and good luck

---

### Post by edemark on 2006-12-19
ok so i installed in ssh via apt-get tightvncserver but there is no such thing like tightvncviewer. 
Any idea?

thanks

---

### Post by DrMega on 2006-12-19
> **edemark said:**
> ssh as far as i know is secure shell it is a way of connecting to remote machines. Actually the server part is not installed by default in any ubuntu system (at least i was only able to connect to my fedora machines but not from them to my ubuntu) so first you might want to install ssh server (ssh is really good you may even use graphical front ends is to say that you can run just your xfce4-panel on a remote machine)

actually i have the same problem that i cannot connect to my xubuntu machine via vnc so i am trying out what was sugested by greyhill.

so thanks and good luck
I sort of found a way to do what I need. In some ways its better than VNCing on because the wife can continue using the machine at the same time.

I enabled remote logon on the target machine. To do this:
1. I went to System->Administration->Login Window
2. Go to Remote tab
3. In the style dropdown, select Enable Remote login. Make sure you tick the boxes to force the remote user to need a password.

Then on the other machine:
4. Log off
5. At the main login screen, in the bottom left corner, choose options
6. Select remote logon via X something or other (can't remember but its fairly self explanatory when you see it). This brings up a dialog which after a few seconds, will list the  target machine)
7. Double click on the icon for the target machine, which will take you a familiar login screen, where you can log in as normal.

The plus side is that you can then work on it remotely while someone else works on it locally and you don't really interfere with each other (you each get seperate desktop sessions). the down side is that some programs seem to detected that you've logged on remotely and refuse to work (but they work if you log on locally as the same user).

---

