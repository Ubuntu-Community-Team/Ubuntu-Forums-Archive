---
title: "Mounting.. not block device"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by 86honda on 2006-06-07
hey im a newbie to linux altogether
1...first for starters i had installed ubuntu 6.06 on vmware(5.5.1 build 19175)        in win xp..
but it didnt work well because vmtools said it coud not find compiling tools when im sure i had installed them...
2...so i switched back to 5.10 ..
now i installed vmtools and it was successful..
so i went ahead to mount my windows file systems.. i shared 2 drives. but neither appears in /dev .. they are seen in /mnt but have a small cross on the icon.. when i try to manually mount it says the device is not a block device.. 

Please help if u can find a solution for either of the problems.. because even tho id like to start with 6.06 i uninstalled it thinking that vmware is not yet compatible with it

---

### Post by giftnudel on 2006-06-08
Hi, I'm not really familiar with vmware but there are a couple of outstanding questions that I didn't get from your post.

First let me rephrase what I believe you did:
1. You only have Windows XP on your PC and don't want so give Ubuntu a partition, so you tried to install it in vmware. 
2. With the 6.06 LTS release, you found out some problems (vmtools could not be found - This is the first problem)
3. You then tried Ubuntu 5.10 and this worked, however you could not mount your windows filesystems (This is the second problem)

There is no sense in trying to answer problem #1, since you don't have it installed anymore unless I know the solution, which I don't, so let's try #2:

1. How did you try to mount your drives and why do you think they should be in /dev? I believe you need samba and network in order to make them work.
2. Have you got networking to work in Ubuntu?

---

### Post by 86honda on 2006-06-08
First off, No i havent got networking on Ubuntu.. but to share my existing windows partitions VMware says i only have to share them and they'll be mounted on linux..

1. I have Win XP/98 Dual boot .. and im a newbie to linux so i installed 6.06 LTS on VMWARE.... 
2. VMWARE told that its version of VMTOOLs is not compatible with the version of ubuntu..
3 so i switched to 5.10.. now i know that from vmware every drive is mounted on /mnt and does not go in /dev.. so i tried configuring that.. im facing a new problem altogether and my frnds working on linux cudnt figure it out..

VMware makes a folder /mnt/hgfs 
in my friend's computers this was it.. they just shared their windows drives and they appeared inside hgfs...
in my case i can see all the files but i cant access them.. they had little crosses next to them.. then i found out that means permissions problem..
so i changed permissions using chmod..

NEW PROBLEM:::(sorry for making this so long)
now the hgfs folder's GUI icon is a footprint which i understand stands for unknown file format.. 
BUT
it can still be accessed through the console.. i can even read all files through console!! so basically my problem is solved i just need to figure out how to get those files on the GUI..
my frnds tell its not a beginners forum problem ..lol

---

### Post by giftnudel on 2006-06-10
Thanks for the clarification, I didn't know that vmware mounted the drives automatically, but that's probably why you need vmtools.

There are still some problems with the permissions, so let's start there:

can you please post the output of
```

ls -l /mnt/
ls -l /mnt/hgfs
id
```
(all run in a terminal)

And well, you are right, this is a very common problem

regards, 
giftnudel

---

### Post by 86honda on 2006-06-10
ls -l /mnt :permission denied  total 0
ls -l /mnt/hgfs/ : permission denied
id: 
uid=1000(honey) gid=1000(honey) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),106(admin),1000(honey)

---

### Post by giftnudel on 2006-06-13
Hi,
 you need some access to /mnt, which should be default, please do ```
sudo chmod a+rx /mnt
``` and post the output of ls -l /mnt again.

giftnudel

---

### Post by 86honda on 2006-06-13
thanks alot.. atleast im back to where i started and its not worse. 
well ls -l /mnt gives::
total 2
dr -x------- 1 root root 4096 2006-06-15 01:18 hgfs

hope u canfix it further...
i can see crosses in gui.. 
can access txt files and linux files .tar.gz etc from gui
but media files yield an error saying video output device is in use..

---

### Post by giftnudel on 2006-06-15
I'm glad it worked, do ```
sudo chmod +rx /mnt/hgfs
``` and reboot the vmware machine, you should have access then, if not, do ```
cat /etc/fstab
``` and post the output here

giftnudel

---

