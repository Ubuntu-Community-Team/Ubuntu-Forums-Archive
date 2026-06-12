---
title: "2 annoying things:"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-11-15
well, i have two hard drives and the second one was connected when xp was on but formatted since. I have no idea what type (NTFS, FAT32...) but i'ts just not showing up in ubu. Secondly There is an offer 

[http://lifehacker.com/software/featured-windows-download/free-evernote-licenses-today-only-normally-50-323299.php ]("http://lifehacker.com/software/featured-windows-download/free-evernote-licenses-today-only-normally-50-323299.php")
heres my uplaoded link to it:
[http://www.mediafire.com/?fez4z1ku2xt](http://www.mediafire.com/?fez4z1ku2xt)

That i really want. But when i run the setup.exe under wine nothing happens, the offer expire in 6 hours so be quick please....

---

### Post by LaRoza on 2007-11-15
To get the partition (disk) information:

```

sudo fdisk -l

```

---

### Post by GavinZac on 2007-11-15
> **nikoPSK said:**
> well, i have two hard drives and the second one was connected when xp was on but formatted since. I have no idea what type (NTFS, FAT32...) but i'ts just not showing up in ubu.
Where did you look for it?

---

### Post by nikoPSK on 2007-11-15
filesystem/media and computer I will try that but i need to know why the file isnt going as well....

---

### Post by nikoPSK on 2007-11-15
> **LaRoza said:**
> To get the partition (disk) information:

```

sudo fdisk -l

```

heres what i got:

niko@home:~$ sudo fdisk -l
[sudo] password for niko:

Disk /dev/sda: 20.4 GB, 20496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15f4a6d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2382    19133383+  83  Linux
/dev/sda2            2383        2491      875542+   5  Extended
/dev/sda5            2383        2491      875511   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5b5a5b5

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 1014 MB, 1014497280 bytes
17 heads, 32 sectors/track, 3642 cylinders
Units = cylinders of 544 * 512 = 278528 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3643      990704    b  W95 FAT32
niko@home:~$

---

### Post by LaRoza on 2007-11-15
It is /dev/sdc1 and is FAT32.

---

### Post by nikoPSK on 2007-11-15
then why cant I see it under those two locations i mentioned? here is the output from when i click the exe (I reinstalled wine)

Cannot open Setup.exe

The filename "Setup.exe" indicates that this file is of type "executable". The contents of the file indicate that the file is of type "DOS/Windows executable". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "DOS/Windows executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.

---

### Post by LaRoza on 2007-11-15
Right click it, and select Wine.

---

### Post by nikoPSK on 2007-11-15
yes, i've tried that. I'm not that dumb :p, could you try getting it from the link on my first post and see what happens for you?

---

### Post by LaRoza on 2007-11-15
> **nikoPSK said:**
> yes, i've tried that. I'm not that dumb :p, could you try getting it from the link on my first post and see what happens for you?

I didn't mean to imply you were. I am downloading now, give me a couple of minutes...

---

### Post by nikoPSK on 2007-11-15
> **LaRoza said:**
> I didn't mean to imply you were. I am downloading now, give me a couple of minutes...

Thats the reason of the smily face. i have quite alot of linux knowledge. ive tried 16 different Os's and started using it (just fooling around) in vmware like two years ago. I had never actaully used it without emulation until windows got a virus and I decided that was it. im quite happy with all that ubuntu has to offer.:D

---

### Post by LaRoza on 2007-11-15
It won't work because it needs DLL's that are not available. The download page did say Windows only...

You can install it any time you want, the download was just limited in time. -- EDIT Perhaps not, but I don't like that type of license...

---

### Post by nikoPSK on 2007-11-15
if there is any place I can get the dll's please tell... 

>  ~**Venki**

Nope, it doesnt mean that. Giveawayoftheday's catch is that you have to install the software within 24 hrs of its release in the website. When you install the software, the activation program will kick in and check the giveawayoftheday.com site to see whether the give away is still available for the day. If so then the program will proceed to install or else it will quit. Once installed its free for ever until you change your PC.
Hope this explains. There are other programs giveaway that has two files a setup.exe and activate.exe. You have to click activate.exe to run the registration of the program. It creates some registry files for the program or gives a pop up window with the registration information.
I have been a user of GOTD software for almost a year. Sometime the softwares that they give away are real good ones.

---

### Post by LaRoza on 2007-11-15
Those DLL's are probably not legally dispersable.

Do you have a Windows setup available?

---

### Post by nikoPSK on 2007-11-16
unfortunately not, (I'm too lazy to hook it up right now...) well, I guess i can hold off but thanks for everything else. (How do i get it to actually *show *my drive?

---

