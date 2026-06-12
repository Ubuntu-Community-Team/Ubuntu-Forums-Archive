---
title: "Ubuntu 6.0.6 Crash Need to restore"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by hwroth1 on 2006-08-27
Hi, 

My ubuntu operation system has crashed. 

These are the things I can do:
1) I can start up a live cd . I was looking for a restore option.

2) I can use 386 kernal that is labeled rescue it boots up to a console screen and waits for a command.  

When I use startx It starts a desktop and I get a message that 

[INDENT][I]the system can not start until the dbus system server is running. The message stays in the center and does not allow me to do anytning but shut down. It continues.... Reboot after starting messaging 
[/I][/INDENT]]

3)When I try to start the 386 kernal the system tries to boot but hangs. This is what happens:

[INDENT][I]The ubuntu splash screen comes up and the bar goes from left to right and then reverts to a console screen. Messages fly on by and then gets stuck with this last item 

                      Starting System Log

At that point it gets stuck and can go no further.[/I][/INDENT]

[CENTER]I would like to fix this without having to install a new OS.[/CENTER]

_I am running a foxconn mini_

    * Foxconn Tuckaway Barebones System (Includes Slim CDRW-DVD Drive)
    * Western Digital WD2500KS 250 GB SATA Hard Drive
    * Single 1 GB DDR400 (PC3200) SuperTalent 184-Pin DIMM
    * Intel Pentium 4 - 3.0 GHz Processor (LGA775)

Tuckaway Specs:

Dimension:	67(W) x 325(H) x 300(L)
Motherboard:	915S09
Processors Supported:	Intel® LGA 775 Pentium® 4 Prescott,
Celeron® D; 533/800 MHz Front Side Bus;
up to 3.4 GHz
Chipset:	Intel 915GL Northbridge; Intel ICH6 Southbridge
Memory:	DDR 333/400 SDRAM; Up to 2GB - 2 DIMM slots
VGA Graphics:	Integrated Intel Graphic GMA 900
Storage Interface:	ATA-133; SATA (Serial ATA)
Expansion Slots:	1×PCI
Audio:	Realtek ALC655 AC97 5.1 channel
LAN:	10/100/1000 Mbps onboard Ethernet controller
Driver Bays:	1 x 3.5” Easy Access Hard Drive Bay
Front Panel:	1× Power button
1× Reset button
2× USB 2.0 ports
1× mini IEEE 1394a port(4 pins)
1× Microphone
1× Earphone
1× 7 in 1 card reader
1× Power indicator
1× HDD indicator
1× LAN indicator
Back Panel:	

1× 19V DC input port
1× 1394 port with 2 USB ports
1× line in/line out/microphone
1× PCI slot
1× RJ45 LAN port with 2 USB ports
1× PS/2 Keyboard/Mouse
1× VGA Port
1× Serial Port
External Power Adapter:	200W (external)

Any help would be greatly appreciated.

hwroth1

---

### Post by Metacarpal on 2006-08-28
Hi!  To know how to fix this, we'll need to figure out what caused the crash.

Is this happening right after your first install of Ubuntu, or have you been using the system for a while?

Did you recently install new software, compile your own kernel, move/delete files or folders, any of that sort of thing?

Suggestion for entering Recovery mode: when it gets to Starting System Log (the part where it hangs up), hit Ctrl+c to bypass that part of the startup process.  It should move on to the next bit.

---

### Post by hwroth1 on 2006-08-28
I did a few things that I remember before the crash. I have been using and upgrading this system for about a week and had it working good.

The last things that I did I changed the video resolution from 1200 x to 800x600. The small print was killing my eyes. 

I used the xine movie viewer to see if vcd's would work it started ok but when I changed the sound switch to something like -1 the sound would not come back up. 

Previous to running the xine movie player. I started the mplayer and it just hung up and wouldn't unload. No matter what I did it would not close. 

I decided to close the system and reboot. I thought the sound would come back. When I did that it hangs at the 

starting system log. 

I then tried the other things I mentioned. Booting with a live cd , and using the resuce mode.

---

