---
title: "Help"
date: 2007-07-19
forum: Apple Intel Users
---

### Post by fishguts182 on 2007-07-19
Hello I am trying to install parallel tools on mac running parallels an linux unbuntu 7.04. can someone give me a guide of what I need to do?

---

### Post by black_raven2525 on 2007-07-19
To install parallels tools you have to click "Install Parallels Tools" under "Actions" then
```
sudo mount /dev/cdrom /media/cdrom0
```
and
```
sudo sh /media/cdrom/parallels-tools.run
```

---

### Post by black_raven2525 on 2007-07-19
[QUOTE=fishguts182][QUOTE=black_raven2525][QUOTE=fishguts182]for the help, in my thread. I would enter the commands you gave me in the terminal of linux correct?[/QUOTE]


correct[/QUOTE]


when I enter sudo mount /dev/cdrom /media/cdrom0

what is suppose to say? I get the following

mount: block device /dev/cdrom is write-protected, mounting read-only
mount: /dev/cdrom already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scrd0 is already mounted on /media/cdrom0[/QUOTE]

This may be an issue if you have a disk in the computers physical drive.  If you have one in there, remove it and try again.  Otherwise, try this

```
sudo umount /media/cdrom0
```

then remount the image with 

```
sudo mount /dev/cdrom /media/cdrom0
```

The line about "mount: block device /dev/cdrom is write-protected, mounting read-only" is normal because the CD is read-only.  I don't have my machine near me to test what else it says but I think that should be all.

---

### Post by fishguts182 on 2007-07-19
I did have a cd in the drive and I removed it. I tried 

sudo mount /dev/cdrom /media/cdrom0

again and it still gave me 


mount: block device /dev/cdrom is write-protected, mounting read-only
mount: /dev/cdrom already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scrd0 is already mounted on /media/cdrom0

I then tried sudo umount /media/cdrom0 and it said unmount: command not found

---

### Post by black_raven2525 on 2007-07-19
> **fishguts182 said:**
> 

I then tried sudo umount /media/cdrom0 and it said unmount: command not found

```
sudo** umount** /media/cdrom
```

The command is umount, not unmount.

---

### Post by fishguts182 on 2007-07-19
thanks for the help, I got it to work

---

### Post by fishguts182 on 2007-07-19
now I am trying to open up the installer and it says could not open the file /media/cdrom0/parallels-tools.run using unicode (UTF-8) character encoding. What kind of character coding do I use to open it up?

---

### Post by black_raven2525 on 2007-07-19
```
sudo sh /media/cdrom/parallels-tools.run
```

If that doesn't work try rebooting and unmounting the drives then remounting.

---

### Post by fishguts182 on 2007-07-19
> **black_raven2525 said:**
> ```
sudo sh /media/cdrom/parallels-tools.run
```

If that doesn't work try rebooting and unmounting the drives then remounting.

ok I ran this and it seemed like it worked. It told me to restart the VM. Now should parallel tools be there or how does that work to open it up? sorry I am new to parallels and linux. thanks

---

### Post by fishguts182 on 2007-07-20
I got things running again and I get the following

You are about to start installing Parallels Tools. Save your data and close all
applications to prevent data loss during possible X-Server restart.
Continue ? [Yes/No]: 

I type in yes and then enter and it keeps giving me the same thing shown below, no matter how many time I type in yes.

You are about to start installing Parallels Tools. Save your data and close all
applications to prevent data loss during possible X-Server restart.
Continue ? [Yes/No]:

---

### Post by cyberdork33 on 2007-07-20
Did you try 'Yes' vs 'yes'

---

### Post by fishguts182 on 2007-07-20
alright that worked. it then said linux tools now installed and restarted linux ubuntu. Now what do I do?

---

### Post by cyberdork33 on 2007-07-20
> **fishguts182 said:**
> alright that worked. it then said linux tools now installed and restarted linux ubuntu. Now what do I do?
what are you attempting to accomplish? You installed the tools. you have a working Ubuntu OS, do whatever you want.

---

### Post by fishguts182 on 2007-07-20
everything is working good now. thanks to everyone for all the help.

---

