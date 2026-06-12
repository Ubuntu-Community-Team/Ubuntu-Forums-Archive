---
title: "Gutsy very slow without a network connection."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by jmail524 on 2007-11-05
I have been running Fesity (7.04) for about the last 3-4 months without any problems.  I have since reloaded my system with Gutsy (7.10) because of the new features that it has.  However, I am having a significant problem and I am hoping that great amount of expertise on this board could help solve my problem.

I have 2 computers, a desktop (Ubuntu Gutsy 7.10 AMD64) and a laptop (Ubuntu Gutsy 7.10 i386).  Both computers exhibit the exact same problems.

If I start my computer without an active network/internet connection, it takes a very long time to reach the desktop (approximately 8-10 minutes.)  Also, when it does reach the desktop the icons and menus look odd.  I get an error message:

----------------------------------------------------------------------------------
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or backgroun settings may not work correctly.

The last error message was:

Failed to connect to socket /tmp/dbus-WFXqpZh8CV: Connection refused

GNOME will still try to restart the Settings Daemon next time you log in.
------------------------------------------------------------------------------------------------------

After that message I am on the desktop.  But, I cannot run any programs.  When I try to start ANY application (Firefox, Terminal, OpenOffice, F-Spot Photo Manager, any game, or enter any folder) nothing happens.  However, if I try to start an application and nothing happens and then I establish a connection to the internet, the program will come up.  It is almost as if Gutsy will not run without an internet connection.  I never had this problem with Feisty.

I have even erased my hard drive and re-downloaded the Gutsy CD images again and re-installed it and I still have the same problem.  Also the problem occurs in both the i386 and AMD64 versions of the OS.

I am at wits end, and am looking for any help with this horrible problem.  AT this point I am truly considering returning to Feisty.

Thanks.

---

### Post by oilchangeguy on 2007-11-05
if 7.04 was working fine. then there was no real reason to change. my first try with 7.10 went bad. i've been using 6.06 sine it came out. the 7.10 cd would get to the install screen and go no farther. some error message about it not being bootable. and yes, i know how to create a bootable cd, from an iso. the bottom line is, 7.10 has problems. go back to 7.04.

---

### Post by mridkash on 2007-11-05
The exact same problem you said bugged me in fiesty, without internet the laptop booted so sloww and took almost 5mins to reach desktop. But now with gutsy its fine. I do get the error you get sometimes. a simple solution is to log out and login again.

---

### Post by lingo123 on 2007-11-08
Same problem with me :( when ever I have net.. my comp works very smotth.. but whne th enet is gone.. its take some 1-2 mins to open any application(connected with gnome).If I open a viode with totme.. it take 2 mins to open.. but if i open with vlc.. its take 2-3 secs to open.. what coold be th eproblem. Also if I turn off the network using the command /etc/init.d/networking stop then everything works fine..

---

### Post by jmail524 on 2007-11-08
Well I just received a few updates to Ubuntu.  Now the problem that I used to have is now much, much worse.  I now get the Gnome Settings Daemon error every time that I boot up.  My Gutsy installation seems to have been crippled with the last set of updates.

This is very disappointing.  It seems that since Gutsy came out, every update that I have gotten has broken something.  I guess I'm being forced back to Feisty,

Thanks to everybody who chimed in.

---

### Post by hamiltonlight on 2008-01-14
I have the same problem still on 7.10 on my work laptop. Whenever I boot it up at home without an Internet connection its very slow, nautilus does not display/refresh the desktop properly and takes 5 mins or so to open a folder. Applications take a varying amount of time to start up.

Is there a fix for this?

Thanks.

---

### Post by eolson on 2008-01-14
I wonder if there is something common between your machines.

I'm running three systems on Gutsy;  and emachines laptop,  a Dell 530,  and an old hombrew and none of them have the problem.

Have heard other complaints of it though.   There must be come common ground.

---

### Post by Palmstroem on 2008-01-16
I am having the same problem (Dell M90 laptop running Gutsy gets extremely slow when not connected to the network). Still no solution!

Nevertheless it's good not to be alone...:)

---

### Post by Noob4Ever on 2008-01-19
I have the same exact problem as jmail.

wonder what it takes to solve it :/

---

### Post by Palmstroem on 2008-01-22
Just adding some observations:

when my laptop is not connected to the usual ethernet network and becomes extremely slow, then
[LIST]
[*]I am **not** able to see a process with ```
top
``` eating up my computer ressources (that puzzles me a bit),
[*]changing settings in the network manager does **not** help,
[*]switching off the network with ```
sudo /etc/init.d/networking stop
``` **does help**!!! Computer speed is back again. lingo123 reported this already.
[/LIST]

---

### Post by Bothered on 2008-02-03
I also have this problem

Oddly I had no issues until a few weeks after installing gutsy.

---

### Post by Krydahl on 2008-02-03
Do you have a loopback set up correctly in your hosts file? 

This is old, but might be worth a look.

[http://ubuntuforums.org/showthread.php?t=230534](http://ubuntuforums.org/showthread.php?t=230534)

---

### Post by Bothered on 2008-02-03
Thanks - adding my host name as an alias for 127.0.0.1 seems to have fixed the problem

---

### Post by Krydahl on 2008-02-03
My pleasure, glad it worked.

---

