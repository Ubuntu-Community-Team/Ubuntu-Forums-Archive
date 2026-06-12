---
title: "Ubuntu install problem (dual boot)"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Synkboy on 2008-04-16
hi guys, after performing a dual boot on my own machine one of my friends was impressed enough to ask me to do the same for him.

I am having a slight problem, I tried a conventional install from the live CD, but it only went so far then stopped, with four lines of text at the top of the page.

So I tried doing it using the safe graphics mode, and the live cd has loaded up(I'm posting this message using it in fact), but when I try and install I get as far as the keyboard locale interface (3 of 7), then it says "loading partitioner", but it never loads.

Could anyone give me a method to troubleshoot this please?, or has anyone else expereienced similar difficulties with the same thing and found a solution?

Would appreciate any help with this.

---

### Post by Mark_in_Hollywood on 2008-04-16
Please use a google keyword search for the brand name of the computer and model number an gutsy and hcl. 

hcl = hardware compatibility list

If your pal's computer is home built, try:

[http://www.linuxquestions.org/hcl/](http://www.linuxquestions.org/hcl/)

If your pal is running a Microsoft OS  on his system have you defragmented?

---

### Post by bumanie on 2008-04-16
I would be tempted to try the alternate cd on your friends computer. It is not always the case, but very often there is some hardware conflict that stops the live cd operating properly and the alternate cd often works as it is text based.

---

### Post by john91 on 2008-04-16
I'm going to echo bumanie's suggestion.  The live cd didn't work on my computer or my friends, but the alternate worked perfectly on both :D

---

### Post by forrestcupp on 2008-04-16
Definitely try the alternate CD with text based installation.  But keep in mind that if you had hardware conflicts with the LiveCD, you may have to deal with them after a successful alternate installation.  But it's a lot easier to fix these problems with an installed Ubuntu than it is a Live CD.

---

### Post by thiebaude on 2008-04-16
I thought you would have to install ubuntu first then Windows?

---

### Post by Synkboy on 2008-04-16
Ok, had a brainwave and disconnected his slave drive, and amazingly it worked first time, thought it might have been conflicting with the partitioner, and it must have been.

Thanks for the input folks!

---

### Post by forrestcupp on 2008-04-16
> **thiebaude said:**
> I thought you would have to install ubuntu first then Windows?

If you do that, the Windows boot loader will overwrite grub.  If you can, it's less of a hassle to install Windows first, then Ubuntu.

---

### Post by zipperback on 2008-04-16
Please provide us with the detailed hardware specifications of your friends computer, also please be sure to do a media check on the media that you are trying to install from. When you boot the cd, select the menu option to verify the media.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-04-16
The following post has links to multiboot tutorials.
[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)

Those may be of some use to you as well.

- zipperback
:popcorn:

---

### Post by Oldsoldier2003 on 2008-04-16
> **john91 said:**
> I'm going to echo bumanie's suggestion.  The live cd didn't work on my computer or my friends, but the alternate worked perfectly on both :D

The alternate cd is always my choice for installations. The live cds are great for trying out Ubuntu without installing it, but the "alternate" cd is the real installer. call me old school but I think that the live cd is junk for installing...

---

