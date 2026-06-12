---
title: "Create a new ext3 partition for your root - help"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by tremendous on 2008-01-22
Can anyone tell me exactly how to do this step

Install ubuntu as usual, except:

1. In the partitioner, select Manually edit partition table
2. Delete /dev/sda3 and /dev/sda4 if they exist
3. Create a new ext3 partition for your root
4. Mount the newly created ext3 partition on '/'

I get the manually edit part, and the delete part (1 + 2) - but what do i need to do, exactly, for the last two points?

---

### Post by dannyboy79 on 2008-01-22
frmo what I remember using the manual partition editor in the installer, you just add a new partition and chose it to be mounted in /. what exactly is your goal, is this a dual-boot system? are sda1 and sda2 for windows and or your /home partition and you don't want them formatted?

---

### Post by tremendous on 2008-01-22
hey

i'm actually following these instructions:

[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

I'm a total novice, so when i see something like 

"Create a new ext3 partition for your root
Mount the newly created ext3 partition on '/'"

i get lost!

---

### Post by housam on 2008-01-22
After steps 1 & 2  you'll got an unallocated space which can be resized to create an ext3 partition and to create a swap partition too.
During the installation process you have to assign the first one as ( / ) root partition to install ubuntu on it.

---

### Post by tremendous on 2008-01-22
thanks housam - so even when i am manually editing the partition table it will be obvious what i need to do? i'm worried i'm going to start this and hit a point where i need to type something and i won't be able to work it out.

all help greatly appreciated.

---

### Post by kellemes on 2008-01-22
Well, I haven't seen the Ubuntu-installer for some time now, so I can only think with you instead giving exact instructions..

When you remove the 2 partitions there must be unpartitioned space left. It's in this space you need to create this partition.
When you're looking at this unpartitioned block on your screen you need to push the "new"-button to create this partition.
Is there a new-button? I don't member, well.. you'll see. ;-)

---

### Post by tremendous on 2008-01-22
Thanks - like i said - i'm trying to get to the bottom of this before i start - trying to avoid any hidden surprises!

---

### Post by kellemes on 2008-01-22
> **tremendous said:**
> Thanks - like i said - i'm trying to get to the bottom of this before i start - trying to avoid any hidden surprises!


Nothing wrong with that.

---

### Post by tremendous on 2008-01-22
i'll see if anyone else comes up with any ideas before i go ahead and do this. still completely unsure about what i'm editing and how!

---

### Post by kellemes on 2008-01-22
> **tremendous said:**
> i'll see if anyone else comes up with any ideas before i go ahead and do this. still completely unsure about what i'm editing and how!


Well, you're on your own I'm afraid.. ;-)

Just see to it you have the most important stuff backed up, just in case..
Good luck.

---

