---
title: "video mode not sipported"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-07-08
Hi all!Apologies first. This is not a Ubuntu question.I have Ubuntu /XP/Suse10.1 as dual boot.Both Ubuntu /XP have no problem with video mode.Suse however gets through the boot sequence upto the 1st logo screen, tries to go further but then displays a dialogue box stating 'video mode not supported'. Question!would this be a graphics card problem? The card is about 4 years old. ATI Radeon7000/RadeonVE.
I cannot post at present on the Suse forum.
Thanks for any help
Regards:)

---

### Post by taurus on 2006-07-08
It's more likely you have misconfigured something (video mode) in /etc/X11/xorg.conf!  the easiest thing to do is to compare /etc/X11/xorg.conf from Ubuntu with your /etc/X11/xorg.conf in SUSE...

---

### Post by Sbarton on 2006-07-08
Thanks taurus for your input. In reality I did not have to configure anything when installing Suse, everything was automatic just as ubuntu did..
I cannot get a terminal up in suse as I can't get passed the 1st sceen.
Regards:)

---

### Post by Sbarton on 2006-07-08
Any other suggestions anyone. Or, is it a mistake to install Suse 10.1 with my graphics card?
Regards:)

---

### Post by taurus on 2006-07-08
If X doesn't work with SUSE, you can still get into a console by pressing <Ctrl><Alt>F2!

---

### Post by DSn0wMan on 2006-07-08
Try CTRL+ALT+f1 to get to a non-graphical login. You can configure from there.

I use this when my xserver gets hangs.

edit: taurus you beat my ba a second or two. CTRL+ALT+F2 should work too.

---

### Post by catlett on 2006-07-08
Can you boot into ubuntu? Just edit the suse configuration file from ubuntu.
First can you get in Ubuntu?
If yes, did ubuntu recognise and mount suse's partition?
If not, do you know how to mount partitions?

---

### Post by Sbarton on 2006-07-09
> **catlett said:**
> Can you boot into ubuntu? Just edit the suse configuration file from ubuntu.
First can you get in Ubuntu?
If yes, did ubuntu recognise and mount suse's partition?
If not, do you know how to mount partitions?

Firstly,apologies for not replying sooner, some problems.Secondly thanks to everyone who replied.
catlett- yes I can boot into Ubuntu.I am not sure whether Ubuntu has recognised and mounted suse. Sorry I am not to familiar with mounting drives (not enough practice:oops: ). One thing is that Suse boots into screen to select OS, this has suse-ubuntu-windows-mepis(no longer on drive)
Selecting ubuntu or windows works fine.When selecting suseit progresses to the next blue screen with suse logo and then goes black with the 'video mode not supported ' box.
Edit: see menu list attachment

---

### Post by bigken on 2006-07-09
boot suse in safe mode and run sax2 reconfigure your graphics ;)

---

### Post by Sbarton on 2006-07-10
> **bigken said:**
> boot suse in safe mode and run sax2 reconfigure your graphics ;)

bigken, suse does have a failsafe option (safe mode I guess).As for your other suggestion to run sax2 and reconfigure graphics, I have'nt a clue how to do this! Can you enlighten me?
Regards:) 
sbarton

---

### Post by Sbarton on 2006-07-10
> **bigken said:**
> boot suse in safe mode and run sax2 reconfigure your graphics ;)

Update, Solved. I found out how to run sax2 then made adjustment to settings a number of times until it worked.
Many thanks to all who responded with suggestions.
Have now tried 3 linux distros and without doubt the best experience and least problems for me has been Ubuntu.
Thank you
Regards
sbarton

---

### Post by bigken on 2006-07-10
Pleased to hear you got it sorted ;)

---

