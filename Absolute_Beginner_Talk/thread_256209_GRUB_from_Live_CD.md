---
title: "GRUB from Live CD"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-09-12
I am trying to reinstall GRUB using a live disk.  I have Dapper on my system already, so when I got to the command prompt in the live mode I typed
```
ubuntu@ubuntu:~$ sudo grub
grub> find /boot/grub/stage1

Error 15: File not found
```
Does anyone know why I am getting this error?  Thank you.

---

### Post by jordanmthomas on 2006-09-12
First you need to mount your Ubuntu partition.
```

mkdir ~/Desktop/poo
sudo mount /dev/[COLOR="Red"]sda1[/COLOR] ~/Desktop/poo
sudo chroot ~/Desktop/poo
sudo grub

```

Of course, use hda1 or whatever your Ubuntu partition is.
Hope this helps

---

### Post by amcavoy on 2006-09-13
Thanks for the reply.  I am almost positive that my Ubuntu partition is hda5, but when I try those commands, I get:

```
ubuntu@ubuntu:~$ mkdir ~/Desktop/poo
ubuntu@ubuntu:~$ sudo mount /dev/hda5 ~/Desktop/poo
mount: you must specify the filesystem type
```
Any ideas?  Thanks again.

---

### Post by bodhi.zazen on 2006-09-13
> **amcavoy said:**
> Thanks for the reply.  I am almost positive that my Ubuntu partition is hda5, but when I try those commands, I get:

```
ubuntu@ubuntu:~$ mkdir ~/Desktop/poo
ubuntu@ubuntu:~$ sudo mount /dev/hda2 ~/Desktop/poo
mount: you must specify the filesystem type
```
Any ideas?  Thanks again.

Wrong partition. If Ubuntu is [color=red]hda5[/color] why sudo mount /dev/[color=red]hda2[/color]

Should it not be sudo mount /dev/hda5 ~/Desktop/poo ?

---

### Post by amcavoy on 2006-09-13
I had a typo in the previous message (I have actually tried both), but I still get the same message.  Is there a command which I can use to check which partition it is?

---

### Post by bodhi.zazen on 2006-09-13
> **amcavoy said:**
> I had a typo in the previous message (I have actually tried both), but I still get the same message.  Is there a command which I can use to check which partition it is?

Not that I know of. You will have to mount them and check the contents.

FYI: I also multiboot and I keep a hard copy of my partition table  listing OS on each partition for just such an occasion.

---

### Post by jordanmthomas on 2006-09-13
Usually I only have one ext3 partition at a time, so that tells me where it is
```
sudo fdisk -l
```
the ext3 partition should be your Ubuntu partition (unless you have more than one...but you know)

Also, since you are using your LiveCD, you can open up Gnome Partition Editor
(System --> Administration --> Gnome Partition Editor)
and maybe figure it out from there.

Also, hda5 is not your Ubuntu partition as ext3 is automatically mounted without telling which it is.
chances are that hda5 is your swap partition

---

### Post by amcavoy on 2006-09-14
It turns out to be hda5, so I guess I'm just going to have to format my disk and reinstall Windows seeing as how the other tutorials aren't working.  I guess I didn't realize that something as trivial as a partition resize could fry my whole system, but I appreciate the help you all provided anyhow.

Thank you,

Alex

---

### Post by xpod on 2006-09-14
My xp is hda1 and ubu is hda5 also

---

### Post by bulldog on 2006-09-14
Just try this and it should work.

Code:

sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)


Finally exit the grub shell
Code:

quit

---

### Post by amcavoy on 2006-09-19
This is what I get:

grub> find /boot/grub/stage1

Error 15: File not found

---

### Post by bodhi.zazen on 2006-09-19
Grub is not installed on any of your hard drives.

Install from the live CD.

---

### Post by Drakkor on 2006-09-19
If you have XP you don't have to reinstall windows,just boot to the XP disk,wait till everything loads and hit "R" for repair,then at the prompt type ```
fixmbr
``` which will write a new master boot record,then follow bulldog's post to reinstall grub ! :p

---

### Post by amcavoy on 2006-09-25
When I used my recovery CD, everything was graphical and I couldn't get a DOS prompt for the 'fixmbr' command.  I ran a system restore and now my Windows partition works, but the grub commands still don't work with the Live CD.  I guess I'll be sticking to Windows on that computer.  Thank you all for your help :) .

---

