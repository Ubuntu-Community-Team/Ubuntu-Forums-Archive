---
title: "OS Image Cloning"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Rich78 on 2007-10-31
Hi,

I was just wondering if I had a particular linux based operating system installed on a machine from new, before I installed anything else would it be possible to clone the image on the disc and keep it as an install disc.

The problem is I'm considering getting a machine which only comes with a Chinese install disc but the installed OS would be in English.

Would it be possible to clone it and use it as an installation disk?

Also is it possible to clone it to a drive other than the local drive?

Thanks

---

### Post by Obfuscater on 2007-10-31
I am in no way an experienced user, but logically if you were to clone the hard disc as an image burned onto a disc the disc, even if it were bootable, would only work for that machine since the install configures itself based on what hardware you have.

I'm doubtful as to whether it will work, but if you're using a free Linux GUI then I'm sure it would be easier to download the install for the appropriate language. If you have to pay for it again then I can understand why you'd want to make a direct copy.

---

### Post by macogw on 2007-10-31
chinese install disc?  what?  i thought all the install discs defaulted to english.

You can use Mondo to make isos of the full system and Mindi to burn them to cd in a way that makes it able to do a "bare metal" recovery (good for backups)

google also turned up this [http://www.improvedsource.com/view.php/Linux-System/18](http://www.improvedsource.com/view.php/Linux-System/18)

there's also Ghost4Linux (think of norton ghost) [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)


Yes, it's true that it'd be configured for your hardware, but Linux is not like Windows.   All the drivers are there to begin with.  You don't have to go and install them like doing that with Windows would require.  If the hardware's anywhere near similar, it'll be fine.  I did a dd of my drive and put it in an enclosure and booted at least 20 computers from it before with no problems.  The most likely problem is graphics, which just means you do a "sudo dpkg-reconfigure -phigh xserver-xorg"

---

### Post by Rich78 on 2007-10-31
Thanks for the replies.

The OS is for one of those new Asus EeePC's so it's a custom version of Xandros.  It only has 4GB HDD space so I'd need to clone it to another drive.

I'm thinking ahead as I don't have one of these yet and this is really my only issue with getting one.

It's fine until I install something that buggers it up and I need to rebuild it.

The clone would always be going on the same machine so there wouldn't be any hardware differences, unless of course I upgrade the RAM or HDD, but I doubt that would be an issue?

---

### Post by julian67 on 2007-10-31
You can easily clone it with [Clonezilla-Live]("http://clonezilla.sourceforge.net/clonezilla-live/"). This gives you a restore image. You can store it on DVD or HDD or spanned across CDs or on another flash drive. It can't be used to install but it can be used to exactly restore the OS to whatever state it was in when you cloned it, which I think is what you intend. 

There's a great CD [GParted-Clonezilla]("http://www.icewalkers.com/Linux/Software/529170/GParted-Clonezilla.html") which gives you Gparted and Clonezilla live on one CD, with this you should be able to do all your partitioning/disk imaging/restores very easily.

---

### Post by ukripper on 2007-10-31
i use clonezilla for cloning much quicker than any other app i ever tried.
100% must use app for cloning

---

