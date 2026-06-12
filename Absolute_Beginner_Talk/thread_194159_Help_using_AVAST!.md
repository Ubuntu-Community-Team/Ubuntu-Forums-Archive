---
title: "Help using AVAST!"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by madu on 2006-06-11
Hey guys...

I downloaded and installed AVAST!. I hope I did it right.
I types AVAST and they asked for the Reg key and I eneterd. Then asked to update and I did.
Now how can I run it? I cant seem to find any icons or menus around with Avast!
How can I run in GUI..? there is no file called avastgui in /bin, as was mentioned in a thred..
Where can I get information on how to run it in cmd line.. or start a gui..?

Thanks a lot guys..

Cheers..
 Madu..

---

### Post by jorn on 2006-06-11
Have you tried typing:
> sudo avast
into terminal?
I havn't used avast so I don't know.

---

### Post by circadianhelix on 2006-06-11
not sure if i should start my own thread or what, anyway. 
i'm hoping to use a virus scanner via linux to fix up my hdd with windows on it, linux itself recognises it but cant seem to get avast to find the directory. Any ideas if this is possible or maybe an alternate? Can't locate the free AVG for linux at all.

---

### Post by gingermark on 2006-06-11
[HOWTO: Install AVG free anti-virus](http://www.ubuntuforums.org/showthread.php?t=136064)

---

### Post by airtonix on 2006-07-16
> **madu said:**
> 
I downloaded and installed AVAST!. I hope I did it right.


well technically we should wait until its in the repos....so we can continue to calim a secure system....um is this important to no one? just a causal ask.

> **madu said:**
> 
Now how can I run it? I cant seem to find any icons or menus around with Avast!
How can I run in GUI..? there is no file called avastgui in /bin, as was mentioned in a thred..
Where can I get information on how to run it in cmd line.. or start a gui..?


One of the cools things i love about the bash is that you can start typing what you think the commands looks like ...then by pressing tab you get a list of all the commands available that start with the string you typed.

hope it helped.

---

### Post by yxlbaz on 2007-12-04
I have just installed Avast 4 (for) home users into my ubuntu system and all seems OK.

So, just for a check -

I downloaded the .deb file "avast4workstation_1.0.8-2_i386.deb" and installed using the package manager - just click the file in the file manager window.

Installation was reported as complete but Avast did not appear anywhere obvious but typing 
avast
or
avastgui

- at a command prompt started avast which asked for a registration number.  You get this by email from the avast web site. After this was entered I just start the gui with the above command and all seems fine.

A couple things to check -

ls /usr/bin/avast* should show you the two links "avast" and "avastgui" to the avast startup program

eg
 $ ls /usr/bin/avast*
/usr/bin/avast  /usr/bin/avastgui  /usr/bin/avast-update

If they are there then check your PATH variable which should include /usr/bin -

eg
$ echo $PATH
...other stuff .....:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/.... etc ...

I think that avast only runs from the command line but you could put a short script to start it on your desktop and/or set up a cron job to run it periodically.

Also look at 
$ man avast

avast does not seem to need "sudo" to start


I have used avast with windows and this linux version seems a lot simpler and you know what's going on.  It doesn't seem to be so automated.

---

### Post by Joeb454 on 2007-12-04
**airtonix** - I'm sure we don't need to wait for avast to be in the repo's, as Avast is a reputable name/company that provide free Anti-Virus for Linux & Windows users alike.

In fact in a security thread I read a little while back it's a suggested AV if you want one.

---

### Post by c0met on 2007-12-21
Hi people,

I don't know if you guys are still after this information. I'm posting it in case useful. The below link at Debian tells you how to install the menu set-up for Avast! once you have installed the program.

[http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html](http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html)

Gotta love Ubuntu :popcorn:

---

