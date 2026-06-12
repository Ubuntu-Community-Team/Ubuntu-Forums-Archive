---
title: "Problem with partitions"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by cairnsww on 2007-05-25
What am I doing wrong?

I have the Feisty disk. I have done this before - last week in fact.

I have a new machine. Vista Home is loaded and I want to keep it loaded in a partition. So I want Ubuntu to partition my disk and - like last time - I want a menu that gives me a sliding bar that says so much for Windows and so much for Ubuntu. 

But that window does not come up during the install process. I get a choice between taking the whole disk or manual partitioning.

Vista is installed and working as well as poor old Windows can. But the installation process refuses to accept that there is another operating system there. Or that is how I am reading it.

What am I doing wrong?

---

### Post by cairnsww on 2007-05-25
Bump

---

### Post by dstew on 2007-05-25
You cannot use the Linux partitioning tools with Vista, even though it is ntfs. You have to use the Volume Management Tool in Vista itself. It will non-destructively shrink and/or move your Vista partition to make room for an Ubuntu installation.

---

### Post by cairnsww on 2007-05-25
> **dstew said:**
> You cannot use the Linux partitioning tools with Vista, even though it is ntfs. You have to use the Volume Management Tool in Vista itself. It will non-destructively shrink and/or move your Vista partition to make room for an Ubuntu installation.

Thanks - but this is my first exposure to Vista. Can you help me with how to do that?

---

### Post by cairnsww on 2007-05-25
The really annoying thing is that I had this working last week. But then the supplier realised that they had given me the wrong PC and replaced it. Now I can't get it to make sense ...

---

### Post by KashvW on 2007-05-25
Hi there,

I've just been looking for info on that and I found this [http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/)
Hope it helps.

---

### Post by cairnsww on 2007-05-25
Thanks much - if I really have to do this then I have to do it!

But I don't believe it. I am not kidding when I say that today i gave a machine back to the supplier and I had Windows Vista and Feisty happily sharing a boot option. I did none of this: I simply installed Ubuntu on top of Vista and it worked. Now it doesn't. I did something then that I am not doing now - and it was not using Vista to create a partition!

I am pulling my hair our!

---

### Post by Wim Sturkenboom on 2007-05-25
> **cairnsww said:**
> BumpHey, give people a chance to type their messages.;)

---

### Post by cairnsww on 2007-05-25
> **Wim Sturkenboom said:**
> Hey, give people a chance to type their messages.;)

Sorry - I thought that when my message fell off the bottom of the screen and nobody had even read it I might be permitted a quiet bump!

---

### Post by dstew on 2007-05-25
Follow the link that KashvW posted. It tells you how to resize a partition in Vista.

As to why it worked before, but doesn't now, that is hard to say. Were the machines substantially different? How did you create your Linux partitions in your earlier installation? Did you shrink the Vista partition? Maybe there was already unallocated space on the drive, so you didn't have to shrink Vista. That happens sometimes, when a new OS is installed, especially on a big disk.

---

### Post by Wim Sturkenboom on 2007-05-26
When I posted, your 1st post was on one hour and your second on 57 minutes. My calculation told me that you bumped after **3 minutes** (although one hour might have been longer, in which case you were a bit more patient).

If everybody starts bumping in this short time, your post will probably fall a lot faster of the bottom of the screen :) But it might indeed be a problem on a forum that is as popular is this one.

On most forums that I visit, there's a (sometimes unwritten) rule not to bump within 24 hours. And some of them (e.g. LinuxQuestions) automatically bump posts with 0 replies after 24 hours for two days; if you bump there, you shoot yourself in the foot as yopu have 1 reply.

---

