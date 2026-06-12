---
title: "copy from usb memory"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-09-08
Hi 
I am trying to copy some files from my usb into a /home folder. When I plug the memory in, a window pop up and I see all the content of my memory card. However, I try to copy files and it says I have not space available in my HD.... duhh I have 137Gb free and my usb memory is only like 5Gb.  What am I doing wrong?

cristian@NARUTO:/export/home/workspace$ uname -a
Linux NARUTO 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

my usb is mounted in 
/media/disk



Cristian

---

### Post by ORBiTrus on 2007-09-08
Please confirm:
"df -h" indicates 137GB free under /home
/home is not write-protected
"touch ~/test" does not generate errors
"cp -a /media/disk/* ~/" does not generate errors

If all the above are fine... uh, it's something?

---

### Post by krisfrajer on 2007-09-08
Yes, there a few errors. How could I go around them?
Maybe reading/writing privileges  are not allowed for my usb memory. What could I do?
Cristian

touch /export/home/test 
                worked without problem

cristian@NARUTO:/export/home$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              61G  4.5G   54G   8% /
varrun                470M  108K  470M   1% /var/run
varlock               470M     0  470M   0% /var/lock
procbususb            470M  116K  470M   1% /proc/bus/usb
udev                  470M  116K  470M   1% /dev
devshm                470M     0  470M   0% /dev/shm
lrm                   470M   39M  432M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/hda6             121G  193M  114G   1% /export/home
/dev/disk/by-uuid/C800E53F00E534DA
                       75G   28G   47G  38% /media/hdb1
/dev/hdc              4.2G  4.2G     0 100% /media/cdrom0
/dev/sda1             7.6G  6.7M  7.6G   1% /media/disk


cristian@NARUTO:/export/home$ cp -a /media/disk/ /export/home/
cp: reading `/media/disk/analysis/SampleID': Input/output error
cp: cannot stat `/media/disk/analysis/ Date': Input/output error
cp: reading `/media/disk/analysis/LiveTime': Input/output error
cp: reading `/media/disk/analysis/\nSlope': Input/output error
cp: reading `/media/disk/analysis/774925\r\n.NoO': Input/output error
cp: reading `/media/disk/analysis/ \r\n 3': Input/output error
cp: reading `/media/disk/analysis/     0 \r.\n 5': Input/output error
cp: reading `/media/disk/analysis/\r\n 8': Input/output error
cp: reading `/media/disk/analysis/    0 \r\n. 10': Input/output error
cp: reading `/media/disk/analysis/.  0': Input/output error
cp: reading `/media/disk/analysis/\n 13': Input/output error
cp: reading `/media/disk/analysis/   0 \r\n.15': Input/output error
cp: reading `/media/disk/analysis/ 18': Input/output error

---

### Post by krisfrajer on 2007-09-08
Also I got the following error when trying to copy a folder from the usb memory to my /export/home

I want to remark that my second partition of my HD is mounted into /export/home
One strange thing is that it seems I can copy files from the USB but not folders. Why is that?

cristian@NARUTO:/export/home/workspace$ cp /media/disk/analysis/  /export/home/workspace/
cp: omitting directory `/media/disk/analysis/'


Cristian

---

### Post by ORBiTrus on 2007-09-08
Copying folders requires the -R (recursive) parameter.  Those input / output errors are a lot (ok, exactly) like what I get when I try to read a CD with bit rot.  Or copy a file onto my serial ata drive which is fubar'd and out-of-warranty [it holds a certain class of movies I could care less about loosing].

That means it's either the USB drive or the hard drive.

Can you read the files when they are on the USB drive or not?  If so, I'm afraid I know of nothing else to do, perhaps someone else does.  If not, I'm afraid that's as far as I can help you, as I am not familiar with Linux's usb-mass-storage drivers.  Perhaps these may be good comments for a bug report if the problem lies in the kernel

Edit: OK, technically it could be any number of things, like motherboard, RAM etc, but then again, all the molecules in the universe might align just so, and I fall through to China.  There's a 99.9999...(56 times) 9% change it's these two.

---

### Post by dwhitney67 on 2007-09-08
> [FONT="Courier New"]cp: reading `/media/disk/analysis/SampleID': Input/output error
cp: cannot stat `/media/disk/analysis/ Date': Input/output error
cp: reading `/media/disk/analysis/LiveTime': Input/output error
cp: reading `/media/disk/analysis/\nSlope': Input/output error
cp: reading `/media/disk/analysis/774925\r\n.NoO': Input/output error
cp: reading `/media/disk/analysis/ \r\n 3': Input/output error
cp: reading `/media/disk/analysis/ 0 \r.\n 5': Input/output error
cp: reading `/media/disk/analysis/\r\n 8': Input/output error
cp: reading `/media/disk/analysis/ 0 \r\n. 10': Input/output error
cp: reading `/media/disk/analysis/. 0': Input/output error
cp: reading `/media/disk/analysis/\n 13': Input/output error
cp: reading `/media/disk/analysis/ 0 \r\n.15': Input/output error
cp: reading `/media/disk/analysis/ 18': Input/output error[/FONT]

The filenames in the analysis folder look awfully strange.  Can you confirm that they are correct?

See if you can condense everything on the USB drive into one file:

[FONT="Courier New"]$ tar cvf /usb.tar /media/disk/*[/FONT]

Then unpack the tar image in /export/home:

[FONT="Courier New"]$ cd /export/home
$ tar xvf /usb.tar[/FONT]

---

### Post by krisfrajer on 2007-09-08
yes... there is something strange. I have to recopy that folder again into my memory stick. The files are very strange. I tried "ls /media/disk" and I have a list of filenames which look "awefull" like garbage characters.

At this point, I assume therw was an error copying the files into the memory stick. I will try again on Monday when I get back to work. Thank you for your comments.
Cristian

---

### Post by krisfrajer on 2007-09-08
BTW, I tried the tar and this is what I have got:

cristian@NARUTO:~$ tar cvf /export/home/usb.tar /media/disk/*
tar: Removing leading `/' from member names
/media/disk/analysis/
/media/disk/analysis/SampleID
tar: /media/disk/analysis/SampleID: Read error at byte 0, while reading 9216 bytes: Input/output error



Cristian

---

### Post by dwhitney67 on 2007-09-08
Too bad you did not follow my instructions to the letter.  I wanted you to create the tar file in the root-directory, thus eliminating the "unknown variable" of /export/home.

That said, I suspect something is wrong with the USB drive.  How is it formatted?  How is /export/home formatted?

My bad... that command I gave you earlier should have been:
[FONT="Courier New"]
$ sudo tar cvf /usb.tar /media/disk/*[/FONT]

I forgot the 'sudo' part.

---

