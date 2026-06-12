---
title: "G3 iMac can't find root after install"
date: 2008-08-08
forum: Apple Hardware Users
---

### Post by eelmonger on 2008-08-08
I was recently given an old iMac and decided to install Xubuntu on it.  The install went fine using the 7.10 Xubuntu PowerPC alternate CD, but when I reboot it hangs for a very long time and eventually says /dev/sda3 doesn't exist and it can't find root so it drops me to the (initramfs) shell.  However, if I use the CD to boot into rescue mode and start a shell in /dev/sda3 and then type "startx" everything is there and works fine.  Does anyone have any suggestions on how to fix this issue?  I've tried reinstalling several times, all with the same results.

Thanks

---

### Post by tiresia on 2008-08-08
Can you please post your yaboot.conf?
```
cat /boot/yaboot.conf
```

---

### Post by tiresia on 2008-08-08
The imac g3 has not a IDE-HD? If so, yaboot should look for /dev/**h**da3

---

### Post by eelmonger on 2008-08-08
Thanks for the offer of help, but I "fixed" the problem by installing 6.06 from the GUI (after resetting the date from the 50s) and was able to boot that and upgrade straight to 8.04 with only a minor known bug.  The process took pretty much all day, but now it's working!  I think part of the problem might have been that the alternate installer doesn't give you the chance to set the date so everything was working off invalid timestamps.  The GUI installer would crash with a DateTime error until I figured out that this old Mac is having a hard time keeping time.

> **tiresia said:**
> The imac g3 has not a IDE-HD? If so, yaboot should look for /dev/**h**da3

Yeah, I'm dumb, I'm just used to typing sda, but it was hda in both the error and the shell.

---

### Post by stream303 on 2008-08-09
That date bug is pretty common with G3 iMacs.  For many, this also surfaces by not being able to get past the gdm login screen which just hangs due to a bad date:

[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

If it really starts acting up, you may want to replace the motherboard's lithium battery.  I've seen them at Radio Shack in the US, although I'm sure you can get them elsewhere.

---

### Post by Armandb on 2008-10-27
Anyhow, I've got the same problem ("can't find hda3") and still don't know how to solve it. 

My date is fine.
I don't have enough ram to boot a live CD.
Here is my /etc/yaboot.conf:
> boot=/dev/hda2
device=/pci@80000000/mac-io@10/ide@20000/disk@0:
partition=3
root=/dev/hda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
       label=Linux
       read-only
       initrd=/boot/initrd.img
       append="quiet splash"


image=/boot/vmlinux.old
       label=old
       read-only
       initrd=/boot/initrd.img.old
       append="quiet splash"

My imac is a Bondie Blue rev B one.

Does anyone has a clue?

---

### Post by stream303 on 2008-10-27
Do you have a newer/larger hard drive than what came with the unit originally?  If so, you may be running into the 8gb partitioning limitation for root.

What I normally do is when first installing Ubuntu on early imacs, is let it automatically calculate the partitions, then use the "go back" feature in the partitioner to delete what it thinks swap and root should be.  Then I manually change root (the third partition) to be about 7 to 7.5 gB, and make a large portion of the new drive my /home partition, and dedicate about 2x for swap.

There are a few ways to manually divvy up the disk, but I found it easier to use the "go back" method to ensure that the critical 1st and 2nd Apple partitions are set up properly.

---

### Post by Armandb on 2008-12-15
I cannot guaranty that it is the original hard drive, but it's a 4GB one, so I guess there's no "over 8GB" problem.

I installed "6.06.1 alternate" in text mode, then the xubuntu-dektop package, and then upgraded through the versions with no worries until 7.04, but the upgrade to 7.10 caused the same problem ("can't find hda3").

I'll try upgrading from 6.06 to 8.04&#8230;

---

### Post by stream303 on 2008-12-15
Hrm.. I think I remember with 7.10 needing a mod for *ide-core*:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot](https://wiki.ubuntu.com/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot)

This might help get 7.10 Gutsy going again.  Be sure to do the post-install process with *initramfs*.

The thing that worries me about xubuntu, is that it is no longer available for 8.04 in the repos, so while one might get updates to other parts of the system, I am wondering if there are any updates coming down for the Xubuntu / XFCE packages themselves....

Gutsy 7.10 might be the last **reliable** stop for Xubuntu I'm afraid.  Then again, there's always Debian for XFCE4 fans...

---

