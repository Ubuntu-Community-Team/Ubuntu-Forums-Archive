---
title: "Can I dual boot OS X and Ubuntu from an external drive?"
date: 2006-07-15
forum: Apple PPC Users
---

### Post by Carbonfish on 2006-07-15
Hi all,

I'll begin by saying that I have not yet installed Ubuntu on my iBook G4 PPC (1.2 GHZ), but have ordered the Live CD, and while I am waiting for it to arrive have been quietly prowling these forums, as well as the Wiki, and just about everywhere else I could find for info. Finally I'll get to my question. I have a big (250 GB) Lacie external HD, and I have it partitioned into three chunks. One is the same size as my internal HD (30 GB), and I use that space for a bootable clone of my internal drive. The other two partitions are approx. 100 GB each and are empty right now. So rather than carving up my little internal drive, I would prefer to use the "big empty space." Is there any reason that I can (or should) not install Dapper Drake to one of the partitions on the external drive and boot to it there? I would like to see how it works and get it set up nicely before I would feel the need to carry it around with me, so having to "plug in" the external firewire drive would not be an issue. Any thoughts?:mrgreen: 

TIA for your patience with my ignorance, and any insights you may have for me.:-k 

KC

---

### Post by projectle on 2006-07-15
In all practicality, you "can" install dapper onto your external drive and *everything* will work just fine(tm).

I have personally seen my own fair share of problems under a Powerbook 1.67GHz to which I have been driven crazy.

For example, I could get my Airport Extreme card to work under Linux, but then when I went back into OS X, I found that it was not working and needed to CTRL-OPT-N-V to get it to work again (and then disapear when I went back into Linux).

