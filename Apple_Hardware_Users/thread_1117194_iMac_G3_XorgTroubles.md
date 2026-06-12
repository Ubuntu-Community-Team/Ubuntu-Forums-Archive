---
title: "iMac G3 XorgTroubles"
date: 2009-04-05
forum: Apple Hardware Users
---

### Post by aeuzent on 2009-04-05
Alright let me walk you through my problem, I'm trying to install Ubuntu for power pc on an old iMac G3. I've been using [this]("http://ubuntuforums.org/showthread.php?t=405934") guide to help me out. I ran right into the problem with xorg and reconfiguring the monitor settings to that it will run on the iMac's built-in monitor. So I did an alternate install of 8.04.1 for the powerpc and used apt-get to install xserver then reconfigured xorg.conf and got the system to display without any complaints. Over joyed I ran 'apt-get install ubuntu-desktop' and now the machine finishes it's boot by going to standby mode. 

I assume what happened is that somewhere in the desktop install something re-configured xorg.conf and now unable to put a picture on the monitor the Mac bios just sends the machine to standby. Ctrl-option-F1 does not kill x and wake the machine up so I'm kind of stuck doing a hard reboot that just leaves me in the same place when it finishes. 

I need any help you guys can give on how to get into linux, reconfigure xorg.conf and keep xserver from running.

---

### Post by stream303 on 2009-04-06
Yep - your modified /etc/X11/xorg.conf got overwritten with default values, and now the monitor shuts down.

You can go back into the installation with "rescue mode" at the yaboot boot prompt by booting with the cd, and (hit TAB) to see the options when it appears and use either "rescue mode" or enter "linux single"

Eventually it will prompt you where to drop yourself as a root shell into, and you'll probably want /dev/hda3 if that is where you have root.  From there, you can fire up vi and edit /etc/X11/xorg.conf again, but it isn't pretty.

Another alternative is to use the powerpc live-cd rescue/sysadmin disk from Finnix to do the job.

[http://www.finnix.org](http://www.finnix.org)

If you used that, you can boot the system, and mount the root partition on the drive:

```
mount -t ext3 /dev/hda3  /mnt
```

(or whatever your system uses /sda3 etc)

Then edit the file, vi, nano, joe etc

```
vi /mnt/etc/X11/xorg.conf
```

and then shutdown -r now to reboot.

---

### Post by aeuzent on 2009-04-06
Ok I feel like we're close here. I downloaded finnix and I have it running. When I try the mount command it tells me the drive is already mounted or the directory I want to mount it to is busy. So I tried a umount it but I was told it wasn't mounted. So then I tried to mount it somewhere else and got the same error message again.

---

### Post by aeuzent on 2009-04-13
bump

---

### Post by stream303 on 2009-04-13
Oops.  Looks like I left of the partition number, ie /dev/hda3

On my system, I actually use /dev/sda3, but you'll have to find yours to mount it temporarily.

---

### Post by aeuzent on 2009-04-14
Is there a command I can use to figure out which hda/sda represents the local drive? I've been through 0-4 on both

---

### Post by aeuzent on 2009-04-16
Alright I made a bit of head way. When I try to mount hda1 or hda2 I get an error that the ext3 file system is wrong (shouldn't be). But hda3 mounts fine. Only problem is that the xorg.conf file in hda3 is already set correctly.

---

