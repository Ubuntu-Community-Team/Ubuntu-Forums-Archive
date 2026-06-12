---
title: "Superusing the new Macbook 6.1 (late 2009)"
date: 2010-01-08
forum: Apple Hardware Users
---

### Post by Skatertjah on 2010-01-08
Good day everyone,

I've recently bought the "new" Macbook from Apple. It obviously came with OSX preinstalled. And I'm obviously not satisfied with the way it works, otherwuse I wouldnt be posting here...

I'm a huge fan of Ubuntu and Linux in general so I thought maybe I could dual boot it with Mac. But since I'm still at school I need to have Windows installed as well. Hmm, triple boot? Yes that would be the answer. But wait, I also need a FAT32 partition so I can share my files between all three OS's. Tricky business. And I thought later on I might try and create me a nice LFS system to learn about Linux and show of to my mates. But doesn't a single hard drive only support up to 4 partitions? Problem.

So off I went and got Ubuntu running besides Mac. It wasnt recognized by neither the default boot-loader nor rEFIt straight away. I had to hold alt to come up with the special BIOS or something every time I needed to use Ubuntu (always). I got up to a point where I could run Ubuntu with wireless, sound and pretty much everything working. Until the kernel updates were installed. Somehow I (or maybe it) managed to screw up and booting had become impossible, for it would crash halfway through with kernel errors and other undefined weirdnesses. Meanwhile I had tried installing Windows 7 on a different partition. Which I found to be catastrophic also.

So no luck and I was forced to put up with OSX, which in my opinion is fine at what it does but it doesn't do very much for me. After a couple of tries I had to give up on fiddling with Ubuntu for I needed Windows 7 to run software for school. So my current partition layout looks like this:
{[efi][   OSX   ][       FILES      ][Windows 7]}
and I'm fortunate to say that it works fine this way... Although I am quite annoyed with the "efi" partition even existing. (I know there's bootloading reasons for it but all the same its in my way.)

So my plan for now is to put all my files on my "FILE" partition and get rid of both the "OSX" and the "efi" partitions to use that space for a nice Linux installation. A waste of OSX but oh well, I can't do much about having a dislike for closed source software and a preference for open source.

Problem is though I need to make sure everything will run fine when I get Ubuntu running. I need wireless to work, sound to work and the kernel updates not to screw up after I've installed the drivers for wireless (broadcom). When I updated x.x.x.14 to x.x.x.16 wireless stopped working, yes I've tried reinstalling the drivers.

I'm sorry for probably wasting a lot of your time with this thread , its indirect format and its length. But my overall questions and enquirers are:

- Has anyone successfully got Ubuntu running on the recent Macbook and if so how and what do I need to do?

- Can I create a secondary partition with a couple of logical drives to run and boot several linuxes? (like this: 
{([Ubuntu][Linux2][linux3][linux4])[MacOSX][Windows7][   FILES  ]}

- Would this be a better compromise if not?:
{[Ubuntu][linux2 (LFS)][     FILES      ][Windows7]}

Please forgive me if I'm totally wrong about this being even possible or if you think that I didn't do enough research, although there's next to no info about Ubuntu on the *new* Macbook. 

Suggestions and criticism are highly welcome:D

Thanks in advance and I hope this problem inspires/interests you as much as it does to me;)
Cheers!

---

### Post by CJN on 2010-01-09
I have 6 partitions on my MBP (supported by EFI by default, no worries) they are as such {{efi}, {OSX}, {MBR/BIOS}, {Windows 7}, {swap}, {karmic} } it's no problem to make lots of partitions (up to 10 I think...) in EFI which is what runs your mac behind the scenes.

---

### Post by Skatertjah on 2010-01-10
That's good news:) So how did you get them booting? And can each OS recognize all the other partitions (important for sharing files)? What method did you use to set this up?

---

### Post by kyuubi777 on 2010-01-10
I've had five partitions on my comp at one point, but if i were you I'd just run windows as a virtual os through parallels.. it's a great program and it will allow you to just have the BM dealing with two partitions..

