---
title: "Can't shut down ubuntu on macbook pro"
date: 2016-01-14
forum: Apple Hardware Users
---

### Post by raif2 on 2016-01-14
I have a macbook pro
MacBook Pro (Retina, 15-inch, Mid 2015)
2.8 GHz Intel Core i7
16 GB 1600 MHz DDR3
Intel Iris Pro 1536 MB
I have a separate partition for mac and ubuntu. Ubuntu is the main partition. it's about 250gig per partition.
I am currently running 15.10, but have had this issue on all the following versions 14.04, 14.10, 15.04 and current 15.10.
My swap partition is 32 gigs.
When I am in ubuntu and I go to settings and shut down, the system hangs on the splash screen. I must hard reboot the system. I have tried to ssh into the box and it is only possible after the reboot. Not when it is frozen.
The same thing happens when I just shut the lid of the laptop. However, after sometime, like the drive home from the coffee shop, the computer is humming and hot. So I immediately hard shut down.
I have been to irc and searched the web and found nothing that helps. If I can't get this to work, I'm going to have to learn how to use osx. Please help.

==== edit ====
after reading another post with similar issue, that user was resolved by upgrading from 4.2.0-19 generic kernal to 4.2.0-20 generic.  
So I thought I should add that I'm using kernal 4.2.0-23 generic
thx

Thanks, Raif

---

### Post by howefield on 2016-01-14
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by raif2 on 2016-01-14
Thanks, didn't know there was one.

---

### Post by este.el.paz on 2016-01-14
Did you do anything to add "fan control" to your install?  Did you read the stickie at the top of the sub-forum page about "heat issues in wintel computers"???

Seems like a couple different problems going on . . . the GUI buttons . . . and "heat" . . . .  Try to read some threads here about "fan control in MBPro" . . . I found Mike Braxner's approach to work for me . . . but still, the kind of tiime and detail to get it entirely dialed in . . . I don't have . . . .  Indeed, OSX runs the computer (MBPro 09) cooler than in linux . . . w/o the "macfanctrl" and other stuff, installed it was Hot in linux . . . .

The other issues with dual boot, might explain why buttons don't work . . . I don't know whether it is needed in newer MBP any more, do you have any boot manager, or did you use the "mac" iso?  How are your partitions formatted?  Might be simple or might be complicated to figure out the GUI buttons . . . but, likely the heat issue needs some stuff added to adjust the fan temp range.

e..

---

### Post by raif2 on 2016-01-15
Thanks for the reply. 
The heat is not to big an issue for me.  I'm more concerned with not being able to shut down the computer.  Also it's not just the gui, it's when I close the laptop, or even push the power button ( physical ), it starts the shut down process and hangs.  I"ve removed the splash screen and the last command that I see is [COLOR=#222426][FONT=Helvetica Neue][37.405858] reboot: system halted.  which is not very informative.
Thanks,
R[/FONT][/COLOR]

---

### Post by este.el.paz on 2016-01-15
> **este.el.paz said:**
> 
The other issues with dual boot, might explain why buttons don't work . . . I don't know whether it is needed in newer MBP any more, do you have any boot manager, or did you use the "mac" iso?  How are your partitions formatted?  Might be simple or might be complicated to figure out the GUI buttons . . . but, likely the heat issue needs some stuff added to adjust the fan temp range.
e..
> **raif2 said:**
> Thanks for the reply. 
The heat is not to big an issue for me.  I'm more concerned with not being able to shut down the computer.  Also it's not just the gui, it's when I close the laptop, or even push the power button ( physical ), it starts the shut down process and hangs.  I"ve removed the splash screen and the last command that I see is [COLOR=#222426][FONT=Helvetica Neue][37.405858] reboot: system halted.  which is not very informative.
Thanks,
R[/FONT][/COLOR]

It's a little "unusual" for there to be "hanging" while shutting down the computer . . . it's more common to happen while booting the system . . . so, possibly this is evading my skill level, but the fact that you can see "reboot:system halted" . . . is informative--it means that the system is initiating shut down . . . but, then it doesn't seem to be received by . . . ??? the motherboard????  And, OSX is a jealous lover, it doesn't play well with others . . . so did you make any changes to open firmware before you did your ubuntu install??  

