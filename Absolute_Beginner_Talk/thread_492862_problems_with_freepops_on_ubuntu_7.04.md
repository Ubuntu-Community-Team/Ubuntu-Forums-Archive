---
title: "problems with freepops on ubuntu 7.04"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by donquijote on 2007-07-05
Hi guys!
This is my first week as an Ubuntu user and my first post on this forum.I must say that I am truly impressed both by the Ubuntu 7.04 that works amazing and by the very useful information I have found here.
I have a single problem that  I don't know how to deal with.It's about freepopsd.
I installed it yesterday and it worked great.But today when powered up my Pc gnome just could not start.
I realized what the problem was.I had added yesterday a line to .profile ( freepopsd  ),hoping that this way Ubuntu will start automatically freepops everytime  i  reboot my PC.I did this because in the same manner I managed to start my pppoe netwok connection (I added to .profile pon dsl-provider) without typing it every time I login in command line.
So I have entered in safe mode and removed the line freepopsd from .profile, I entered after that in graphical mode, typed in command line freepopsd and everything works fine now except that I had to reconfigure the pppoe.But it's a pitty that I cannot get Ubuntu to start  freepops automatically at startup.
Is anybody gere who could help a Linux newbee?
Thank you very much

---

### Post by DBStevens on 2007-07-05
Do you have settings > autostarted applications on your menu?

I'm running a mashup of Xubuntu and Kubuntu both of these flavors have an easy to add to startup program system, I'd assume (a very bad thing to do when dealing whith software systems) that the Gnome based system also has one.

---

### Post by donquijote on 2007-07-10
I have both gnome and kde desktops installed on ubuntu, but I cannot find any settings option in my menu.Thank you for your reply

---

### Post by DBStevens on 2007-07-10
In KDE you can place a link to a program(script) you wish to  start after login into your home directory's  .kde/Autostart folder.

For the system there  is a script that you can add commands to called /etc/rc.local.  This will if set to execute start at the end of the system boot sequence.   It is also possible to add the required commands in a script that is placed into /etc/init.d and setup to run via the system initialization system.

I'm sure the other windows managers also have places they look for links to programs that they will start upon login.

There is an autostart folder in .config in your home directory that looks like it is used by xface.

I just finished dumping a link into the .kde/Autostart that went to a terminal emulator and then logged off and back on.   When KDE fished starting it launched my terminal session.

Be sure to be careful if you play around with the system boot process.  I use that method to startup code on    some servers.

Good luck.

---

