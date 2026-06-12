---
title: "Linux Partitions and Stuff"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Nut on 2006-10-15
Hey, what kind of file system do I need? Ext3? Make it primary? Do I need two partitions? I am dual booting so I have a Windows XP partition, and I am making a Linux one.

---

### Post by taurus on 2006-10-15
Yes, you need at least two partitions: one for / and one for swap.  You can format your / as ext3 and swap as a swap.  The installer will do that for you so no need to format them before you install it.

---

### Post by Klaidas on 2006-10-15
Great guide - [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Nut on 2006-10-15
> **taurus said:**
> Yes, you need at least two partitions: one for / and one for swap.  You can format your / as ext3 and swap as a swap.  The installer will do that for you so no need to format them before you install it.

Primary or the other option though? So, like this:

1. / ext3
2. / swap

Right? What size should I make them? I mean, I thought I'd just split it in half, but yeah. Which needs the most space? Which do I install on?

I wanna get this right.

---

### Post by Klaidas on 2006-10-15
Well, I would give /swap twice as much as your RAM, 
and I'd give / as much as I need storage (but I would recommend >10GB). And you should install on /

---

### Post by Nut on 2006-10-15
Twice as much as my computer's ram? That's only like 1 GB!

---

### Post by Kateikyoushi on 2006-10-15
Don't make swap bigger than 1GB it is like paging file in windows, most likely 512MB is enough.
Make / take up the rest of the space.
You only have a windows partition so can make both primary partitions.

---

### Post by Nut on 2006-10-15
Tell me exactly what I need to do. Exact size and everything. What partitions do I make? Where do I install it? Tell me everything.

---

### Post by Nut on 2006-10-15
Let me tell you what I've got here...

160 GB hard drive.
512 MB ram.

1 partition (Windows), 74.5 GB (I think), NTFS file system.
74.51 (or something) unpartitioned space.

What do I need to do? I'm looking for instructions...

Example:

First, make a partition with the settings (blah blah blah). Second, do this.

HELP!

---

### Post by Klaidas on 2006-10-15
> **Nut said:**
> Tell me exactly what I need to do. Exact size and everything. What partitions do I make? Where do I install it? Tell me everything.

Look at my previous post ([http://www.ubuntuforums.org/showpost.php?p=1620515&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1620515&postcount=3))

---

### Post by Nut on 2006-10-15
Ok, but I've had problems with it multiple times... And, something happened during the boot up of the demo CD that didn't display there. It did the little check for this thing and "ok" thing but in a black screen with white text, after it did it with "the Ubuntu style".

Basically, after it did [this]("http://img144.imageshack.us/img144/9720/w2u218vo.png"), it went to a black screen and did the check for thing and "ok" thing with white text. No Ubuntu header or anything. It checked for like, some drives or something, and there were two things that weren't "oked".

Is that bad?

---

### Post by Nut on 2006-10-15
That didn't really help me but to choose the first option. Should I do that? What will it do?

---

### Post by AndyCooll on 2006-10-15
For all your information follow the "HOWTO dual boot" in my signature. The link for which has already been posted in this thread.

It really does walk you through!

:cool:

---

### Post by Nut on 2006-10-15
Well, I don't even have the resize option. All I can do is manually edit.

---

### Post by Nut on 2006-10-15
The tutorial for the desktop CD doesn't show you how to dual boot...

"You'll then be presented with three options. This first option is ideal for users who want to set up a dual-boot (where you can choose whether you want to use Windows or Ubuntu each time you boot up your computer) but know very little about setting one up. Ubuntu will automatically shrink your Windows partition and create a new Ubuntu partition out of the free space."

I don't have the first option. It won't let me resize. I already made it where Windows only took up half my hard drive.

---

