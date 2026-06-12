---
title: "Issues Installing on Power Mac G5 - Video Feed Issues"
date: 2011-10-22
forum: Apple Hardware Users
---

### Post by MacPenguin1972 on 2011-10-22
Hello

I have just acquired a used G5 to replace my G4 that died a couple months ago. My old IDE hard drive that contains a working installation of Ubuntu is not compatible with my G5 tower, since this runs SATA.

I have repartitioned my hard drive for Mac OS X leaving 60GB of free space for Ubuntu.

My machine is ppc970 according to the Terminal. It is a dual PPC G5 2.3Ghz with 4GB of RAM.

I use a Gateway flatscreen monitor (don't ask, I got it free!) that works fine with my machine using a standard VGA converter plug.

When I attempt to boot into the Ubuntu CD to install, the first black screen comes up. I hit enter to load the kernel. A white screen with some text comes up.

Then it goes black. My monitor will shortly show "no video input" and this does not change.

How can I get Ubuntu to maintain video feed for installation? Is there perhaps a way to make it do a text-based installation? Or something that will cause it to NOT lose video signal to my monitor?

Any ideas?

Please help. Thanks. I would appreciate any input on this. :-)

BTW-- I have tried the PPC Ubuntu 10.10 -- should I use the Alternate version? Which version will work best with the G5 as I have described it? Thanks again.

---

### Post by dpny on 2011-10-22
Which video card do you have? The Mac version of the X800 is unsupported in PPC Linux.

---

### Post by MacPenguin1972 on 2011-10-22
> **dpny said:**
> Which video card do you have? The Mac version of the X800 is unsupported in PPC Linux.

In the system profiler it under Graphics/Displays it says:

(according to Mac OS X 10.4.11 Tiger)

NVIDIA GeForce 6600:

  Chipset Model:    GeForce 6600
  Type:    Display
  Bus:    PCI
  Slot:    SLOT-1
  VRAM (Total):    256 MB
  Vendor:    nVIDIA (0x10de)
  Device ID:    0x0141
  Revision ID:    0x00a4
  ROM Revision:    2149
  Displays:
FPD1520:
  Resolution:    1024 x 768 @ 75 Hz
  Depth:    32-bit Color
  Core Image:    Supported
  Main Display:    Yes
  Mirror:    Off
  Online:    Yes
  Quartz Extreme:    Supported
Display:
  Status:    No display connected


I might also add that I used the very same Gateway flatscreen monitor with my now-deceased G4. 

Same adapter plug. In fact I can boot Debian PPC 6.x but I don't want to use Debian because it wastes the empty space- loading everything up until you get to installing "yaboot" which it fails to do. Then I can't restore the drive partition to a blank, usable linux partition again. (You can't do it using Disk Utility in OS X, that is for sure)

---

### Post by MacPenguin1972 on 2011-10-23
Update:

I have since been able to install Ubuntu 10.04 (not 10.10) in my desired partition on my hard drive. However one of two problems remains constant:

1. When holding down option to select between Linux and OS X - the computer will sometimes "shut down" the USB port that controls the mouse and keyboard. The laser light on my optical mouse will go out, and the mouse will not work. Neither will the keyboard.  A total system restart is required to remedy this problem.  

2. If I DO get past this and get to booting Ubuntu, I still have the same problem where, after the white screen I lose video signal to the monitor and cannot get it back.

Apparently Apple does not allow systems other than OS X to be used on the G5? They will shut down your mouse/keyboard if you try or you lose video. 

Are there any hacks to prevent either of these two things from happening?

Thanks.

---

### Post by dpny on 2011-10-23
> **MacPenguin1972 said:**
> Apparently Apple does not allow systems other than OS X to be used on the G5? They will shut down your mouse/keyboard if you try or you lose video.

Apple doesn't stop anyone from installing anything on a G5, as I know of other successful installs. I can't help you, as my video card is unsupported, but you might want to check out mintppc, and the mintppc forums. It's a Mint-based distro specifically for PPC Macs.

---

### Post by rsavage on 2011-10-23
The answer to installing Ubuntu is not to install MintPPC!
 
Check out my lubuntu thread (linked on the last few pages of the sticky thread) for how to solve video problems.
 
I don't understand why you have to press the option key? Is this common on a dual boot? Is there something wrong with your yaboot config? Gentoo have an excellent guide to yaboot [http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=10) which says you need to specify an ofboot line for the G5.

---

### Post by MacPenguin1972 on 2011-10-24
> **dpny said:**
> Apple doesn't stop anyone from installing anything on a G5, as I know of other successful installs. I can't help you, as my video card is unsupported, but you might want to check out mintppc, and the mintppc forums. It's a Mint-based distro specifically for PPC Macs.

The problem is- Well two problems actually-- 

One -- I could not replace my current Ubuntu partition without reformatting the entire hard drive. It seems to me based on what I have experienced that you can only install linus on a partition with "free space" - nothing on it whatsoever. No HFS, no Fat32. NTTS, Big Mac, McDs, or any other file format system.

I would have to back up my existing Mac OS X stuff to an external drive, wipe the drive to recreate my original partition scheme on a 250GB hard drive which I allocate about 55GB for Linux and the rest for Mac. Then "Mint" would have an empty partition to use. II know of no other way to do it without destroying my files on the Mac OS part of the partition -- DiskUtility is kind of a crappy program for stuff like this)

