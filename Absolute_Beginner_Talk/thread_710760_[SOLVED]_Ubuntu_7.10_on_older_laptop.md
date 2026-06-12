---
title: "[SOLVED] Ubuntu 7.10 on older laptop?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Crossbow on 2008-02-28
I got the Dell 530N PC with Ubuntu 7.10 preinstalled, and I like it so much I want to install 7.10 on my laptop. But when I try, it seems to be installing, looks like it's ready to go, and then suddenly goes to a blank screen with colored stripes. Which are pretty, but not terribly useful.

Both times I tried it, there was an error message: "Buffer I/O error on drive fd0, logical block 0." It appeared twice each time.

The second time I tried it with the Ubuntu disk in one drive and the driver disk in the other. I don't know if that makes a difference.

Is my laptop just too old? It's a Dell Inspiron 8100. I got it used, and I think the guy told me it was a 2002 or 2003.

I'm told that error is a floppy error, but I don't have the floppy drive in the computer. I have two CD drives.

---

### Post by freebeer on 2008-02-28
fd0 is, indeed, a floppy disk designation.  It would appear that Ubuntu is identifying the 2nd(?) CD-ROM as a floppy.  Is this, by any chance, one of those dual-disk jobbies?  It's kind of hard to say how exactly the second CD is configured.  (You can get some odd hardware configurations in laptops.)  Can you disable the second CD-ROM in the BIOS?  I'm thinking that if you could do that, you'd be able to proceed with the install, then later on figure out how to get the second CD-ROM drive working.

As for your primary question, you should be ok with Ubuntu on a machine from that era, but much depends on the processor and memory.  What's the processor and how much memory does it have?

---

### Post by Crossbow on 2008-02-28
It is one of those where you can switch the CD and floppy drives. I put in the floppy drive and tried again and I stopped getting that error, but I am still getting nothing but striped bars after it finishes setting up. 

The memory is 512 kb.

---

