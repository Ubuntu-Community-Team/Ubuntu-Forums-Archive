---
title: "Mac mini (Intel) external HD install"
date: 2007-02-08
forum: Apple Intel Users
---

### Post by DaveGee on 2007-02-08
I initially posted this in the 'general' group (sorry for the repost)... It's just that.

1 - Newly posted topics slide down 2 or more pages every hour or so
2 - Mac (even if its an Intel Mac) specific questions seem to get ignored
3 - PC specific questions also seem to get ignored
4 - My Mac brothers are usually much more willing to help. :KS 

Really simple question but as I search and search I can't seem to find any current (working) solutions....

The short of it:

Mac Mini, 1GB RAM, Intel Dual Core CPU, External USB2 Drive

I currently have:

Internal Drive (Mac OS - On a mac partition)
Internal Drive (WinXP - On an NTFS partition)
(refit)

Refit sees both OS's and boots each properly....

What I want:

Ubuntu installed on an External USB2 hard drive.

1 - Downloaded and burned the latest release
2 - Plugged in USB2 Drive
3 - Inserted Ubuntu Install CD (this is the 'regular one' (not the 'alt version')
4 - Rebooted

refit sees the CD and allows me to boot from it!!

5 - Answer all the questions
6 - Select Manual when we get to Parted (disk partitioning)

Parted starts out showing me the internal drive - I change it to display the USB2 external drive.

7 - Create an Ext3 partition and flag it as boot
8 - Create a 3GB swap-partition and flag as such
9 - Exit Parted and answer yes the the proceed question

At this point I remember something about selecting mount points and such...

10 - I choose the main (boot) partition and have it mount to /
11 - Similar process for swap

Oh also somewhere in that process it asked about GRUB?? and where to install it... It's default was DISK0 but I didn't think I should use that and was afraid if I did I'd kill my MacOS and WinXP drives (and working without a net..... yea yea yea I know I know)

Anyway.... I changed that from DISK0 to DISK1

Intermission for install process... get soda and/or snacks as needed... 

Finished.... reboot....

refit pops up and shows MacOS Logo (as usual) - WinXP Logo (as usual) & Penguin (NEW!)

Tried to boot Linux....

Screen goes blank (black) and (I'm using an Apple Display) the screen powers light goes dark/off it will blink back on for a moment if you wait long enough but the display is still black (not even a cursor).

Note: USB Drive show no activity...

Searched around and saw messages about going into refits partition manager but it didn't say anything about it needing to update anything **and** it only shows the partitions on the INTERNAL drive.

Search some more and rebooted with CD and got back to Parted - the partition on the external drive is still EXT3 and set for mounting on / and is flagged as boot.

What could or should I do now? I'm pretty sure this will be solved with some combination of refit and/or lilo voodoo :confused: but I just don't know where to go next.

Help me Obi-Wan I'm a total dope!  

Dave

---

### Post by DaveGee on 2007-02-09
Could I really be the first person attempting to install Ubuntu on an external drive (on an Intel Mac?!?!) :confused: Looks like I'm gonna have to move on to a more popular distro... One where something as mundane as installing on an external HD isn't such an impossibly complex task that people are simply unable (or unwilling) to explain the steps in a clear and straight forward manner. :( 

I've gotta tell you... I've had experiences with quite a number of different Un*x flavors (including A/UX) and I'm more than able to search for answers... But with all of that I've yet to find any sort of READABLE installation guide for Ubuntu when it comes to Intel Macs... Well one that doesn't fall into quite a few of the following categories anyway...

- Out of date
- Run-on
- Is more that 6 pages long and STILL has comments from people who are having trouble.

And my favorite:

- Brings up steps that make no sense
  One in particular mentions quite BOLDLY to make sure you RESET the mount point
  back to /  (okay that WOULD make sense) but NOWHERE did it ever state that mount
  point was (or needed to be) set to something different EVER!!

Kinda like:

Set the alarm clock to on
Turn the clock upside down
Turn the clock right side up
Look to the right
Look to the left
And most important, MAKE CERTAIN you go back and reset the alarm clock to on!

People bring up lilo and the windows users say "Why not just use GRUB?" Mac oriented Ubuntu sites have this to say about Grub.

- It WILL work
- It WON'T work
- It MIGHT work

So, with an overwhelming vote of confidence... I'm left to assume Grub is NOT ready for prime time (on the Mac) or... Maybe it is... :confused: 

Well sorry about this rant and before anyone takes it personal... This wasn't really directed toward anyone (or group) but its just a rant caused out of total frustration... :( Well, with any luck my post will dissuade other potential Mac users from trying the Ubuntu distro and look for something that has even a modicum of support. 

Dave
First & Last Cup of Ubuntu

---

### Post by grazie on 2007-02-09
DaveGee,

I'd really like to help you, but for the most part your machine is x86. Looks to me like the x86 users are either unwilling, unable or unaware that they can help you. PPC users are very unlikely to be able to help at all. I suggest you post something on [this thread]("http://www.ubuntuforums.org/showthread.php?t=353026"), along the lines that you need some assistance, but you've got nowhere to go. Stick a link back to this thread.

The only real difference between your machine and other x86 machines is the way it boots. You don't want grub, you want bootcamp (I think it's called that). Although Ubuntu doesn't (yet) have a distro for your type of machine, there are loads of peolpe running *Ubuntu on them.

Hope this helps. When I get my next machine I think it will almost certainly be an Intel Mac.

---

### Post by natemonster on 2007-03-11
DaveGee, i'm having the exact same problem. mac mini dual core intel 1gb ram mac 10.4 and win xp installed. i have a external firewire drive and trying to install ubuntu on it. i just do a basic install nothing special with partitioning. when it comes to rebooting, refit comes up with mac, windows, linux on firewire drive. if i select the peguin, it tells me i do not have the latest firmware (for ubuntu i guess) and crashes. :( i might try elilo boot loader insted of grub and maybe the non-alternate version

---

### Post by Chrisj303 on 2007-03-14
Yeah mate, i feel your pain - it took me 2 weeks to successfully get my macbook triple booting. This was down to fragmented information (which was often just plain wrong), on an already confusing process. A lot of the guides assumed differing levels of prior kowledge to Linux/Ubuntu, which often leaves those who potentially needed it the most out in he cold.
I went with UBUNTU because of the fabled support forums - i've yet to receive an answer to any of my problems.

---

### Post by natemonster on 2007-03-14
well i have no clue how to do this. i could erase my main hard drive, partition it with two partitions on for mac 10.4 and one for edgy and then install xp with boot camp on my external firewire drive but ubuntu doesn't matter that much to me. most likely in the next release it will support intel macs.

---

### Post by jimmydie on 2007-03-14
I am triple booting macbook pro from a 80g hd. It is scary because I have 40g osx, 18g ubuntu and 21g for Windows XP (not much room). I've reinstalled Ubuntu like 10 times, because I don't yet know how to fix a linux kernel panic problem.

I would think that everyone would want a configuration with 3 respectable operating systems (in my opinion). I'm beginnning to wonder if the shine of 3 operating systems has worn off, and that I am in a small group of people who want OSX Linux and Windows. Unfortunately I'm not to the point where I've tried to boot to a flash drive, because I'm searching high an low for infomation that is sometimes hard to follow about triple booting. I started another post that talks about triple booting with Vista, OSX and Linux (I'm upgrading my HD to 160g). I'm not so optomistic. As soon as I get my harddrive in, I may be face with booting to some sort of flash drive. Sorry for posting something that does not help you at all. I know where you are comming from.

---

### Post by cyberdork33 on 2007-03-14
I will try this on my imac and an external drive today, see if I can figure anything out...

Well, I tried to install you an external USB hard drive. the install seemed to go fine, rebooted, and the install showed in rEFIt. However, when I select the icon for the linux install on the external drive, it gets an error in the EFI console:

```
Starting legacy loader
Using load option 'USB'
Error: Not Found returned from legacy loader
Error: Not Found from LocateDevicePath
Error: Not Found from LocateDevicePath
Error: Not Found from LocateDevicePath
...
Error: Not Found from LocateDevicePath
Error: Not Found from LocateDevicePath
Error: Load Error while (re)opening out installation volume

Please make sure that you have the latest firmware update installed.

*Hit any key to continue*
```

and hitting "any key" doesn't do anything.
Seems like an issue with rEFIt to me.

---

### Post by Chrisj303 on 2007-03-14
> **jimmydie said:**
> I am triple booting macbook pro from a 80g hd. It is scary because I have 40g osx, 18g ubuntu and 21g for Windows XP (not much room). I've reinstalled Ubuntu like 10 times, because I don't yet know how to fix a linux kernel panic problem.

I would think that everyone would want a configuration with 3 respectable operating systems (in my opinion). I'm beginnning to wonder if the shine of 3 operating systems has worn off, and that I am in a small group of people who want OSX Linux and Windows. Unfortunately I'm not to the point where I've tried to boot to a flash drive, because I'm searching high an low for infomation that is sometimes hard to follow about triple booting. I started another post that talks about triple booting with Vista, OSX and Linux (I'm upgrading my HD to 160g). I'm not so optomistic. As soon as I get my harddrive in, I may be face with booting to some sort of flash drive. Sorry for posting something that does not help you at all. I know where you are comming from.

Read step 4 of this guide : [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
That might sort out the kernel panics.

My macbook tripleboots like yours - and yeah, i can't belive more people don't do this.
BUT, as you touched on, the information regarding the install process is very fragmented and in some cases is just plain wrong.
But when it finally works it's great!

cheers,
chrisj303

---

### Post by natemonster on 2007-03-14
i get the same message. it basicly freezes at that screen because pressing any key does nothing. i checked to see if i had the latest version of rEFIt (0.8) and i do. so i don't know.

---

### Post by xGuse on 2007-04-10
Bump!

I work in biology and there are many bioinformatic apps written in linux and only so many get ported to OSX, and even then you have to wait for updates to be brought over, and EVEN THEN it feels like a kluge at best.  I would REALLY like to run Ubuntu from a USB HD if possible.

Has ANYONE gotten past this issue?!  Please!?


Gus

---

### Post by natemonster on 2007-04-10
> **xGuse said:**
> Bump!

I work in biology and there are many bioinformatic apps written in linux and only so many get ported to OSX, and even then you have to wait for updates to be brought over, and EVEN THEN it feels like a kluge at best.  I would REALLY like to run Ubuntu from a USB HD if possible.

Has ANYONE gotten past this issue?!  Please!?


Gus

i gave up and erase my startup disk and made 2 partitions one for os x and on for ubuntu. you can use your usb drive for stogage. go into disk utiliy and select partion and pick "free space" :D

---

### Post by siepo on 2007-04-10
I also failed to create a bootable Ubuntu on an external drive for my macbook. I have os x and ubuntu on the internal disk, plus a fat32 partition for exchanging data between both. 

I wanted to try Feisty on an external disk so as not to jeopardize my existing installation. But, as I said, I coudn't make it work. Either the internal installation would boot, or I would get this rEFIt screen that others mentioned.

---

### Post by natemonster on 2007-04-10
> **siepo said:**
> I also failed to create a bootable Ubuntu on an external drive for my macbook. I have os x and ubuntu on the internal disk, plus a fat32 partition for exchanging data between both. 

I wanted to try Feisty on an external disk so as not to jeopardize my existing installation. But, as I said, I coudn't make it work. Either the internal installation would boot, or I would get this rEFIt screen that others mentioned.

i'm running feisty and it's beautiful. can't you upgrade through update manager.
a fat32 partition? hmmm... when i try to copy files to my external drive or to my os x hard drive it says i don't have permition. would this work...?

---

### Post by siepo on 2007-04-11
I upgraded with aptitude dist-upgrade. But on various occasions I would certainly have appreciated a working Edgy as a fall-back.

---

