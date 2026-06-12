---
title: "Horribly botched upgrade from Dapper to Edgy"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Ian Adkins on 2007-04-12
I tried upgrading from Dapper to Edgy, and failed spectacularly.

I started by entering this in the terminal:

```
gksu "update-manager -c"
```

Then, when downloading the update files, it always hung on the last file, finally timing out.  So I commented out all the third-party repositories, and tried again, and it seemed to run fine.

Except: there were a number of directories that gave the error message "cannot overwrite directory such-and-such, directory is not empty," or something to that effect.  Didn't bother the installer any; it just went on the to the next thing.

So then the installation looked to be done, except that a perfectly empty window persisted.  Meanwhile, the menu bar prompted me to restart.  So I did as I was told.  I happened to catch a new error message as Ubuntu shut down -- "Halting RAID something-or-other [failed]."

The machine finished halting other things, and restarted.  I didn't get beyond the hardware specs screen before it dropped me into BusyBox:

```
 BusyBox v1.1.3 (Debian 1:1.1.3-2 ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
(initramfs)
```

So I typed 'help,' and didn't see many familiar commands, beyond chmod and some stuff I know from very rudimentary telnet server stuff.  (If you can't tell, I really don't know what I'm doing -- though I'd like to!)

Then I tried to mount my hard drive manually:

```
mount /dev/hda1 /root -1 ext3
```

It told me that that volume couldn't be found.  I gave up, put the Dapper setup CD in, and I'm running it as a live CD until I can figure out how to get Edgy to work, or otherwise rescue my data, wipe the drive and start over with Dapper.

Incidentally, at almost the very same moment as I first get dropped into BusyBox, the motherboard fries on the Windoze machine I keep as a backup.  Talk about synchronicity!

---

### Post by freebird54 on 2007-04-13
I am a skeptic when it comes to synchronicity.  Was there an electrical storm perchance?  It might help to explain the issues you face...

(hope not!)

---

### Post by houstonbofh on 2007-04-13
Useing the live cd, can you see data on those partitions?  Can you 'fsck' those partitions?

---

### Post by Ian Adkins on 2007-04-13
Freebird: 

Synchronicity abounds!  Or at least that's what I'm supposed to say -- I'm doing a master's degree on Jung.

Houston:

```
ubuntu@ubuntu:~$ fsck /dev/hda1
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
fsck.ext2: Permission denied while trying to open /dev/hda1
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$
```

I may not be doing it right, but that's what I get.

---

### Post by freebird54 on 2007-04-13
You did it right - but you did it first!  The drive has to be mounted first, before it can be fsck'd.   I gather thay it wouldn't mount for you in the first place though...

Have to think about this one for a bit.

---

### Post by Ian Adkins on 2007-04-13
That would make sense, but when I tried mounting the hard drive, I got "permission denied, only root can do that."

---

### Post by freebird54 on 2007-04-13
I haven't done this from Live - but presumably you need to preface your command with sudo.  the password to use would be the question!  oem  maybe?  ubuntu maybe?  Someone here will know.  Anyway - if you get it mounted, I think the cmd you want is

```
e2fsck -C0 -f /dev/hda
```

 the -C0 makes it show progress bar in terminal, and -f forces the fix mode.  you could add a v after -f if you want verbose reporting...

good Luck!

---

### Post by Ian Adkins on 2007-04-13
I don't know if this helps, but this is what "mount" lists as mounted: 

```
unionfs on / type unionfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
```

I tried preferencing mount commands with "sudo," but each time it just gives me the mount help screen.

---

### Post by houstonbofh on 2007-04-13
From the Live CD you can sudo with no password.  Says so when you open a term. :)
'sudo fsck /dev/hda1'

---

### Post by Ian Adkins on 2007-04-13
That worked.  Here's what I got:

```
ubuntu@ubuntu:~$ sudo fsck /dev/hda1
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hda1: recovering journal
Clearing orphaned inode 2441279 (uid=0, gid=0, mode=0100755, size=31432)
/dev/hda1: clean, 139563/7323648 files, 1721609/14643239 blocks
ubuntu@ubuntu:~$
```

---

### Post by Ian Adkins on 2007-04-14
Any ideas as to what's next?  :(

---

### Post by freebird54 on 2007-04-14
I would gather that the disk repair wasn't enough?  What exactly do you get now when trying to start up?  Perhaps things can be individually patched up from the CD without a re-install...

---

### Post by Ian Adkins on 2007-04-14
Alas, no -- it dropped me into BusyBox, just the same, when I rebooted.

Can the Edgy-upgraded OS be repaired from the Dapper CD?  Remember, I upgraded (well, attempted to, anyway) through system update.

---

### Post by freebird54 on 2007-04-14
Probably not.  DO you have a way to get the .ISO of Edgy?  I can't believe there's that much wrong - if we could figure out what is...

---

### Post by Ian Adkins on 2007-04-14
I'll try -- when I initially tried to switch over to Ubuntu, I didn't have a whole lot of luck trying to get the CD image burned as a useable CD.  Which is why I eventually had a free CD shipped to me.

But let's suppose I have some success getting a CD burned in the next couple days -- what would I do then?

---

