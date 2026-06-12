---
title: "hdd to hdd is that possible?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-22
Hello I have 2 hdd both 200gb each and one of them is windows xp the other wone is Ubuntu 6.06 and i want to know if i can get in to the winXP hdd and get the things i need without something bad happening like formation becous i really need some dvd movies that i got on the WinXP hdd please help :KS

---

### Post by jcrnan on 2006-09-22
> **haxer said:**
> Hello I have 2 hdd both 200gb each and one of them is windows xp the other wone is Ubuntu 6.06 and i want to know if i can get in to the winXP hdd and get the things i need without something bad happening like formation becous i really need some dvd movies that i got on the WinXP hdd please help :KS
here: [http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)


That whole faq there will in general give you answer to just about any basic linux question.

---

### Post by haxer on 2006-09-23
Theres tons of things there how would i know what is what? am i going to do it all? :confused:

---

### Post by gn2 on 2006-09-23
I had similar problems trying to read Windows files with Ubuntu on a dual-boot system and cured it by replacing my Ubuntu install with PCLinuxOS.

---

### Post by haxer on 2006-09-23
I dont want pclinux i want ubuntu :) [-o<

---

### Post by gn2 on 2006-09-23
Have you tried XP hdd in external USB enclosure?

---

### Post by DOD1951 on 2006-09-23
How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only

    * Read [#General Notes]("http://ubuntuguide.org/wiki/Dapper#General_Notes")
    * Read [URL="http://ubuntuguide.org/wiki/Dapper#How_to_list_partition_tables"]#How to list partition tables 
[/URL]
    e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS) 
    Local mount folder: /media/windows 

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

    * Append the following line at the end of file 

/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

    * Save the edited file
    * Read #How to remount /etc/fstab without rebooting

---

### Post by haxer on 2006-09-23
Hmm.. then i got to buy a external cabinett and put in my other windows hdd and then i will have to make grub work? Or i could try out the FAQ site i got but i dont know what of those things im going to try out ;)

---

### Post by haxer on 2006-09-23
Ok ill try it thanks

---

### Post by DOD1951 on 2006-09-23
It would be lot easier if you had a dual boot pc with Windows being the other  operating system which you might want to use at times like this :)

---

### Post by haxer on 2006-09-23
Ok now i tried to "mount" my hdd 

ill only get this 

oem@haxer:~$ sudo mount -a
mount: /dev/hda1 already mounted or /media/windows busy
mount: according to mtab, /dev/hda1 is mounted on /tmp/disks-conf-hda1
oem@haxer:~$



How to open up my windows hdd?

---

### Post by haxer on 2006-09-23
Hmm.. when i try to open my hdd it says 

you dont have the rights bla bla bla--- "disks-conf-hda1".

---

### Post by haxer on 2006-09-23
Please help [-o<

---

### Post by gn2 on 2006-09-23
I know you want Ubuntu, I do too, it runs single booted on my laptop, but for the reasons you are discovering, and my own laziness I opted to go with PCLinuxOS on my dual hard drive desktop PC.
It's easier and I like easy.
Others may prefer the hard way and good luck to them.

---

### Post by haxer on 2006-09-23
Thanks :) hehe..

---

### Post by haxer on 2006-09-23
> **haxer said:**
> Hmm.. when i try to open my hdd it says 

you dont have the rights bla bla bla--- "disks-conf-hda1".

How to i get this working?

---

### Post by haxer on 2006-09-23
Please help me [-o<

---

### Post by macdo on 2006-09-23
Just install the ntfs-3g driver: read/write access to ntfs disks!

[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

It's very easy, and seems perfectly stable.

---

### Post by haxer on 2006-09-23
Why cant i just do it with the instructions ive got already gaaaah i only wont to open my other hdd so i can get like 5gb of data so i can get rid of windowsXP and totally just use Ubuntu can someone help me please im begging [-o<

---

### Post by macdo on 2006-09-23
The thing is that the instructions you've got already don't work. That's why people are suggesting rather more arcane things (although suggesting that you install PCLinux is a bit cheeky, I agree :-) )

Having said that, try this, to remount: ```
sudo umount -a
sudo mount -a
```
Note that after the umount command, you will probably receive some errors - don't worry about them, it's just that you can't unmount disks in use.

---

### Post by haxer on 2006-09-23
Omfg thank you so much oooh im almost hugging you yout the man thanks :KS

---

### Post by haxer on 2006-09-23
Will i get problems with grub now? :S

---

### Post by macdo on 2006-09-23
I take it that worked...
Cool!

---

### Post by macdo on 2006-09-23
> **haxer said:**
> Will i get problems with grub now? :S

Grub deals in operating systems, not disk mounting, so you shouldn't, no.

---

### Post by haxer on 2006-09-23
Omg i must say that you just helped me really much i cant describe how much :)

---

