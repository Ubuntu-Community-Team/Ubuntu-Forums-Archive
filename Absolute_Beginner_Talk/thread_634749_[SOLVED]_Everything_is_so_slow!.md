---
title: "[SOLVED] Everything is so slow!"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by agerfe on 2007-12-08
Just don't know what happened! Ubuntu was working great and now suddenly everything - from the system boot to the opening of something simple like the terminal for example - takes minutes! :(

I have a dual boot system: Windows XP / Ubuntustudio, but both OS's are on different HDD's.

I have a dual core 1.86GHz, 2Gb of RAM and two 250GB HDD's

I'd appreciate any help!

---

### Post by zidty on 2007-12-08
after you logon .. have you tried using system monitor to check if some application is choked up .. ??

---

### Post by jimmj43 on 2007-12-08
Look for a coincidence in timing. There have been a (very) few reports that some updates can create totally unexpected problems.

---

### Post by spai on 2007-12-08
Actually the same thing used to happen with Fedora for me. That is why I switched to Ubuntu. The update at startup could make it slow. Or of course you can always check system monitor to see which app is eating memory.

---

### Post by agerfe on 2007-12-08
I just reinstalled Ubuntustudio and although the speed has improved a lot I still have to wait between 5 and 10 seconds for a window to open (terminal, network, etc)

Maybe the problem is related to the fact that I cannot connect to the Internet. I have posted another thread for help on this: [http://ubuntuforums.org/showthread.php?t=634799]("http://ubuntuforums.org/showthread.php?t=634799")

My guess is that some app is trying to access the Internet and that causes the slowdown.

---

### Post by derby007 on 2007-12-08
If u disconnent from the internet, (pull the plug), does this increase performance. My Ubuntu PC isnt connected and its very fast !!!

---

### Post by Canuckelhead on 2007-12-08
check your USB devices...  I sometimes slow down a bit if I have too many things (drives in my case) connected via usb... usually I let it boot, connect all my devices and then do a proper shut down... next boot is fast as hell...  until I make a change

my two cents...

---

### Post by agerfe on 2007-12-08
The only usb devices are the mouse and the printer and this one is turned off (which is just like not having it plugged). Could this all be because of the mouse?

I'll try unplugging the cable to see if that works.

---

### Post by agerfe on 2007-12-08
Now it's incredibly slow again!...... Eventhough I have reinstalled Ubuntustudio....... formatting the partitions!

I got this message when booting:

> Failed to connect to socket /tmp/dbus-HUTy3EauhE:

---

### Post by agerfe on 2007-12-08
I'm posting some screenshots of the monitor.

Everything seems to be ok!

I'm getting a view of the terminal between the logo and the desktop. All entries in the right hand column show OK.

The booting of the whole desktop can take between 5 and 10 minutes.

What is wrong here?

It was working of just a few hours ago. Besides the configuration of my PC should be more than enough to run Ubuntu. It's obviously not a problem of RAM, so what is it?

Anyone, please help! :confused:

---

### Post by agerfe on 2007-12-08
Meant it was "working fine"........ not "working of".......... I'm getting sleepy! :lolflag:

---

### Post by agerfe on 2007-12-09
Yesterday I discovered the problem. It seems there's a bug in Ubuntu. I posted a thread in the launchpad. Here's the link: [https://bugs.launchpad.net/ubuntu/+bug/174989]("https://bugs.launchpad.net/ubuntu/+bug/174989")

---