### Post by hwroth1 on 2006-08-28
> **Metacarpal said:**
> Hi!  To know how to fix this, we'll need to figure out what caused the crash.

Is this happening right after your first install of Ubuntu, or have you been using the system for a while?

Did you recently install new software, compile your own kernel, move/delete files or folders, any of that sort of thing?

Suggestion for entering Recovery mode: when it gets to Starting System Log (the part where it hangs up), hit Ctrl+c to bypass that part of the startup process.  It should move on to the next bit.
I tried Ctrl C and it didn't do anything. 

hwroth1

---

### Post by insub2 on 2006-08-28
do you got files and such you need to keep?

if not, i suggest a reinstall.

---

### Post by hwroth1 on 2006-08-28
I don't have a lot but I spent a lot of time on upgrades and reconfiguring files. It was several hours of work and downloading. 

If I do reinstall will this happen many times. In windows I can restore to a better time when it was working. Does ubuntu have such a feature.

---

### Post by handy on 2006-08-28
It does not happen many times.

The best thing you can do, is setup with a separate **/home** partition on your drive, or a separate **/home** drive.  Then if you have to do an upgrade or rebuild, all your data & the file structure stays intact.

Here is a great guide for setting up a [separate home partition]("http://www.psychocats.net/ubuntu/separatehome.html").

In case you don't know about [Automatix]("http://www.getautomatix.com/"), it may save you some time in setting up, it certainly saves me some...

All the best... :KS

---

