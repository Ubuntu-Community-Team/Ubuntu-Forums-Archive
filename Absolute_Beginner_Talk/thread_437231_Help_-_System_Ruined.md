---
title: "Help - System Ruined?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by RageRhinos on 2007-05-08
OK so i installed Ubuntu for the first time today.  All was working perfectly.  Then i decided to go and try to instal Beryl.  Apparently that was a mistake.

I installed and then when nothing really happened, i went online and found some "code" script for installing, that i ran.  Not even sure what it was at this point.

Still nothing was happening.  I couldnt even find the "Beryl Manager" anywhere....just the settings manager.  so i decided to go into the "prompt" or whatever its called and typed in "Beryl Manager" some script ran through, my desktop background changed color and that was about it.  i closed the "Prompt" thing and then the desktop went back to its normal color, but now when i open anything it is stuck in the top left hand corner and has no title bar.  i don't know what to do.

how do i restore ubuntu or how to i reinstall.  please help!  :(

---

### Post by moredhel on 2007-05-08
have you tried restarting first?

---

### Post by RageRhinos on 2007-05-08
no, will do now.

---

### Post by RageRhinos on 2007-05-08
ok restarted...and "seems" to be working properly.

still dont understand how to get the beryl thing to work.  ive tried looking at things ive found on google, but has just confused me.

any help on this or should i just uninstall until i become more familiar with the system.

---

### Post by moredhel on 2007-05-08
first, is open gl working ok?

type glxgears into terminal to see.

also, what graphcis card manufacturer are you on?

---

### Post by mtgrocks04 on 2007-05-08
Presuming that you have it all set up correctly then you should be able to run beryl-manager from terminal. also it could be found in the system menu. After running it a small red gem icon should appear in your system bar. Right click on it and select Beryl as your window manager. Hope this helps

---

### Post by H.E. Pennypacker on 2007-05-08
The best resource for Beryl questions is the Bery website.  Please see their forums at:

[http://forum.beryl-project.org/](http://forum.beryl-project.org/)

---

### Post by RageRhinos on 2007-05-08
> **moredhel said:**
> first, is open gl working ok?

type glxgears into terminal to see.

also, what graphcis card manufacturer are you on?

Yes Gears Worked.

No idea on graphics card.  how do i find out?

im on a toshiba laptop Satelite

---

### Post by RageRhinos on 2007-05-08
> **mtgrocks04 said:**
> Presuming that you have it all set up correctly then you should be able to run beryl-manager from terminal. also it could be found in the system menu. After running it a small red gem icon should appear in your system bar. Right click on it and select Beryl as your window manager. Hope this helps

shaun@shaun-laptop:~$ beryl-manager
The program 'beryl-manager' is currently not installed.  You can install it by typing:
sudo apt-get install beryl-manager
Make sure you have the 'universe' component enabled
bash: beryl-manager: command not found
shaun@shaun-laptop:~$ 


that is what i got.  but weird considering i know i installed beryl.  also i have this....

Applications>System Tools>Beryl Settings Manager

And it opens fine......

---

### Post by RageRhinos on 2007-05-08
i understand beryl is off limits here.

can someone just tell me how to determine my graphics card?

---

### Post by k1001001 on 2007-05-08
Go to the terminal and type lspci. Your graphics card/adapter should be one of the last things listed.

---

### Post by floke on 2007-05-08
You might also need to manually edit your /etc/X11/xorg.conf file - do as was suggested earlier and check out the beryl project website for the installation method suitable for your card and distro.

Good luck.

** EDIT ** Don't forget to back it up first! From the terminal type: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
Simply reverse to restore it - ie sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by mtgrocks04 on 2007-05-08
beryl and beryl manager are not the same thing. In the stickies on Absolute beginner talk there is a page about beryl with a howto linked in it. I used that several times on a few different computers and have not had a problem. Also you may need to install emerald themes...try using the how-to:
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

in the part about adding the repos switch edgy to whatever distro you are using...ie. feisty main or dapper main or edgy main...or whatever it may be. This should work. If you run it from the menu and it opens the little red gem in the task bar, right click it and select window manager as beryl.

hope this helps.

---

### Post by psyopper on 2007-05-08
Open the terminal (the promt thingy...) and type:

```
lspci
```

Post the results here and someone will be able to help you out.

For instance I have this as my VGA entry:

```
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

```

---

### Post by t2000kw on 2007-05-08
> **mtgrocks04 said:**
> Presuming that you have it all set up correctly then you should be able to run beryl-manager from terminal. also it could be found in the system menu. After running it a small red gem icon should appear in your system bar. Right click on it and select Beryl as your window manager. Hope this helps

I also am new to Linux (sort of--dabbled a bit a few years ago when you had to hack XFree86 to get it to work with an LCD laptop screen), and I would like to know if you can have multiple GUI's available, switching between them to see what they have to offer.

If you can, where would you change from one to the other?

---

### Post by floke on 2007-05-09
Yes its easy. Just install them -eg KDE, Enlightenment etc. and select the one you want from the login screen.

---

### Post by t2000kw on 2007-05-10
Sounds pretty simple.

---

