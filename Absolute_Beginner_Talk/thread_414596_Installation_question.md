---
title: "Installation question"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by doubleuicked on 2007-04-20
hi guys,

have always been an windows user, just recently jumped into the ubuntu bandwagon, after waiting for feisty to  be released i finally downloaded it. did my research and then subsequently did the necessary partitions, installed it, and then it asked me to reboot the computer with the live cd, then the "menu" screen comes up for me to choose which OS to load, i choose ubuntu, then i wait, and wait and wait,  then the following appears

undevd-event[1923]: run_program: 'sbin/modprobe' abnormal exit

am i doing something wrong? please help me if you can and ur help is greatly appreciated


cheers

---

### Post by nereid on 2007-04-20
Normally this shouldn't happen. modprobe is the program to load the required kernel modules. The only way I could think of that this could happen would be some very esoteric hardware setup.

Are you sure your ISO image of Feisty was correct and not corrupted?

---

### Post by doubleuicked on 2007-04-20
i burned it using ISO recorder, so i would imagine that it is correct. Is there anyway i can check?

---

### Post by doubleuicked on 2007-04-20
i actually just checked the cd using the check function on the cd, and it says its fine with no errors,

what else could be the problem?

---

### Post by greybirds on 2007-04-20
When downloading large files, very occasionally an error will creep in. ISOrecorder might have written the data correctly to the cd, but if the data had an error in it in the first place you'll have a screwy cd.

You should check the md5 sum for the iso file you downloaded against this list. Make certain all the numbers/letters in the code are the same for the file you downloaded.

[http://releases.ubuntu.com/7.04/MD5SUMS](http://releases.ubuntu.com/7.04/MD5SUMS)

I'm assuming you're doing this under Windows, in which case this page can help you find your iso's md5 sum: [http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)

If by some chance you're using linux, you can open a terminal and type

```
md5sum name-of-the-file.iso
```

---

### Post by doubleuicked on 2007-04-20
unfortunately, the md5sum thing turned out fine also.

any other takers?

---

### Post by siucdude on 2007-04-20
try the alternative cd.  that always works for me when its a issue with live cd.  let us know what other things you get. 

thanks
tj

---

### Post by doubleuicked on 2007-04-20
do i have to wipe out my previous installation or do i just pop in the alternative cd and i'll be good to go?



thanks

---

### Post by josephus on 2007-04-20
i tried to look for some other posts related to your problem, and other people seem to have similar problems, but doesn't look like there is straightforward solution. you might have better luck trying to reinstall with the alternate cd but it's hard say for sure. 

anyway it looks like one of the modules is having trouble loading up, but which one i don't know.if you want to try to debug this, my only suggestion is to boot up using the live cd and mount your hard drive and go into the logs from your last boot.  there should be a file /var/log/udev that logs these events.  try to find the entry with the sequence number = 1923, that will tell you what is failing and hopefully someone will point you in the right direction from there.

i've only been using linux for a couple of months so all this could be wrong, but it's the best that i can think of at this moment).

---

### Post by doubleuicked on 2007-04-20
i'll definitely give the alternate cd a try, but since i've already "installed" ubuntu on the normal cd, do i have to wipe anything out or do anything, or do i just pop in the alternate cd and do the same thing all over again?


thanks in advance

---

### Post by doubleuicked on 2007-04-20
so after a multiple tries, i FINALLY got it working!!!

first off thanks to those who gave me help, u guys are awfully friendly here, thats awesome


and for those who may have ran into the same problem as me, i ended up reinstalling it using the normal desktop cd, but just before all the options are selected, there is a "advanced" tab, where you'll find a section i believed called boot loader. this default value will be hda(0), i changed this to hda(0,1) because im installing ubuntu on my first harddrive (hence 0) and on the 2nd partition of the drive (hence ,1). 


so i am now so excited and cannot wait to explore ubuntu


cheers!!

---

