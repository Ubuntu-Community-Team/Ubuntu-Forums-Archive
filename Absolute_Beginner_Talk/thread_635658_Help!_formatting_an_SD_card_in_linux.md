---
title: "Help! formatting an SD card in linux"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Watchtow3r on 2007-12-08
I'm trying to format my sd card from ntfs to something else for linux. Won't ntfs not work in linux? sorry, I don't know. Anyways, I want to format it to a format that works good with linux. Which is a good one to do, and how do I do it? I tried using the code on [this]("http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/how-do-i-format-an-sd-card-to-fat16-using-linux-so-that-i-can-use-it-on-my-pda-533725/") page, but I got this error:  

ubuntu@ubuntu:~$ sudo mkdosfs -F 16 /dev/sda1
mkdosfs 2.11 (12 Mar 2005)
WARNING: Not enough clusters for a 16 bit FAT! The filesystem will be
misinterpreted as having a 12 bit FAT without mount option "fat=16".
mkdosfs: Attempting to create a too large file system

What's wrong? also, is sda1 necessarily the name of my sd card?  I've been trying to put Ubuntu onto the sd card following [these]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") instructions, but when I type in the fdisk -l command, instead of getting something showing /dev/sdb for my flash drive, it says /dev/mmcblk0. What's wrong? Please help!

---

### Post by Nano Geek on 2007-12-09
Yes, NTFS will work in Linux, but most SD cards are FAT32. Try running this and see what happens. ```
sudo mkdosfs -F 32 /dev/sda1
```

---

### Post by Watchtow3r on 2007-12-09
ok, I did that, and I got this:

ubuntu@ubuntu:~$ sudo mkdosfs -F 32 /dev/sda1
mkdosfs 2.11 (12 Mar 2005)
ubuntu@ubuntu:~$ 

It looks like it did something, but when I look at the device's properties, in the filesystem type it still says ntfs.

---

### Post by Nano Geek on 2007-12-09
Try unmounting it and then plugging it back in.

---

### Post by Watchtow3r on 2007-12-09
I did and it's still saying ntfs

---

### Post by Nano Geek on 2007-12-09
Try installing GParted, and see if you can change it from there. ```
sudo apt-get install gparted && sudo gparted
```

---

### Post by Watchtow3r on 2007-12-09
I'm running linux from the live cd, can I install things in this? also, sorry, i'm new, how would I use gparted to format the card?

---

### Post by Stormspireiv on 2007-12-09
GParted should be already on the live cd. Just go to System>Administration>Partition Editor on the menu bar at the top.

Or if you are running Feisty not Gutsy, System>Administration>GNOME Partition Editor

---

### Post by mridkash on 2007-12-10
Hey wait a minute, how can sda1 be a sd card. sda or sdb drives are SATA hard drives not sd cards. 

sda1 means that your SATA drive has a partition. It may be your windows partition if you dual boot. Check to see. That command might have erased that partiton.

SD card comes up as mmcblk0 use this in the command not sda1

---

### Post by rockinlinux on 2007-12-10
> sda1 means that your SATA drive has a partition. It may be your windows partition if you dual boot. Check to see. That command might have erased that partiton.

SD card comes up as mmcblk0 use this in the command not sda1

+1

---

### Post by Nano Geek on 2007-12-10
> **mridkash said:**
> Hey wait a minute, how can sda1 be a sd card. sda or sdb drives are SATA hard drives not sd cards. 

sda1 means that your SATA drive has a partition. It may be your windows partition if you dual boot. Check to see. That command might have erased that partiton.

SD card comes up as mmcblk0 use this in the command not sda1I can't believe I didn't see that. I hope that his data is OK. ](*,)

---

### Post by Watchtow3r on 2007-12-11
uhh... yeah... just to follow through you're exactly right... I ended up erasing everything on my hard drive. I'm now in the  process of purchasing an external hard drive enclosure so that I can use some recovery software to try to get my data back. I'm using a different computer now as mine won't even boot up. Thanks for the help every1 anyways.

---

