---
title: "Make command not installed?"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by timmahhny on 2006-06-29
I am trying to install the ndiswrapper among other items and I can't seem to get the make to work. 
I use "make clean" and I get a return bash no command for make clean. Or make help, or any type of make command.
Do I have to install another package?
I just downloaded  and installed the PC Ubuntu version 6.6 I guess it is, the newest one.
Any help out there would be great.
Tim

---

### Post by Maggot on 2006-06-29
I would think 'clean' is not one of the options for ndiswrapper. Check the README or INSTALL files.

Have you check to see if make was installed?

---

### Post by hod139 on 2006-06-29
you need to install the package build-essential

---

### Post by Jucato on 2006-06-29
To install/compile programs from source code, you need to install the build-essential package, which will install everything that you need to compile

You can find them easily in Synaptic, or if you want to use the command line

```
sudo aptitude update
sudo aptitude install build-essential
```

I recommend using aptitude instead of apt-get in this case, so that removing all the packages installed together with build-essential will be as easy as

```
sudo aptitude remove build-essential
```

---

### Post by timmahhny on 2006-06-30
I will install it right now, thank you all for helping me out and will let you know how it worked. I am attempting to get my wireless card to work; it actually works, but I guess the network connection doesn't recognize it.
I used WiFi Radar and that could not make the connection as well, but it did see my network, so I am going to try the ndiswrapper.
Thanks once again
Tim

---

### Post by timmahhny on 2006-06-30
I was using make clean, make all, etc.. on Red Hat and Mandriva and assume that it is the same with Ubuntu. But am not sure.
Thank you
Tim

---

### Post by timmahhny on 2006-06-30
[QUOTE=Fenyx]To install/compile programs from source code, you need to install the build-essential package, which will install everything that you need to compile

You can find them easily in Synaptic, or if you want to use the command line

```
sudo aptitude update
sudo aptitude install build-essential
```

I recommend using aptitude instead of apt-get in this case, so that removing all the packages installed together with build-essential will be as easy as

```
sudo aptitude remove build-essential
```[/QUOTE]

I don't have it installed I guess and I don't have internet connection with that laptop yet. I will try to locate it and install it.
Thank you very much for your help
Tim

---

### Post by Jucato on 2006-06-30
*make clean* is a valid make command, as per the GNU Make Manual:
[http://www.gnu.org/software/make/manual/make.html#Simple-Makefile](http://www.gnu.org/software/make/manual/make.html#Simple-Makefile) and
[http://www.gnu.org/software/make/manual/make.html#Phony-Targets](http://www.gnu.org/software/make/manual/make.html#Phony-Targets)

Btw, you can install build-essential even without an internet connection, as long as you have the CD installer with you (Desktop CD or Alternate Install CD). Go to the command line, type in
```
sudo apt-cdrom add
```
and put in the CD when it asks for it. The CD will be added as a repository, and you can install build-essential from there.
Just remember to disable the cdrom repository after you're done.

---

### Post by timmahhny on 2006-06-30
[COLOR="DarkRed"]I will do that right now. I just down loaded those files but am getting error messages, so I will try the cd before I do anything else.
Thank you very much for the quick replies
Tim[/COLOR]



[QUOTE=Fenyx]*make clean* is a valid make command, as per the GNU Make Manual:
[http://www.gnu.org/software/make/manual/make.html#Simple-Makefile](http://www.gnu.org/software/make/manual/make.html#Simple-Makefile) and
[http://www.gnu.org/software/make/manual/make.html#Phony-Targets](http://www.gnu.org/software/make/manual/make.html#Phony-Targets)

Btw, you can install build-essential even without an internet connection, as long as you have the CD installer with you (Desktop CD or Alternate Install CD). Go to the command line, type in
```
sudo apt-cdrom add
```
and put in the CD when it asks for it. The CD will be added as a repository, and you can install build-essential from there.
Just remember to disable the cdrom repository after you're done.[/QUOTE]

---

### Post by timmahhny on 2006-06-30
[COLOR="DarkRed"]=D> Fenyx it worked thank you and the rest of the group who helped me out. I just hope that one day I can have the knowledge to help others in the same manner you shown to me.
Once again thanks to all.
Tim[/COLOR]


[QUOTE=Fenyx]*make clean* is a valid make command, as per the GNU Make Manual:
[http://www.gnu.org/software/make/manual/make.html#Simple-Makefile](http://www.gnu.org/software/make/manual/make.html#Simple-Makefile) and
[http://www.gnu.org/software/make/manual/make.html#Phony-Targets](http://www.gnu.org/software/make/manual/make.html#Phony-Targets)

Btw, you can install build-essential even without an internet connection, as long as you have the CD installer with you (Desktop CD or Alternate Install CD). Go to the command line, type in
```
sudo apt-cdrom add
```
and put in the CD when it asks for it. The CD will be added as a repository, and you can install build-essential from there.
Just remember to disable the cdrom repository after you're done.[/QUOTE]

---

### Post by timmahhny on 2006-06-30
**[COLOR="DarkRed"] How do you disable the cdrom repository?[/COLOR]**

[QUOTE=Fenyx][Just remember to disable the cdrom repository after you're done.[/QUOTE]

---

### Post by Jucato on 2006-06-30
You can either use Synaptic or the Software Properties from the System Menu to uncheck the cdrom repository. 

You could also manually edit /etc/apt/sources.list to delete the cdrom line (only that line)
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by timmahhny on 2006-06-30
Fenyx one more question at least for a few days.

 I am having problems with the USB Flash Drive disappearing on me and then I have to reboot in order to get it back.

 How do I use the command line to get into the flash drive? In a nut shell if you know, is there a way to make a link as in Mandriva 2006 to the flash drive? Or do I have to write a script for it?

Once again thank you for your help, I have learned a great deal over the last day from this forum. 

 Take care
Tim

---

### Post by Jucato on 2006-06-30
What do you mean it disappears?
I'm not really that familiar with USB drives, but AFAIK, when you plug in a USB drive, it's automatically detected and mounted. In Ubuntu, I think the "Places" menu on the panel or in Nautilus would have an entry for it. In Kubuntu, it would be in System > Storage Media menu on the panel (or type in media:/ in Konqueror).

You can also navigate to the mount point in the /media directory (you can do this both in the command line and in Nautilus/Konqueror). I think USB drives are usually mounted on /media/sdx (sda, sdb, etc).

I'm not really familiar with USB drives, though. You would probably get better answers if you made a new thread about this problem. But try using the Search feature of the forums. You might find an answer.

---

### Post by timmahhny on 2006-06-30
Fenyx; when I place the thumb drive, flash drive, USB drive, into the USB port and icon appears on the desktop and then opens up the drive. But, sometimes it will just disappear and I can't locate it,so I reboot. 
 I think it has to do with my mouse going haywire, which happens with the optic mouse that I was using. It has not happened yet using the mouse pad on the laptop.

 I am going to close out this thread because you all have answered my questions about the make command and I am searching these forums for the remaining problems (two that I am currently working on).
I figure I will give myself three or four days before I post for help. This way I will, I hope, learn more.
Take care and thanks once again for your great help.
Tim \\:D/

---

