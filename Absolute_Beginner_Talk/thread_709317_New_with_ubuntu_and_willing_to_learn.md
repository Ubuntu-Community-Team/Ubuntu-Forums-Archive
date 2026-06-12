---
title: "New with ubuntu and willing to learn"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by DarkRanger on 2008-02-27
Hi guys,

I'm new here, and I want basic help setting up ubuntu and getting it to work (I hate MS Vista) Anyhow, can you guys please let me know which programs is an absolute must in ubuntu and which programs are almost direct substitutes for windows apps.

I'm currently doing Java programming at the University of Pretoria (South Africa) and will need a good editor for that (currently using BlueJ).  I also use Scintilla Text Editor and adobe design suite premium.  So good alternatives for these is what I want! :-D

Then another thing, whenever I switch my pc on, GRUB bootloader loads, and when I select the first option for ubuntu (not the recovery or memtest options) ubuntu DOESNT boot? What can cause this?  I have to go into recovery mode, and type exit and THEN it loads ubuntu.   Is there any fix for this?

Also, how do I install newer drivers?

Thanks guys!! Looking forward to all the help! :-D

DarkRanger

---

### Post by SOULRiDER on 2008-02-27
> **DarkRanger said:**
> Hi guys,

I'm new here, and I want basic help setting up ubuntu and getting it to work (I hate MS Vista) Anyhow, can you guys please let me know which programs is an absolute must in ubuntu and which programs are almost direct substitutes for windows apps.

I'm currently doing Java programming at the University of Pretoria (South Africa) and will need a good editor for that (currently using BlueJ).  I also use Scintilla Text Editor and adobe design suite premium.  So good alternatives for these is what I want! :-D

Then another thing, whenever I switch my pc on, GRUB bootloader loads, and when I select the first option for ubuntu (not the recovery or memtest options) ubuntu DOESNT boot? What can cause this?  I have to go into recovery mode, and type exit and THEN it loads ubuntu.   Is there any fix for this?

Also, how do I install newer drivers?

Thanks guys!! Looking forward to all the help! :-D

DarkRanger

1) I like Eclipse for Java development, I use an eclipse distribution called EasyEclipse, just download, umpack and youre ready to go. [http://easyeclipse.org](http://easyeclipse.org)

2) Havnt used that editor so I dont know any alternatives to offer.

3) Im not into design so i cant help you much, but GIMP works as a replacement for Photoshop and Inkscape for Illustrator.

4) Not sure about your booting problem.

5) Drivers and software will be automagically updated for you, you dont need to do anything.

---

### Post by Therion on 2008-02-27
> **DarkRanger said:**
> 
... can you guys please let me know which programs is an absolute must in ubuntu and which programs are almost direct substitutes for windows apps.

[Linux alternatives](http://www.linuxalt.com/) to Windows apps.

GRUB is not my area of expertise, so I'll pass on trying to help you with that.

> Also, how do I install newer drivers?

Well there's the Restricted Driver Manager located in System/Administration or you can use [Envy](http://albertomilone.com/nvidia_scripts1.html) if you have a graphics solution from nVidia or ATI.  But really, if the driver ain't broke, I wouldn't go fixing it.

---

### Post by DarkRanger on 2008-02-27
Hi SOULRiDER,

Thanks for the alternatives.  Problem is, I download my drivers and software from work as I do not have ADSL at home and basicaly come running on home with the install files.  Like for instance, I downloaded the nvidia drivers, new ones, and don't have ANY clue on how to install it.

O, another thing, compiz, how do I get that working (got Ubuntu 7.10) :D

---

### Post by DarkRanger on 2008-02-27
Thanks Therion.  Gonna download the Envy thingy now.

---

### Post by SOULRiDER on 2008-02-27
> **DarkRanger said:**
> Hi SOULRiDER,

Thanks for the alternatives.  Problem is, I download my drivers and software from work as I do not have ADSL at home and basicaly come running on home with the install files.  Like for instance, I downloaded the nvidia drivers, new ones, and don't have ANY clue on how to install it.

O, another thing, compiz, how do I get that working (got Ubuntu 7.10) :D

If you have enough RAM at work, you could use APTonCD to carry packages home and be able to install them easily. Check out APTonCD here:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

And just in case, check this out, its something very important when you decide to migrate.
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by bbqsandwich on 2008-02-27
> **DarkRanger said:**
> O, another thing, compiz, how do I get that working (got Ubuntu 7.10) :D

Go to Add/remove programs

Under Preferences, enable all of the repository sources, including "partner" (though you probably don't need the "source" one)

Search for "compiz"

Install the compiz config settings manager

& then your compiz control panel will be in your settings menu, along with Appearance and all the other goodies... it's called Advanced Desktop Effects or Advanced Desktop Settings

In my opinon, compiz has good stuff and some flashy-but-impractical stuff... I love Expo and Enhanced Zoom Desktop. The cube is the compiz feature most often featured when people are showing off but I never use it for actual work :P

---

### Post by DarkRanger on 2008-02-28
Hi guys,

I'm still strugling with my GRUB bootloader.  Anybody have any idea on how to fix it?

---

### Post by PmDematagoda on 2008-02-28
Boot Ubuntu in Recovery Mode and post the output of:-
```
cat /boot/grub/menu.lst
```

---

### Post by hyper_ch on 2008-02-28
does anything appear on the screen when the bootloader fails

---

### Post by DarkRanger on 2008-02-29
Nothing apears on the screen hyper_ch.  It says kernel loaded and then kernel alive, and then goes black.  If I boot in recovery mode, it runs through all the commands and then waits for user input.  If I type exit, it loads into ubuntu then.

---

### Post by bmfgeorgin2 on 2008-02-29
I am like this to

---

