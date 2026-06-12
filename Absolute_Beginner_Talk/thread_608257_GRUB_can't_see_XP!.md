---
title: "GRUB can't see XP!"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Bionic Apple on 2007-11-09
I installed Ubuntu Gutsy on my computer a week ago on my secondary hard-drive (80gigs). My primary hard-drive (160gigs) has Windows XP on it.  GRUB was working great.  It saw both OS's.  Then I reinstalled Ubuntu.  Nothing bad happened.  But, unfortunately I reinstalled it a third time.  Now GRUB can't see Windows XP in the menu!  How would I fix it?

---

### Post by MQMike on 2007-11-09
Sounds like you need a boot entry for Windows in your GRUB menu.

In Ubuntu, access /boot/grub/.
Open menu.lst as root (Right-click, Actions > Edit as Root).
Do you have a boot entry there for Windows XP that looks like this:

title Windows XP or something like this
rootnoverify  (hd0,0)
chainloader  +1

(It might say just root (hd0,0).)

You need such a boot entry in that menu.lst -- you can put it at the end for now, aftter *** End Automagic kernel list.  Note the space after rootnoverify; and the space after chainloader.

Then File > Save, File > Quit.

---

### Post by Bionic Apple on 2007-11-09
I don't get that Edit as Root option in my right-click menu.

---

### Post by PmDematagoda on 2007-11-09
You can do:-
```

sudo gedit /boot/grub/menu.lst

```
to edit the file in root mode.

---

### Post by Maestro23 on 2007-11-09
> **Bionic Apple said:**
> I don't get that Edit as Root option in my right-click menu.

Open a terminal:

> gksudo gedit /boot/grub/menu.lst

---

### Post by Bionic Apple on 2007-11-09
Ok, I put this in after the last line...

title                   Windows XP
rootnoverify       (hd0,0)
chainloader        +1

and I got a Dell Hardware Diagnostics menu (which looks like a live CD) that popped up when trying to boot it.  So, I don't even think it got to the hard-drive.  However, I did use tabs instead of spaces between "title" and "Windows XP" and etc.  I don't think that matters though because the Ubuntu entries had tabs instead of spaces.

---

### Post by osxcapades on 2007-11-09
Try

```
sudo update-grub
```

---

### Post by Bionic Apple on 2007-11-09
> **osxcapades said:**
> Try

```
sudo update-grub
```

Doesn't work.

---

### Post by MQMike on 2007-11-09
I've heard of cases where Windows was put not on (hd0,0) but on (hd0,1).
Where (hd0,0) was reserved for some system/recovery stuff; perhaps Dell did this, too.

Try (hd0,1).

EDIT:  Remember to File > Save and File > Quit when done editing.

---

### Post by Bionic Apple on 2007-11-09
> **MQMike said:**
> I've heard of cases where Windows was put not on (hd0,0) but on (hd0,1).
Where (hd0,0) was reserved for some system/recovery stuff; perhaps Dell did this, too.

Try (hd0,1).

EDIT:  Remember to File > Save and File > Quit when done editing.

You fixed it, Thanks!  However, because I don't want to make another thread above this (I hate spamming), I have one unrelated question.  There is a green pixel on my booting screen for Ubuntu (the one with the orange bar) and I was just wondering if that is fixable since I have an LCD monitor.  If you don't want to bother with it, I understand.

---

### Post by MQMike on 2007-11-09
Hey Bionic -- sorry -- the pixel-graphical thingy is not my specialty .
Glad you got XP booted, though.
Someone will chine in and help with the colors.
:)

---

### Post by Bionic Apple on 2007-11-09
Oh wait, I forgot something!  How would I make it so GRUB skips the 5 second thing.  It used to go straight into the menu, but now it gives me 5 seconds to press escape to go to the menu.  If that is impossible, then I will settle for increasing the wait time.

---

### Post by MQMike on 2007-11-10
You can change the "timeout" and the "default" operating system (that boots if you don't intervene), easily, again by editing menu.lst as root:

timeout = ???     # whatever you wish, in seconds
default = ???

"default" is some integer, 0, 1, 2, 3, etc. that specifies the operating system that will boot if you don't touch any key.  The counting starts at zero.  And you count each line that starts with the word "title" (without any comment sign #).
In your menu.lst, you can move boot entries around, just as you placed Windows where you wanted it, BUT DO NOT mess with any OSs that are between the line *** Begin Automagic kernels list and the line *** End Automagic kernels list. (Not for now, anyway, until you get the hang of this game.)  And do not place any OS between those two lines (just leave your main Ubuntu and others where they are between those two lines).  

For now, then, you can put other OSs either before the line *** Begin Automagic or after the line *** End Automagic.

Here's my How-To (at Kubuntu) on these things:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(Scroll down through the posts for various topics, especially the first Reply; please post any questions you have elsewhere, in the forums, here or under "Installation & Booting" categories.))

Here's Herman's, which is a standard reference now in Linux circles:
Bigpond, home:   [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
See the GRUB page etc.

Note:  herman's is written for Ubuntu.
Mine is written for Kubuntu.
But both apply to both and to many other distros.
But there are trivial differences, like you used gksudo gedit /boot/grub/menu.lst in Ubuntu.  In Kubuntu, you would use kdesu kate /boot/grub/menu.lst.  There are only just a very few of these at the beginner's level that are different, so not to worry!  And there's plenty of help here.

I'll leave you with two more classic references for Ubuntu/Linux, along with the bigpond link, about almost every subject for beginners, and tuxfiles is a great place to start for command-line basic, mounting, permission, etc., and psychocats has a full index of topics, including dual booting:

Tuxfiles:   [http://www.tuxfiles.org/](http://www.tuxfiles.org/)
Psychocats:   [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