Second-- what runs on Mint? Everything I have seen is generally geared for the "big boys" - Ubuntu, Debian, and Fedora. Programs designed for those systems won't run on a totally foreign system like Mint.

I have noticed each Linux distro is it's own OS, and a world unto itself. So if the program is made for Ubuntu, you're NOT going to run it say, on Debian for example. Debian programs are not made to run on Ubuntu, etc.  This has been my observation so far.

Sorry, just that I'm not enough of a "hacker" to do these things any other way. If there are other methods I do not know them and they are not readily available to the linux novice.

So that is my dilemma.

---

### Post by MacPenguin1972 on 2011-10-24
> **rsavage said:**
> The answer to installing Ubuntu is not to install MintPPC!
 
Check out my lubuntu thread (linked on the last few pages of the sticky thread) for how to solve video problems.
 
I don't understand why you have to press the option key? Is this common on a dual boot? Is there something wrong with your yaboot config? Gentoo have an excellent guide to yaboot [http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=10) which says you need to specify an ofboot line for the G5.


Last question first-- Mac OS X it seems has a big ego. Once you boot into Mac OS X it thinks it is the only OS on the machine. When you restart after that the machine will go right to OS X. "Doesn't matter what 'yaboot' thinks" it seems.

To override Mac OS X, holding down the option key immediately at startup will bring up a menu showing all bootable systems on the machine. You can then click on the Linux or Mac OS X icon and boot into whicever system you want. 

Gentoo? Was looking at that one. But I have the same question about Gentoo that I would Mint-- what runs on it? It seems as I mentioned in my reply to dpny that each linux platform is almost like it's own OS where things designed to run on THAT version of linux will not run on another (necessarily anyways) 

So if I junk Ubuntu (which I am getting very close to doing- I love Ubuntu but I can't see it when it loads- there's no point in having it. It ran on the G4 I had but my Power Mac G5 says "no dice, pal!" - I may have to hunt down a used G4 like the one I had- the silver mirror door tower, just to turn it into a linux box.)   Make no mistake- I LOVE Ubuntu- I've tried Yellow Dog, Debian, and Fedora and I like Ubuntu the best and want to run it. But I can't get it to work worth a damn. Ubuntu is no longer supported for Power PC, so that's that. (I don't see Ubuntu 11 on Power PC do you? That would be sweet, I've used it on a PC!)

My apologies. I just don't know enough about Linux yet to be able to hack it and all that right now.

I will check out the thread you mentioned.  Give this thing one more shot after I read it. :-)

I hate sounding like such a tough customer and I am probably speaking largely out of ignorance. There is a lot I don't know and it's hard to find the precise answers I need with a simple keyword search on Google. 

The other question is-- am I supposed to be using the standard PPC version, or should I be using the alternate version? And then 32 or 64 bit?? I'm not aware that the G5 is a 64bit machine.

Sorry about all the questions, there is a lot I am trying to learn.

Thanks. :-)

---

### Post by rsavage on 2011-10-24
> **MacPenguin1972 said:**
> I don't see Ubuntu 11 on Power PC do you?
er... yes
 
> **MacPenguin1972 said:**
> I will check out the thread you mentioned. Give this thing one more shot after I read it. :-)
You probably should of done that before writing.
 
> **MacPenguin1972 said:**
> 
I hate sounding like such a tough customer and I am probably speaking largely out of ignorance. 
er... yes
 
> **MacPenguin1972 said:**
> 
There is a lot I don't know and it's hard to find the precise answers I need with a simple keyword search on Google.
I pointed you in the direction of the documentation you need to solve your video problem.
 
> **MacPenguin1972 said:**
>  
The other question is-- am I supposed to be using the standard PPC version, or should I be using the alternate version? And then 32 or 64 bit?? I'm not aware that the G5 is a 64bit machine.
It really isn't hard to find this out. The G5s are 64 bit.
 
 
Your yaboot problem is caused by how you've partitoned your hard drive I think [https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot)
 
Regarding the suggestion by dpny: MintPPC is basically debian. Their forum is excellent for people like yourself who can't cope when things go wrong.
 
I wasn't suggesting you install Gentoo, I just pointed you to their yaboot guide.

