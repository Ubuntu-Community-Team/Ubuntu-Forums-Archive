---
title: "How could Gparted do its job &amp; lose Ubuntu in the process?"
date: 2008-07-26
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-07-26
Hi,
 This is a question that is post-process, meaning that it's all done and I've recovered from the error already, but I need to post this question and hopefully find out what went wrong. 

I had a dual boot with Leopard/Ubuntu 8.04 on my Macbook Air, using rEFIt. Everything was fine - I simply thought I needed more hard drive room for the Ubuntu partition. It was getting tight and I had only 5 GB left.

So I put in the Ubuntu LiveCD and let it run Ubuntu from the LiveCD so that I could use Gparted (which is preinstalled on the liveCD). Things went smoothly (or so I thought). I shrunk the Mac partition and Gparted performed that quickly and efficiently. 

Then I proceeded to expand the Ubuntu partition. This seemed to go fine except that it took a very, very long time to process, like around 55 minutes. But I had never done this before, so I thought maybe that's how it works.

Now, keep in mind, in NO way did I ever choose to format ANY partition or drive. 

Well, the expansion finished - I rebooted and went into rEFIt, but the penguin was missing...Oh no. I rebooted to the Ubuntu part as best I could and then this message appeared alone on the black screen: 

```
Missing Operating System
``` 

Well, needless to say, I reinstalled Ubuntu from scratch and everything is right now and I do have the partition sizes like I want them.

So my question is: What happened and what did I do wrong? The Mac partition did not lose its OS. Everything remained intact there. 

Is this something that happens on a partition expansion? That it gets reformatted in the process?

I appreciate any clarity anyone could offer on this. 

Many Thanks, Frank B.

---

### Post by BLTicklemonster on 2008-07-26
Good question. I just spent three days trying to restore grub after only resizing a partition on a separate hard drive from the one where Ubuntu resides. I gave up and loaded Ubuntu up on a spare partition and am in the process of moving all my stuff over. I tried everything under the sun, and when I finally got to where I thought it would work, I got 

error 18: selected cylinder exceeds maximum support by bios.

Yeah, that's when I threw in the towel and just set up Ubuntu fresh on a spare partition.

---

### Post by Brightbelt on 2008-07-26
Thanks for the nod. I myself have never, ever solved a grub error successfully. 

I ALWAYS end up reinstalling Ubuntu and that fixes it every time.

---

### Post by cyberdork33 on 2008-07-27
Since you likely had Grub installed to the Ubuntu root partition (how we usually instruct people to do it in this forum) changing the starting cylinder of the partition will break grub. reinstalling grub may have fixed the issue.

The "Missing Operating System" error reflected this because the bootcode that should have been in the beginning of the Ubuntu partition was no longer there, and thus it believed the OS was missing on that partition.

If you find yourself in a situation with a non-bootable system, remember that a livecd is the best tool you could have. You should be able to boot your livecd, mount the system partitions, and chroot into the unbootable system. There you can run updates, reinstalls, etc just like you were running in the installed system itself. Even if you cannot fix the bootability of the system, you can get your files off the partition before you reinstall.

---

### Post by BLTicklemonster on 2008-07-27
My system is still there, but it's not part of my menu.lst at all any more on my new install.

I tried everything listed in [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)  from the live cd, and still never got it working. I'd love it if I could get it back again. Granted, I never downloaded and burned the supergrub cd...

---

### Post by cyberdork33 on 2008-07-27
> **BLTicklemonster said:**
> My system is still there, but it's not part of my menu.lst at all any more on my new install.

I tried everything listed in [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)  from the live cd, and still never got it working. I'd love it if I could get it back again. Granted, I never downloaded and burned the supergrub cd...
Sorry, I don't really know what your situation might be. I was really responding to brightbelt. The Macs really have some special partitioning methods and are really picky about changes...

---

### Post by Brightbelt on 2008-07-27
Interesting, though Cyber, that my Mac partition came through like a champ. That would have been a greater loss; I was grateful that it stayed in one piece.

I give Gparted a lot of credit for handling the Mac partition so well.

---

### Post by cyberdork33 on 2008-07-27
> **Brightbelt said:**
> Interesting, though Cyber, that my Mac partition came through like a champ. That would have been a greater loss; I was grateful that it stayed in one piece.
Yes, but you likely resized the partition from the right, no? There is usually nothing even on the end of a partition...

The Ubuntu partition on the other hand, though the data on the filesystem was likely preserved, also contained code in the header section of the partition. This is the part that was likely broken. (This really doesn't excuse gparted though. You might file a bug report and/or search of there already is one.)

This i probably way too much info, but it can be interesting and is related:
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by Brightbelt on 2008-07-27
Thanks Cyber.

---

