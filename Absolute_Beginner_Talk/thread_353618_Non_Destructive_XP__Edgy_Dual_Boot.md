---
title: "Non Destructive XP / Edgy Dual Boot"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by winterj on 2007-02-04
Hello,

I've been using Edgy on my old pc for about a week now and it's great, i've decided to install it on my main system running xp.  The problem is, every guide to install Edgy on an xp machine seems to involve reinstalling windows, and my pc did not come with an XP cd.

So, does anyone know of any links that can show me how to do this while keeping my windows system intact?  Also, I don't have much experience with bootloaders, is GRUB my best choice?

---

### Post by riven0 on 2007-02-04
You should be able to install Ubuntu without reinstalling Windows. The problems come from installing Windows *after* installing Ubuntu. You'll mess up your Ubuntu bootloader like that.

Make sure you defrag you Windows hd first, and let GParted do the partitioning. You can let it automatically resize the hd to half if you don't want to mess around with it manually. Then Ubuntu should automatically detect Windows and add a boot entry in Grub and you'll be set to go!

---

### Post by Coelocanth on 2007-02-04
Try Herman's [Dual Boot Guide](http://users.bigpond.net.au/hermanzone/).

---

### Post by raul_ on 2007-02-04
> **winterj said:**
> Hello,

The problem is, every guide to install Edgy on an xp machine seems to involve reinstalling windows

Are you sure? :rolleyes:

---

### Post by orb9220 on 2007-02-04
Yes I installed edgy on same HD as my xp install. And got a dual boot system.

1) Make sure you understand the partition scheme. Example mine:

First HD is hda and winxp is hda1 and my root / partition is hda2 and my swap is hda3 all on same hd. where people mess up is overwrite there xp partition. 

But at the gpart where you assign partitions make sure that the xp drive is there with NO checkmark to reformat.

Verify that your / root is set in pull down menu to the hd partition that you have made for it example:hda2 and swap is hda3 or they can be reversed doesn't matter. And the check mark to reformat is checked.

If you install xp after ubuntu then grub has know way of knowing this since it only looks at drives during the install phase. If you do you can reconfig grub by this thread.  [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by closetpirate on 2007-02-04
My experience has been that if you use a live CD like Knoppix and use qtparted to resize your xp partition that you will be fine

its always a good idea to defragment even a couple of times first though

---

