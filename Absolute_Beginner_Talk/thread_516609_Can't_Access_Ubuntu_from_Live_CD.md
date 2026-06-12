---
title: "Can't Access Ubuntu from Live CD"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Captain Legless on 2007-08-03
I'm a complete green newbie to Linux but I'm wanting to "give it a go".

I've downloaded a few distros from the net and am having the same problem with all of them - "OUT OF RANGE" error when trying to run from the active CD.

I've managed to have a look around Mepis by choosing the lowest boot up option on the splash screen, infact I am on the net using Mepis and Firefox to access this form as I type!

I have been unable to run Knoppix for the same reason as Ubuntu and I would like to check out all of these three distros before I decide to go ahead with any particular one. 

Ubuntu and Knoppix have both been given good reports and Mepis is said to be a bit stale and slow on updates. Having only been able to check out Mepis I am expecting big things of Ubuntu as I am impressed with what I have seen of the Mepis distro and the way it has detected hardware even down to giving me immediate web access!! I haven't checked out my wireless net work as yet.

Having said all that, how do I get past this damned "OUT OF RANGE" problem with Ubuntu?:confused:

I've tried all the screen resolution options on the boot screen of Ubuntu 7.04 Desktop Version. (64 bit )

My computer is an AMD 64 3000+ with 1Gig Ram and 160Gig HDD
Video adapter :- SiS 315_315E
Monitor :- Benq FP19G+ LCD 19"

I've looked through various forums and threads and have done nothing but blind myself with meaningless information whilst trying to find an answer to this problem. Some replies to similar questions mention editing scripts at log in. If this is the case when running from CD, how are the alterations supposed to take effect if you have to reboot ??:(

What I need is a list of step by step instructions, Can you help........or do I opt for Mepis?:confused:

Thanks in advance.:KS

---

### Post by shearn89 on 2007-08-03
Did you download the AMD version of the disk? Also, you need to check the md5sum of the disk after downloading, and burn at around 4x speed to ensure it doesn't get errors.

---

### Post by thefoolisme on 2007-08-03
Since you're having a problem with all the distros, I have to ask, did you verify the MD5 checksum after downloading, burn them at 4x or slower, and check the disk for errors?  These are the most common issues for the live CDs not running right.  Also, it's not your CD drive, right?  I just had an issue installing a distro from a disk I knew was good, and it turned out the drive was going bad.

---

### Post by Rocket2DMn on 2007-08-03
I think Out of Range is talking about the monitor.  Have you tried installing with the alternate cd?  It is a text based install which does not load the Xserver.  You can sort out GUI problems easier after the OS has been installed.

---

### Post by Majorix on 2007-08-03
> **Rocket2DMn said:**
> I think Out of Range is talking about the monitor.  Have you tried installing with the alternate cd?  It is a text based install which does not load the Xserver.  You can sort out GUI problems easier after the OS has been installed.

I second that. Use the alternate cd to install in text mode, then configure X with
```
sudo dpkg-reconfigure xserver-xorg
```
and make sure you select the correct range for your monitor under there.

---

### Post by Hospadar on 2007-08-03
Also are you sure you are properly burning the images to the cd?  Burning an iso to a cd isn't exactly the same as burning files to a disc.  If you are getting any sort of ubuntu boot messages though this is probably not the case.  If you do suspect that maybe you arn't burning it the right way there's some detailed instructions linked to on the download page.

If you do have a proper disc copy, you might try plugging your monitor into the motherboard and removing the graphics card temporarily (if your mobo has onboard graphics).  If you have an odd graphics card it might be causing the issue and just not using at first might help you sort things out.

Also you might try just using the 32 (x86) bit edition, a lot of things work better and for the average user there won't really be any noticable performace difference

---

### Post by Captain Legless on 2007-08-03
OK - thanks for the advice so far guys, I'm taking it all on board!!

Unfortunately it's past 3am in te morning here in the land of sunshine and blow flies and I've been at this keyboard for 17 hrs !! I gotta do some sleeping!!!!!!

I will attack this thing again when I get time to spare.

In reply so far:- 
Yes I downloaded the AMD 64 bit version.
I've tried all 3 of the distros on 3 different HDDs (2 on this machine, 1 on another).
Mepis would seem to be working perfectlyfrom the CD having got past the boot screen.
I didn't burn the CDs at low speed :(
Does Ubuntu merge with Windows as easily as Mepis seems to do? I can access all my data in my Windows folders and can open and use mpgs, mp3s, docs, pps, xml...........etc etc.

Cheers

---

### Post by Inxsible on 2007-08-03
Burn the CD at 4x or slower speeds.