Couple other points, you could check launchpad bug report to see if there are any similar bugs reported; generally I found that Xubuntu ran better on my 09 MBPro than other flavors; and lastly and possibly most painful . . . from my reading on dual boot (Ihave a triple boot set-up) it's considered ***best practice*** to have OSX loaded first in the disk, installed first . . . then install your linux flavor of choice after that.  Seems like possibly the mobo doesn't "know what to do" with your shut down commands--did you try to shut down from the terminal??  Try
```
sudo shutdown -r now
``` and see what happens . . . .

Lastly, since linux is always pushing the bleeding edge I have found that the LTS versions are a little more stable and therefore worth the time spent getting them set up . . . so 14.04 or now 16.04 is moving into Alpha testing and should be good for several years of support.

e..

---

### Post by raif2 on 2016-01-15
Hi, I'm sorry, I forgot to clarify, I"m not "dual booting" I have seperate partitions and the main partition is ubuntu.  There should be no interaction with osx.  I think. Also I get the hanging from terminal shutdown too.

---

### Post by este.el.paz on 2016-01-15
> **raif2 said:**
> Hi, I'm sorry, I forgot to clarify, I"m not "dual booting" I have seperate partitions and the main partition is ubuntu.  There should be no interaction with osx.  I think. Also I get the hanging from terminal shutdown too.

Separate partitions within the same HD IS "dual booting" . . . as opposed to running in virtual, etc.  Depending on how you formatted your linux partitions and other stuff, sometimes it gets interesting in this dept) . . . it's not that OSX is "interacting" . . . but jobs get handed off to the mobo . . . and that mobo works for Apple . . . but, if things are "disordered" it may not get the message.  You could attach a screenshot of GParted tables . . . possibly might give some insights???

e...

---

### Post by raif2 on 2016-01-15
[ATTACH=CONFIG]266766[/ATTACH]

That's a good idea.  I hope this helps.  The bottom partition is the main ubuntu one.  The computer boots into this one.
Thanks,
R

---

### Post by este.el.paz on 2016-01-15
> **raif2 said:**
> 

That's a good idea.  I hope this helps.  The bottom partition is the main ubuntu one.  The computer boots into this one.
Thanks,
R

OK, that table looks OK on the face of it, usually I like the swap after the ext4 partition, but, seeing that this is showing "EFI" . . . how are you booting this system?  I think I asked about boot manager, like rEFInd, do you have that installed?  And, what about GRUB?  Does GRUB show up in boot process?  Lastly, did you check the md5sum number on the iso before you did the install?  If iso is corrupted the install may say "successful" but there is "corruption" . . . .

e...

---

### Post by raif2 on 2016-01-15
Hi, I believe I made the ubuntu partition primary so it just boots right into ubuntu.  I can't remember about the osx side, I know that if I start the machine with the option key down I can select "Macintosh" drive and it boots into osx.  As for grub, I'm not quite sure about that.  I'm kind of new to ubuntu.  How do I tell if grub shows up?
Thx

---

### Post by este.el.paz on 2016-01-15
> **raif2 said:**
> Hi, I believe I made the ubuntu partition primary so it just boots right into ubuntu.  I can't remember about the osx side, I know that if I start the machine with the option key down I can select "Macintosh" drive and it boots into osx.  As for grub, I'm not quite sure about that.  I'm kind of new to ubuntu.  How do I tell if grub shows up?
Thx

How did you "make" the ubuntu partition "primary"???  It's possible, but, did you boot into open firmware and flag the ubuntu partition?  OR, you just installed ubuntu last, so it is booting as the first choice??  What about, with the option key, does the "penguin" show up there as well?  And if you pick the penguin does it boot?  As far as GRUB goes, for your problem of not being able to shut down, GRUB may not be involved . . . but, it might be . . . .  In my case on my MBPro, if I used "automatic" as the installer . . . it would say "install successful" . . . but GRUB wasn't installed . . . in my case that meant it wouldn't boot.  So I have to set up a small 10MB partition flagged as "bios_grub" . . . and then GRUB "gets installed" . . . and the linux side boots, using option key (because I have triple boot) takes me to "windows" which launches the GRUB window . . . which then boots the system.  

