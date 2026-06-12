---
title: "Have one hard drive duplicate the other"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-08-26
Hello. I have two identical 500 GB hard drives on Ubuntu. How can I set it up so that the second hard drive always duplicates the data on the first hard drive? This is just to give me protection if one drive fails. I want this duplication to be real time. Thank you.

---

### Post by Scorpuk on 2007-08-26
What you need is software RAID 1 (Mirroring)


Not sure how you go about switching an existing system to RAID 1.


Anywho the installation process for RAID is not exactly easy as you need to use the ALT cd for a text based installation. :(



Just remember to backup your vital data before you attempt anything. ;)

---

### Post by amitroy5 on 2007-08-26
Well, my PC will then have a total of 3 hard drives. The first hard drive will contain the operating system.

The second and third will be dubpicating each other. Thus, I won't have to worry about reinstalling Ubuntu.

---

### Post by Scorpuk on 2007-08-26
Ahh cool. 


Installing on RAID was a pain. Did it for my MythTV server.


Anywho for you if you follow this guide: [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188) 

Then you should be good to go.

Remember this will format both drives so backup, backup, backup ;)


Oh yeah and where it says:

```
sudo mdadm –create –verbose /dev/md0 –level=5 –raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1
```

you need to type:

```
sudo mdadm -–create -–verbose /dev/md0 --level=1 -–raid-devices=2 /dev/sda1 /dev/sdb1
```

replacing sda1 and sdb1 with the correct drives you wish to raid.


```
sudo fdisk -l
``` (lower-case L)

will show you what drives you have connected. (I think)


If unsure come back here and ask some more. No harm in that and stops you doing something you can't undo ;)

---

### Post by amitroy5 on 2007-08-27
I am getting the following error:

user@Server:~$ sudo mdadm &#8211;create &#8211;verbose /dev/md0 -level=1 &#8211;raid-devices=2 /dev/sdb1 /dev/sdc1
mdadm: An option must be given to set the mode before a second device is listed
user@Server:~$ 

I'm pretty sure I set an option.

---

### Post by Scorpuk on 2007-08-27
looks like you only have one - where you need two -- with each option:

```
user@Server:~$ sudo mdadm –create –verbose /dev/md0 -level=1 –raid-devices=2 /dev/sdb1 /dev/sdc1
mdadm: An option must be given to set the mode before a second device is listed
```

try

```
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
```


I know the page I referenced only shows a single - on each option, but if you check the help file it shows two


```
mdadm --help
```


Goodluck

---

### Post by amitroy5 on 2007-08-27
Thank you so much. I was able to raid my two hard drives. If one drive were to fail, how would I know? Also, if it did fail, could I separate the drives and mount each as a single drive?

Also, on the instructions found here: [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)
Is it OK if I skipped this part:

```
sudo echo &#8220;DEVICE partitions&#8221; > /etc/mdadm/mdadm.conf
sudo mdadm &#8211;detail &#8211;scan >> /etc/mdadm/mdadm.conf
```

The reason I skipped this part was because I could notget it to work. Thank you.

---

### Post by Scorpuk on 2007-08-27
Ahh when you tried that part did you use 1 - or 2 -'s?


again the command should be:


```
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```


As for if a drive fails.


Not really sure, but I think it woudl tell you which drive failed, although as to which controller / cable the drive is connected I'm not sure.


You can find more info on raid here: [http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

including drive failure.

---

