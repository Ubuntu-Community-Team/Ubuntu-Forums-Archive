---
title: "Grub keyboard usage and Windows drivers"
date: 2007-06-26
forum: Apple Intel Users
---

### Post by omax on 2007-06-26
Hi guys.

I use grub to boot up Xubuntu and Windows XP Home.

The thing is that it's rarely that the keyboard works in grub. It seems like the kernel has to load before keyboard is available.


Is there any fix to this? I can't choose what OS to boot.


And another question. I have Windows, but need to install drivers on my Macbook C2D

Apple says that I should use boot camp to burn a cd with the drivers. But since I fixed my partitions on my own I can't start boot camp.


Boot Camp says:
The startup disk must be formatted as a single Mac OS Extended (Journaled) Volume or already partitioned by Boot Camp Assistant for installing windows.

Does anyone has this CD and could send it to me? Or upload it somewhere.

For my Macbook C2D 2.0Ghz


Thanks!

---

### Post by cyberdork33 on 2007-06-26
Keyboard problem in grub is known issue. You can switch to lilo or, after making your selection in refit, start hitting up/down several times, and usually your keyboard will be recognized.

On Bootcamp Driver CD Image:
[http://www.macosxhints.com/article.php?story=20070329224224572](http://www.macosxhints.com/article.php?story=20070329224224572)

---

### Post by cyberdork33 on 2007-06-26
delete

---

### Post by cyberdork33 on 2007-06-26
delete

---

### Post by duffman25 on 2007-06-26
> **cyberdork33 said:**
> Keyboard problem in grub is known issue. You can switch to lilo or, after making your selection in refit, start hitting up/down several times, and usually your keyboard will be recognized.

On Bootcamp Driver CD Image:
[http://www.macosxhints.com/article.php?story=20070329224224572](http://www.macosxhints.com/article.php?story=20070329224224572)


The grub issue is reported here: [https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/79172](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/79172)

Surprisingly, the lastest mepis live cd does work. If only they publish their source packages instead of selling them ... I've filled this bug everywhere I could think of, I hope someone can get those patches upstream or another fix ...

---

### Post by ronocdh on 2007-06-26
> **duffman25 said:**
> The grub issue is reported here: [https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/79172](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/79172)

Surprisingly, the lastest mepis live cd does work. If only they publish their source packages instead of selling them ... I've filled this bug everywhere I could think of, I hope someone can get those patches upstream or another fix ...
I don't understand why there's a [double post]("http://ubuntuforums.org/showthread.php?t=476447") of this issue, but it happens. That's very interesting about the mepis CD, duffman... let's keep our fingers crossed for the future.

---

### Post by luisbg on 2007-06-29
Because of this bug I recommend using rEFIt.

Great interface, catches any loadable CD, and best of all... it's free software (libre).

luis

---

### Post by ronocdh on 2007-06-30
> **luisbg said:**
> Because of this bug I recommend using rEFIt.

Great interface, catches any loadable CD, and best of all... it's free software (libre).

luis
I don't see how this gets around the issue of the keyboard not responding on the GRUB screen... in a triple boot setup, choosing Linux or WinXP from the rEFIt screen just loads the same GRUB menu. If the keyboard doesn't respond on this screen, the default OS (usually Linux) will be loaded, and that's the problem.

The user can edit the GRUB menu list to boot a different OS by default, or just lower the countdown time so it's not an issue in a dual boot setup, but this doesn't solve the problem for triple booters.

---

### Post by Milamber_Cubed on 2007-06-30
> **ronocdh said:**
> I don't see how this gets around the issue of the keyboard not responding on the GRUB screen... in a triple boot setup, choosing Linux or WinXP from the rEFIt screen just loads the same GRUB menu. If the keyboard doesn't respond on this screen, the default OS (usually Linux) will be loaded, and that's the problem.

The user can edit the GRUB menu list to boot a different OS by default, or just lower the countdown time so it's not an issue in a dual boot setup, but this doesn't solve the problem for triple booters.

I think your triple boot setup must be incorrect somehow. On mine, I have the timeout for grub set to 1 second because GRUB only shows up for me when I choose Linux from the rEFIt menu. Choosing Windows jumps straight to the Windows XP loading screen for me. 

At a guess, I would say that you have installed GRUB to the master boot record instead of or in addition to just to your Linux partition.

---

### Post by omax on 2007-09-12
Is there any news about this?

I have tried to reinstall Grub on my Linux partition instead of the MBR. Which did not work, must have done something wrong.

Does lilo work at all time during boot?

---

### Post by pxwpxw on 2007-09-12
> **omax said:**
> Is there any news about this?

I have tried to reinstall Grub on my Linux partition instead of the MBR. Which did not work, must have done something wrong.


When you reinstall grub from the MBR to the linux partition boot sector, you also have to restore the MBR for the whole diisk to XP  format, then refit will show a windows flag and a linux tux.
It may also need to rerun the refit  Partiton tool gptsync, and reset flags using gparted. Use with  care and backups.

---

### Post by cyberdork33 on 2007-09-12
> **omax said:**
> Is there any news about this?

I have tried to reinstall Grub on my Linux partition instead of the MBR. Which did not work, must have done something wrong.

Does lilo work at all time during boot?

There is no fix for the keyboard problem.

---

### Post by Misosaki on 2007-09-12
Not sure if this helps any, but have found that the keys usually work if you wait about 10-15 seconds in the rEFIt menu before selecting Linux/Win which then loads Grub (this presumably gives the keyboard drivers time to load). It's a slower boot, but at least it should work (or last resort, plug in an Apple keyboard.)

---

### Post by cyberdork33 on 2007-09-12
> **Misosaki said:**
> Not sure if this helps any, but have found that the keys usually work if you wait about 10-15 seconds in the rEFIt menu before selecting Linux/Win which then loads Grub (this presumably gives the keyboard drivers time to load). It's a slower boot, but at least it should work (or last resort, plug in an Apple keyboard.)

The only option to force a keyboard to work everytime is to plug in a USB keyboard on the bootloader screen

---