But, in terms of why you can't shut down, even with power button . . . a bit strange . . . so I'm looking for anomalies on the install side, the place where generally errors get made . . . .  Didn't hear back if you checked the md5sum, what about rEFInd?  etc, etc, etc . . . .

e..

---

### Post by raif2 on 2016-01-16
Hi, thanks for your attention.
So it's been a while since I worked on this problem, so I'm sorry for the hazy memory.
I believe it went like this.  I had osx installed of course. I then booted unbuntu from a usb, I loaded parted created my partitions and installed ubuntu. I can't remember quite how I got ubuntu to be the main partition but I;m pretty sure I did it through parted specifying the "kind" of partition or something.  I will say that I actively made it primary, it wasn't install order.  I configured it... somehow :(
When I boot with the option key, what I see looks like  picture of a hard drive and a drop down box saying "network" then the various networks start to show up as additional drives. There does not appear to be a valid option for booting ubuntu.  I choose the first one "mac".  Then it boots into osx as normal.  In side of osx, the close lid suspends the system and the shut down and restart all work as expected.  the restart will default into ubuntu. 
As for the md5sum, I started this process with 14.04.  Mac doesn't have any process for dual boot for linux. just windows, so I had to follow some tutorials on how to do it.  I have installed every version between 14.04 and 15.10 in a couple different ways.  I have had this problem with all of them.  That makes me think that it's not the particular install file.  And it also makes me think that it may not be the particular install process either. It was pretty clunky a couple of times, not asking if I wanted to install to a partion, rather giving me the option to wipe the whole disk or upgrade ( I guess during some of my upgrade processes ) .
Sorry this is sort of stream of consciousness as I'm remembering.  
So I did fresh installs, and upgrade installs, the upgrade installs were the ones that were sometimes kind of funky.  Every successful install had the shutdown problem.
As far as grub is concerned, I do believe I have it installed, I recall doing things ( recommendations ) and then being told to restart or reboot grub.  
Thanks again,
R

---

### Post by este.el.paz on 2016-01-16
> **raif2 said:**
> 
As for the md5sum, I started this process with 14.04.  Mac doesn't have any process for dual boot for linux. just windows, so I had to follow some tutorials on how to do it.  I have installed every version between 14.04 and 15.10 in a couple different ways.  I have had this problem with all of them.  That makes me think that it's not the particular install file.  And it also makes me think that it may not be the particular install process either. 
So I did fresh installs, and upgrade installs, the upgrade installs were the ones that were sometimes kind of funky.  Every successful install had the shutdown problem.
As far as grub is concerned, I do believe I have it installed, I recall doing things ( recommendations ) and then being told to restart or reboot grub.  
Thanks again,
R

@raif2:

OK, thanks, I'm a stream of consciousness guy myself . . . good news is that if everything works OK on the OSX side it's probably not a hardware issue.  But, if you used the Software services upgrade to do upgrade, a particular problem file could still be left in place . . . .  One other guess is about the "mac" version iso . . . I've seen some people mention that with that file they don't need rEFInd, but I'm running Linux Mint on my MBPro right now so I don't know about that as a viable option.

So far I  haven't seen rEFInd mentioned, and it does look like your mac is EFI boot, since there is an EFI partition . . . this is an area slightly beyond my skillset, but linux uses another system??? to boot, and that is what rEFInd is for, coordinating the hand-off, etc.  I'd say to find the "rodbooks" site/wiki on installing rEFInd in the OSX side . . . it's a small file, and you just drag the "sh" file (from memory) to the OSX Terminal . . . and hit return to install it . . . it sets up a folder in the Macintosh "root" file . . . .  But, read the instructions . . . because I also had to install "gdisk" . . . in OSX side.  The "interesting" part is that you can boot and run, but then have problems on shut down . . . but that still poiints to "power management" . . . those details are not so clear to me.

If you "have" GRUB . . . then you should "see" the GRUB window . . . sort of a black screen with the list of possible boot options, including OSX . . . so GRUB should show up before the ubuntu splash . . . GRUB has a "recovery" mode option, which you could try to run.  Possibly if GRUB is partially installed it might influence the shut down process???

One other idea, how about when you run "apt" for update/upgrade . . . does it show any "broken packages"???  You could check the same idea in "synaptic package manager" . . . there is a "fix broken packages" drop down menu under one of the tabs . . . .

e....

---

### Post by MikeBraxner on 2016-01-16
@rail2 ... Given your initial description, I would assume your problem lies either with the kernel version used, or with a driver that goes belly up ... I'd suspect a driver for starters. As a suggestion, you might want to check your logs wrt a driver beginning to sign of/unload/shut down, but not finishing, or reporting an error. If you find one, try unloading it before shutdown. 

If you can't immediately spot something, I would successively try to unload certain drivers before a shutdown, specifically the wireless and video ones. 

Good luck.

---

### Post by este.el.paz on 2016-01-16
> **MikeBraxner said:**
> @rail2 ... Given your initial description, I would assume your problem lies either with the kernel version used, or with a driver that goes belly up ... I'd suspect a driver for starters. As a suggestion, you might want to check your logs wrt a driver beginning to sign of/unload/shut down, but not finishing, or reporting an error. If you find one, try unloading it before shutdown. 

If you can't immediately spot something, I would successively try to unload certain drivers before a shutdown, specifically the wireless and video ones. 

Good luck.

@Mike:

Thanks for lending a hand, "drivers" does sound feasible, but, since he's had three iterations installed I don't think the kernel itself would be the problem since this problem has been consistent across all of them, unless it's a bug that hasn't been fixed . . . which IS possible . . . .  So, OK, "drivers or kernel" . . . since raif is "new" to ubuntu, what logs would you suggest he look at . . . i.e., with specific code commands for him/her to run, etc.

@raif:

Going with the wireless and video drivers . . . those are usually added . . . did you add them?  If so, how?  Did you use "additional drivers"?  Or some other way?  Or, didn't add them??

e...

---

### Post by BobUgh on 2016-01-16
You seem to have several problems: (1) shutdown, (2) sleep (or suspend), and uh, now I don't remember if there was more. I am having suspend problems myself, so I don't think I can help you there.

By the way, your Gparted graphic showed your swap partition is 31 MiB, not 31 GiB. If you need swap on top of 16GB of RAM, that isn't going to help you much.

> **raif2 said:**
> … I"ve removed the splash screen and the last command that I see is [COLOR=#222426][FONT=Helvetica Neue][37.405858] reboot: system halted.
R[/FONT][/COLOR]

That sounds like it has shutdown all the way except cut off power. I have been on various unix systems where the shutdown command had an option to just halt, not kill power, or that was the default and the option was required to cut power. Long time ago power was a real throw switch that couldn't be controlled with software. I remember when I was younger waiting to see "system halted" before cutting off the 120VAC. I have no idea if "halted" message should come up if one is trying to reboot.

I'm in OSX now, I don't see the options I was thinking about in OSX shutdown(8) but I see a -u option that leaves power on for 5 minutes for when a UPS is used… If you are getting halted and the system boots up next time fine w/o fsck, I would consider the requiring to press the power key a mere annoyance.

Learning OSX isn't difficult, it is unlearning that is hard. With the Ubuntu problems on apple hardware, I am considering learning how to run Ubuntu in a VM in OSX. A different set of problems.

---

### Post by este.el.paz on 2016-01-16
> **BobUgh said:**
>  I am having suspend problems myself, so I don't think I can help you there.

By the way, your Gparted graphic showed your swap partition is 31 MiB, not 31 GiB. If you need swap on top of 16GB of RAM, that isn't going to help you much.

Learning OSX isn't difficult, it is unlearning that is hard. With the Ubuntu problems on apple hardware, I am considering learning how to run Ubuntu in a VM in OSX. A different set of problems.

@Bob:

Thanks also to you for lending your eyes, I was looking to see formatting and whether he had GRUB, totally glossed over the swap . . . "31 MB" . . . right, probably a tad "small" . . . but, in my MBPro just doing "normal" web stuff I don't think I've used much swap . . . ever???  But, swap does relate to "suspend" . . . in various systems on various, mostly PPC computers I have had and still have, suspend problems . . . that also is in the kernel . . . .  Mostly I just reboot out of linux side when I'm done messing with it, OSX runs the unit cooler than LM . . . .  But, like I mentioned in your post, probably running in virtual is probably the "best" choice, then native hardware/software is running the base functions . . . and you can play with linux w/o worrying about whether it is "factory spec" or not . . . .

e...

[edit:  Stepping away from the console to work on my truck . . . had the thought that perhaps it IS the small swap partition that is messing with the system.  I searched "swap and shutdown problems" . . . something like that, and there are other threads on this issue . . . the top hit from "mandriva" has this quote:

> The only considerations normally given to swap is "how big does it need to be ???".
Normally twice your memory value but not necessary to be above 512mbs.  Any larger is just a waste of space but does no harm. The size of your  swap, or what HDD it is on is not likely to be the source of your  problem.
Cheers.                                        John.

Could be by getting swap up in size the issue will resolve????]

---

### Post by raif2 on 2016-01-20
Hi, it seems, would you say, that this is an unusual case.  My hardware is not unusual and my os' are not unusual, so my install must somehow be unusual.  I'm not above repaving and starting over... again.  But not with out an iron clad series of steps.  There must be a path that people take/have taken that works, and I must have gone my own way.  
Let me know if you think this is the right choice.
Thanks,
R

---

### Post by BobUgh on 2016-01-20
Before starting over, I would first try enlarging the swap partition to be larger than your ram size. If that is difficult to do, then delete your swap partition and see if that makes any difference.

---

### Post by este.el.paz on 2016-01-20
@raif:

It's not really like there is a "paved" road to follow . . . but, Bobugh tapped the ball up on the rim for you . . . and then I slamdunked it . . . on the sizing of the swap partition as the ****possible**** next step for you to take . . . and, then, see how that goes . . . report your progress, etc.

e....

---

### Post by raif2 on 2016-01-21
Ok, well I have actually done considerable work on the swap partition.  eventually enlarging it to 32 gig (or it appears to be 31 for some reason ) which is double the size of my ram.  Subsequent to that, I have been severely chastised for doing so in previous attempts to resolve this.  On Ask Ubuntu I think.  They said they wouldn't even help me till I reduced to what they considered a reasonable size.  I chose not to do that as, I started with a small swap file, had the problem, repaved with bigger swap file, had the problem, and didn't feel like repaving again to go back to a smaller swap file. The only thing I haven't done, is to remove the swap partition entirely.  As you can imagine I'm hesitant to do that.  If I need to go back to having a 32 gig swap file after that I will be super frustrated, and I will have to repave my system to get there, as far as I know.
Re there not really being a blessed or sanctioned path to installing ubuntu, especially on one of the most popular laptops out there, I just find that very frustrating too.  I mean I hate microsoft.  I've been running that crap for 20 years.  But at least I can install it on any system and it tends to work with the hardware.  I don't mean to sound inflammatory, I just want to run what I find to be the best OS for me and I can't.
Thx
r

---

### Post by este.el.paz on 2016-01-21
@raif2:

OK, you have to have some "patience" when it comes to running linux on an apple machine . . . it's a little "non-stock" . . . and so, there are the "rules of installation" which are well known and provided on the web . . . and then the "practical application" of getting it to run on macintosh.  The "variation" in the "sanctioned rules" is the need for something like "rEFInd" . . . and/or in my case, GRUB . . . .  If I don't have both I can't boot linux; but other people on their machines don't seem to need either one . . . .

So, pragmatically speaking, on apple machines OSX is "the best" OS . . . because it is designed more specifically for the hardware . . . linux is more "generic" . . . designed to work on a wide range of machines . . . and then it needs to be tweaked for the specific hardware . . . .  So, I personally like "dual-boot" . . . if I need OSX it's there . . . and then, when I get bored with stability and I want to play with the system I have the linux side . . . .  Having said all that, indeed it is "non-stock" to have shut down problems . . . so that is why the data is more "thin" as far as your situation.

It might be helpful to have another forum helping out, but, sometimes more cooks don't improve the flavor of the soup . . . .  It sounds like you increased the size of the swap . . . but that didn't seem to change anything?  So, after you did that did you run a system update/upgrade??  Like I mentioned on another thread here, many times the linux system "learns" what it needs or figures itself out, so, if you have some patience . . . leave the swap for now, it probably would not need to be 32 GB, but, that shouldn't interfere . . . AND, use the system a bit, then run "sudo apt-get update" . . . and then "sudo apt-get upgrade" . . . if you haven't done that post install that MAY provide some packages that might fix the problem . . . reboot . . . use the system a bit more . . . try to do a GUI shut down . . . if that doesn't work, use the power button . . . .  If the button doesn't shut it down, reboot to OSX and shut down that way.  Wait for awhile, longer than a few seconds . . . and cold boot to linux . . . repeat . . . use the system for a few minutes . . . check/run update/upgrade . . . see if anything new shows up, install it . . . etc, etc.  Try that for a few days . . . see if the system "learns" what it should be doing . . . .

Other option, try another flavor of Ubuntu . . . Xu or Lu or possibly Ku . . . burn the live DVD . . . boot the system . . . and use the GUI "shutdown" . . . does it work??  Then probably you could try an fresh install of that system . . . .  But, be patient . . . it should be straight forward to get linux running and able to cleanly shut down . . . .

e...

e...

---

### Post by MikeBraxner on 2016-01-21
@raif2 ... Three brief thoughts.

First, if you'd like to try without Swap, just comment its mounting line in your /etc/fstab ... though I don't think this will make a difference.

Second, have a look at [coldraven's comment]("http://ubuntuforums.org/showthread.php?t=2305441&p=13402519#post13402519"). Apparently, a switch to 4.2.0-18-generic kernel sorted things out for him. If this doesn't help, give him a shout, maybe he has a different idea.

Third, if you opt for re-install, you might want to start with a look at [some basic guides]("https://help.ubuntu.com/community/MacBookPro"), they tend to be rather helpful. Keep in mind that, despite your perception, every time Apple releases new/upgraded hardware, they're sure to fumble around with some subsystem, which means that there are as many 'versions' of 'a MBPr' as there are releases. While most of the changes can be ignored by the user, some of them will cause headaches ... and sometimes nose-bleeds. If you do get stuck, try running a general google search, and keep checking backwards on the forum ... they tend to turn up more than you might expect.

---

### Post by BobUgh on 2016-01-22
> **raif2 said:**
>  Re there not really being a blessed or sanctioned path to installing ubuntu, especially on one of the most popular laptops out there, I just find that very frustrating too.  I mean I hate microsoft.  I've been running that crap for 20 years.  But at least I can install it on any system and it tends to work with the hardware.  I don't mean to sound inflammatory, I just want to run what I find to be the best OS for me and I can't.
Thx
r

I hear you, and feel the same way. In my experience, running Ubuntu on a machine less than a few years old can be fraught with problems, as it takes Canonical some time to catch up with new hardware features. Apple hardware, even more so since (1) it was rare for someone to buy a new Mac and put Ubuntu on it and (2) Apple is so proprietary, worse than Microsoft in some ways, (3) Ubuntu on Macs is a small %. Heck, Apple intel macs alway used EFI and GPT, stopped putting DVD drives some time ago, new computers with Windows preinstalled now use GPTand still Canonical uses the iso and GPT as lowest common denominator.

And even Apple does what it can to stop users from running older OSs on newer hardware, e.g. If the machine is shipped with OSX 10.10.8 on it, you can not install any 10.10.7 or anything earlier on it, without playing tricks.

The big exception as for new hardware running well with Ubuntu are the machines manufactured with open OSs in mind.

Buy a 2012 mac book pro, 13", non retina; you can buy them new or refurbished from Apple.

Or, with a machine as nice as yours, run Ubuntu within a VM.

I had a much nicer post here but because I didn't post it with n minutes, the forum asked me to login and the last 12 minutes of my edits were gone.

---

### Post by BobUgh on 2016-01-22
Apple doesn't allow you to run their OSs that predate the machine, so don't expect Ubuntu released before your machine to either

---

### Post by este.el.paz on 2016-01-25
@raif2:

Something that hasn't been mentioned here before is that possibly this is a "bug."  Over the last couple days I tested out a daily live of U-MATE 16.04 Alpha . . . and on two machines there were "problems" with "restart" via the GUI . . . where it just dropped into a "black" screen, but it was "active" or "alive" . . . as opposed to a "dead" black . . . if you get my drift; i.e., it had not shut down.  So, this could be a new problem, possibly with the kernel or possibly "power management" . . . these could be "distinctions" on how or where you could post your bug.

But, that would now be my suggestion, to go to launchpad bug report and search there to see if other people have already filed a similar bug report/problem . . . if not, then you could start a fresh bug report . . . if you do, post the number here . . . that way, if and when I do a MATE install, if I find a similar problem I can add my name to it, etc.  The more people who find an issue the better chances of it being fixed . . . .

e....

---

### Post by Robert_Jackson on 2016-05-08
I have this problem too on a Mac book pro 11.5. I have reinstalled many times and 14.04 always behaves the same. It does two dots on the gui and hangs. I have to hold the power to reboot.

After selecting Ubuntu from grub I do see some sort of error about the Radeon GFX driver having an issue.

---

### Post by Robert_Jackson on 2016-05-09
Interesting that restart works fine.
Restart gets to same two dots in gui but then launches back into grub.
Shutdown still hanging at two dots in the gui.

---

### Post by gabriele.bianchi on 2016-06-06
Hi to everybody. 

Unfortunately I do not have more to offer than to confirm the problem on my Macbook pro 15'' Retina, mid 2015 (version 11.4), Intel graphic card. 
I have installed Ubuntu 16.04 yesterday, in dual boot with Os X, and the system does not shut down. I use Linux (mostly Ubuntu and Linux Mint) as the main OS since more than 10 years, but it is the first time that I install it on a Mac.

---

### Post by este.el.paz on 2016-06-07
> **gabriele.bianchi said:**
> Hi to everybody. 

Unfortunately I do not have more to offer than to confirm the problem on my Macbook pro 15'' Retina, mid 2015 (version 11.4), Intel graphic card. 
I have installed Ubuntu 16.04 yesterday, in dual boot with Os X, and the system does not shut down. I use Linux (mostly Ubuntu and Linux Mint) as the main OS since more than 10 years, but it is the first time that I install it on a Mac.

@g.b:

Welcome to dual-boot on a mac . . . hopefully you read through the posts in this thread, so I won't repeat what I've already suggested . . . except to try first logging out of your session, then try to shut down from the log in window . . . see if things go "faster" or work doing it that way.  In my PPC installs if I try to shut down from the GUI session it takes a long time before anything happens . . . or it drops to a black screen and just hangs there for a couple minutes . . . and then it will "shut down" . . . .

e...

---

### Post by gabriele.bianchi on 2016-06-07
@este.el.paz

Thanks a lot for your reply. 
I have tried to shut down from the (graphical) login prompt but the behaviour does not change. The last messages that I see when I remove the ''quiet splash'' from the relevant line in the grub menu  are "Reached target shutdown'' followed by "Reboot: Power down", but the Macbook  does not switch off. 

The last lines of the file /var/log/syslog before system halt are;
Jun  7 23:53:21 francesco2 systemd[1]: Stopping User Manager for UID 108...
Jun  7 23:53:21 francesco2 systemd[1014]: Stopped target Default.
Jun  7 23:53:21 francesco2 systemd[1014]: Reached target Shutdown.
Jun  7 23:53:21 francesco2 systemd[1014]: Stopped target Basic System.
Jun  7 23:53:21 francesco2 systemd[1014]: Stopped target Paths.
Jun  7 23:53:21 francesco2 systemd[1014]: Stopped target Sockets.
Jun  7 23:53:21 francesco2 systemd[1014]: Starting Exit the Session...
Jun  7 23:53:21 francesco2 systemd[1014]: Stopped target Timers.
Jun  7 23:53:21 francesco2 systemd[1014]: Received SIGRTMIN+24 from PID 2162 (kill).
Jun  7 23:53:21 francesco2 systemd[1]: Stopped User Manager for UID 108.
Jun  7 23:53:21 francesco2 systemd[1]: Removed slice User Slice of lightdm.

If you meant to try to start the os reaching a text console without starting the graphical interface (and to issue shutdown from there), I do not know how to do it. I used to know how to do it in ancient times,  before the arrival of grub 2, but not anymore.

@ RalphBraxton

Regarding what you wrote about the possible responsibility of some driver, possibly video or wifi, and about trying to unload them before issuing shutdown, I can try. I have not loaded any particular driver after installation, graphics and wifi works out of the box. How would I do? Should I unload some modules from the kernel?  

gabriele

---

### Post by gabriele.bianchi on 2016-06-07
@este.el.paz

Ok I managed to boot to a root console, via the "recovery" entry of the grub menu, and I issued shutdown from there, but nothing changed.

gabriele

---

### Post by este.el.paz on 2016-06-07
> **gabriele.bianchi said:**
> @este.el.paz
Ok I managed to boot to a root console, via the "recovery" entry of the grub menu, and I issued shutdown from there, but nothing changed.

gabriele

@g.:

OK, well any console in ubuntu can be "root" if you use "sudo" . . . so before you wrote this I was thinking to have you try "sudo shutdown -r now"  from the Terminal . . . I think there are other variations on that command, but, that is the general idea.  So, question is how did you issue shutdown?  By GUI or by using something like I just suggested?

Anyway . . . without going into the install process; or checking if the md5sum or some other checksum number is correct; as I did previously I would suggest that you try another flavor of "ubuntu" for a fresh install, or burning a "liveDVD" and booting it up and testing it for shutdown.  On my MBPro I couldn't get straight "Ubuntu" to run too well, I found XFCE and/or LXDE to be "better."  You could try to add "XFCE" or MATE DE to your install and see if you can shut down from that session . . . that **might*** give you some insight.  On my PPC PowerMac I have Ubuntu-MATE & XFCE as the DEs; in MATE session my optical drive will eject any disk that is put in during the session; if I log out and back into XFCE there is no problem with the optical drive.

Just investigate to find what works "best" for your computer; since you have experience with LM, you could try that . . . right now I think that is still based on 14.04, which is perhaps linux "stable" . . . whereas 16.04 is still "testing" or perhaps "sid" . . . .

e...

---

### Post by gabriele.bianchi on 2016-06-08
@e.:

Linux Mint 18 beta should be released in a *few* days, and I will try that and report here any novelty. However it is based on Ubuntu 16.04 and I do not know whether it may behave differently from Ubuntu 16.04 regarding basic aspects like shutting down. The Arch Linux wiki reports success regarding these aspects on the most recent Macbook Pro, and if everything else fails I will give that too a try. Let us cross fingers.

Gabriele

---

### Post by este.el.paz on 2016-06-08
:.g@

***Possibly*** this relates to the "retina" aspect, as I have seen reference to "non-retina" as a qualifier for easier install on Apple units.  Since I don't have a retina item I'm not looking into the issues . . . just doing a check on basic install procedures as many times there is some error there . . . .

But, as you are not alone on this problem, try also to find out if anyone has filed a bug report about it, on Launchpad . . . or there is another bug report site, "Bugzilla"????  don't take that as gospel . . . possibly something with  "www.bugs.freedesktop.org"????  I checked out the second place but it wasn't "obvious" how to file a bug, whereas the LP location is a little more clear.  Either add your name to the bug report(s) or start a new one--the devs may reply and ask for more data, or may declare it "invalid" . . . or, it may be considered "valid."  : - )

Looking through your posted report it does show that the software is running the script to "shutdown" . . . but, then . . . it's not happening???  As I said in my PPC installs of Xenial, there is a significant delay in the time between clicking shutdown, and that happening . . . so, there probably is a "bug" element to the problem.

---

