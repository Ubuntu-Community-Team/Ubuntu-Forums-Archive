---
title: "external hard drive help"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by nicholas mccarthy on 2007-11-05
im having difficulties working my external hard drive. when i click on it, it says "Unable to mount the volume 'SimpleDrivePS' (the name of the hard drive) does anyone know how to fix this? id really like to use my external hard drive again.

---

### Post by The Tronyx on 2007-11-05
Can you please pastebin your /etc/fstab?

Not sure if that will help me help out, but it's worth a try:)

**Ignore this part about fstab

---

### Post by nicholas mccarthy on 2007-11-05
im sorry, im not that computer smart. what do you want me to post where? (i think i know what your talkin about for where to put it, but not sure)

---

### Post by The Tronyx on 2007-11-05
> **nicholas mccarthy said:**
> im sorry, im not that computer smart. what do you want me to post where? (i think i know what your talkin about for where to put it, but not sure)

In a terminal, with your hard drive plugged in, type:
> 
sudo fdisk -l


Copy and paste the results here =]

---

### Post by nicholas mccarthy on 2007-11-05
this is what it said in the terminal after i typed that in:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0459e643

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4725    37953531   83  Linux
/dev/sda2            4726        4865     1124550    5  Extended
/dev/sda5            4726        4865     1124518+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1cb31993

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7301    58645251    7  HPFS/NTFS




i dont know if it did anything. i tried to access the hard drive and it still said the same thing. do i need to restart after doing that or anything?

---

### Post by The Tronyx on 2007-11-05
How big is your external HD?  I'm guessing it's the NTFS one so try this

Make a mount point
> 
sudo mkdir /media/external


Try to mount it:
> 
sudo mount /dev/sdb1 /media/external


---

### Post by nicholas mccarthy on 2007-11-05
its 60 GB.

heres what happened for the first one:

mkdir: cannot create directory `/media/external': File exists
stephen@ubuntu:~$ sudo mount /dev/sdb1 /media/external
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/external -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/external ntfs-3g defaults,force 0 0
stephen@ubuntu:~$  mount -t ntfs-3g /dev/sdb1 /media/external -o force
mount: only root can do that
stephen@ubuntu:~$  /dev/sdb1 /media/external ntfs-3g defaults,force 0 0
bash: /dev/sdb1: Permission denied
stephen@ubuntu:~$ 

then it says the same for the 2ndthing you gave me

---

### Post by The Tronyx on 2007-11-05
> **nicholas mccarthy said:**
> 

mkdir: cannot create directory `/media/external': File exists
stephen@ubuntu:~$ sudo mount /dev/sdb1 /media/external
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/external -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/external ntfs-3g defaults,force 0 0
stephen@ubuntu:~$  **sudo** mount -t ntfs-3g /dev/sdb1 /media/external -o force
mount: only root can do that
stephen@ubuntu:~$  **sudo** mount /dev/sdb1 /media/external ntfs-3g defaults,force 0 0
bash: /dev/sdb1: Permission denied
stephen@ubuntu:~$ 

then it says the same for the 2ndthing you gave me

Looks like you left out the sudos on the mkdir and the force mount?  I added in the sudos it looks like you might have left out, they are bolded.

EDIT*** Forget that stuff up there.  Run this

> 
sudo mount -t ntfs-3g /dev/sdb1 /media/external -o force


This assumes you have a /media/external.  I am not sure if you issued it right before but if not, issue "sudo mkdir /media/external" without the " "s

Unfortunately I have to go to work but if no one stops by to assist you further, stop by the Ubuntu IRC channel.  Lots of very helpful and knowledgable people there.  Best of luck to you and sorry that I have to go.

---

### Post by nicholas mccarthy on 2007-11-05
NOW heres whati got, lol:

stephen@ubuntu:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/external -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.

so, now what?

---

### Post by nicholas mccarthy on 2007-11-05
thank you! i can access the stuff on the hard drive now! thanks alot!

---

### Post by supachicken on 2008-01-27
I'd just like to thank 2point0 and Nicholas McCarthy for their interaction.

I'm a newbie to Linux/Ubuntu and have just recently loaded Ubuntu 7.10 on my old Toshiba laptop.

I have been amazed at how well the intial install configured mostly everthing on my laptop from wireless to graphics.

However there have been a couple things I couldn't connect such as my Iomega mini max hard drive.

But just a few quick serchs in the Ubuntu forums have provided solutions for me and installed a confidence where people like myself can ask for help from a community where people are so generous with their advice.

So I'd thought I'll post a reply to say thank you to you both and others who post and answer questions from those who take the time to search the forums for answers.

Thanks again
Supa

---

