---
title: "Thinkpad R50 problem"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-08-17
After installing ubuntu I plugged in my ethernet cable to the computer but I still cannot go online.  Anyone know why?

I thought all I had to do was put the wire in.  As you can tell I'm completely new at this.  Any help would be appreciated.

---

### Post by GavinX on 2005-08-17
Try to reboot with the cable plugged in and see what happens.

---

### Post by racermike1967 on 2005-08-17
Should it find the connection automatically?
I also have a network error symbol on the top right of my window where the time and sound icon are located.  double clicking on it tells me that no network devices found.  Is that a problem?

---

### Post by numberexhaust on 2005-08-17
Try a couple of things...

First off, as mentioned above, do try to reboot with the cable plugged in.  This will most likely work (most Thinkpads are very compatible with linux).  If not, go into a command line and type:

```
sudo ifup eth0
``` 

If this doesn't work, it gets more complicated.

Edit - oh yeah, after doing that, go into System-Administration-Networking and set the default gateway device to eth0.  I'm not sure if it does that automatically.

---

### Post by racermike1967 on 2005-08-18
When I start up Ubuntu, after loging in, I get the message:
"Could not look up internet address for laptop.  This will prevent GNOME from operating correctly.  It may be possible to correct the problem by adding laptop to the file/etc/hosts" 

Here I have to option of clicking either "log in anyway" or "Try Again".

I always get this message even if I have my ethernet cable plugged in.  I tried the above replies to connect to the internet but they haven't worked.  

Can anyone help me with my previous post as well as this one???

Thank you

---

### Post by numberexhaust on 2005-08-18
BINGO!  Ok, I had this problem for a while.  What it is is that when you ran your installation, you set the local hostname to be laptop.  Keep it to the default "ubuntu" if you don't want to get that message.  I don't know how to change that without reinstalling the OS, but if you really can't afford to reinstall, let me know and I'll play around and try to figure it out for you.

---

### Post by racermike1967 on 2005-08-18
I don't mind reinstalling ubuntu.  The only thing is, will that fix my internet connection problem?

---

