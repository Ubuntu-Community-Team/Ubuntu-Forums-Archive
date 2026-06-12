---
title: "How to dual-boot Edgy &amp; SimplyMepis?"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by derspiess on 2006-11-10
Hi all,
I'm back to playing around with Ubuntu after a several month hiatus.  I really like some of the newer features with Edgy (though I'm having some issues with nvidia drivers-- leaving them uninstalled until I figure out the problem), and I want to show Ubuntu and another flavor of Linux with a buddy of mine, who has been asking me about Linux & will be visiting this weekend.

Currently, I have Ubuntu installed on one 80GB hard drive, and Vista RC2 installed on a secondary 60GB hard drive.  

I'd like to also install SimplyMepis on that 80GB drive on a separate partition.  What is the best way to go about this?  I guess I need to create another partition & load SimplyMepis on to it, but when I tried that a few days ago, it seemed to wipe out my Ubuntu installation, or at least make it inaccessable.

I know this is probably a pretty basic question, but I've looked around the forums & haven't found a precise (and idiot-proof) solution.

Thanks in advance!

---

### Post by djsroknrol on 2006-11-10
How are your partitions set up on the 80 GB drive?...

I would suggest using the Gparted live CD to make the other partition for Mepis, and then after installing it, edit grub manually to add SimplyMepis to the menu.lst in Ubuntu...

---

### Post by confused57 on 2006-11-10
Yes, you could use the Gparted Live CD to create a partition for Mepis:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

or the Mepis installer could create the partition...you could do a manual install, opt to use the same swap partition as Ubuntu and to install grub to the Mepis root partition.  You'd just need to add an entry to your Ubuntu /boot/grub/menu.lst to boot Mepis:

title          SimplyMepis
rootnoverify   (hd0,1)
chainloader +1

if Mepis is installed on the 2nd partition(hda2).  This has been the easiest way for me to set up multiple Linux distros on one hard drive.

There is another way, if you're interested...I did the same thing that you did, installed SimplyMepis on the 2nd partition(Dapper was on the 1st).  Mepis grub was installed to the mbr, but didn't detect Dapper...I did a **cat /boot/grub/menu.lst**, wrote down the exact entry to boot Mepis.  Then I used the Dapper live cd to restore the Dapper grub(which didn't detect Mepis):
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

then I added the Mepis boot entry to Dapper's menu.lst.

You can do it either way, but I think the 1st method is easier.  Using the 2nd method, I have to update the Mepis entry in Dapper's grub every time there's a kernel update to boot the new kernel.

---

### Post by derspiess on 2006-11-10
First off, thanks for the help thus far.

Here's what I did:

I created a 35GB partition on the 80GB hard drive & installed Mepis to it.  Then I went ahead & edited grub in Ubuntu with what you suggested.

Now I see "SimplyMepis" in Ubuntu's grub when I boot up, but it does not boot into Mepis when I select that from the list-- I guess I am still missing something.

I did *not* install grub when installing Mepis, because when I tried this once before, Mepis's grub would always show up when I boot up, rather than Ubuntu's grub (and thus, I would have no way to get to Ubuntu).

Any thoughts on what to do now?

Thanks,
derspiess

---

### Post by bodhi.zazen on 2006-11-10
When installing Mepis, install grub to the (Mepis) root partition and not the MBR.

---

### Post by confused57 on 2006-11-10
You could boot the Mepis live cd, select install, and there's an option on the left that allows you to reinstall grub...you might want to go to the Mepis website & find some screenshots of this...as bodhi.zazen mentioned, select to install grub to the Mepis root partition, then add the chainloader entry to Edgy's grub.

If you want to try manually adding a Mepis entry to Edgy's /boot/grub/menu.lst, here's mine right after I installed Mepis(it was the last release candidate):

```
title     MEPIS at hda3, kernel 2.6.15-25-386
root       (hd0,2)
kernel     /boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 nomce quiet vga=791
boot
```

The final release SimplyMepis6.0 probably had the 2.6.15-26 kernel & you might need to adjust your entry accordingly, with your partitioning scheme.

You can always mount the Mepis partition from Edgy and get the Mepis entry from /boot/grub/menu.lst

As I mentioned in my first post, using the chainloader method works best for me.

Edit: Found some screenshots of the Mepis install, showing the screen for reinstalling grub:
[http://www.mepisguides.com/install/install-mepis/Install-Mepis-Linux.html](http://www.mepisguides.com/install/install-mepis/Install-Mepis-Linux.html)
[http://www.mepisguides.com/](http://www.mepisguides.com/)

You might want to check out the forum:
[http://www.mepislovers.com/forums/index.php](http://www.mepislovers.com/forums/index.php)

---

### Post by derspiess on 2006-12-05
I got this to work perfectly & really appreciate the help!

Was checking some threads today & realized I never said thanks :-D

---

