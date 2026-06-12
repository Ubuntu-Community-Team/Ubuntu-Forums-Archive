---
title: "trying (failing!) to check my hard drive for errors"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-08-11
On this thread;
[http://www.ubuntuforums.org/showthread.php?t=230090&highlight=problem+sounds+hardware+troubles](http://www.ubuntuforums.org/showthread.php?t=230090&highlight=problem+sounds+hardware+troubles)
 The Wizard said:
"your problem sounds like hardware troubles. please check your ram and hdd!
- for testing your ram you can use the Memtest86+ that is in the ubuntu startup menu and in the menu of the installation cd.
- for testing your hdd use e2fsck. it is on the rescue-cd, which you can download from [http://rescuecd.sourceforge.net/](http://rescuecd.sourceforge.net/) . to test your first hdd, type "e2fsck -c -c /dev/hda""

I did the memtest and waited until it had 3 passes and no errors, which I guess means the ram is okay.

Then I booted from the rescue CD and ran the command like The Wizard said. It said this:

"e2fsck 1.35 (28-feb-2004)
couldn't find ex2 superblock, trying backup blocks...
e2fsck: Bad maguc number in super-block while trying to open /dev/hda

The superblock could not be read or does not describe a correct filesystem. If the device is valid and it rally contains an ex2 filesystem (and not swap or ufs or somehting else) then the superblock is corrupt, and you might try running e2fsck with an alternate superblock
e2fsck -b 8193 <device>"

I don't understand what it is trying to comunicate, but anyway I went ahead and tried typing in e2fsck -b 8193 /dev/hda" on the offchance that was the correct next step. It just gave the same message again.

Anyone know what to do now? Or is that what it was meant to do already?
Thanks
Justin

---

### Post by matthewv on 2006-08-11
I would check to make sure that /dev/hda is indeed the correct thing to check. /dev/hda refers to the first ide hard drive, while, if I remember correctly, that tool is designed to check a partition, rather than a hard drive. Try substituting in your partition, eg /dev/hda1 (first hard drive, first partition) .

---

### Post by woodlandjustin on 2006-08-11
> **matthewv said:**
> I would check to make sure that /dev/hda is indeed the correct thing to check. /dev/hda refers to the first ide hard drive, while, if I remember correctly, that tool is designed to check a partition, rather than a hard drive. Try substituting in your partition, eg /dev/hda1 (first hard drive, first partition) .

Hi Matthew
I tried that too, exactly what you said. It gave the same result.

---

### Post by matthewv on 2006-08-11
You might want to check that you are trying to check the correct partition (or maybe I'm all wrong ;) ) 
From the system rescue cd, which is what I think you're using, run the command ```
fdisk -l /dev/hda
```
This should list a number of partitions, one of which will then be your linux partition (type 83). Then you can substitute in the device of that partition (it will look something like /dev/hda1) into ```
fsck <device>
```

---

### Post by woodlandjustin on 2006-08-12
> **matthewv said:**
> You might want to check that you are trying to check the correct partition (or maybe I'm all wrong ;) ) 
From the system rescue cd, which is what I think you're using, run the command ```
fdisk -l /dev/hda
```
This should list a number of partitions, one of which will then be your linux partition (type 83). Then you can substitute in the device of that partition (it will look something like /dev/hda1) into ```
fsck <device>
```

Okay I did fdisk -l /dev/hda and that told me the linux partition was hda2. So I guess I cannot check the windows partition nor the linux swap (whatever THAT is!)?
Then I did fsck /dev/hda2 but that didn't seem to do anything useful. So then I did 
e2fsck -c -c /dev/hda2
That seemed to do the trick. It went on testing for a long time, and finally said something like
pass 1
pass 2
pass 3
pass 4
pass 5

/dev/hda2: **** File System was modified ********
/dev/hda2: 93367/1769472 files (1.1% non-contiguous), 901420/3534300 blocks


What does that mean?I like the "pass 1" etc. But the rest, is that good or bad or what??
Thank you
Justin

---

### Post by woodlandjustin on 2006-08-17
Bump

---

### Post by woodlandjustin on 2006-08-20
I have no progress in this matter. As youu may be able to see, I did the test, but was unable to understand the outputted "result" of the test, and so I have no idea whether my computer passed the test or not, no idea whether something is bad or in need of fixing etc. I know *something* is up with my computer, judging from its behaviour sometimes.
Advice appreciated!
Thank you
Justin

---

