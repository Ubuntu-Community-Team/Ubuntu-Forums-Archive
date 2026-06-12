---
title: "Remote Desktop"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-04-03
I was wondering if I can access my Ubuntu desktop and have total control from my Windows XP desktop, kind of like how GoToMyPC and LogMeIn work. Thanks!

---

### Post by nanotube on 2006-04-03
yes, set up the remote desktop function in ubuntu (system>preferences>remote desktop), then install the tightvnc client on your windows box, and you can connect and view/control your ubuntu desktop. 
that's that, in a nutshell. :) you can get more details if you search these forums for remote desktop or for vnc...

---

### Post by amitroy5 on 2006-04-05
How do a connect from a remote host? For example, from accross the country. Do I just enter the IP address of the computer I want to connect to? Thanks!

---

### Post by dvarsam on 2006-04-05
[QUOTE=amitroy5]How do a connect from a remote host? For example, from accross the country. Do I just enter the IP address of the computer I want to connect to? Thanks![/QUOTE]

I think so... but I am no expert...

You might be asked for a username & password to enter though...

Depends how it is setup.

There are settings like "host.allow" & "host.deny"...

Look in your "/etc/hosts" file...

P.S. I have not done this... but read a lot...so, I can NOT help much...

---

### Post by mlind on 2006-04-05
Vnc server&client stuff is definetly the way to go. I've found tightvnc somewhat
sloppy with windows desktop usage. We've used UltraVNC on different windows
box's, but I don't know if it's available on Linux.

There's several threads floating around forums about more robust vnc solutions.

---

### Post by pete on 2006-04-05
I used VNC for this for a while, but have found Freenx to be a much better solution.  It's compressing at the X level, so it's much more responsive than VNC over a slow connection.  Plus, it's encrypted via SSH, and you don't have to jump through hoops to be able to connect to your Ubuntu machine when it's not logged in.

There's a pretty thorough howto in the wiki: [URL="https://wiki.ubuntu.com/FreeNX"]https://wiki.ubuntu.com/FreeNX
[/URL]

If the machine you're trying to connect to is behind a router, you'll have to tell the router to forward whatever port the connection, regardless of whether you're using VNC or freenx.

---

### Post by amitroy5 on 2006-04-05
It is behind a router, but I am not sure which port to forward.

---

### Post by amitroy5 on 2006-04-05
I noticed that for VNC, you need to forward ports 0 and 5900 for it to work. Also, what if I want to change the port it connects to on Ubuntu, such as port 22, for example.

---

### Post by amitroy5 on 2006-05-11
Also, I want to remotely access another Ubuntu desktop from an Ubuntu desktop I am on right now. What would be a good program? Thanks!

---

