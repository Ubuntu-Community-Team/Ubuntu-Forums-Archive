---
title: "Using ubuntu to recover HD data"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by JuliusT on 2006-12-20
I am tryin to use ubuntu to recover some HD data (My friend told me I could run ubuntu from the CD) since my WindowsXP partition seems to be corrupted. I know absolutely nothing about linux other than what I have read on a couple of posts.

To the problem, I burned the latest version of Ubuntu onto a cd and put it into my laptop before start up and restarted.

The Ubuntu dialouge shows up and I select "Start or Install Ubuntu" and it displays the loading linux kernal dialouge (which completes). Now at the Ubuntu loading screen, i get the following error

```

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
(initramfs)

```

upon pressing ctrl+alt+F1 i get

```

cp: unable to open '/root/var/log/': No such file or directory
mount: Mount /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mount /sys on /root/sys failed: No such file or directory
mount: Mount /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

```

Im pretty sure i got a clean burn and download of the ubuntu cd image, and all my laptop hardware is working correcty.

I have read this post:
[http://ubuntuforums.org/showthread.php?t=301529](http://ubuntuforums.org/showthread.php?t=301529)

and only understood that he installed Fedora Core 6, another OS that has the fix to the problem. But I have no idea of the steps he spoke of to extract the needed files nor am I willing (or have the means) to install Fedora Core 6.

As I said before, I am not versed in Linux commands so I ask if anyone can help me with a simple solution or fix and if not simple, please explain to me step by step what i need to do in order to get Ubuntu to run straight off a CD so that I may use it as an interface to recover data from from my HD.

Thank in advance with anyone who can provide any insight to my problem.

---

### Post by LookTJ on 2006-12-20
NTFS system mount [url=http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_onlylink[/url]

FAT system mount [link](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

to find out what partition your Windows is

type this in terminal.

```
sudo fdisk -l
```

---

### Post by bluefrog on 2006-12-20
if you need quick hd data recovery it would be simpler to use knoppix livecd and have another computer hooked on your network to transfer the files to.

James

---

### Post by JuliusT on 2006-12-20
bump, any other suggestions?

---

### Post by JuliusT on 2006-12-20
Ok, i tried using knopnix, it ran fine on my system. But upon further inspection some problems occured:

It did not detect the partition containing the data i need to recover
It did not detect my USB hardrive

Although it was able to detect 2 seprate partitions, it seemed to have created one for itself on the freespace of my internal hardrive and it also detected the previous partition in which i attempted to install windows on.

I also checked to see if my data was a seprate partition so that i did not mistakenly erase it, I did this by inserting a windows cd, looking to see which partitions it detects.

Weird thing is that it detects 3 entities:

Unpartition space - 8mb
D: Partition2[NTFS] - 5114MB (4582MB free) <failed attempt to install windows on a seprate partition on internal HD)
C: Partition1[NTFS] - 71194MB (6779MB free) <original data im trying to recover on internal HD

This is really bugging me and i need to get that data quick... anyone tell me how i can get Knoppix to detect?

---