---

### Post by Skatertjah on 2010-01-10
Is the trial version of Parallels any good? Does it expire? And can I still dual boot or does it take over my whole system? Anyway, I started the download for the trial version. But I'm skeptical about its performance. And it would still give me problems because I want to install a Linux as host to make an LFS system on a different partition. So it'll still be 5 partitions right? Which gave me issues before...

EDIT: The trial version of Parallels doesn't do much:S

---

### Post by Odin Overland on 2010-01-13
I have never had any problems running VirtualBox - and it will fit your Open Source taste.

---

### Post by Skatertjah on 2010-01-18
I'm now running VirtualBox, I love it, parallels sucks compared to it:P

Anyway, no success getting any Linux fully working yet, I will try when I have more time, which I currently don't have:P

Thanks for your help,
If I make any progress I'll be sure to keep you posted;)

Cheers

---

### Post by sml on 2010-01-21
> **Skatertjah said:**
> - Has anyone successfully got Ubuntu running on the recent Macbook and if so how and what do I need to do?


why start a new thread?

[http://ubuntuforums.org/showthread.php?t=1330781](http://ubuntuforums.org/showthread.php?t=1330781)

---

### Post by Skatertjah on 2010-01-26
hmm, I have browsed the forums but havnt found this thread, thanks for finding it for me, this will help me greatly:)

---

### Post by Megafag on 2010-01-27
> **Skatertjah said:**
> But wait, I also need a FAT32 partition so I can share my files between all three OS's. Tricky business.

just use a rather large NTFS partition, there are freeware NTFS readers for Mac OS X, im using one on my hackintosh.

---

### Post by Skatertjah on 2010-01-28
Sweet, thanks :), I do think NTFS will perform a lot better than FAT32. I'll have a look for an NTFS reader;)

---

### Post by Odin Overland on 2010-01-28
When you put Boot Camp 3.0 on your Windows partition you can read your Mac OS Extended (HFS plus) partition while booted in Windows.  I am sure you could use this to your advantage.  Boot Camp 3.0 should be available on your Mac OS install DVD (assuming your computer came with Snow Leopard).

---

### Post by Skatertjah on 2010-05-25
I'm now using Ubuntu 10.04 on my Macbook and I'm loving it! The only thing that has stopped working is screen brightness control...

I still got my Mac OS partition (which I never boot into) and I'm running Windows in a VirtualBox. I've had no problems with it since 10.04. It runs perfect!

Thanks for everyone that's pointed me somewhat towards the right direction back when Ubuntu didn't run well on my Macbook.

Cheers:)

---

### Post by NeddyDownUnder on 2010-05-25
> **Skatertjah said:**
> I'm now using Ubuntu 10.04 on my Macbook and I'm loving it! The only thing that has stopped working is screen brightness control...

I still got my Mac OS partition (which I never boot into) and I'm running Windows in a VirtualBox. I've had no problems with it since 10.04. It runs perfect!

Thanks for everyone that's pointed me somewhat towards the right direction back when Ubuntu didn't run well on my Macbook.

Cheers:)

Does your DVD drive work correctly on your Macbook 6,1 when you are in Ubuntu? Mine does not... If anyone is interested here's a link to the thread I started detailing the problem...
 [[COLOR="RoyalBlue"]"Macbook 6,1 Ubuntu Lucid 10.4 DVD drive not working after install"[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1470885") If anyone has any ideas I'd be happy to hear them.

Cheers

---

### Post by Skatertjah on 2010-09-30
The DVD drive sometimes behave a little odd. Ejecting is sometimes a problem when in the GUI environment. The button is software controlled for as far as I know, and it might not be working because of some Ubuntu configuration. If you need to eject you can just terminal: 

```
eject
```

and it should work ;)

Cheers

---

### Post by NeddyDownUnder on 2010-09-30
Thanks for the reply. A software update has fixed the problems I was having... I'm really happy, everything works great now.

Cheers.

---