---

### Post by MacPenguin1972 on 2011-10-24
> **rsavage said:**
> Regarding the suggestion by dpny: MintPPC is basically debian. Their forum is excellent for people like yourself who can't cope when things go wrong.

That's a cheap shot.  Period.

And your comment is typical of the god-complex mentality some people get in the IT world. Not everybody is going to understand things the same way.

All I know is Ubuntu worked on the G4, it does not work on the G5 and I'm trying to see if there is still a way.

Also, I work and go to school full time, so I do not have time to sift through thousands of messages to find an answer. I need to find answers quickly. I'm not a basement dwelling geek living at my parents' house with all the time in the world.  So forgive me if I can't spend hours and hours reading forum threads.



> 
     Quote:
                                                                      Originally Posted by **MacPenguin1972**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11388109#post11388109")                 
                 *I don't see Ubuntu 11 on Power PC do you?*
                                 
er... yes
Gee, the last version I have ever seen released on the PPC is 10.10 and that is what comes up on a google search of "download Power PC Ubuntu" And I'm not at the level of rewriting lines and lines of code just yet to make a PPC version of 11. So you'll have to bear with me.

---

### Post by jumil on 2011-10-24
Ubuntu 11.10 (currently Xubuntu) runs like a charm on my iBookG4, so there is nothing keeping PPC from running it per se.
I am totally new with any under-the-hood-work in Linux as well (6 months of simply using Ubuntu on my amd64 Desktop machine and now 2 weeks of kicking it into shape on my old old PPC notebook) and have learned a lot during the last two weeks :D
Keep trying. Bite that problem and never ever let it go. i found that a great way to learn my way around Linux.
In fact I think getting Ubuntu to run in a complicated environment like PPC is probably far more instructive then just using it where it is supported.

---

### Post by tiresia on 2011-10-24
I have the same machine as you, PowerMac G5 2x2,3 GHz. I believe your problem is related to the nvidia Grafic Card. Notice that the NVIDIA GeForce 6600 has two DVI connections. You should use the first one. If the monitor is connected to the second one you don't get any video signal.

If you install correctly Linux (Ubuntu and Debian work very well on your machine) you shouldn't need to press the Opt-Key during start-up. You can choose the OS at the first yaboot prompt.

Yes, MacOSX is quite 'egocentric' - therefore it is advisable to install it as first but to create the bootstrap partition for Linux as second partition. Your partition map should look like [here]("http://ubuntuforums.org/showthread.php?t=994882")

---

### Post by MacPenguin1972 on 2011-10-28
> **jumil said:**
> Ubuntu 11.10 (currently Xubuntu) runs like a charm on my iBookG4, so there is nothing keeping PPC from running it per se.
I am totally new with any under-the-hood-work in Linux as well (6 months of simply using Ubuntu on my amd64 Desktop machine and now 2 weeks of kicking it into shape on my old old PPC notebook) and have learned a lot during the last two weeks :D
Keep trying. Bite that problem and never ever let it go. i found that a great way to learn my way around Linux.
In fact I think getting Ubuntu to run in a complicated environment like PPC is probably far more instructive then just using it where it is supported.


Really? Just I remember the whole fiasco with BeOS years ago. One of the reasons BeOS failed was because Apple would not allow it to run on the Power PC.  Of course it was at a time when the foundations were a bit shaky (not as bad as the PC crowd would have you believe) and Steve Jobs just got back at the helm after Apple bought his company NeXT. (I remember all the doomsayers claiminh Apple would fold up! HAH!)   (I speak from first hand experience about the BeOS)

But they have always been about making sure their machines run with their OS, etc. So as I'm having trouble with a more recent G5 model I was wondering if this was part of the issue. But since OS X was a Unix-based OS and Linux is basically a derivative of the Unix platform I figured the machines running OS X should in principle be able to handle Linux. Or any Linux version tailored to run with the Power PC chip set that is.

