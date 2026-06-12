---
title: "dvdrw drive will not open"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by catroaring on 2008-02-23
i installed ubuntu 7.04 from my dvd drive, so it works.  it lists as cd-rom1 but i cant get it to open.  
any help?

cat

---

### Post by yabbadabbadont on 2008-02-23
If there is a disc in the drive, and it is mounted (i.e. there is an icon for it on your desktop), then you cannot eject it until it has been unmounted.  Right click on the icon on the desktop and take the option to either unmount or eject, whichever is listed.

---

### Post by catroaring on 2008-02-23
there is no disk in drive.

---

### Post by BaffledMollusc on 2008-02-23
> **catroaring said:**
> i installed ubuntu 7.04 from my dvd drive, so it works.  it lists as cd-rom1 but i cant get it to open.  
any help?

cat

You mean if you press the eject button when you're logged in nothing happens? Something that might work is holding down the eject button as you reboot.

Also, most CD/DVD drives have a very small hole into which you can insert something like a straightened out paper clip. Pushing something into this hole is the emergency override eject method. If *that* doesn't work, I have no idea.

---

### Post by yabbadabbadont on 2008-02-23
> **catroaring said:**
> there is no disk in drive.

In a terminal window, run "mount" (without the quotes) and please post the results.

By the way, to open a terminal, Applications->Accessories->Terminal  (I think, it has been a while since I last used Gnome)

You can select the text in the terminal with the mouse and then middle-click to paste it into your post.

---

### Post by shad0w_walker on 2008-02-23
Try pressing Alt-F2 and running this command:

```
eject
```

---

### Post by catroaring on 2008-02-23
this is what i get from "mount"  with no cd/dvd in drive.

/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda2 on /media/HUMAN'S IPO type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)


also, while restarting.  and opening the drive it opens.  when i put a cd or dvd in it.  after ubuntu loads everything is fine.  drive ejects.  its only if i restart with no cd/dvd in drive that it 
doesnt open.

and alt-F2 eject does not work if no cd/dvd present.

---

### Post by shad0w_walker on 2008-02-23
I assume you mean the eject command just won't cause the drive to eject? Because I know for a fact that it will eject a drive regardless of having a disc in it.

---

### Post by harold4 on 2008-02-23
Try running "eject" from the terminal to see if you get any output, or if it will actually eject that way.

---

### Post by catroaring on 2008-02-23
it does not eject if no media is in the drive when i restart.

---

### Post by harold4 on 2008-02-23
So you have ubuntu installed and are booting into ubuntu NOT from the cd?

You open a terminal, "alt + f2" then type "gnome-terminal"
Then you enter the command "eject" in the terminal you just opened and it does nothing?

---

### Post by catroaring on 2008-02-24
human@amd1800:~$ eject
eject: tried to use `/dev/hda' as device name but it is no block device
eject: unable to find or open device for: `cdrom'


does nothing

---

### Post by catroaring on 2008-02-24
booting not from cd

---

### Post by harold4 on 2008-02-24
The default device that eject points to does not exist.  What's your output of
```
ls /dev/cd*
```

---

### Post by catroaring on 2008-02-24
/dev/cdrom  /dev/cdrw

---

### Post by harold4 on 2008-02-24
try 
```
eject /dev/cdrom
```

or

```
eject /dev/cdrw
```

EDIT: Also, what's the output of
```
ls -la /dev/cd*
```

---

### Post by SR_ELPIRATA on 2008-03-03
I have this same problem but with 7.10. I was able to install the OS without problems, and as long as I start the computer with a cd or dvd in it I can open it fine, but if I make the mistake of turning the system on without a CD or DVD inside, it simply WONT OPEN.

I was trying to configure my nforce card with a howto on this forum and in one of the steps asked me to put the ubuntu cd, so I removed the black hawk down dvd and then put in the ubuntu cd, the terminal kept asking for /media/cdrom and I had to kill it because it wouldnt read it.

What is funny is... you could see /media/cdrom and /media/cdrom0 but none had contents, but at the same time there was a /media/ubuntu....., same when I had the black hawk dvd, it would appear on /media/BLACK_HAWK_DOWN.

I tried the suggested eject commands and all I get is about to eject one of my windows hard drives, and dont want to eject these.

BTW all the LS commands say "No such file or directory"

ELP

---

### Post by shadowforte on 2008-04-02
I am having the same problem. Also running 7.10

---

