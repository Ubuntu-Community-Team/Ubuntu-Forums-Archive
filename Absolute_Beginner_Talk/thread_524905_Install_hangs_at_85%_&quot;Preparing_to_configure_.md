---
title: "Install hangs at 85% &quot;Preparing to configure xubuntu-docs&quot;"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Curbuntu on 2007-08-13
Okay, I'll admit I'm pushing the "minimum spec" envelope.  My test system is a Pentium I, 64 Mb RAM, using about 2.5 Gb (of a 4 Gb HDD) in a dual boot (old NT install) system, and I'm using the alternate install CD of Xubuntu 7.04.

Currently (and for the last eight hours or so) the install has been stalled at the message: 

**[CENTER]Preparing to configure xubuntu-docs[/CENTER]**

But, if I read the Xubuntu web page correctly, these bare-minimum specs should work.  (Indeed, I have Xubuntu 7.04 and OOo Writer up and running on a P-I 96 Mb Toshiba laptop, after learning how to tweak the xorf.conf settings).

Now, I'm fairly patient about learning *buntu, and this is particular install is hardly a mad-rush item.  It's more on the lines of finding out "Can it *really* install and run on only 64 Mb of memory?"  (It looks like I soon inherit another 64 Mb of RAM from a clone of this particular machine, though.)  I can wait out the install if it's *really* still installing.  But I'm curious about why it would hang here.  I was expecting (and prepared to deal with, thanks to other posts on this forum) the hang at 65% ("configuring anthy"), but this install actually paused about that time to ask me what to do; when I answered, it continued on its merry way.

Any ideas on why this install is stalled at this point?

---

### Post by gnuman on 2007-08-13
First of all: I can't help!

But, I just wanted to comment that I had exactly the same thing happen to me when trying to install Xubuntu 6.0 on an older computer with specs slightly higher than you listed.  I dreaded that 85% spot.   

I just wanted to get something on that old beast.  Eventually I went though all the PuppyLinux and Damn Small Linux options and such.  I ended up going with an old Fedora Core 4 install. :(

---

### Post by Curbuntu on 2007-08-13
> **gnuman said:**
> I just wanted to comment that I had exactly the same thing happen to me when trying to install Xubuntu 6.0 on an older computer with specs slightly higher than you listed.  I dreaded that 85% spot. 

Well, actually, knowing I'm not the only one (I didn't actually think I was, but one never knows until a response comes back) is something of a help.

> I just wanted to get something on that old beast.  Eventually I went though all the PuppyLinux and Damn Small Linux options and such.  I ended up going with an old Fedora Core 4 install. :(

At the moment, I've only got one real "production" machine for all my work -- a Compaq Presario laptop that has done yeoman duty.  So I'm essentially using "junkers" cobbled together or reclaimed from the garage (or others) on which to learn U/K/Xubuntu.  I'll make my mistakes, discoveries, and experiments on these machines.  If I break them, blow them up from the command line, or whatever, I can chalk it up to "a learning experience."

But my goals are longer term.  I really want to KNOW (in reality, not just website specs) what the *real* minimum specs are realistically.  That's because for a threefold reason (recycling old computers, helping the less fortunate, and feeding my inner geek) I'd like to get old, usable hardware up and running, test it out, load it with Ubuntu (or whatever the hardware will really bear), and give it away.  Although I've used DSLinux and considered other low-requirement distros, the Ubuntu family is the first one I've seen that looks like: a) it's the most Windows-like; and, b) the GUI will remain more or less consistent over the long haul.  Considering that the small group of us who want to do this will have to offer some minimal level of support, it would behoove us to standardiize on one type of Linux and stick with it, knowing it very well, inside and out.

Along these lines, finding (in reality) the "lowest common denominator" when it comes to hardware, we'll also be defending ourselves from a pile of junk, that is, machines that are just TOO underpowered to be useful for any level of *buntu.  It's easier to say "no, sorry," up front to a potential machine donor than to have to deal with *really* recycling and having to pay to dispose of someone else's hardware corpses.

So, I'll plod along with the current install at least for the rest of the night.  Actually, I had it Xubuntu installed once on this machine (sort of), but X shell never "took," so the GUI never worked.  I did get a root prompt, though, so (if nothing else) I can do some command-line fiddling.  But I'm almost to the point where we'll draw the line at nothing under 128 Mb of RAM.

---

### Post by panther_sn on 2007-08-13
I had similiar probs on a p3 366mhz with 64mb ram what I did at that point where it kept freezing press ctrl C and see if it will continue, worked for me

---

