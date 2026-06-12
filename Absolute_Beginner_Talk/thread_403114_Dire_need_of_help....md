---
title: "Dire need of help..."
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by ravosava on 2007-04-06
Let me give you the rundown:
I know hardly NOTHING about computers, and I was convinced to use Ubuntu by someone who compared to me is a computer god. 
I like Ubuntu, but one day (that day being today), I started my computer and it went to the OS menu, but Ubuntu wasn't a choice, I only had Windows.
I decided I'd re-install Ubuntu, but it's still installed, I just don't know how to get it on the menu at start up...
Please help me. I know I sound like a moron, it's because I am when it comes to this kind of thing...but don't leave me out in the cold, I can learn

---

### Post by Happy_Man on 2007-04-06
Did you use the LiveCD to install? If so, do you still have it?

---

### Post by ravosava on 2007-04-06
Yes, I used the live CD, I don't have the same liveCD I used to install it, I have another one though, if that makes sense. In fact, Im using the liveCD right now, because Windows is giving me weird problems...

---

### Post by SOULRiDER on 2007-04-06
Your problem is quite easy to solve actually, check out this guide: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you have any issues or dont udnerstand something, just come ont he kubuntu channel on IRC and ill help you.

---

### Post by Happy_Man on 2007-04-06
This is good; very very good. Now enter this into your terminal (Applications-->accessories-->Terminal):

```

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu

```

This is, of course, assuming your Linux partition is on /dev/hda1. If it isn't, just substitute whatever it is on for that.

EDIT: actually, listen to soulrider. That page details everything you need.

---

### Post by ravosava on 2007-04-06
Thank you guys so much, I did what he says, I hope it works. I really appreciate it :)

---