### Post by rockinlinux on 2007-12-11
i dont think you are going to be able to get your data back, im pretty sure it is GONE GONE. also if you are going to buy a external case you could save some money and just buy a sata/ide to USB adapter. plus these are more handy because you cand use them with cd, dvd, sata and ide HD's and anything else that is sata or IDE...i have one and i love it. you should be able to get one for less than 20 $
[COLOR="Red"][U][B]
note to everyone!! [/B][/U][/COLOR]You guys need to read very careful before you tell new people what to do. this simple thing costed this guy all his data, and if you dont know the sda cant be a SD card then you should not be helping him format it....

im not meaning to be mean but you all know a very bad thing happened in this thread. I understand that mistakes happen and there is no one at fault here....just please try to be careful.....oh and please no one take it personally...like i say, its no one fault....mistakes happen. 

Watchtow3r- Im very sorry for what happened to you, just know that a thing like this very rarly happens here. These people do know what they are doing, they made  a simple mistake and im sure feel bad about it. once again you can trust us but im sorry.

---

### Post by Nano Geek on 2007-12-11
> **rockinlinux said:**
> [COLOR=Red]_**note to everyone!! **_[/COLOR]You guys need to read very careful before you tell new people what to do. this simple thing costed this guy all his data, and if you dont know the sda cant be a SD card then you should not be helping him format it....

im not meaning to be mean but you all know a very bad thing happened in this thread. I understand that mistakes happen and there is no one at fault here....just please try to be careful.....oh and please no one take it personally...like i say, its no one fault....mistakes happen. 

Watchtow3r- Im very sorry for what happened to you, just know that a thing like this very rarly happens here. These people do know what they are doing, they made  a simple mistake and im sure feel bad about it. once again you can trust us but im sorry.I too am very sorry Watchtow3r. If I had looked closer I might have seen that, but we all make mistakes, and it's always best, no matter what, to make a backup of your data. 

If you still trust me with your computer, I'll do anything I can to help you get set-up again.

---

### Post by mridkash on 2007-12-12
This is a really serious issue. A format command is one of the listed dangerous commands in linux. A bad response by "asjdfwejqrfjcvm msz34rq33" has caused harm to a users computer.

The OP was very clear in describing the problem

> **Help! formatting an SD card in linux**
>  What's wrong? also, is sda1 necessarily the name of my sd card?

---

### Post by mattmole on 2007-12-12
Hi All,

Some of my memory sticks / memory cards show up as /dev/sdaX. It was a VERY unfortunate thing to happen but noones fault!

mattmole

---

### Post by Nano Geek on 2007-12-12
> **mridkash said:**
> This is a really serious issue. A format command is one of the listed dangerous commands in linux. A bad response by "asjdfwejqrfjcvm msz34rq33" has caused harm to a users computer.

The OP was very clear in describing the problemYes it is serious, but why state that again. I have already apologized to the OP, and, if he wants it, I have offered to him any help that I can give. 

In all fairness though, that command came from LinuxQuestions.org and I simply didn't look at what it was formating. 

So I again apologize to Watchtow3r and I will help you to get Ubuntu set up for you again if you want me to.

---

### Post by mridkash on 2007-12-12
I'm sorry, I sound rude there. I just committed a mistake myself by clicking on post reply button before looking at the second page with your post.

Anyways, the error started when a normal end-user like OP copied and pasted command from a geeky website ([this page]("http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/how-do-i-format-an-sd-card-to-fat16-using-linux-so-that-i-can-use-it-on-my-pda-533725/")) without knowing what that means. 
Actually, the damage would already be done if that fat-16 error didn't came up.

That page comes up when you search for "sd card format linux" in google.
I admit its nobody's fault here. 
Sorry for being rude.

---

### Post by Nano Geek on 2007-12-12
> **mridkash said:**
> I'm sorry, I sound rude there. I just committed a mistake myself by clicking on post reply button before looking at the second page with your post.

Anyways, the error started when a normal end-user like OP copied and pasted command from a geeky website ([this page]("http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/how-do-i-format-an-sd-card-to-fat16-using-linux-so-that-i-can-use-it-on-my-pda-533725/")) without knowing what that means. 
Actually, the damage would already be done if that fat-16 error didn't came up.

That page comes up when you search for "sd card format linux" in google.
I admit its nobody's fault here. 
Sorry for being rude.Don't worry about it, though I could bang my head against the wall for not seeing that.

---

