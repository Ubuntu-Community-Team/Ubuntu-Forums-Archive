---
title: "I can't find any step by step information"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by rickjack on 2006-11-12
](*,) 

I've been reading all of the official info. about Ubuntu and all seem to require a certain pre-requisite understanding of the way the OS works.
I wanted to access media files from my XP partition on my computer and it seems that I just mount the partition using "sudo umount /media/hda1"
but there is no explination as to where to type this in.
I know I click on system, administrator, then disk and then click partition, but that's the end of the explination. Everything just says type that in, but where. I typed it in to the access path window and clicked ok, but that did nothing. So I clicked on the change button which took me to another window having no clear place to input the code. 
I downloaded Ubuntu with the advice of a friend that told me I could run my system faster without as many bugs as windows and that I would easily be able to access all of my files from XP, but that isn't the case. Ubuntu is not at all intuitive. 

Currently my XP partition reads: Device: /dev/hda1, File system: Windows NTFS, Access path: /tmp/disks-conf-hda1 

The acess path for Unbutu is blank, and the file system is "Extended 3"

What do I do?

thanx,
rick

---

### Post by guitarist549 on 2006-11-12
Go to Applications | Accessories | Terminal

---

### Post by rickjack on 2006-11-12
> **guitarist549 said:**
> Go to Applications | Accessories | Terminal

Ok, so I went to that window and pasted in sudo umount /media/hda1
after some other code that was already there. But, I hit return after typing in the code and it
asked my for a password. I tried to type it in but nothing would post.

rick

---

### Post by Rui Pais on 2006-11-12
sorry, but are you trying to mount or unmount your partition?

---

### Post by Irony on 2006-11-12
Look here;

[http://makuchaku.info/amnesty/#windows](http://makuchaku.info/amnesty/#windows)

What this does is create a folder called windows in the media folder. You then mount your windows partition to it, i.e. view your windows partition throught the windows folder.

If you scroll down a bit you can also find instructions on how to make it mount on boot up.

---

### Post by bodhi.zazen on 2006-11-12
> **rickjack said:**
> Ok, so I went to that window and pasted in sudo umount /media/hda1
after some other code that was already there. But, I hit return after typing in the code and it
asked my for a password. I tried to type it in but nothing would post.

rick

LOL :lol:

[list=number][*]When you use "sudo" it will ask for a password. Use your log-in password and then hit enter. Nothing will appear on the screen as you typ for security reasons.

[*]umount will UNMOUNT the partition. This is not what you want, you want MOUNT.

[*]Like this (assuming your windows aprtitions in /dev/hda1):```
suod mkdir /mnt/windows
sudo mount /dev/hda1 /mnt/windows -t ntfs
```

[*]Edit fstab to make the mount automatic at boot:```
sudo gedit /etc/fstab
```Add:> /dev/hda1 /mnt/windows ntfs auto,users 0 0[/list]
See here for more information; [fstab](http://ubuntuforums.org/showthread.php?t=283131)

To mount ntfs with read/write use [ntfs-3g](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support)

---

### Post by aysiu on 2006-11-12
Here are some step-by-step instructions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

