---
title: "Previous Files"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Dipz on 2006-07-08
Hi, im totaly new to linux and on my hdd i had files from my windows day... i'd like to retrieve them while using linux but i dont know how.

for example i dont know how to search my hdd for my mp3's using the music player.

all help is appreciated

Dipz

---

### Post by Sonofmoog on 2006-07-08
Go to Places Menu, Search for Files.  If you have multiple partitions, they will be mounted (shown) under the /media folder.

---

### Post by Dipz on 2006-07-08
tired that, no luck. 

forgot to mention that my hdd used to be on windows, and im using a live cd at the moment, i havent installd fully, as i dont want to loose all my files

sorry

Dipz

ps: i checked, and according to ubuntu, im not the owner of the drive and therefore i cant change the permissions

---

### Post by Sonofmoog on 2006-07-08
OK.  Open a console Window on the LiveCD.  Issue the following commands:

```
 sudo mkdir /media/windows 
```

then

```
sudo mount /dev/hda1 /media/windows 
```

That should give you access to your Windows folders .. 

Or .. 

I don't recall if Ubuntu LiveCD has command line options.  Press F2 at the prompt to see the help.  You're looking for something that begins fstab

From the LiveCD prompt, issue this command:

```
livecd fstab=rw,auto
```

That should automatically mount your hard drive and all its partitions and give you access.

---

### Post by Dr. Nick on 2006-07-08
Try here

[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

---