Then, there were issues when I tried to use MOL under Dapper where I could no longer boot into OS X at all, however could still access it through MOL if I restricted myself to 800x600 (pretty sad full screen resolution on a 17" 1680x1050 widescreen).

Aside from those, everything went alright (And no, that part is not sarcastic).

---

### Post by Uta on 2006-07-15
I have a G4 iBook that is a dual boot on the iBook's internal drive(Tiger and Ubuntu) and an additional Linux distro on an attached firewire drive. The mistake I made and something you might consider is; I installed to the FW drive last so it made itself the bootloader and got it's blessing. I had a nice 3 way boot but if I dettached the FW drive my iBook wouldn't boot, so I had to move the bootloader back to the main internal HD. The point being if you put your bootloader on an external drive, how would you possibily get the main internal drive boot option; where would your boot call come from if you didn't have the FWD (I'm assuming it's FW and not USB?) attached? I am not an expert by any means on yaboot and just don't know if you can get listed 2 different Mac OSs, plus the linux distro? If you do manage this, please share your results (or defeats) Good Luck.(My 3 way boot is very stable and I had zero issues with the Airport card)

---

### Post by Carbonfish on 2006-07-15
Hi Uta,

This is something that I had not considered. I assumed that if I installed Ubuntu to the firewire drive that the "bootcall" would stay with the internal drive as it would be the only drive available unless the external drive was plugged in. Then I would just use the startup disk utility (or hold option key at re-start etc.) in my sys. prefs. to boot to Ubuntu on the external drive in the same way that I am able to boot to my OS X clone to sync it or erase/re-clone etc.

It seems that there is obviously more that I need to know??

Oh yeah, I forgot to mention that I am aware that these are "noob"questions. So if anyone/everyone thinks it would be more appropriate for me to take them to the beginners forum, please let me know. I just thought that since I am a Mac user that I would start here. Thanks 

Thanks for responding, and I am grateful for all insights. I would love to use Ubuntu, and want to make the transition as fun and painless as possible. So your help is invaluable and greatly appreciated!:mrgreen: 

KC

---

### Post by Nels on 2006-07-15
I've just set up a dual boot OSX Tiger and Ubuntu on my PowerBook G4. Whenever I started up the Ubuntu bootloader would take over as the primary loader and it would give me the option to chose which OS to load. I didn't really want to have that way. I wanted OSX to load by default and have the Ubuntu option only when I powered up with the option/alt key held. I got what I wanted on the OSX side of things by going into "system preferences >start up disk", and simply choosing to use OSX as start up. Now it works just the way I want. I can even easily go into Ubuntu on a OSX restart by holding down the option/alt key, and vice versa without the option/alt key. Now if I could only get the WPA wireless working.

---

### Post by Carbonfish on 2006-07-15
Hi Nels,

Thanks for responding. It sounds like that is working fine for you (sort of), but it also sounds like both operating systems are on the same drive, yes? I think that just to clear this up in my mind I would have to ask: Can I just load Ubuntu onto an empty partition on my external drive and then use my start-up disk preference (or whatever) to boot to it without ever worrying about what Ubuntu's bootloader wants to do, since unless the external drive is mounted, OS X wouldn't know it was there? Did that make sense?

Thanks for your thoughts everyone.:mrgreen: 

KC

---

### Post by projectle on 2006-07-15
I personally did not have an issue by installing placing yaboot to /dev/sda1 and then blessing the drive after all was said and done.

---

### Post by Carbonfish on 2006-07-15
> **projectle said:**
> I personally did not have an issue by installing placing yaboot to /dev/sda1 and then blessing the drive after all was said and done.

                             

                             :-k   ?

---

### Post by Nels on 2006-07-15
Carbonfish, yes, both Ubuntu and OSX are on the internal HD as I wanted to be able to take both around with me, though I was thinking of installing it on an external. All the same, I believe this would work similarly with Ubuntu on an external HD. But I am really new to this and this is not experience based, so listen to others for better ways.

---

### Post by Carbonfish on 2006-07-15
Thank you Nels.

I appreciate your candor and your advice. I'll keep watching this thread and hope that someone can steer me in the right direction. That said, every little bit helps.

KC

---

### Post by king_arthur on 2006-07-16
> **projectle said:**
> I personally did not have an issue by installing placing yaboot to /dev/sda1 and then blessing the drive after all was said and done.

Hi there, could you please be a bit more descriptive? 
How did you do it?

I have tried to install Dapper on my external FW hard disk but, as usual, the installer fails on the Yaboot part.
In Breezy, there were issues with both, yaboot and FireWire, as the lack of FW support in the kernel made it impossible to boot Ubuntu after install unless you replaced the kernel and did some additional hacking to the yaboot.conf file.

I was hoping for this to be fixed by now... :(

BTW How comes your Apple Partition is missing? it should be:
sda1 = Apple partition map,  
sda2 = new World BootLoader (needed for yaboot), 
sda3 = ext3 (the filesystem), 
sda4 = swap


/P

---

### Post by Carbonfish on 2006-07-16
Okay, now we're getting somewhere. Perhaps my title should have been: "Can I install Ubuntu on an external drive?"

I am really not interested in trying to install another OS on my little 30 GB HD in my iBook. So the nuts and bolts of it comes down to that question, "Can I install Ubuntu on an external drive?", and secondarily, can I just use my "start-up disk" utility (or whatever other method I choose) to boot to that volume on the FWHD?

If this has already been answered and I am just too thick to see it, could someone just point me to the algorithm by which I might achieve my ends. Or in the case that it can't be done with this iteration of Ubuntu, please let me know that so that I don't spin my wheels for nothing?

Oh yeah, I almost forgot to ask, am I going to have to download and install "Boot Camp" to install from the live CD regardless of where I choose to install to, or will my disk utility see the live CD all by itself?

TIA for your patience and advice.

KC

---

### Post by Carbonfish on 2006-07-16
I guess that when I edited a while ago it caused a double post. Just fixing that here.

---

### Post by king_arthur on 2006-07-16
> **Carbonfish said:**
> Okay, now we're getting somewhere. Perhaps my title should have been: "Can I install Ubuntu on an external drive?"


The short answer is yes.

The long answer is yes but it involves quite a bit of hacking and, frankly speaking, I don't think it's worth the effort... ;) 

Having said that, if you really want to go ahead with it, a good place to start is this wiki: [https://help.ubuntu.com/community/BootFromFirewireHardDisk](https://help.ubuntu.com/community/BootFromFirewireHardDisk) and further links to macubuntu.blogspot.com.
I followed that how-to step-by-step and albeit it is a complex process, it worked.

Most of the documentation is relevant to Warty or Breezy, I was expecting this issue to be fixed with Dapper but so far, it does not look like it has been unless **projectle** is going to tell us how he did... :)

Good luck!

/P

---

### Post by Carbonfish on 2006-07-16
K_A,

Thank you for your reply, and thanks as well for the links. I will head over there when I am done typing this and see what I can see. I am beginning to wonder whether I might be done with Ubuntu for PPC  before I ever got started. I am considering going out and buying a used x86 laptop to try Linux on and not attempt to make this iteration work on my Mac, but that makes me feel like I am giving up too easily. Oh well, thanks again, and if anybody has a workaround for this issue please post it. I really would like Ubuntu living on my FWHD, and there's still a couple of weeks before the Live CD arrives in the mail.

EDIT: king_arthur, I just found this:  [http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html](http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html)   out in the world. It's old, and I don't know how reliable it is. But it's an interesting read.
KC

Thanks,:-\" 

Kent

---

### Post by Carbonfish on 2006-07-17
Well, I guess that after a couple of days of reading through the recent (and not so recent) past I have to admit that I asked a commonly asked question, that so far has not been satisfactorily answered. Or perhaps more accurately, can be done, but nobody seems to agree on just *how* it is done.

Since I don't want to try to install Ubuntu onto what is left of my 30 GB internal HD, I guess I'll just have to wait until the community builds an iteration that includes external boot-ability.

Sad.   :neutral:

KC

---

### Post by khulse on 2006-07-17
Hi, just a note to say I have been trying to do the same thing on my Mac mini but the only Linux I have got working off a firewire drive is Yellow Dog 4.1 (now available as a free download) - which isn't surprising since it is built specifically for ppc. In fact, Yellow Dog is the only flavour I have managed to install full stop - most of the other flavours fail for differing reasons. Like you said, though. Sad.

---

### Post by king_arthur on 2006-07-17
> **Carbonfish said:**
> K_A,


EDIT: king_arthur, I just found this:  [http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html](http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html)   out in the world. It's old, and I don't know how reliable it is. But it's an interesting read.
KC

Thanks,:-\" 

Kent
Well, that's the one I mentioned in my reply.
It is proven to work as I managed to succesfully boot from my external FWHD following those instructions.
Still I wonder why the developers are not taking care of this issue.
Consider it is a longstanding bug reported several times in bugzilla and all it takes to be fixed is build a kernel with FW support.

Should be an easy fix for the Ubuntu team but than, again, (I khow this is not going to be popular) who needs Linux when you can have OSX?.. :D

 
/P

---

### Post by Carbonfish on 2006-07-18
Okay guys,

I'll ask one more question out of ignorance before I give up and use YDL instead of Ubuntu, so please bear with me.

If I boot OS X from my firewire drive and then try to install Ubuntu into a free space partition on the same drive, why would Ubuntu think that it was going to an external drive? Is it that "firewire" itself is not supported, or that the drive is not yet supported at that stage (pre-yaboot)of the install?

I guess what I am trying to say is, if I am installing Ubuntu to the same drive as OS X, just in a different volume, why does the Ubuntu installer (or bootloader, or yaboot) care if it's the internal drive or the firewire drive? It is one HDD, no?     :-k 

I'll wait a while for an answer, and then go download YDL.

Thanks to all of you who tried to shine some light on this for me.
**Hey Ubuntu developers, read this post!** 

KC

---

### Post by king_arthur on 2006-07-18
> **Carbonfish said:**
> Okay guys,
If I boot OS X from my firewire drive and then try to install Ubuntu into a free space partition on the same drive, why would Ubuntu think that it was going to an external drive? Is it that "firewire" itself is not supported, or that the drive is not yet supported at that stage (pre-yaboot)of the install?


Hello Carbonfish,

the reason why Ubuntu at present cannot boot from an external FW drive without "tweaking" is simply because the kernell (image) installed by the standard Ubuntu installer lacks FireWire support.

As for starting OSX from the external and than installing Ubuntu that is not possible as you need to start your computer from the Ubuntu disk to install, pretty much the same as you would do with OSX.

Mind you that Ubuntu will install just fine wherever you want it to live, the problem is it won't boot from external FW because of the reason I mentioned hereabove.
The Apple boot mechanism on (NewWorld) PPC macs is through Open Firmware.
You have to tell the BootRom where to find a valid boot loader (Yaboot takes care also of this part) and that's what you can seen by holding down the option key on startup.
So the boot sequence will be as follows: bootrom tells from which bootloader you want the computer to start. If it finds Yaboot, Yaboot tells the computer to load a kernel image, and that will work untill it will try to load the Root filesystem and as you need FW support to do that, the loader will bail out from the process with a kernel panic.
The solution is to manually change the original kernel image with a suitable one as clearly explained in the links I gave you.

Finally, let me say you could go either way (Ubuntu or YDL) on a Mac, it doesn't matter however, if all you want is just to play with it to get the feel of Linux, personally I would raccomend a cheap PC as the i386 port is much better supported and your experience would be a lot more enjoyeable.

But life is a school of hard knocks and I believe you will have to experience by yourself in order make up your mind and judgement.

/P

---

### Post by Carbonfish on 2006-07-18
Hello king_arthur,

Thank you for your patient explanation. I understand now. I appreciate your advice and will most likely attempt to find a used x86 machine to tinker with. My hope was to be able to do away with "proprietary" software on the machine that I use all the time. Since that is my iBook, ideally that is where I would have liked to make the change. I guess that is not practical at this time. I rely far too much on this machine for my day-to-day survival to experiment with it. I suppose that this might indicate that I lack the courage of my convictions. Perhaps I do.

Thanks again for your helpful information and advice.

Kent

---

### Post by sivart6 on 2006-07-19
hi. looked at this thread because i have a similar question. I have Tiger installed on an external 160GB FW drive connected to my PPC Mac mini. the internal drive is empty at the moment, and i have a 400GB USB data drive connected also. What I am wondering is, can i install ubuntu onto the empty internal drive, then make Tiger boot by default?

---

### Post by Carbonfish on 2006-07-19
sivart6,

From what I have read I don't see why that wouldn't work (someone please jump in if I am getting my foot close to my mouth), as you would just be able to do a "normal" install of Ubuntu onto the internal drive, and as long as Ubuntu supported the external drive after installation you should be able to boot to that. Once running OS X, I would think that you could just select which startup disk you wanted to use in sys. prefs. Again, **I have not tried this, so if I am wrong someone please jump in with correct information**. I am here to learn, so I encourage correcting me if my hypotheses are off the mark.

Good luck.

KC

---

### Post by king_arthur on 2006-07-20
Hi there everybody,

If you have a "Neworld" mac you can install OSX or Ubuntu on whatever HD disk you like pretty much the same way.
Just start the computer with the installer disk into the CD drive and hold down the "C" key and follow the instructions.

Once you are finished installing your dual-boot (triple?) system, you will be facing a number of options:

If you install OSX first and Linux later, you may find yourself with the Yaboot bootloader taking over control. You can change this easily from OSX System preferences --> Startup disk.

If you install Linux first and OSX later, OSX is taking over but using the option key at startup will prompt you for the graphical OpenFirmware menu where you can choose to start from whatever bootable volume/partition you have.

Another option you have is to startup from Yaboot as standard and choose from there what you want to boot next. Yaboot configuration file gives you plenty of flexibility and it works pretty much the same as the LILO loader on a 386 machine. You will have to do this by editing /etc/yaboot.conf from within Linux and run the **ybin** command at the end to make the changes permanent.

Sounds a little confusing but once you practice a couple of times you will fully understand. :)

Hope this helps.

/P

---