> Does Ubuntu merge with Windows as easily as Mepis seems to do? I can access all my data in my Windows folders and can open and use mpgs, mp3s, docs, pps, xml...........etc etc. Yes

---

### Post by wpshooter on 2007-08-03
I think it might make your life easier if you considered using the 32bit version of Ubuntu instead of the 64bit version.

Did you try starting Ubuntu using the safe graphics mode parameter or using the I think it is the F4 key to choose a specific graphics resolution ?  If those don't work try the ALTERNATE 32bit version.

---

### Post by Captain Legless on 2007-08-04
OK - the story so far!!

I've downloaded and burnt the 32bit version (at 4X burn speed), and tried the Live CD install from that. (The disc has no errors).
Guess what - same problems persist!!:mad:

I chucked the disc into my old notebook - Dell Latitude and it looked like I was making some progress. I actually managed to get past the menu on the start up screen as far as the Ubuntu logo and the oscillating progress bar. That's as far as it got. Just sat there for a couple of minutes before the screen went black on the cursor went home to the top left of the screen where it sat blinking inanely !!:-?

I tried a variety of the resolutions available when pressing F4 including the safe graphics mode option (F3), same result every time.](*,)

It has been suggested by a couple of you that I could do some editing of the boot script using xserver-xorg. I can't see how to do that. I've hit ESC as the machine was booting but the only command line prompt I get after that is < BOOT:> (without the brackets). When I enter anything after that, I get the message, "No Kernel for....whatever"

Bear in mind I am just trying to run a "Live CD" version to test drive the distro before committing to installing one particular distro with a dual boot system.

I downloaded the latest Mepis distro which loaded OK so long as I used an option that dumbed down things a bit and automatically inserted a command line:-
init =/etc/init apm=power=off vga=normal quiet drvr=vesa
This allowed Mepis to run from the CD perfectly well and picked up everything on my system, including a fully functional wireless network.:)

I can't help but ask myself why Ubuntu is supposed to be so good when there's so much hassle just trying to get it to run in a demonstration mode? Surely if Mepis can get it running properly from the Live CD, Ubuntu can't be that much different?? :confused:

Just as a matter of interest - well it may be to some of you geeks, when  Mepis was going through it's boot sequence, I picked up on the log something that seemed to make a reference to "915 resolution", could that be the key to the problem??:-k

---

### Post by Rocket2DMn on 2007-08-04
That 915 resolution is referring to an onboard intel video card (even though this isn't what you said in your first post).  LiveCDs are certainly imperfect because there is only so much that can be fit onto one, and they leave little room for editing since nothing is on your hard drive.  The LiveCD just doesn't work for everybody.  If you want to install Ubuntu, you can use the alternate cd like I mentioned before.  You can get the alternate cd at their website simply by selecting the Alternate CD checkbox at the bottom - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
If you choose to install, you will be able to get the correct i915 drivers and you Xserver will work correctly.
Sorry that the LiveCD doesn't work.

---

### Post by Captain Legless on 2007-08-04
Oh well, thanks for you time and efforts in trying to get me sorted using Ubuntu from the Live CD. I'll carry on trolling my way through the forums and maybe come up with something that will allow me access t it, I don't like to "give in" when I'm faced with a problem like this!:mad:

Just as a matter of interest, seeing as how I am having luck with Mepis, what is the general consensus of opinion with regard to Mepis as a Linux distro?

Thanks guys.

---

### Post by Captain Legless on 2007-08-05
I SOLVED THE PROBLEM!!

Or rather, I did nothing and it worked!

I was continuing trying to mess with things and had put my Live CD (64bit) back in the HDD and was going through various reboot options AGAIN, when, after doing a reboot I was called away for a few minutes. When I came back to the machine UBUNTU had loaded and was sitting waiting for me!!!!! :shock:

I rebooted and just sat back to see what happens when you leave it to it's own devices.:-k

It went through all the same boot process as I'd seen it do a dozen times already and stopped at the menu screen with the 30second counter ticking away waiting for some input at the menu. :-\"

I refrained from touching it and watched it time out. There was the usual blank screen then the familiar error message - "[COLOR="Red"]Out of Range[/COLOR]" popped up - I did noting just sat back and waited.[-(

Lo and behold, after approximately 2 minutes the disk drive kicked into life, the screen went black, then grey, then textured grey then there was the UBUNTU desk top!!:shock:

It looks like I spent 2 days buggering about trying to find some way to load it could have been saved by 2 minutes doing nothing!!:roll:

Ah well, now I can road test it!!	O:)

Anybody want to buy half a dozen plain CD's each of which holds a fully funtional version of UBUNTU !!#-o

---

