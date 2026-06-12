---
title: "Trying to access music folder in OSX partition."
date: 2010-10-22
forum: Apple Hardware Users
---

### Post by mrmayor92 on 2010-10-22
Hi, I am trying to access my music folder in my OSX partition but every time I click double click on it I get an error message that says "You do not have the permissions necessary to view the contents of "Music". I would really like to use Ubuntu more because I find it to be a wonderful experience so any help is appreciated, thanks!

I am running a Macbook Pro 5,5 if that helps.

---

### Post by linux-hack on 2010-10-22
well you just need to mount it as root.

so you open a terminal and type this :
You create first the macosx folder with 
```
sudo mkdir /mnt/macosx

```
after you mount the partition with this command :
```
sudo mount -t hfsplus /dev/sda1 /mnt/macosx
```
The sda1 is an example. You need to put the name of your partition that you can get with ```
sudo fdisk -l
```
if you want it permanently you need to put this in the /etc/fstab
a line like this :
```
/dev/sda1 /mnt/macosx hfsplus defaults 0 0
```

---

### Post by mrmayor92 on 2010-10-23
> **linux-hack said:**
> well you just need to mount it as root.

so you open a terminal and type this :
You create first the macosx folder with 
```
sudo mkdir /mnt/macosx

```
after you mount the partition with this command :
```
sudo mount -t hfsplus /dev/sda1 /mnt/macosx
```
The sda1 is an example. You need to put the name of your partition that you can get with ```
sudo fdisk -l
```
if you want it permanently you need to put this in the /etc/fstab
a line like this :
```
/dev/sda1 /mnt/macosx hfsplus defaults 0 0
```

Pardon me for being a complete noob in ubuntu, but for step two the name of my partition is two words "Macintosh HD" do I type in the space or an underscore? And how do I go about editing the /etc/fstab file and where do I put
```
/dev/sda1 /mnt/macosx hfsplus defaults 0 0
```

Again thank you!

---

### Post by linux-hack on 2010-10-24
Ok. So to edit the /etc/fstab file you type this in a terminal :

```
gksudo gedit /etc/fstab
```
And paste in:
```
/dev/sda1 /mnt/macosx hfsplus defaults 0 0
```

to find out the name of your partition you have to type in a terminal :
```
sudo fdisk -l
``` and post here the output.
The "Macintosh HD" is the label of your partition.

---

### Post by mrmayor92 on 2010-10-25
AHH i give up, i cannot figure this out for the life of me. thanks for the help though

---

### Post by WanderingOak on 2010-10-25
You might want to take a look at [this]("http://ubuntuforums.org/showthread.php?t=1604669") thread here. I had a similar problem and was able to fix it by changing my Ubuntu UID so it was identical to my Mac UID. Rather than using the terminal as I did, I would change my UID through 'Users and Groups'. You can get your Mac UID in Ubuntu by examining the details of your Mac directories.

---

