---
title: "Watchtower Library 2006 Fiesty"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by metaphor- on 2007-04-19
Can anyone walk me through an install of watchtower library 2006 for feisty?

I did the wine install from the page, using the fix for the 64 bit version....but i just cant figure this out.

Thanks in advance.

---

### Post by metaphor- on 2007-04-20
I have this problem solved thanks to the help of a friend of mine, if anyone needs instructions just post here.

---

### Post by ubuntu27 on 2007-04-20
> **metaphor- said:**
> I have this problem solved thanks to the help of a friend of mine, if anyone needs instructions just post here.

Good! :)

How about posting how did you solve? 

We could use it as a future reference ;)

---

### Post by metaphor- on 2007-04-20
assuming that you have wine installed, you have to go into your media directory ( cd /media/cdrom) then run " wine setup".  Do the hard disk install. 

you have to go to the wine regedit  and add the MEPSCommon directory (full path) to the system path in the registry.

Run "wine regedit" and open this key : [HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager\Environment]  Change "Path" to"c:\windows\system32;c:\windows" to"c:\windows\system32;c:\windows;c:\Program Files\Watchtower\MEPSCommon"("Program Files" maybe has another name in your language), 

the file system for wine is ~/.wine/drive_c

you have to go into the directory which contains wtlib.exe, which is

~/.wine/drive_c/program files/watchtower/watchtower library 2006/e/wtlib.exe

run " wine wtlib.exe" and it should work, it would be helpful to create a shortcut to this so go into system preferences, main menu. Then go click add. Bring up the command line, ctrl+l, and put in the command line  : wine "~/.wine/drive_c/Program Files/Watchtower/Watchtower Library 2006/e/wtlib.exe"

It should work, happy studying!

---

### Post by ubuntu27 on 2007-04-20
Awesome. :)

---

### Post by mainephotonut on 2007-04-21
> **metaphor- said:**
> assuming that you have wine installed, you have to go into your media directory ( cd /media/cdrom) then run " wine setup".  Do the hard disk install. 

you have to go to the wine regedit  and add the MEPSCommon directory (full path) to the system path in the registry.

Run "wine regedit" and open this key : [HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager\Environment]  Change "Path" to"c:\windows\system32;c:\windows" to"c:\windows\system32;c:\windows;c:\Program Files\Watchtower\MEPSCommon"("Program Files" maybe has another name in your language), 

the file system for wine is ~/.wine/drive_c

you have to go into the directory which contains wtlib.exe, which is

~/.wine/drive_c/program files/watchtower/watchtower library 2006/e/wtlib.exe

run " wine wtlib.exe" and it should work, it would be helpful to create a shortcut to this so go into system preferences, main menu. Then go click add. Bring up the command line, ctrl+l, and put in the command line  : wine "~/.wine/drive_c/Program Files/Watchtower/Watchtower Library 2006/e/wtlib.exe"

It should work, happy studying!
Perhaps a silly question, but when you installed the WT Cd-Rom, did it work OK? The only reason I ask is because I have tried to use the WT CD on numerous other Linux distros, only to have it work only partially. I.E. can do a general search, but cannot jump down into different books and search those independtly. Having the WT CD work completely is the only thing holding me back from switch over to Linux entirely. 

**Thanks** 

Kevin, 
Maine USA

---

### Post by metaphor- on 2007-04-21
> **mainephotonut said:**
> Perhaps a silly question, but when you installed the WT Cd-Rom, did it work OK? The only reason I ask is because I have tried to use the WT CD on numerous other Linux distros, only to have it work only partially. I.E. can do a general search, but cannot jump down into different books and search those independtly. Having the WT CD work completely is the only thing holding me back from switch over to Linux entirely. 


sadly there are still a few bugs in watchtower. Some of the searches lag and a few of the bars don't work correctly. There is a way around it if you know the program, but if you plan on using each feature i recommend windows for wtlib until its fixed.

---

### Post by Baikonur on 2007-06-06
Do the tooltips work in the English version, in the Finnish version I use, they show as blank. I find them very handy, so it would be nice to get them working. I wonder if it's because I don't have the correct font, of if it's something more complex altogether.

Edit: Oh yeah and thanks for the regedit tip!

---

### Post by metaphor- on 2007-06-07
do your tooltips work if you click where they are supposed to be?

---

### Post by Baikonur on 2007-06-07
No, I see the little yellow box where the tooltip should be, but it's size is only one space, and it's empty. And otherwise they work as tooltips by definition do, ie. they dissappear when I move or click the mouse.

---

### Post by mat_n_mel on 2007-09-18
Thanks guys,
I switched to Ubuntu (Edubuntu) 6 months ago and this was the one hitch that was gonna make me have to switch back to Windows. Hopefully the 07 will be easier. It would be nice if , since we ARE international, They would have a Linux version so people can get an opensource OS and not have to fork over $200 bucks to MS.:)

---

