---
title: "Linux Live question"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by vm367 on 2008-03-07
sorry if this is answered somewhere but im having trouble strting up windows and I decided to run the ubuntu linux live cd, I have it running, is there anyway I can access any of the files that are on the harddrive, such as a word file I had saved in windows. I dont want to open it I just want to e-mail it to myself.  THANKS

---

### Post by x05 on 2008-03-07
I remember there was one Live disk that I did that. Either SLAX, or Ubuntu. Anyways, the Live disk doesn't want to boot.. hes playing hard to get :rolleyes:
Anyways, if someone doesn't help you before I get my disk working, I can get you an answer in about 35 minutes.

---

### Post by taurus on 2008-03-07
You just have to mount your harddrive first before you can access it.  Open a terminal and post the output of this command here to see which partition is your windows.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Crafty Kisses on 2008-03-07
> **x05 said:**
> I remember there was one Live disk that I did that. Either SLAX, or Ubuntu. Anyways, the Live disk doesn't want to boot.. hes playing hard to get :rolleyes:
Anyways, if someone doesn't help you before I get my disk working, I can get you an answer in about 35 minutes.

I think Knoppix would let you access your files.

---

### Post by x05 on 2008-03-07
Ah thanks. Thats what it was!

---

### Post by miluns on 2008-03-07
You should be able to click on places in the top panel and select the hard drive you need.


ETA: Oh well too late. You guys are fast!!

---

### Post by vm367 on 2008-03-07
ok, I assume blocks reffers to the size of the HD, what do I do once the list opens?

DAm you guys are fast, so you would recommend I get knoppix instead of ubuntu cause it will easily let me access my files?

---

### Post by Tatty on 2008-03-07
> **vm367 said:**
> ok, I assume blocks reffers to the size of the HD, what do I do once the list opens?

Post the output on here.  Copy and paste it.

Then we can see which one your windows partition and hopefully give you a command to mount it.

---

### Post by vm367 on 2008-03-07
Device        Boot      start       End     Blocks      Id            System
/dev/sda1                 1          8       64228+     de         dell utility
/dev/sda12                9         1314     10485760    7         HPFS/NTFS
/dev/sda13      *       1314        19131    143117312   7         HPFS/NTFS
/dev/sda14              19131       19458    2621440     f         W95 Ext'd (LBA)
/dev/sda15              19131       19458     2620416    dd        Unknown

---

### Post by taurus on 2008-03-07
```
sudo mkdir /media/sda12 /media/sda13
sudo mount -t ntfs /dev/sda12 /media/sda12 -o umask=0222
sudo mount -t ntfs /dev/sda13 /media/sda13 -o umask=0222
df -h
```

---

### Post by vm367 on 2008-03-07
its telling me  mkdir: invalid option --t

---

### Post by taurus on 2008-03-07
I think you have mixed up the two commands.  

What was the exact command that you ran to get that error message?

---

### Post by vm367 on 2008-03-07
```
sudo mkdir /media/sda12 /media/sda13
sudo mount -t ntfs /dev/sda12 /media/sda12 -o umask=0222
sudo mount -t ntfs /dev/sda13 /media/sda13 -o umask=0222
df -h
```

---

### Post by taurus on 2008-03-07
Which command from above did you run to get this error message, "mkdir: invalid option --t"?

---

### Post by vm367 on 2008-03-07
my bad, I ran the whole thing, sorry this the first time I have dealt with linux ever, or with code, which order should I do this in?

---

### Post by taurus on 2008-03-07
Type each line in the order in my reply, one line at a time.

---

### Post by vm367 on 2008-03-07
after sudo mount -t ntfs /dev/sda12 /media/sda12 -o umask=0222   its telling me Failed to access '/dev/sda12' :No such file or directory  when I open the media folder, sda 12 and 13 are there but empty

---

### Post by vm367 on 2008-03-07
by doing it wrong the first time, did I mess anything up?

---

### Post by Tatty on 2008-03-07
No you didnt mess anything up, all the first line does is create two directories for you to mount your drives to.

Try running the commands slightly differently:

```
sudo mkdir /media/sda12 /media/sda13
sudo mount /dev/sda12 /media/sda12
sudo mount /dev/sda13 /media/sda13
```

And see if that works.  Copy and paste each line if you can...

---

### Post by vm367 on 2008-03-07
its telling me mount: special device  /dev/sda12 does not exist  , same thing for the other one   WAIT, I think i know what Im doing wrong !

---

### Post by taurus on 2008-03-07
Post the output of this command again.

```
sudo fdisk -l
```

---

### Post by vm367 on 2008-03-07
ok, i mounted the drives   waht doesFailed to read NTFS $Bitmap: Input/output error   mean, cause it says that and then unmounts the drive...only the second one though....does the * under boot next to that drive have anything to do with that?

---

### Post by vm367 on 2008-03-08
is there anyway I can mount a specific folder and not the whole drive?

---

