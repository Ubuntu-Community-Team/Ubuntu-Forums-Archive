---
title: "Questions: Installing Ubuntu on MacBook Pro"
date: 2016-10-02
forum: Apple Hardware Users
---

### Post by Saffo on 2016-10-02
Hello everyone!

So--- a few years ago I bought a laptop from System 76, which was a terrible mistake (they make really crappy computers) but I really enjoyed Ubuntu, despite the fact that tbh I don't understand it super well and I'm definitely not an expert. Well, that laptop just got stolen and I ended up buying a refurbished MacBook Pro which I am hoping to install Ubuntu on. Anyway, the moral of the story is I've never installed Ubuntu before so I don't exactly know what I'm doing and while I think I get the gist of things a lot of the documentation online is very confusing and I'm hoping not to screw up majorly. I have a few questions so even if you can just help with some of them that would be really appreciated!

So I had a few questions about installing Ubuntu on a MacBook which is currently running OS X 10.11.6 Also, I am hoping to do a dual boot.

First, I have a Macbook 9,2 and I looked at this webpage: [https://help.ubuntu.com/community/MacBookPro9-2/Utopic](https://help.ubuntu.com/community/MacBookPro9-2/Utopic) I'm a little bit confused about this, but does this mean that Wifi won't work if I run Ubuntu? And these things with question marks may or may not work? That sounds a big scary, so I'm not sure I want to do that. But tbh I am a bit confused by this page and I'm not sure if I'm looking at the right thing.

So that would kind of be a dealbreaker if I woudn't be able to get on the internet with Ubuntu.

If that's not the case then I have a few other questions...

I'm a bit confused about the partitioning. How much space should I partition? I'm hoping to do dualboot but probably do most of my stuff in Ubuntu. Am I correct in assuming that from Mac OS I won't be able to read the files on the Ubuntu partition and vice versa? If so, should I make a third partition that could be read by both OSes? If I'm planning to mostly run Ubuntu should I allocate most of the harddrive to Ubuntu? (The harddrive is 500 GB) 

I'm planning to back everything up before I do this, but like I said, I just got this laptop so I don't have a whole lot of stuff on it. But I assume if I run timemachine on an external drive, then if I majorly screw up during the process I should be able to recover OS X by booting from the external drive, correct?

Anyway, that's it for now. I'm sure I'll have more questions later.

Thanks so much!

---

### Post by &amp;KyT$0P# on 2016-10-03
> **Saffo said:**
> First, I have a Macbook 9,2 ... does this mean that Wifi won't work if I run Ubuntu? And these things with question marks may or may not work? That sounds a big scary, so I'm not sure I want to do that. But tbh I am a bit confused by this page and I'm not sure if I'm looking at the right thing.

So that would kind of be a dealbreaker if I woudn't be able to get on the internet with Ubuntu.
Read my signature, especially all the physical hardware mentioned, and ask yourself whether Internet will work for you on 14.04. ;)

Wi-Fi does not work out-of-box, but you can install the proprietary driver and it will then work as well as your Ethernet.

>  How much space should I partition?
No one can answer this for you.  Give the Mac OS at least 40 GB **free space** and you'll be fine.

> Am I correct in assuming that from Mac OS I won't be able to read the files on the Ubuntu partition and vice versa?
Close but not quite.  Ubuntu can read the files on the Mac OS partition.  Ubuntu cannot, however, write to the files on the Mac OS partition - can only be mounted read-only.

>  I assume if I run timemachine on an external drive, then if I majorly screw up during the process I should be able to recover OS X by booting from the external drive, correct?
It is unsafe to assume that.  I made that mistake in my Mac OS X days and ended up stuck with a "lame" system until I did a full clean install.
Do use the Time machine though, it will back up all the important data.

You need a separate, bootable Mac OS installer partition in order to be sure you could properly restore Mac OS.

---