### Post by Papa-san on 2008-02-28
This is a verified bug in 7.10. 
[https://bugs.launchpad.net/gparted/+bug/155047](https://bugs.launchpad.net/gparted/+bug/155047)


It picks it up from the BIOS. 

use:```
sudo gparted /dev/sda
```I don't know if you are trying gparted, but whatever it is where you designate partitions, you need to specify your hard-drive: '/dev/sda'

Make sure you set your swap partition to be big enough to hold two times your memory, at least. 

I have been stopped from installing 7.10 on my Dell C-610 because I only have 256M of memory. If you have this or less, you will need to use the alternate install CD because the graphic installer uses too much memory...

The striped bars is because your video isn't set right. I'm not exactly sure how to get into the settings, but the default resolution is far beyond the capability of older laptops. see if you can change your resolution to something like 1024x786 or even 800x600 until you can get it set up.

---

### Post by freebeer on 2008-02-28
I believe that you can also try the test-based install option.  You get menu selections, but it's text based.  This by-passes and issues you may have with the graphics card settings.  Once installed, you can then grab the correct graphics drivers and get set up that way.

(Sorry that I couldn't be more explicit... I've been lucky and have never had to use the text option, so I'm unfamiliar with it.)

---

### Post by Crossbow on 2008-02-28
> **Papa-san said:**
> This is a verified bug in 7.10. 
[https://bugs.launchpad.net/gparted/+bug/155047](https://bugs.launchpad.net/gparted/+bug/155047)


It picks it up from the BIOS. 

use:```
sudo gparted /dev/sda
```I don't know if you are trying gparted, but whatever it is where you designate partitions, you need to specify your hard-drive: '/dev/sda'

Make sure you set your swap partition to be big enough to hold two times your memory, at least. 

I have been stopped from installing 7.10 on my Dell C-610 because I only have 256M of memory. If you have this or less, you will need to use the alternate install CD because the graphic installer uses too much memory...

The striped bars is because your video isn't set right. I'm not exactly sure how to get into the settings, but the default resolution is far beyond the capability of older laptops. see if you can change your resolution to something like 1024x786 or even 800x600 until you can get it set up.

If I change the resolution in my current OS (which is 6.10, I believe) will it stay set? Because I can't do anything at all in 7.10. 

I don't know what you mean by alternate install CD. 

I also don't know what to do about the partitions. When I originally installed Ubuntu, I just did what the prompts told me. Since it was the only thing on there, I didn't think I needed to worry about it. When it goes through the 7.10 set up it never gets to the point of prompting me for partitions. 

If it helps, I don't run multiple operating systems, and I pretty only use that computer for writing and email, so I'm not doing anything fancy with it.

---

### Post by eriqjaffe on 2008-02-28
> **Crossbow said:**
> I don't know what you mean by alternate install CD.The alternate install CD has different install options, including a "text mode" install, which is recommended for older laptops.

[http://releases.ubuntu.com/7.10](http://releases.ubuntu.com/7.10)

...although if your laptop has 512mb of RAM, the standard disc should be alright.  I had to use the alternate CD for my **very** old laptop (366mhz Pentium II w/128mb of RAM), but I did a command-line install and build up a graphical interface around that.

---

### Post by EmoDx on 2008-02-29
> **Papa-san said:**
> This is a verified bug in 7.10. 
[https://bugs.launchpad.net/gparted/+bug/155047](https://bugs.launchpad.net/gparted/+bug/155047)


It picks it up from the BIOS. 

use:```
sudo gparted /dev/sda
```I don't know if you are trying gparted, but whatever it is where you designate partitions, you need to specify your hard-drive: '/dev/sda'

Make sure you set your swap partition to be big enough to hold two times your memory, at least. 

I have been stopped from installing 7.10 on my Dell C-610 because I only have 256M of memory. If you have this or less, you will need to use the alternate install CD because the graphic installer uses too much memory...

The striped bars is because your video isn't set right. I'm not exactly sure how to get into the settings, but the default resolution is far beyond the capability of older laptops. see if you can change your resolution to something like 1024x786 or even 800x600 until you can get it set up.

I have a Micron GX 850Mhz P3 w/256 MB ram. The install took close to an hour and a half. I upgraded the hardrive to a 5200 RPM drive and it shaved off 15 minutes from the install. The graphical install was fine here. In regards to the partitioning, I used 518 MB for my swap, putting it at the beginning. I used a 10 GB partition for my OS, and the last 29 GB for my \usr files.
The text installation might be the way to go for you. Your graphics card is your hold up. Probably an onboard chip sharing system ram. Best of luck!

Emo

---

### Post by wolfen69 on 2008-02-29
i would go with Xubuntu Feisty alt cd.  works great with 256 ram.

---

### Post by Papa-san on 2008-02-29
> **Crossbow said:**
> If I change the resolution in my current OS (which is 6.10, I believe) will it stay set? Because I can't do anything at all in 7.10. 

I don't know what you mean by alternate install CD. 

I also don't know what to do about the partitions. When I originally installed Ubuntu, I just did what the prompts told me. Since it was the only thing on there, I didn't think I needed to worry about it. When it goes through the 7.10 set up it never gets to the point of prompting me for partitions. 

If it helps, I don't run multiple operating systems, and I pretty only use that computer for writing and email, so I'm not doing anything fancy with it.Your re-setting video options in the current OS won't help. The live CD sets it's own, and it's too high for your system. (There is an option at the initial boot-up screen to change the resolution, (f4, I believe) But I have had it work only when I use the second install option... with video support or something.)

There are two (at least) different .iso images you can download. The standard one gets put into your cd drive and you boot it. It will get you to an Ubuntu desktop with a desktop icon that is a shortcut to install the OS. That is the one with the graphical interface that is pretty resource heavy for older machines to use. Some can handle it, as EmoDx mentioned, but some don't. For those of us who can't use this, we need to download the 'alternate install' image. Go here,
  [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) 
and below the Start Download button, there is a checkbox that says to check it if you need the alternate Desktop CD. That's what you want. Can you get one of those? If so, I can help walk you through getting your partitions set up so your '/home' is on it's own partition, so you don't lose data when they change the kernel. 

What size is your hard drive? how much memory is in the system?

---

### Post by cmittle on 2008-02-29
Are you using a cd that you downloaded and burned to try to install this, or the install cd from your new laptop?

---

### Post by sneeks on 2008-02-29
there is a safe graphics mode on the live cd,give that a try...

---

### Post by Crossbow on 2008-03-01
To answer the previous questions: 

The memory is 512. 

The CD is the one that came with my Dell desktop, not one I burned myself. I can do that, but it means using my roommate's PC (mine can't burn) which is Windows and takes half an hour to do ANYTHING and gives me a headache, so I've been putting off trying. 

I'm being told in another forum that the bars I'm seeing mean I don't have enough RAM to run the live CD but it should work once it's installed, the only problem is installing it. I've already backed up all the files I had on there, so I don't mind losing everything. 

Will go look for that "safe video" option now. Thanks.

---

### Post by Crossbow on 2008-03-01
I think it's working now! I hit F4 and was able to change the resolution before doing the safe graphics install.

---

### Post by Papa-san on 2008-03-01
Awesome!

If this has solved the issue, please mark the thread as 'Solved'. (That way, the next person who runs into that problem knows this is a good thread to follow!) The 512 megs of memory eliminated the possibility that it was a memory related thing anyways.

---

