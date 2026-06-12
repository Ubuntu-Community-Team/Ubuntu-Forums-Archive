---
title: "Need Help with Grub dual boot"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by squidward_tentacels on 2008-04-10
Hello, been reading but need a little help,

Have XP on hda1

on hdb first partition is FAT shared storage area (hdb1)

Next comes Debian;

hdb2  swap
hdb3  /
hdb4  /home

When I made the partitions, I set bootable flag on hdb3,  I am thinking I made a mistake with that, because after I finished the install and wrote grub to the mbr, grub failed with error 21. Needing the computer back quickly, I just restored the boot sector back with windows "fixmbr" command, so xp boots fine.

My question(s)  is this, I know I need to rewrite grub back to the mbr, but what would be proper syntax to direct grub to the loaction of debian (hdb3) , and how to add xp...I seem to recall something with the chainloader command.
Also should I remove the bootable flag from hdb3? Id there an interactive way to edit grub, or do I neeed to let it install & then edit grub.conf?

Thanks for reading this, any help is welcome.

---

### Post by keratos on 2008-04-10
you will need to boot the liveCD to a command prompt (failsafe) then reinstall grub using an appropriate menu.lst.

Many ways to do this but for me, I would boot the liveCD, mount hdb3 and "chroot" to it, running grub to reinstall the bootloader.

Like I said, this can be done many other ways, but for me that would be the quickest!

---

### Post by Dazed_75 on 2008-04-10
Just saw this reference in another thread.  The only caution I would add is to read it carefully since a number of methods are described and reading it overly quickly could confuse someone.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by squidward_tentacels on 2008-04-11
Well, It turns out the problem is a Dell-centric hardware issue, Bug #8978 in grub.

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8978](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8978)

The workaround for this one really sucks.

---

### Post by bumanie on 2008-04-11
Could you copy and paste the output of > cat /boot/grub/menu.lst and > sudo fdisk -l (that's a lower case L)

---

### Post by Biggy on 2008-04-11
Install Startup-Manager  [here]("http://www.gnomefiles.org/download.php?soft_id=2051&where=http%3A%2F%2Fdownloads.sourceforge.net%2Fstartup-manager%2Fstartupmanager_1.9.9-1_all.deb")

---

### Post by keratos on 2008-04-12
> **Biggy said:**
> Install Startup-Manager  [here]("http://www.gnomefiles.org/download.php?soft_id=2051&where=http%3A%2F%2Fdownloads.sourceforge.net%2Fstartup-manager%2Fstartupmanager_1.9.9-1_all.deb")
He cannot, for he cannot boot the system.

---

### Post by keratos on 2008-04-12
> **bumanie said:**
> Could you copy and paste the output of  and (that's a lower case L)
He cannot, unless he boots the system from a LIVE CD.

---

### Post by keratos on 2008-04-12
squidward...

you need to boot from a LiveCD as I said above.

THEN there are many options however, **bumanie** is correct in asking for the initial data..., post the output of the menu.lst and output of the "fdisk -l" command, for it could be that your system is just configured incorrectly and not actually a bug. NOTE you will need to post the output of the grub config from your root filesystem and not the CD!! To do this, mount your /dev/hdb3 on a temporary directory and post the output of menu.lst from that filesystem. e.g.
```

sudo mkdir /mnt/tmp
sudo mount /dev/hdb3 /mnt/tmp
sudo cat /mnt/tmp/boot/grub/menu.lst

```


Error 21 is an error reported by the stage2 bootloader when an unknown error has occured. Typically in my experience this is because a bootable partition specified in the bootloader (when installing Grub into MBR) cannot now be found. This is usually consequent on either HDDs settings changing in the BIOS; the BIOS remapping the first sector of the MBR; or some kind of transient partition error.

Check your BIOS and make sure the HDDs are operating in IDE mode and not RAID and that no mappings or amendments to the IDE geometry is active, etc.

---

