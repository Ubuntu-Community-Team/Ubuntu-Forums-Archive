---
title: "newbie here"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by chaereth on 2007-06-14
I downloaded the iso file of Ubuntu 7.04 and then burned it on a CD. And now I'm currently running it with the CD boot or something (dunno how it's called) and I must say that I love it!

Anyway, I have Windows XP home edition installed as my current OS. And as far as I know I only have one big partition, and I am not so keen on doing a format and losing some files and programs there. So my question is:
Is there a way to have both operating systems on one partition? If there is, is it risk free (as in it wouldn't screw the computer up?)

---

### Post by w4ett on 2007-06-14
I'ts called a Dual Boot installation, and the live cd will install it for you if you desire......Almost automatically.  just click the install icon on the desktop and 'Let er' Rip"

---

### Post by OldTimeTech on 2007-06-14
Because you are running the 7.04 version.....when it comes to partition you will be able to save your windows and make a partition for 7.04 and a swap file.  Also because of the 7.04 version it will give you automatic dual boot.

---

### Post by Catsworth on 2007-06-14
> **chaereth said:**
> 

[...]

So my question is:
Is there a way to have both operating systems on one partition? If there is, is it risk free (as in it wouldn't screw the computer up?)

The answer to the OP's *actual* question is NO.

It is NOT possible to have two Operating Systems on the SAME partition.  You can do it on the SAME PHYSICAL DRIVE, but you would need to resize the partition to create the space, and then create a new partition for your Linux installation - this operation is not without risks.

---

### Post by phr0ze on 2007-06-14
Nothing is Risk Free. Not even those products on the info-mercials. Please back up your critical data.

However I have done the automated dual boot many times and I have never had a problem. The number one tip is to defrag windows first.

---

### Post by phr0ze on 2007-06-14
> **Catsworth said:**
> The answer to the OP's *actual* question is NO.

It is NOT possible to have two Operating Systems on the SAME partition.  You can do it on the SAME PHYSICAL DRIVE, but you would need to resize the partition to create the space, and then create a new partition for your Linux installation - this operation is not without risks.

Not true Catsworth, but for the point of this discussion I agree. However, there are installations which run off a volume stored as a file within another volume. (Maybe just not for Ubuntu.) And I'm not referring to a virtual machine.

Also to clarify, the automated install will do all this resizing and partitioning work for you.

---

### Post by chaereth on 2007-06-14
Thanks for all the help...

Now I read some of the stickies on this forum (first post and then read the stickies, very smart of me :S) and I found this topic [http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194") . I am a bit worried because I have and ATI Radeon graphics card (can't be sure about the number but I recall it being a X1300 or something). Now, should I download this alternate version and use that text mode installer or should I carry on with the current one I have?

---

### Post by w4ett on 2007-06-14
> **chaereth said:**
> Thanks for all the help...

Now I read some of the stickies on this forum (first post and then read the stickies, very smart of me :S) and I found this topic [http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194") . I am a bit worried because I have and ATI Radeon graphics card (can't be sure about the number but I recall it being a X1300 or something). Now, should I download this alternate version and use that text mode installer or should I carry on with the current one I have?
 It never hurts having the alternate install disk available...however, if the live CD is working OK then you should be all right with it.  The problems with the ATI cards are not insurmountable..(I'm using one myself) just Back up your data in your windows partition, Defrag it and The live cd will partition your disk for you and install itself.  If you do have difficulties with the ATI drivers, UF is always here for answers.

---

### Post by Tyke91 on 2007-06-14
they're right on the defrag bit... do it 2-4 times before you install

i didn't and i lost some data in wierd places (some music files, documents... etc)

---

### Post by chaereth on 2007-06-14
Okay, thanks for the help. I'll go and defrag on windows for about 6-7 times just to be safe ^^

---

