---
title: "From WinXP to Ubuntu 7.10"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Nalroff on 2007-12-06
I'm a long time windows user/programmer, and I've just now gotten into the swing of things with linux. I'm really clueless on a lot and I need some help.

I'm dual booting Ubuntu and XP right now, and all works great.
Occasionally when I click on Pidgin or run it from the terminal, it won't come up.
Beryl is acting wierd (being moody), but I really don't understand the Linux file system. I'll do some reading on that.
I have a SeaGate external hard drive, and I have no idea how Linux does drivers/support for hardware. I also have a Canon PIXMA iP1600 that will install with the 2200 drivers, but not print.
I know this thing is more powerful than Windows (and it uses half the resources)
I know the DOS command prompt like the back of my hand, so any translations other than the basics (i got ls, mkdir, clear, pwd, etc) would be appreciated.

Thanks,
Nalroff

---

### Post by LaRoza on 2007-12-06
> **Nalroff said:**
> 
I know the DOS command prompt like the back of my hand, so any translations other than the basics (i got ls, mkdir, clear, pwd, etc) would be appreciated.


Welcome! You will find things very different, but hopefully better if you stick with it.

For the commands, you should know about "man", it will give you the manual for any command after it.

[http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

What other commands do you commonly use in Windows?

For deleting, "rm" is used.

For running as another user (root) use "sudo"

---

### Post by nrs on 2007-12-06
> **Nalroff said:**
> I'm a long time windows user/programmer, and I've just now gotten into the swing of things with linux. I'm really clueless on a lot and I need some help.

I'm dual booting Ubuntu and XP right now, and all works great.
Occasionally when I click on Pidgin or run it from the terminal, it won't come up.
Beryl is acting wierd (being moody), but I really don't understand the Linux file system. I'll do some reading on that.
I have a SeaGate external hard drive, and I have no idea how Linux does drivers/support for hardware. I also have a Canon PIXMA iP1600 that will install with the 2200 drivers, but not print.
I know this thing is more powerful than Windows (and it uses half the resources)
I know the DOS command prompt like the back of my hand, so any translations other than the basics (i got ls, mkdir, clear, pwd, etc) would be appreciated.

Thanks,
Nalroff

For *nix equivalents to cmd.exe commands / scripts you're really going to have to go on a case by  case basis. Sometimes there are equivalents, sometimes not. Usually it's Windows that's worse in that regard (doesn't even have an equivalent to lsof!) for a general list though: [http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html](http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html)

As for the filesystem: man hier

Need in know how Beryl is being moody in order to help. To see if Linux properly supports your drive you'll need to Google the model # along with something like "linux support" 
[http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html](http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html)

---

### Post by Nano Geek on 2007-12-06
> **Nalroff said:**
> I'm a long time windows user/programmer, and I've just now gotten into the swing of things with linux. I'm really clueless on a lot and I need some help.

I'm dual booting Ubuntu and XP right now, and all works great.
Occasionally when I click on Pidgin or run it from the terminal, it won't come up.
Beryl is acting wierd (being moody), but I really don't understand the Linux file system. I'll do some reading on that.
I have a SeaGate external hard drive, and I have no idea how Linux does drivers/support for hardware. I also have a Canon PIXMA iP1600 that will install with the 2200 drivers, but not print.
I know this thing is more powerful than Windows (and it uses half the resources)
I know the DOS command prompt like the back of my hand, so any translations other than the basics (i got ls, mkdir, clear, pwd, etc) would be appreciated.

Thanks,
NalroffHey, welcome to Ubuntu.

Problem with Pidgin: Can you copy and paste what Pidgin outputs in the terminal here? It may tell us what's going wrong.

Problem with Beryl: Are you sure you are using Beryl, or are you using what came with Ubuntu, because Beryl has been replaced by Compiz-Fusion.

Problem with HDD: If it's USB, then it should just be plug-and-play. If you still can't get it to work I'll cook up some more help.

Problem with Printer: Are you sure there weren't any drivers for you specific printer? If not then try to use whatever is closest. 

And for the terminal commands, [look at this site]("http://www.linuxdevcenter.com/linux/cmd/"). It's a list of 600 some odd Linux commands with descriptions.

And again, welcome to Ubuntu. ;)

---

### Post by Nalroff on 2007-12-06
> Need in know how Beryl is being moody in order to help.

