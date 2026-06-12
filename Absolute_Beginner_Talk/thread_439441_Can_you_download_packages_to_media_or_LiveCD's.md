---
title: "Can you download packages to media or LiveCD's?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-10
Just a quick question here.

I am using partimage a lot since I am playing around in Ubuntu to see if it's a keeper.  The only thing that's taking any real time at all every time I want to restore my base image is that I have to download and configure partimage every time.

Is there anyway to place it in my LiveCD or on my USB key with my restore image?

---

### Post by e_james on 2007-05-10
The short answer is yes but I don't know the details except that I believe it is more complex than either of us would want to try right now. On the other hand there are downloadable live CDs with partimage already in place. 
Try this link 
[http://software.newsforge.com/article.pl?sid=05/06/22/1941242](http://software.newsforge.com/article.pl?sid=05/06/22/1941242) 

I'm not in a position to check it out right now but partimage could be on one or more of the ubuntu live CDs. 

Edit. Sorry. If it was there you wouldn't be asking how to put it there. Sometimes I write without thinking.
The Knoppix live CD is another possibility. It's primarily aimed at people who need to repair systems.

I just had another idea. If you have sufficient drive space, there's no reason why you can't have 2 or more linux installations on the same pc. You could keep one operational to do the repairs / replacement on the other one.

---

### Post by gohanssjn on 2007-05-10
Hmmm, interesting.  Maybe I'll make a small Ubuntu install and remove EVERYTHING that is not essential to do this...

---

### Post by e_james on 2007-05-10
One additional suggestion. If you should break your grub installation and can't boot up, the SuperGrub CD will let you boot into any working OS (at least any linux). I found it extremely useful when I had to swap a second hard drive into first position.

---

### Post by gohanssjn on 2007-05-11
What I'd LOVE to do is have a Linux that can boot off a USB drive that has Partimage installed so I can just restore from that all the time.

Since my laptop can boot from USB, maybe I can use that CDLinux for that?

---

### Post by e_james on 2007-05-11
OK. I'm no linux expert (see signature), but this is what I have done and what I think I know. 

I have installed ubuntu 6.06, 6.10 and 7.04 several times in dual boot with Windows XP Pro. I have always used the Alternate install CD because I believe it gives me more choices in the way that the drives are partitioned. It's also useful for working with older limited hardware because the pc doesn't have to run the live system before it starts the install.

Based on my own experiences and comments from others on these forums etc, ubuntu (linux) is much more versatile than Windows when it comes to partition management and boot choices. For instance linux seems to have no problem with the idea of copying a partition to or from an external usb drive (usb key included?). I haven't tried it but I expect that you could install ubuntu on to your usb key simply by having it inserted during the install process. Using the alternate CD there are a number of grub install choices. I set up a friend's pc so that it always boots to Windows XP unless he inserts a special boot floppy; then it boots to ubuntu. The usb boot facilty is commonly used to support an external floppy drive for laptops etc, but I think it is also used to boot from devices like your usb key. It depends on the hardware and firmware specification. The BIOS has to be right and the usb key has to be right.

If you can install ubuntu on the usb key and space is available, there is no reason why you couldn't also install partimage and Gparted. A smaller linux distro with all the necessary software (maybe Puppy or DSL) is another possibility but the installation to usb key might be tricky.

It is also possible to install a "portable" linux on a usb key which can be run within a Windows environment but I think this might take more effort than you want to apply at this time. It wouldn't be so amenable to experiments.

You know best what you're willing to change and what you want to preserve, but I think there are many possible configurations available to you.

---

### Post by gohanssjn on 2007-05-11
Awesome, guess I'll get crackin tonight :)

What I would also like to do, which may be an idea, is DL the LiveCD, use an ISO manager to slip in the package I need, then burn it.  But a USB key is much nicer since my image aslo fits on the key.

Fun night ahead.

---

### Post by e_james on 2007-05-11
What you are talking about is a customised live CD or a customised install CD. I have never seen procedures for doing this for ubuntu but there are instructions for other distros. I would rate the skill level required about  semi-expert. Creating a live and install CD seems well into the expert category.

The main reason ubuntu has a live / install CD and an alternate CD is that each CD is filled with as much as can be squeezed in. Not having to run a live GUI allows the alternate CD to hold more options. If you wanted to add something to one of these you would also need to leave something out.

For most of the past year I have been observing these forums (mainly beginner). If I think I can contribute something useful, I jump in, but more often I learn something new for my own situation. When I find a thread I might want to look up later I add a bookmark. Looking through my bookmarks I found the following

[http://ubuntuforums.org/showthread.php?t=346946](http://ubuntuforums.org/showthread.php?t=346946)
[http://ubuntuforums.org/showthread.php?t=349040](http://ubuntuforums.org/showthread.php?t=349040)
[http://ubuntuforums.org/showthread.php?t=341400](http://ubuntuforums.org/showthread.php?t=341400)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
[http://www.howtoforge.com/taxonomy_menu/1?](http://www.howtoforge.com/taxonomy_menu/1?)

A quick google search for "rescue CD" turned up these urls

[http://www.phenix.bnl.gov/~purschke/RescueCD/](http://www.phenix.bnl.gov/~purschke/RescueCD/)
[http://www.bootcd.us/](http://www.bootcd.us/)
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

I expect there are some useful ideas in these.

---

