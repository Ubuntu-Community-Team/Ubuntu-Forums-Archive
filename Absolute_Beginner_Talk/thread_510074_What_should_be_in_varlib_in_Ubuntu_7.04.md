---
title: "What should be in /var/lib/ in Ubuntu 7.04?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by stevehaines on 2007-07-26
Ubuntu 7.04 on Athlon 950. I had to fsck the partition and fix a lot (70+) of inode and other errors. After that I could not get GDM to start, but system ran in TTY1 and startx did run an X-windows session.

It looks like /var/lib/ is bombed: Only 16 subdirectories, and no /gdm, /apt, /dpkg, or /aptitude.  It does have /synaptic, but I can't run synaptic because of "Gtk-WARNING **: cannot open display."  A parallel Kubuntu installation has 46 subdirectories in /var/lib/.

Can this installation be saved? I can't use apt-get or aptitude or dpkg. Would running from the live CD let me copy the contents of /var/lib to the hard disk /var/lib?

---

### Post by asmoore82 on 2007-07-26
```

asmoore@asmoore-laptop:~$ ls /var/lib/
acpi-support   dhcp3                logrotate            synaptic
alsa           dictionaries-common  misc                 tex-common
apt            doc-base             mozilla-firefox      texmf
aptitude       dpkg                 mozilla-thunderbird  ucf
aspell         gcj-4.1              NetworkManager       update-manager
avahi-autoipd  gconf                python-support       update-notifier
belocs         gdm                  scrollkeeper         urandom
binfmts        gstreamer            security             vim
bittorrent     initramfs-tools      sgml-base            x11
dbus           initscripts          slocate              xkb
defoma         locales              snmp                 xml-core
asmoore@asmoore-laptop:~$ ls /var/lib/ | wc
     44      44     410
```

how exactly did this problem start?

---

### Post by stevehaines on 2007-07-26
Working fine for a week or two after installation (multiple systems on one disk: XP, Ubuntu, Kubuntu, Freespire).

One morning Ubuntu crashed at start up saying unreadable superblock. That also blocked Kubuntu. I loaded Knoppix and ran fsck on Ubuntu partition. Lots of inode and other errors. Answered manually to each question saying "fix" or "repair". Moved a bunch of blocks to lost and found.

Now hda5 with Ubuntu checks clean, but on start-up balks at GDM saying:

Server authorization directory (daemon /ServAuthDir) is set to /var/lib/gdm but does not exist. Please correct GDM configuration and restart GDM.

At this point system goes to TTY1 console mode. Works okay, but cannot run dpkg or apt or aptitude or synaptic -- thus no apparent way to repair gdm.

I'm going to copy the contents of /var/lib/apt and var/lib/dpkg over from live CD to hda5, plus make a directory /var/lib/gdm and put the two files in it: :0.Xauth and :0.Xservers.

I really think this installation is hosed, but I'll play with it a bit to learn what I can before reinstalling.

---

### Post by asmoore82 on 2007-07-26
i would start up a LiveCD, open a terminal and
1. make sure the LiveOS is _not_ using any SWAP on the hard drive.
2. test your entire hard drive for bad blocks (assuming it is primary Master IDE)

```
~ $ sudo swapoff -a
~ $ sudo badblocks /dev/hda
```

If the 'badblocks' command spits out _any_ output in the term before your prompt comes back then it _has_ found badblocks on your hard drive and you need to _not_ power up that hard drive again _until_ you are ready to pull whatever data you can off of it to a new/working drive.

---

### Post by stevehaines on 2007-07-26
Thanks, I'll do that. For now, here is what worked (I think). 

As root, I made /var/lib/gdm. Then I wrote two files in /gdm with pico. ":0.Xauth" is a blank with nothing in it. ":0.Xservers" has a line of obscure code -- I copied it from the same file while running the Live CD. That got me my GDM sign-on screen back.

I copied the contents of /var/lib/apt and var/lib/dpkg to a memory stick. Then in XP I made a CD with that on it. Back in the broken Ubuntu I copied the contents into /var/lib/apt and /var/lib/dpkg. That restored apt and synaptic.

The last problem that I can see is that the "Hardware Abstraction Layer" is broken. I get that message when signing on. The system no longer finds the ZIP drive or the USB memory stick. Any ideas for that?

---

### Post by stevehaines on 2007-07-26
From asmoore82:

If the 'badblocks' command spits out _any_ output in the term before your prompt comes back then it _has_ found badblocks on your hard drive and you need to _not_ power up that hard drive again _until_ you are ready to pull whatever data you can off of it to a new/working drive.

OK, I ran badblocks on my 60 GB hard drive. Report was 129 bad blocks. If each block is 1kb -- and it appears so as the count ended around block # 60,000,000 -- then the problems begin at around the 45 GB mark.

Is it worth trying to mark the bad blocks and continue using the drive?

---

### Post by az on 2007-07-26
Stop writing to the drive.  That will minimise the chance of you corrupting any remaining data.

Salvage any files that you still can access that you need ( in your home directory).  Forget about /var/lib.  Throw the drive in the garbage and reinstall Ubuntu on another hard disk.

---

