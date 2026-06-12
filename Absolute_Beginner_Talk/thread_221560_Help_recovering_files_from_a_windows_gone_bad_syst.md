---
title: "Help recovering files from a windows gone bad system"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by kolwon on 2006-07-23
I'm trying to save some of my fathers documents from the desktop of a windows install. I put in the live cd and booted in linux, but i can't find the files. my hard drives aren't showing up in the places menu. i'm using the breezy. all that i want to do is mount a couple fat32 partitions and copy some things to my jump drive. when i put in my jump drive it shows up under places and im able to use it just fine. i just can't find my windows partitions while using the live cd.

---

### Post by Saphira on 2006-07-23
[http://doc.gwos.org/index.php/BreezyGuide](http://doc.gwos.org/index.php/BreezyGuide)

Have you looked here?

---

### Post by confused57 on 2006-07-23
Probably just a matter of mounting the partitions:

[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

### Post by catlett on 2006-07-23
You need to manually mount the partitions. To find out the name of the partitions, put this command in the terminal (the terminal is found under Applications<Accessories<terminal)```
 sudo fdisk -l
```
Just for the sake of example, I am going to use /dev/hda1 and /dev/hda2 as the partitions. Obviously replace them with the naming from fdisk.
The other party is to make sure they are fat32. Fdisk will tell you this as well but it seems you already know.
First you have to make a location to mount them to.
```
sudo mkdir /media/windows1
```
```
sudo mkdir /media/windows2
```
Now you use the mount command to mount them.
```
sudo mount /dev/hda1 -t vfat /media/windows1
```
```
sudo mount /dev/hda2 -t vfat /media/windows2
```
If all goes well, there will be 2 icons on your desktop with those 2 partitions. If the icons do not appear, then go to the top panel and select Places<Computer<Filesystem<Media inside the media folder will be the 2 folder windows1 and windows2. Just double click to open them.
What medium are you useing to copy them to? If you have an issue with the cd mounting, just post back with the error.

---

### Post by kolwon on 2006-07-23
thanks alot for that link saphira, it seemed to have eluded me earlier. the psychocats one wasn't of any help when i looked. mounting the drives wasn't a problem, now my only problem is that i don't have permissions to do anything. hopefully i get this figured out on my own, thanks for all of the replies.

---

### Post by catlett on 2006-07-23
Launch the file browser with this command and you will be root. You can then open any file or folder and drag/drop.
In the terminal
```
gksudo nautilus
```

---