### Post by Curbuntu on 2007-08-14
Well, I tried your **ctrl-c** trick last night, but nothing seemed to happen.  I figured I'd give the process one more night.

This morning when I went in to check, the install program was waiting for a reply from me.  And it has asked for input  7 or 8 times already this AM.  But once I tell it what it wants to know (e.g., how I want "man" set up, whether I want encrypted passwords, info about a *dial-up* ISP account, etc.) it goes back to the progress bar, still at 85%.

BTW, I don't recall having to answer any of those questions on my laptop Xubuntu install.  I wonder if (ultimately) those were triggered by the ctrl-c?

---

### Post by Luinar on 2007-08-14
Don't know if this will work, but you could always try just installing the base command line system (I think there is an option for that on the alternate install disc) and then when that is up and running, grabbing the xubuntu-desktop/xfce (not entirely sure what it is for xubuntu) package from apt. 

The Ubuntu install would keep hanging on my main machine (512Mb RAM, so definitely met the specs); that was the only way I could get Ubuntu up and running...

---

### Post by overdrank on 2007-08-14
> **Curbuntu said:**
> Okay, I'll admit I'm pushing the "minimum spec" envelope.  My test system is a Pentium I, 64 Mb RAM, using about 2.5 Gb (of a 4 Gb HDD) in a dual boot (old NT install) system, and I'm using the alternate install CD of Xubuntu 7.04.

Currently (and for the last eight hours or so) the install has been stalled at the message: 

**[CENTER]Preparing to configure xubuntu-docs[/CENTER]**

But, if I read the Xubuntu web page correctly, these bare-minimum specs should work.  (Indeed, I have Xubuntu 7.04 and OOo Writer up and running on a P-I 96 Mb Toshiba laptop, after learning how to tweak the xorf.conf settings).

Now, I'm fairly patient about learning *buntu, and this is particular install is hardly a mad-rush item.  It's more on the lines of finding out "Can it *really* install and run on only 64 Mb of memory?"  (It looks like I soon inherit another 64 Mb of RAM from a clone of this particular machine, though.)  I can wait out the install if it's *really* still installing.  But I'm curious about why it would hang here.  I was expecting (and prepared to deal with, thanks to other posts on this forum) the hang at 65% ("configuring anthy"), but this install actually paused about that time to ask me what to do; when I answered, it continued on its merry way.

Any ideas on why this install is stalled at this point?


HI an yes you are pushing the min requirements 
```
Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only required you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.

```
I have installed on 64 mb of ram before but your video card cant be on the motherboard because it shares the ram of the system and at 64mb you should get a warning to create a swap partition. If you can do this first it should install, Good Luck!

---

### Post by Curbuntu on 2007-08-14
> **overdrank said:**
> HI an yes you are pushing the min requirements

I'll say!  But that's part of the fun.  If I actually get it running, at least I can say that Xubuntu will actually install and run with that amount of memory.

> ```
Minimum system requirements

...or 192 MB RAM to install. The Alternate Install CD only required you to have 64 MB RAM.
```

Even though I'm not using the Live CD install, I see that I had forgotten that 192 Mb RAM are needed for that.  I need to file that away in some mental drawer.  For the time being on these creaking dinosaurs, I'm using the Xubuntu alternate install CD.

> ```
To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended 
to use at least 128 MB RAM.
```

No problem in HD space.  And Xubuntu wasn't even phased by the fact that this unit has a SCSI drive, rather than an IDE drive.  Truthfully, after this experience, I, too, will **"strongly recommend"** a minimum of 128 Mb RAM! :)  In fact, the friend who donated this machine to me has two more exactly like it.  The mobos (old Asus AP5T, Rev. 3's) can take four 32 Mb SIMMs or two 128 Mb DIMMs (but DIMMs and SIMMs can't be mixed on the mainboard).  I'm going to see if they'll donate another unit (the one I got was tagged to go to the dumpster, eventually) so that I can cannibalize the two 32 Mb SIMMs and bolster this critter's RAM.

> I have installed on 64 mb of ram before but your video card cant be on the motherboard because it shares the ram of the system and at 64mb you should get a warning to create a swap partition. If you can do this first it should install, Good Luck!

Shared VRAM?  This mobo is so old, I don't even think shared VRAM had been thought of.  No, this has a "discrete" ISA[!] video card with a whopping 1 Mb of VRAM on it!  (I have no shame!)

---

### Post by Curbuntu on 2007-08-14
Well, it's time to hang up this 64 Mb attempt.  After two days, the install process ended with a failure to properly install the "X" level under the GUI.  Time to scrounge 64 Mb more of memory...

---

