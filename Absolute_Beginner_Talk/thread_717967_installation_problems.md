---
title: "installation problems"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Joseph5000 on 2008-03-07
I don't get past resizing the disk
 "an error occured while writing the changes to the storage devices.The resize operation is aborted"
I push continue and it brings me back to partitioning. I choose Guides Partitioning.
It asks for partitioning method: and I choose Guided - resize SCSI1 (o,0,0,), patitioning #1 (sda) and use freed s. and so on I just follow the steps and I come back to the red screen with the error. I checked the Ubuntu disk and its OK. I am lost

---

### Post by taurus on 2008-03-07
I assume you already have windows on that machine and want to dual boot.  Perhaps you need to boot into windows and defrag the harddrive a couple of times first before you try to resize it from the LiveCD.

---

### Post by Joseph5000 on 2008-03-07
Can't do that. MS is for some reason totally messed up and doesn't let me in. What are my options??? and how do I boot from live cd?

---

### Post by uberlube on 2008-03-07
If you are still having problems after the defrag. Give partedmagic a try.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by Joseph5000 on 2008-03-07
Well, I can't defrag, because I can't get into the OS. SO I am at lost ,

---

### Post by taurus on 2008-03-07
You can't get into windows and you want to save it?

---

### Post by uberlube on 2008-03-07
Were you unable to get into M$ before? Or was it just after you resized that you had the problems?

---

### Post by Joseph5000 on 2008-03-07
The MS problem was before, so I thought I install Ubuntu and hope to save some of the files I have. THe hard drive has the space I know that,

---

### Post by taurus on 2008-03-07
Well, you should be able to access your harddrive with windows on it from Ubuntu LiveCD.  Boot your machine with the LiveCD and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That is a lower case letter L, not number 1.

p.s.  LiveCD is the same as the desktop CD.

---

### Post by uberlube on 2008-03-07
If you grab PartedMagic, you can run it as a live CD. From within it you can access your windows partition and save any file that you cant live without. After that you can use the great tools they provide to repartition your HD with enough room for a new windows install as well as for ubuntu. If you have any questions about how to use it to get your files, just ask.

---

### Post by uberlube on 2008-03-07
Sorry taurus, I didnt mean to steal your thunder here. I though you were off doing something else. Listen to Taurus, he'll know what to do alot better than I would. LoL :)

---

### Post by Joseph5000 on 2008-03-07
I understand, but which option in the beginning of the disk do I use to boot over the disk

---

### Post by Joseph5000 on 2008-03-07
I understand you guy's????
I have the following options:
Install in text mode
OEM install
Install Command line
Rescue a broken...
Boot from first hard drive.

which one do I use to boot from this disk??

---

### Post by taurus on 2008-03-07
> **Joseph5000 said:**
> I understand you guy's????
I have the following options:
Install in text mode
OEM install
Install Command line
Rescue a broken...
Boot from first hard drive.

which one do I use to boot from this disk??

You downloaded the alternate CD.  You need to get the desktop CD--LiveCD--though.

> **uberlube said:**
> Sorry taurus, I didnt mean to steal your thunder here. I though you were off doing something else. Listen to Taurus, he'll know what to do alot better than I would. LoL :)

No need to worry.  Go for it.

---

### Post by uberlube on 2008-03-07
Are you using the alternate install cd? If I understand you correctlly you are trying to use the live cd to acces your windows partition right. You cant do this from the alternate install cd, but you can install ubuntu on your HD with it. Stop me if im wrong.

---

### Post by Joseph5000 on 2008-03-07
Alright, got Parted Magic and running. I get some errors: Cluster accounting failed at 13404369(0xcc88ec): extra cluster in$Bitmap

Are there any external ways to defrag the drive like from a live cd??

---

### Post by uberlube on 2008-03-07
Nope a defrag can only be done within windows, and since something is corrupted, your pretty much hooped. Can you get parted magic running or is that an error that you get when trying to boot from it?

---

### Post by Joseph5000 on 2008-03-07
I have Parted open, just don't know really what to do with it. Still learnig

---

### Post by Joseph5000 on 2008-03-07
I just get that error when I double click the big partition

---

### Post by uberlube on 2008-03-07
Ok this is what your probably gonna have to do. Your going to have to mount your windows partition (if you still can) and with it mounted you can save your important data to another medium. Your windows is now completely messed up because you tried to resize it. It is not recommended to use the ubuntu installer to resize an NTFS partition due to this problem, but its ok because you didnt know. What youll have to do after saving your data is format the NTFS partition and reinstall windows. You dont have a choice now. So do you know how to mount a partition from the command line and get to your data?

---

### Post by Joseph5000 on 2008-03-07
Make that a NO

---

### Post by uberlube on 2008-03-07
ok go into the terminal and type in:

fdisk -l

and tell me what partition is the NTFS

---

### Post by Joseph5000 on 2008-03-07
I went into the Parted Magic terminal. And it doesn't mention the NTSF

---

### Post by uberlube on 2008-03-07
did you type in fdisk -l?

---

### Post by Joseph5000 on 2008-03-07
Yes, I did, and it came up with a lot of info, but didn't mentioned the NSTF.
How about we lwet it go. I don't know enough. What would happen if I wipe the disk and try the Ubuntu CD again?

---

### Post by uberlube on 2008-03-07
Ya I think you totally damaged the NTFS beyond even getting you data back. If you want you can use the partitioner in Parted magic to completely format your drive and start from scratch. You can make the partitions for ubuntu in there to. make a swap partition that is 2wice the size of you ram. Then make another partition that is ext3 that you can mount ubuntu on while you are installing. Or just wipe the whole HD and use the guided install and it will take care of everything for you. Whatever youd like.

---

### Post by Joseph5000 on 2008-03-07
Thank you very much for your time. I deeply appreciate

---

### Post by uberlube on 2008-03-07
feel free to click the ribbon with the star under my post and i would be greatly appreciated :lolflag:

---