### Post by xyz on 2006-08-28
This will not help you this time around but to prevent it from happening again, you might want to take a look at the howto Backup and Restore thread (pretty much the same as Win's System Restore!) ...and of course a /home partition is great as well. Hope you'll be able to keep your data safe.

[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

---

### Post by hwroth1 on 2006-08-28
Now that it seems there is no cure for my problem I need to protect myself if it happens in the future. 

All the posts have been most helpful.I will read the suggested material before I install again. 

This is the third time I have had to install ubuntu. If anyone has other suggestions I would appeciate. Thank guys. 

hwroth1

---

### Post by Metacarpal on 2006-08-28
> **hwroth1 said:**
> Now that it seems there is no cure for my problem I need to protect myself if it happens in the future. 

All the posts have been most helpful.I will read the suggested material before I install again. 

This is the third time I have had to install ubuntu. If anyone has other suggestions I would appeciate. Thank guys. 

hwroth1

3rd time?  Really?  The only time I've had to reinstall was when I'd been putzing around with my settings too much and broke it myself.  Even then it was probably fixable, I was just too lazy. :-\" 

In how short a time period have these reinstalls been needed?  If they've been fairly close together, that might indicate gradual hardware failure...

---

### Post by hwroth1 on 2006-08-28
> **Metacarpal said:**
> 3rd time?  Really?  The only time I've had to reinstall was when I'd been putzing around with my settings too much and broke it myself.  Even then it was probably fixable, I was just too lazy. :-\" 

In how short a time period have these reinstalls been needed?  If they've been fairly close together, that might indicate gradual hardware failure...
I should have made this clear. This last time it crashed only after I tried to reboot. The computer was working before I rebooted. It was just doing some weird things. 

The two previous times I was trying to install multiple os's and damaged my install. Each time I have had to re-install it has taken up a lot of time doing the same things over again and over. 

I see that their is a way to backup and restore to an older backup and I can also set up a /home partition so I can save my files. 

hwroth1

---

### Post by xyz on 2006-08-28
**handy**, in a previous post, suggested you install *Automatix* probably because the latest Automatix version has a sort of automated Backup and Restore feature...among other things! And Automatix can be most trusted to do the job. I have not tried it myself,though. Let us know how it goes!

[http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)

---

### Post by hwroth1 on 2006-08-28
> **xyz said:**
> **handy**, in a previous post, suggested you install *Automatix* probably because the latest Automatix version has a sort of automated Backup and Restore feature...among other things! And Automatix can be most trusted to do the job. I have not tried it myself,though. Let us know how it goes!

[http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)
Thank you. I am downloading the new 6.06.1 right now on bit torrent. 

When completed I am going to set up a /home partition a partition for ubuntu a swap and a 1mb partiton for grub.

I will install automatix after I get the installation set up. I will let you know how it worked out. 

hwroth1

---

### Post by xyz on 2006-08-28
Perhaps you may fell more comfortable with this...so many ways to do it...!!
[url]http://joelbryanonsoftware.blogspot.com/2006/05/3-ubuntu-home-backup.htm

l[/url]

Good luck to you with the install.

---

### Post by toasted on 2006-08-28
On the /home partition subject - 
If you reinstall and copy your /home back, do you have to reinstall all the programs again?

---

### Post by handy on 2006-08-28
> **toasted said:**
> On the /home partition subject - 
If you reinstall and copy your /home back, do you have to reinstall all the programs again?

Not all programs, but some throw themselves around the system a bit, or a lot, as the case may be.

As an example, if you are a Cedega user, who no longer subscribes, & you want to be covered for a Ubuntu upgrade, or failure of some kind that required a reinstall. You need to have copies of the Cedega Engine:-
 
[http://downloads.transgaming.com/files/cedega-engine-5.2.5-local-update.i386.cpkg](http://downloads.transgaming.com/files/cedega-engine-5.2.5-local-update.i386.cpkg)

backed up somewhere safe, (CD/DVD) & possibly the Cedega_small.deb:-

 [http://downloads.transgaming.com/files/cedega-small_5.2.3_all.deb](http://downloads.transgaming.com/files/cedega-small_5.2.3_all.deb)

(Depends on their version numbers) Because Cedega does throw itself all over the system... :(

You would need to be sure to have the latest copies of these 2 files before your subscription runs out. :D 

A separate **/home** partition is definitely not the whole solution, another form of backup is required to compliment the benefits of the **/home** partition.

If you spend an evening reading in the forums you will have a good understanding of the situation, there were some links given in this thread, they may be all you need to read!

**[Edit:]**  *I just checked out the links in this thread, & [this one]("http://www.ubuntuforums.org/showthread.php?t=35087") supplied by  **xyz** earlier in the thread, is an old friend of mine, read it through, you will know the in's & out's of more than one method after reading it!*

---

### Post by handy on 2006-08-28
> **xyz said:**
> Perhaps you may fell more comfortable with this...so many ways to do it...!!
[url]http://joelbryanonsoftware.blogspot.com/2006/05/3-ubuntu-home-backup.htm

l[/url]

Good luck to you with the install.

Your link seems to be broken...

---

### Post by toasted on 2006-08-29
> **handy said:**
> 
**[Edit:]**  *I just checked out the links in this thread, & [this one]("http://www.ubuntuforums.org/showthread.php?t=35087") supplied by  **xyz** earlier in the thread, is an old friend of mine, read it through, you will know the in's & out's of more than one method after reading it!*

I tried the backup last night from this link but stopped it. 
I used this code to initiate the backup procedure: ( copied from the tut)
```
tar cvpzf backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys
```
But I also added this to the command at the end with a single space just as the others:

--exclude=/media

As the backup ran, I noticed that it backed up /home which is on a different partition... ok thats no problem, a good thing actually

BUT it also started to back up /media in which I have several things mounted including my win partitions. I really didnt want to back up my windows crap in this file so I just closed the terminal. 

Any idea why /media was not excluded from the backup?

Also, I have noticed that programs are installed in different places. Thats why I dont see the importance of having the separate /home

I would think that saving any important stuff to my shared fat32 part would be sufficient, either that or backing up the whole shebang.

---

### Post by xyz on 2006-08-29
> Any idea why /media was not excluded from the backup?
I may have the solution to that one as I did the same thing the 1st time I used the Howto: take a close look at the "exclude command" and you'll see this ** --exclude=/mnt** instead of what you want which is --exclude=/**media**.

---

### Post by xyz on 2006-08-29
> **handy said:**
> Your link seems to be broken...

No idea why this is happenning so go and check **Bou's** thread. It's the 2nd link of the 1st post:
[http://ubuntuforums.org/showthread.php?t=185761](http://ubuntuforums.org/showthread.php?t=185761)
Works for me!

---

### Post by toasted on 2006-08-29
> **xyz said:**
> I may have the solution to that one as I did the same thing the 1st time I used the Howto: take a close look at the "exclude command" and you'll see this ** --exclude=/mnt** instead of what you want which is --exclude=/**media**.

In the original command was exclude mnt but I added exclude media to it. 
I dont follow what you are saying cause I did it.... maybe they should both not be in there is that it?

---

### Post by xyz on 2006-08-29
> **toasted said:**
> I tried the backup last night from this link but stopped it. 
I used this code to initiate the backup procedure: ( copied from the tut)
```
tar cvpzf backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys
```
But I also added this to the command at the end with a single space just as the others:

--exclude=/media

As the backup ran, I noticed that it backed up /home which is on a different partition... ok thats no problem, a good thing actually

BUT it also started to back up /media in which I have several things mounted including my win partitions. I really didnt want to back up my windows crap in this file so I just closed the terminal. 

Any idea why /media was not excluded from the backup?

Also, I have noticed that programs are installed in different places. Thats why I dont see the importance of having the separate /home

I would think that saving any important stuff to my shared fat32 part would be sufficient, either that or backing up the whole shebang.


Sorry handy! My mistake...for some reason (read too quicly) I thought 
**hwroth1** had posted the above quote and that he had copied/pasted your [code] thus forgetting to read the line you included below the code;i.e, --exclude=/media
Didn't mean to confuse things!

---

### Post by toasted on 2006-08-29
:mrgreen: 

np mate

---

### Post by handy on 2006-08-29
> **xyz said:**
> No idea why this is happenning so go and check **Bou's** thread. It's the 2nd link of the 1st post:
[http://ubuntuforums.org/showthread.php?t=185761](http://ubuntuforums.org/showthread.php?t=185761)
Works for me!

Thanks for that! :)  I will install & check it out, looks like a nice simple way to keep things backed up... :cool:  Also, the coder sounds like he is very open to suggestions too, so it should develop really nicely, has got to be one to watch!

---

### Post by xyz on 2006-08-30
Sure looks like it's one to watch!Good day...out there!

---

### Post by handy on 2006-08-31
> **handy said:**
> Not all programs, but some throw themselves around the system a bit, or a lot, as the case may be.

As an example, if you are a Cedega user, who no longer subscribes, & you want to be covered for a Ubuntu upgrade, or failure of some kind that required a reinstall. ***_You must have copies of the Cedega_small.deb & Cedega Engine.cpkg_***:-
 
[http://downloads.transgaming.com/files/cedega-engine-5.2.5-local-update.i386.cpkg](http://downloads.transgaming.com/files/cedega-engine-5.2.5-local-update.i386.cpkg)

[http://downloads.transgaming.com/files/cedega-small_5.2.3_all.deb](http://downloads.transgaming.com/files/cedega-small_5.2.3_all.deb)

To reinstall Cedega from these files you first use the **Cedega_small.deb**, after which you can install the **Cedega_engine.cpkg**.  The small & engine names are not accurate, but they are all you need to know to identify the files that you need to download from transgaming.

Any Cedega user who no longer subscribes really should take note of this information, because Cedega really does throw itself all over the system... :(

You would need to be sure to have the latest copies of these 2 files before your subscription runs out. :D 

A separate **/home** partition is definitely not the whole solution, another form of backup is required to compliment the benefits of the **/home** partition.

If you spend an evening reading in the forums you will have a good understanding of the situation, there were some links given in this thread, they may be all you need to read!

**[Edit:]**  *I just checked out the links in this thread, & [this one]("http://www.ubuntuforums.org/showthread.php?t=35087") supplied by  **xyz** earlier in the thread, is an old friend of mine, read it through, you will know the in's & out's of more than one method after reading it!*

**[EDIT:] *After doing a reinstall, & putting the above information into practice, I found a serious error re: reinstalling Cedega, which I've now repaired & enhanced. The above information regarding Cedega is accurate as of this writing, I have just tested it! :KS ***  

Sorry about that! :rolleyes:

---

