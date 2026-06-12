---
title: "Downloading Apps"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-05-15
Okay, here is my problem, I want to download VNC application, I looking through this forum and it asked me to download an application to my home directory, well I tried it and it keeps downloading to my Desktop.  How can i change it to download to my home directory?  Is there a way I can move it from my Desktop Directory to my Home directory?  Oh yeah, and when I went to look for my home directory on the terminal, ( I typed ls -a) I didn't see a directory named home.](*,)

---

### Post by aysiu on 2006-05-15
I'll break it down for you.

In the file structure, there are a whole bunch of folders at the top level: /etc, /boot, /tmp, /usr, /root...

One of those folders is called /home

Inside of that top-level directory are all the user "home" directories. So when someone says "your home directory," she really means

/home/neogreen

not

/home

And your desktop folder is

/home/neogreen/Desktop

Note that *Desktop* is capitalized--files and directories are case-sensitive.

Sometimes people will refer to /home/neogreen as ~/ and /home/neogreen/Desktop as ~/Desktop.

---

### Post by NeoGreen on 2006-05-15
Oh, okay I get it thanks:)

---

### Post by ProjectGod on 2006-05-15
i'm surprised youre downloading VNC... there should already be utilities equivilant to both VNC viewer and server on the ubuntu... my breezy bad-badger does anyway... :)

in the terminal type . "cd /"
then type "ls" you should be able to see the directory structures... 

use the "mv" to move files from directory to directory. :-D

---

### Post by aysiu on 2006-05-15
Good point, ProjectGod.

Make sure you're aware of the easy way to install things before you do something complicated like installing from source.

[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by NeoGreen on 2006-05-15
Where or how exactly can I get these Apps running if they are already installed?  This is why I want to do this:  I installed FC5 on an old Dell and I was playing around with VNC, which came automatically installed( which to me means I can go to Applications Accessories and Wa-La there it is right below Terminal), I got on it and typed the ip address of my laptop (which has Ubuntu installed on it) and to my surprise I could see the desktop of my laptop on my FC5 monitor.  Wow!!!! (remember I am new to this)  So know I want to be able to do this same on my laptop to not just be able to see what is the FC5 computer but also my Windows XP computer.:)

---

### Post by aysiu on 2006-05-15
Ubuntu comes with the ability to share desktops via VNC server. I'm not sure if it has a VNC viewer built in, but you can easily install it: ```
sudo apt-get update
sudo apt-get install xtightvncviewer
``` Then, when you want to use TightVNC, use the command ```
vncviewer
``` It'll prompt you for the IP address and password of the server.

---

### Post by ProjectGod on 2006-05-15
SYSTEM ... PREFERENCES .. "REMOTE DESKTOP" is the VNC Server equivalent.

APPLICATION ... INTERNET ... "TERMINAL SERVER CLIENT" is the VNC client equivalent... (even better than the usual VNC client cause it is also compatible with windows RDP protocol)

they're both pretty self explanatory tools to use.

---

### Post by NeoGreen on 2006-05-15
Got it thanks.:)

---