I really appreciate it guys... man that was quick! Anywho, the Beryl thing is kinda trivial, I had it set to run at startup with Sessions, and it worked perfect for a long time. Then I went messing around with trying to install the JDK (Java Dev Kit) and reinstall Pidgin to get it working (I know I'm doing half this stuff wrong, lol) I altered the xorg.config slightly, if that might have anything to do with it because my Title bars (decorations?) were missing. It would "run" but no settings were recognized. When I entered "beryl" on the command line though, the desktop came up with all my settings. After just a few seconds, though, an "untitled window" block came up on my taskbar and the machine locked up. Any ideas?

Also, the USB HDD is detected, but how do I use it? I'm such a n00b, lol.

Cheers,
Nalroff

---

### Post by b3y0nd on 2007-12-06
Nalroff, i'm about a week ahead of you. Im a computer technician (or should I say Windows tech), and have recently started using Ubuntu in a duel boot config. I have used allot of the utility boot cds that are linux based, but even those are easy to use. 

Ubuntu, while simple in its own way, is something different. 

First off, I LOVE this OS. Gorgeous, powerful and fasst... at least when you get past the configuration kinks. Video seems to be the hardest hardware to config, for me and alot of other from what I have seen. I offer no real advice, per se, but everything (including printer) besides my ATI card works fine...hardware wise. So far I have lived with staying with a duel boot config and I switch back into XP for gaming and development..... ive spent hours trying to get my graphics worked out and i'm making progress... but oh too slowly.

Your not alone, I personally look forward to the day I can format Windows completely and be rid of the whole MS experience. 

Tip: If beryl is not behaving properly go into Beryl settings manager > General Options > DesktopBackground (right pane) and uncheck " Desktop Manage Supports Viewports" 

This helped clear up performance issues with beryl, now beryl works fine, but compiz and metacity still perform doggy. 

Your external drive will work fine, plug n play much like windows, but be sure to "eject" it           (in linux AND windows) so when done or it will fail to mount it upon reconnect. If you get that failure error view the details of the error and it will give you two option to try. 

Good luck and welcome to Ubuntu!



beyond

---

### Post by kpkeerthi on 2007-12-06
> 
Occasionally when I click on Pidgin or run it from the terminal, it won't come up.

You may want to launch pidgin from the terminal with -d option to print some debug messages. That should give some insight as to what is going on.
```
pidgin -d
```
------------
> 
Beryl is acting wierd (being moody), but I really don't understand the Linux file system. I'll do some reading on that.

Any specific reason why you are running beryl in Gutsy. Gutsy has compiz-fusion builtin which is better in terms of stability and performance. Also let us know about your hardware configuration.
------------
> 
I have a SeaGate external hard drive, and I have no idea how Linux does drivers/support for hardware. 

It is plug and play and you should see an icon on your desktop. If it is not mounting, let us know how it is formatted. Plug the USB drive and run the command
```

sudo fdisk -l

``` and let us know what it prints
------------
> 
I also have a Canon PIXMA iP1600 that will install with the 2200 drivers, but not print.

Sorry I cannot help you with that.
------------
> 
I know the DOS command prompt like the back of my hand, so any translations other than the basics (i got ls, mkdir, clear, pwd, etc) would be appreciated.

[www.linuxcommand.org](www.linuxcommand.org)

---

### Post by bob1668 on 2007-12-06
  Well guys I must tell you, im learning allot from these forums.  I have learned that, no matter what you do in linux, it can be fixed.  LOL.  A buddy of mine has been helping me by showing me around linux.  Plus all the reading of the posts seems to help a great deal.  Im starting to really love the reliability of this operating system.

Bob

---

### Post by TNakos on 2007-12-06
im sure they have drivers for what u are looking for.

---

### Post by Nalroff on 2007-12-06
i really appreciate it guys. I think I'm gonna format my HDD and start over so that I can have things not so screwed up with XP in the mix. I do have backup copies and I don't really play games that much (the ones I do have are old and apparently work with something called "WINE", still fuzzy on those details) so I think I'll be ok with openoffice.org and stuff. If this is unadviseable, plz let me know.

Cheers,
Nalroff

---

### Post by Nano Geek on 2007-12-06
Good for you. And [Wine]("http://en.wikipedia.org/wiki/Wine_%28software%29") is a program that will let you run some Windows apps in Linux, but it takes a little configuring to make it work.

---

### Post by Nalroff on 2007-12-06
ok, so i'm getting there. i formatted and reinstalled ubuntu without anything else. but i'm now trying to install this Compiz-Fusion thing. I installed the compiz files just fine (i think) but all the commands i'm finding to install the xgl (again, whatever that is) are coming up not found. To be exact the terminal output is
```
goob@myLaptop:~$ sudo apt-get install xserver-xgl
[sudo] password for goob:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl

```

Any help would again be appreciated. I apologize for my n00b1n355. :)

Cheers,
Nalroff

---

### Post by Nano Geek on 2007-12-08
When you installed Ubuntu, did you have an internet connection to the computer?

---

