---
title: "Changing Ubuntu versions"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by sonyack on 2005-09-20
I think I should take the advice someone at the forum suggested to me and replace the 5.10 with 5.04.  Things don't seem to be working well with this 5.10.  By that I mean the stuff that should just go ahead and work.  One example is the time.  It never runs correctly and I have to sync everytime I log on, so I tried checking the button for periodically updating the time and got a dialog for installing ntp thingy and so I said sure, go ahead, and a progress bar came up and then it said finished and yet nothing changed, so when I clicked the button again, another dialog box came up and wanted to install the time checking gizmo again....another is that I copied some files off a cd-r so I would have them in Ubuntu for checking sound and video players and this little folder in home is locked.  Totem won't play them, Beep will play the mp3 file, but only if I access it through the Beep interface....my thought is that I would be better off not having to deal with little glitches in a beta version and use a more tried and true version to learn this stuff.

But I wonder how to ditch 5.10 and install 5.04 and if I do that, would I lose the boot set-up, i.e., will what is on the hda MBR still boot 5.04 or will I have grief over a new grub in the MBR, etc.  I should mention that 5.10 is entirely on my secondary drive, where I would want any replacement.

---

### Post by LucasLinard on 2005-09-20
Hi!
I really can't understand waht you're saying. Sorry.
One thing came to my mind about the files you copied from a cd-rom. try to right click on them and chosse something like properties, and then look for permissions. and choose the right permissions you want.
Hope this can help.
 :???:

---

### Post by Kapre on 2005-09-20
[QUOTE=sonyack]IBut I wonder how to ditch 5.10 and install 5.04 and if I do that, would I lose the boot set-up, i.e., will what is on the hda MBR still boot 5.04 or will I have grief over a new grub in the MBR, etc.  I should mention that 5.10 is entirely on my secondary drive, where I would want any replacement.[/QUOTE]

sonyack - If you want to ditch 5.10 for 5.04, just install over it. Meaning when your installing 5.04, make sure to select/choose the partition where 5.10 was previously installed. Then go with process. With regards to installing GRUB, are you dual booting with another OS or Distro? If you are, during the GRUB install (of 5.04) it will detect whatever OS is installed so I think it wouldn't be a problem.

K

---

### Post by sonyack on 2005-09-20
Yep, I had tried that, but the property sheet says the same as the .jpg  files I copied from a floppy, everything looks normal.

Well, I would like to get rid of 5.10 and replace it with 5.04.  Ubuntu is entirely on my secondary [slave] drive.  Upon installation, ubuntu put grub on my primary [master] drive, where XP is installed, so I would have a choice of os's upon restart/startup.  I need to know therefor:
1]  How to get rid of 5.10
2]  If I get rid of 5.10, will this grub [which stays on the primary drive] work with the ubuntu version 5.04 that I want to put on the slave drive?

Because, if I just format the 2ndary drive, then grub, on the drive with XP, will "detect" another os and yet it won't boot because it won't be there and I will not be able to boot XP either.  So I will have to put 5.10 back on the 2ndary drive, unless this same grub will detect 5.04 instead of 5.10.  I guess I need to know if the grub that is installed with 5.10 is the same grub that would be installed with 5.04.

I don't think 5.04 can be installed over 5.10, are you sure?

p.s. I rechecked the properties/permissions tab and saw that "write" was not checked and I had to go through right clicking the folder and then each of the files in it to change them to include 'write' and NOW they will move etc.  But they still won't play in Totem and still won't open in Beep unless I access them through Beep.

---

