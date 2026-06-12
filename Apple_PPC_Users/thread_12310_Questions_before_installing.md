---
title: "Questions before installing"
date: 2005-01-23
forum: Apple PPC Users
---

### Post by jjramsey on 2005-01-23
I've been thinking of installing Ubuntu on my eMac. I have a fair amount of Linux experience--but only on x86, so I do have some questions about what I can expect on a Mac.

[list=1]
[*]How do I avoid display problems? I noticed that [this guy](http://krussell.com/mini/2005/01/display-issues.html) had some issues. I also notice that I don't have information on the horizontal and vertical sync rate ranges for the CRT of my eMac. What should I watch out for? What steps can I take to make sure I get it right?

[*]Should I expect USB printing problems?

[*]Can I put my eMac to sleep under Linux the way I can in OS X?

[*]Will the CD burner work?

[*]Does anyone have any experience with MOL? How fast does it run? How do I point it to an OS X installation? (The docs seem a bit fuzzy on that point.) 

[*]When I install Ubuntu Linux, can I get it to do a text login at startup instead of a graphical one? (I have a Wacom tablet, and I'd like to install Ubuntu, set up X for the Wacom, and *then* start up X.)
[/list]

---

### Post by Viro on 2005-01-23
2. You won't have problems printing. My printers work fine. You might want to install the cupsys-driver-gimpprint to use the gimp-print drivers which are far superior to the standard drivers that ship with Ubuntu.

3. No, sleep support on Linux is very poor at the moment and doesn't look like it's going to change. You might be able to get sleep working eventually, but it's something I wouldn't hold my breath for.

4. Yes, out of the box with no modifications.

No idea about the rest of your questions, so you'll need someone who has more experience to come by.

---

### Post by DJ_Max on 2005-01-23
1.)He had the new Mac mini, you have an eMac. The Ubuntu installer *should* detect everything fine.

5.)I used MOL when I was using YellowDog, but didn't use it much. I believe it reads your yaboot.conf, which is setup by the Ubuntu installer.

6.)I'm not booted up in Linux right now, but there's a file somewhere you can edit /etc/inittab (I think) And you would change the run level. There's commented lines to help at the top. You might have to find that file.

---

### Post by jjramsey on 2005-01-23
[QUOTE=DJ_Max]
5.)I used MOL when I was using YellowDog, but didn't use it much. I believe it reads your yaboot.conf, which is setup by the Ubuntu installer.
[/QUOTE]

So, to use MOL, I'd need to set up a dual boot between Ubuntu and OS X?

> 
6.)I'm not booted up in Linux right now, but there's a file somewhere you can edit /etc/inittab (I think) And you would change the run level.


That much I knew. What I was trying to ask was whether during installation I could tell the Ubuntu installer *not* to run X at startup. (I'd rather not start X until I'd configured it for the Wacom.)

---

### Post by DJ_Max on 2005-01-23
> So, to use MOL, I'd need to set up a dual boot between Ubuntu and OS X? 
Yeah, because MOL is just a program to use Mac OS X while still booted in Linux, so you'd need to have OS X installed on the same machine.

> That much I knew. What I was trying to ask was whether during installation I could tell the Ubuntu installer not to run X at startup. (I'd rather not start X until I'd configured it for the Wacom.) 
oh, I forgot if there's was a choice to do that in the installer. :oops:

---

### Post by Viro on 2005-01-23
Couldn't you manually edit the XF86Config-4 file yourself? Just make a note of what your current XF86Config is like and copy the entry for the Wacom tablet over.

---

### Post by jjramsey on 2005-01-23
[QUOTE=DJ_Max]Yeah, because MOL is just a program to use Mac OS X while still booted in Linux, so you'd need to have OS X installed on the same machine.
[/QUOTE]

I had thought maybe that MOL was in one way like vmWare, where one essentially installed Windows on top of a "phony" virtual machine. Shows what I know.

---

### Post by jjramsey on 2005-01-23
[QUOTE=Viro]Couldn't you manually edit the XF86Config-4 file yourself? Just make a note of what your current XF86Config is like and copy the entry for the Wacom tablet over.[/QUOTE]

Well, that *is* the plan. Let the installer configure X the way it usually would, but *not* let X run at startup. Then I'd make my changes to XF86Config-4 and *then* start X. Basically, I'd rather that X not start until I get it configured the way I want it.

---

### Post by DJ_Max on 2005-01-23
[QUOTE=jjramsey]I had thought maybe that MOL was in one way like vmWare, where one essentially installed Windows on top of a "phony" virtual machine. Shows what I know.[/QUOTE]
heh, as per their site,
> MOL is a "virtual" machine. Theoretically, MOL allows you to boot any (PowerPC) OS within MOL (what is more or less specific to the OS is the boot-loader and a set of custom device drivers interfacing the "virtual" hardware of MOL). 
[http://www.maconlinux.org/userguide/index.html](http://www.maconlinux.org/userguide/index.html)

Hope that helps.

---

### Post by jjramsey on 2005-01-27
[QUOTE=DJ_Max]1.)He had the new Mac mini, you have an eMac. The Ubuntu installer *should* detect everything fine.[/QUOTE]

Judging from [this thread](http://www.ubuntuforums.org/showthread.php?t=924), maybe not.  :(

---