But even now- with Apple using Intel chips, they made sure to let everyone know that only Apple machines are supposed to be able to run the OS. (Which, I hear it's not hard to build a decent Hackintosh for half the cost of a low end Mac Pro) 

At any rate, was thinking it was just something they put in to prevent or inhibit the use and one would have to find some kind of hack or workaround.


At any rate-- if I have Ubuntu 10.10 on my machine, would I have to wipe the partition and reinstall Linux? Or would Linux on my Power Mac upgrade to Xubuntu 11.10 from a DVD or CD if I was running my installed OS? 

I'm thinking with the difference in the name it should be again a different OS- BASED on Ubuntu, but not quite? Or am I wrong? 

Thanks again.

---

### Post by MacPenguin1972 on 2011-10-28
> **tiresia said:**
> I have the same machine as you, PowerMac G5 2x2,3 GHz. I believe your problem is related to the nvidia Grafic Card. Notice that the NVIDIA GeForce 6600 has two DVI connections. You should use the first one. If the monitor is connected to the second one you don't get any video signal.

If you install correctly Linux (Ubuntu and Debian work very well on your machine) you shouldn't need to press the Opt-Key during start-up. You can choose the OS at the first yaboot prompt.

Yes, MacOSX is quite 'egocentric' - therefore it is advisable to install it as first but to create the bootstrap partition for Linux as second partition. Your partition map should look like [here]("http://ubuntuforums.org/showthread.php?t=994882")


First- 

Thanks for the tip. I'll be darned! I tried that and it worked. I wonder why that would make such a difference? Clearly there is no dual-monitor option then for Linux on the Power Mac.

The other part-- 

Actually it is strange. I took the risk  and let the machine boot without holding down option and the Yaboot came up with the options of Mac OS, Linux or a CD/DVD ROM.  (I say "risk" - I mean the "risk" of having to wait for Mac OS X to fully boot so I could safely restart the machine if OS X took over the boot, wasted time, etc.)

I have been letting it restart a few times now without holding down option to make sure it wasn't a fluke but it appears to be working. This didn't work on my G4- in fact, I had to hold down option every time and Yaboot on THAT machine only recognized Linux and the CD/DVD ROM - not OS X.  I do have Linux as the second partition this time.  On the original attempt. Linux was given the first 40GB of my hard drive and Mac OS got the rest. This time it is the reverse you suggested.

Now the question becomes-- can I upgrade Ubuntu 10.10 to Xubuntu or Lubuntu 11.10 from a disc with what is on my hard drive running or do I need to do a clean install. 

Debian? didn't work worth a darn. I think it's too old. The last version for the Power PC was version 6.x and they're up to 11 or 12 now?  

Tried Fedora too, no dice.  Thing is I'm getting a 1TB external firewire, and I hear Apple machines can boot from an external ONLY if it's firewire. So if that is the case I may experiment with Mint on a partition there. 

I have yet to get ANY Linux version to work on Virtual PC 7 for Mac so I can have a "linux box" while running OS X. (The only one that would work was Damn Small Linux- I did get that to work on VPC7)  

Anyhoo... that's for the tip, I did work. Now I want to see what else I can mess with here. :-)

---

### Post by tiresia on 2011-10-29
> **MacPenguin1972 said:**
>  Clearly there is no dual-monitor option then for Linux on the Power Mac.
Right, at least not with that Grafic Card. I guess it should work on PowerPC Desktop

> Actually it is strange. I took the risk  and let the machine boot without holding down option and the Yaboot came up with the options of Mac OS, Linux or a CD/DVD ROM. This didn't work on my G4- in fact, I had to hold down option every time and Yaboot on THAT machine only recognized Linux and the CD/DVD ROM - not OS X.
I guess, it happened because sometimes the yaboot installer failed to recognize MacOSX - this happened to me very often with the Fedora Installer

> Now the question becomes-- can I upgrade Ubuntu 10.10 to Xubuntu or Lubuntu 11.10 from a disc with what is on my hard drive running or do I need to do a clean install.
You can do it and it should work. You don't need a CD, you can just change the repositories in /etc/apt/sources.list 
Anyway I would make a clean install, it takes not more than half an hour. 

> Debian? didn't work worth a darn. I think it's too old. The last version for the Power PC was version 6.x and they're up to 11 or 12 now?
That's not true, Debian is not too old. And the version of Debian is not at all related to the Ubuntu version. On my PowerMac Debian Squeeze runs VERY well.

> Thing is I'm getting a 1TB external firewire, and I hear Apple machines can boot from an external ONLY if it's firewire. So if that is the case I may experiment with Mint on a partition there.
You can boot a PowerMac also from an USB Drive. If you didn't you can also install a second internal SATA HD. Take care by multibooting, where the yaboot will be installed. I suggest you to read the link I gave you in my previous post.  

> I have yet to get ANY Linux version to work on Virtual PC 7 for Mac so I can have a "linux box" while running OS X. (The only one that would work was Damn Small Linux- I did get that to work on VPC7)
Yes, it works quite well, but don't expect a fast OS.

---

### Post by MacPenguin1972 on 2011-11-05
> **tiresia said:**
> You can do it and it should work. You don't need a CD, you can just change the repositories in /etc/apt/sources.list 
Anyway I would make a clean install, it takes not more than half an hour. 

What would I change it to? I tried to update from the CD I made of 11.10 but it ran into a wall with the install, said something about the mirror being invalid.

I admit I'm a novice on some of this stuff but that's why I am on the forums, so I can learn about it.

Do you know what the correct mirrors are and how to change the program to access those mirrors?

Thanks in advance, and for the input on your last comments also.

MP. :-)

---

