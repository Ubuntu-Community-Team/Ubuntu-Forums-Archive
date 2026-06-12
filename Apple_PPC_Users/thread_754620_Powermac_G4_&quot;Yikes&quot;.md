---
title: "Powermac G4 &quot;Yikes&quot;"
date: 2008-04-14
forum: Apple PPC Users
---

### Post by Mreyebrows on 2008-04-14
I have a Powermac G4 "Yikes" model

this is a pretty old computer, coming with only a 450 mhz processor, 128 mb of RAM, a ATI 128 rage graphics card, and a 10gb hardrive. 

When i received this the Hard Drive was pretty much gone. 
I stripped an old Imac G3 (one of the original 233mhz cpu models) and took the old 4g hard drive from it just so i could install an operating system, thinking ill get an ATA 80gb hard drive when i can afford it

First I installed another stick of Ram to meet the minimum requirements for install, so 256mb of RAM now(should i install more?)

But no matter what i try, whether it be Ubuntu, Yellow Dog, Xubuntu, Kubuntu, none of them will work! I can load the livecd fine, even started the installation process, but their is always something that stops it. Its quite infuriating as i have been trying to get this thing installed with linux for about a month now, i guess its finally time to ask for some help. They will boot to the bootprompt, ill type in live-nosplash-powerpc itll load, show me the large "Ubuntu" banner or "Kubuntu" banner then take me to the livecd desktop. Then just stop. 

I now have a stack of Linux install cd's (and i did make sure they were powerpc) ranging from 6.10 to 7.04 of different flavors of Ubuntu

Help Me Please

---

### Post by stream303 on 2008-04-14
I think this is your machine here:
[http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450.html)

I would definitely recommend not using the live-cd version, and use the "alternate" non-live installer.   Maybe you have one, but I'd start with Feisty 7.04, get it working, and then see if you want to upgrade to Hardy when it is released.  Feisty alternate:

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

actually, many would probably recommend the lighter Xubuntu Feisty, and again with the "alternate" installer:
[http://cdimage.ubuntu.com/xubuntu/ports/releases/feisty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/feisty/release/)

That secondary ram might also not be up to spec, unless you know for sure, so you could try installing Xubuntu with just the original 128mb and see where that goes.  The "alternate" install is definitely your friend here.

It looks like there were many hard-drive options available for that machine, so we might be running into a multiple controller issue, but hopefully not.

Anyway, welcome aboard, and I'm sure any one of us will be happy to help get your "yikes" working!

---

### Post by Mreyebrows on 2008-04-14
Indeed that is my machine

i thought about using the alternative installer but i had the assumption it was only for intel/AMD processors

guess i didnt read very far down and just wanted to get linux up and running

the original RAM that came on the machine was PC100 and the extra stick i got was PC133, would that be a problem? I checked the mac fourms and it said that PC133 RAM would be fine, it just would run at PC100 speed
And i will try to download the alternative installer cd and see what happens, ill report back later

Thanks for the welcome!

Edit: Ive downloaded Xubuntu 7.04 alternative installer disk image, should i edit anything in it before i burn it to a disk?

---

### Post by stream303 on 2008-04-14
> **Mreyebrows said:**
> Edit: Ive downloaded Xubuntu 7.04 alternative installer disk image, should i edit anything in it before i burn it to a disk?

Should be good to go!  I'd try it with all the ram you have at first, and after an install, you can check it:

```
free -m
```

and see what the total is in the first column..

---

### Post by Mreyebrows on 2008-04-14
What if it doesnt install?

remove some RAM then try again?

---

### Post by stream303 on 2008-04-14
Right.  Try with all you have currently, and if that doesn't work, perhaps try without the extra ram, just in case it isn't up to spec.  Sounds like it is, so pop that baby into the drive, hold down the "C" key and boot! :)

---

### Post by Mreyebrows on 2008-04-15
poo

just when i thought it was gonna work it slapped me

for some reason the monitor refuses to accept the signal from the graphics car (Old ATI Rage 128)
so i removed the graphics, blew into the little PCI slot, and after longing to play a SNS again, i reinstalled it into the PCI slot. 

but still it will not accept the signal!

suggestions?

---

### Post by stream303 on 2008-04-15
I have heard that when adding or removing components from a Mac, it might be a good thing to reset the nvram / pram and possibly the smu/pmu.  I usually do it on donated machines to ensure I'm working with a clean slate.  I haven't had any problems, but YMMV.

nvram / pram:
[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

smu / pmu reset:
[http://docs.info.apple.com/article.html?artnum=86760](http://docs.info.apple.com/article.html?artnum=86760)

---

### Post by Mreyebrows on 2008-04-16
Well, it almost worked

at least the monitor accepted the video cards signal (it wasnt fully plugged in)

I booted into the Xubuntu 7.04 alternative install disk, typed live and hit enter

it brought me to the very DOS-esk blue screen, and i went about filling our my keyboard info, language, ex..

but then while it was trying identify my cd-rom disk drives it failed, brought me to a busybox shell? at least it think it was, and started outputting the message 

"Illegal Instruction"
over and over again, 

so then i try again, this time booting using the live-powerpc command and it didnt even get to the bluescreen before it started doing the "Illegal Instruction" thing

but at least its progress

---

### Post by stream303 on 2008-04-17
> **Mreyebrows said:**
> I booted into the Xubuntu 7.04 alternative install disk, typed live and hit enter

The "alternative" installer isn't live, it is just a straight text-based installer.

The best bet here is to just boot the disk, and let everything time out - usually only takes a few seconds to go from the first stage of yaboot to the second stage, and then on to installation without needing any intervention.

---

### Post by Mreyebrows on 2008-04-17
K ill try that

i really need a second  monitor i keep having to switch back and forth with my main machine adn the powermac 0.-

---

### Post by Mreyebrows on 2008-04-18
Nope, no luck

this time it booted to the install then started to scan cd-drive or files of the cd-drive but then crashed and did the 
"illegal instruction"
until i turned off the machine

---

### Post by stream303 on 2008-04-19
Hmm...  have you tried installing without that 3rd-party ram just to be sure?

Were the disks burnt at low-ish speeds?  And are you trying to use Hardy Alphas, which originally had the cd detection problem?

---

### Post by Mreyebrows on 2008-04-19
I forgot about the RAM, ill try that next

and i burnt it at x4 speed, the lowest it would allow

IM not sure if i used the hardy alpha, i downloaded from the link you posted (xubuntu 7.04)

---

### Post by Mreyebrows on 2008-04-19
Success! 

After a long install period, and after removing the RAM, I found out it was suppose to be PC100 RAM, but i bought PC133 RAM by mistake, i have successfully installed xubuntu 7.04!

I am now the proud owner of a Powermac G4 with Xubuntu! Im  giddy with joy!
Iam getting a weird monitor error saying im on the wrong operating frequency, but it goes away after i turn off and back on the monitor.
I have succesfully logged onto my account, played around with the app's, messed with the backrounds, and discovered that the audio works, i thought it was gonna be buggy 0.-


One more thing if its not too much trouble, how do i get Flash, java, and shockwave to work on firefox?
Thanks for everything this far!

---

### Post by stream303 on 2008-04-20
Super!  I was hoping it wasn't ram, but at least you found it.  Maybe you can return it.  Remember that if you install some new ram, you'll most likely need to increase the size of your swap partition, which is typically 1 - 1.5 maybe 2 times the overall size of ram.

Easily fixed by reinstalling the Hardy release due out next week. :)

Maybe we can fix that monitor issue too if it isn't running at it's native resolution.  What is the brand and size of the monitor you are using - we can look up the specs, and see if your /etc/X11/xorg.conf file needs a minor tweak.

For now, we have to use Gnash as a substitute for flash, and you may want to enable the "backports" in software sources to get the latest they offer - but it won't be as good as the real thing - for now - the devs are working on it.

No java experience here, so someone else can point out the way...

Again, congrats on getting the Powermac up and running.  Mind-blowing, huh?

---

### Post by Mreyebrows on 2008-04-20
THe monitor im using is the original monitor that came with the powermac. an old old 17-inch Apple Studio Display CRT

The RAM however is not a problem, i only paid like 15 bucks for the 128mb chip, and i didnt really expect it to work either. 


and doesnt Adobe have a linux installer on their site?

---

### Post by stream303 on 2008-04-20
> **Mreyebrows said:**
> THe monitor im using is the original monitor that came with the powermac. an old old 17-inch Apple Studio Display CRT

Ok, here's the link to the specs:
[http://www.everymac.com/monitors/apple/studio_cinema/specs/apple_studio_display_17_cl.html](http://www.everymac.com/monitors/apple/studio_cinema/specs/apple_studio_display_17_cl.html)

Ok, the crt isn't as finicky about native resolutions like lcd's are, and I wonder if you like the resolution you are at, or what options work for you in the display prefences.  Is the screen too large, too small, or just right?

> The RAM however is not a problem, i only paid like 15 bucks for the 128mb chip, and i didnt really expect it to work either.

Ok, maybe the system will be usable with what you have now depending on what you are doing.  Should be inexpensive enough to get more ram if you find you really need it.

> doesnt Adobe have a linux installer on their site?

Yep, but it isn't for PPC.  Don't hold your breath waiting for that either. :)

---

### Post by Mreyebrows on 2008-04-20
I would say that the screen is perfect that way it is

when i turn the monitor on with the computer it gives me a weird little window that says

Out of Frequency
HF : 40.6khz
VF : 30.0khz

Operating Frequencys
HF : 30->85Khz
VF : 47->160khz
Power safe after *secounds

*is a countdown from 20

if i just turn the monitor off and on again, it shows the xubuntu login window and everything goes on without problems

---

### Post by stream303 on 2008-04-21
I found an even better spec manual for your monitor (several apple monitors actually) :
[http://docs.info.apple.com/article.html?artnum=50124](http://docs.info.apple.com/article.html?artnum=50124)

It appears that your vertical and horizontal frequencies in **/etc/X11/xorg.conf **may not be correct, although you do get a display with a a warning from the monitor initially.

I looke through what I thought was your monitor, and see that it lists
Horiz 30-85
Vertical 48-160
just like the warning box that came up.

If you feel like changing it, I would backup your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf   /etc/X11/xorg.conf.original
```

Then you can edit it with:
```
gksudo gedit /etc/X11/xorg.conf
or in a terminal
sudo nano -w /etc/X11/xorg.conf
```

and change the horizontal and vertical frequencies.  Here's a snippet of mine:
```
Section "Monitor"
        Identifier      "Color LCD"
        Option          "DPMS"
        HorizSync       28-84
        VertRefresh     43-60
```

Save the file, and reboot and see if those warning messages come up on your monitor.  So if you find your monitors specs in those docs, and they don't really match what is in your xorg.conf file, you have the option of fine-tuning it.

---

### Post by Mreyebrows on 2008-04-22
Would i have to change the Xorg config to make it work with mac mini again? 

if not thanks alot

---

### Post by avtolle on 2008-04-23
Regarding your inquiry about Java, here is what I did to install.

First, see [https://help.ubuntu.com/community/Java#head-25783e6fd5d8a3eb6e7959868128252a178e70b3-2](https://help.ubuntu.com/community/Java#head-25783e6fd5d8a3eb6e7959868128252a178e70b3-2)
for some general information on installing Java on PPC.

Second, if you want to use the latest IBM java, which is Java 6, once the Medibuntu Repository for your release is included within your package list under Synaptic, select ibm-j2skd1.6 as the package to install. See the wiki link above on the procedure to add the Medibuntu repositories and the key to your sources file.

Third, once the package is downloaded, you will need to build a symbolic link to the file libjavaplugin_oji.so for Firefox to find it in ~/.mozilla/plugins. To do so, assuming you have not previously installed an earlier version of IBM Java in Firefox, you need to open a terminal (Application -->Accessories-->Terminal) or Ctrl-Alt-F2. At the terminal, enter the following:
```
 mkdir ~/.mozilla/plugins
cd ~/.mozilla/plugins
ln -s /usr/lib/j2sdk1.6-ibm/jre/plugin/ppc/ns7/libjavaplugin_oji.so

```Once you have completed the process, start Firefox and type about:pugins (that's about COLON plugins) in the bar; if successful, the java plugin will be included in the plugins installed in Firefox.

This is the process I used to install the updated ibm java in Ubuntu Gutsy to Firefox. The wiki article discusses how to install earlier versions of the ibm java. 

It goes without saying that Firefox should not be open when doing this. Good luck, and I hope you find this of help to you.

---

### Post by Mreyebrows on 2008-04-24
Wow!

thanks so much, now i can play all those nifty java games
=D

---

### Post by marklar2u on 2008-04-25
Mreyebrows:

just curious, but to my knowledge you should be able to run faster memory, 133 in a 100 slot, not the other way around.

Were you able to exchange it?  

Most often the 133 stuff runs w/ a different latency at the lower speed, and if you have more than one stick of memory the lowest speed / longest latency is setting the speed for all of it...

I've had great luck and service w/ owc (macsales) and transintl for memory in the past.

Good luck.

---

### Post by marklar2u on 2008-04-25
Mreyebrows:

just curious, but to my knowledge you should be able to run faster memory, 133 in a 100 slot, not the other way around.

Were you able to exchange it?  

Most often the 133 stuff runs w/ a different latency at the lower speed, and if you have more than one stick of memory the lowest speed / longest latency is setting the speed for all of it...

So, it's probably a bad stick of memory, not the rating per se.  So I'd first try to exchange the 133 for another 133... I usually buy that speed cause you can always use it in other SDRAM machines, but not vice versa...

If you need a different vendor, I've had great luck--and service-- w/ owc (macsales) and transintl for memory in the past.

Good luck.

---

### Post by Mreyebrows on 2008-05-01
The odd thing is that when I use the PC133 RAM in the powermac, it will be fine for about 5 minutes. It will be recognized by the machine and it will say in the system usage 256mb of ram recognized or 150mb of 256mb recognized. But while browsing the internet, or trying to open a file, it will start to glitch up. IT wont show the window, or have alot of graphic errors. When i try the same task with just the first 128mb of ram it will take longer, but wont glitch up at all. Ive used it for up to an hour without glitches with it.

So your assumption that the RAM is just bad is probably correct. I will probably go exchange it tomorrow

Edit: I tried booting with the extra RAM, and it worked, it booted up worked well for about 5 minutes, then started to glitch up. So i turn it off and reboot without the extra RAM. when booting it had to repair and delete some extra files, im not sure of the specifics, but could an extra file be causing the issues?

---

### Post by stream303 on 2008-05-06
I'm not a memory expert, but I believe that the ram is sensitive to issues like CL=2 / 3 , Non-ECC, unbuffered and so on.  Perhaps a trip to crucial.com or some other memory vendor might turn up something or reveal what might be on the edge with your current ram..

One thing you can do is try to walk the memory up to where it might be going wrong if just some parts of that additional chip are good.

At the second-stage boot: prompt, hit -tab- to stop the countdown, and specify a kernel parameter to limit memory something along these lines:

```
Linux mem=384M
```

Note the capital "M"

If you needed additional kernel parameters just tag them on, say if you needed nosplash

```
Linux nosplash mem=384M
```

Maybe you can experiment to see if part of that new ram is stable...

---

### Post by vivichrist on 2008-05-09
I'm having problems with the same mac [http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_400_agp.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_400_agp.html) except its 400mhz g4. how do i tell if my ram is cl?, note I don't have the original ram or keyboard, mouse, screen, hdd, dvd-writer, you name it. on boot I get udev-event[1890]: run_program: '/sbin/modprobe' abnormal exit. hardy and feisty seem to flip out over ohci1394. hardy-livecd managed to boot into gnome but no mouse or keyboard function so, can't do any thing. hardy gets to a prompt but same story. feisty brings up the ubuntu logo which hardy didn't but then goes to a black screen with the above message and stops.

---

### Post by garlicsalt2 on 2008-05-09
Hey everyone, I have a Blue and White G3, which is nearly the same board as Mreyebrows' G4 "Yikes". In fact I have ordered, through eBay, a G4 CPU from the Yikes platform, since the socket type is the same: ZIF.

My question, which is directec at Mreyebrows, but open to everyone, is: When you boot-up Ubuntu, do you notice any of the following messages (you may need to specify "nosplash" to see them, or press Alt/Option + F1, after the boot sequence starts):

Something about "Cannot access system clock by any known method, add --debug [...]"

Something like "/dev/pmu does not exist."

I am reinstalling OS X, right now, so I don't have these messages right in front of me. I wish I knew which log file contained system boot messages. I'll have to do an fgrep, later on.

I have previously reset the pram, but only recently reset the PMU. This may have already solved these problems, but in the mean time, I am wondering if anyone has these messages?

---

### Post by garlicsalt2 on 2008-05-09
> **vivichrist said:**
> I'm having problems with the same mac [http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_400_agp.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_400_agp.html) except its 400mhz g4. how do i tell if my ram is cl?, note I don't have the original ram or keyboard, mouse, screen, hdd, dvd-writer, you name it. on boot I get udev-event[1890]: run_program: '/sbin/modprobe' abnormal exit. hardy and feisty seem to flip out over ohci1394. hardy-livecd managed to boot into gnome but no mouse or keyboard function so, can't do any thing. hardy gets to a prompt but same story. feisty brings up the ubuntu logo which hardy didn't but then goes to a black screen with the above message and stops.

You probably have either bad RAM, not enough RAM, or a faulty motherboard.

Might I ask how much RAM you have installed?

Also, check the connections inside the machine. Ie, take out the video card, RAM, etc., and carefully put them back in. You can also try resetting the PRAM, and PMU units.

If none of that works, I'd try to identify the faulty component. Use the same Boot CD/DVD for this test. Boot up, and note the point of failure - that is where does the first error message occur. Use the live-nosplash to see the full boot log. If the log seems to be pretty consistent, then try switching the RAM chips around. If this changes where the system starts to "Mess up", then it is probably the RAM.

You state that it "flips out" over ohci1394"? That is the Firewire module. Try turning off any external Firewire peripherals, and unplug the Firewire cables going to the Mac itself. If this doesn't make a difference, or if there are no modules in the first place, then maybe try to unplugging the Firewire component from the motherboard. and try again.

I know, that is a lot of info, I am very talkative in person too...

If some of this doesn't make any sense, ask questions first, rather than risk making mistakes.

---

### Post by vivichrist on 2008-05-11
I have 384MB of RAM installed and I've had partial success with ctrl+alt+P+R @boot and feisty-desktop, install is ok up until "loading module 'aec62xx' for IDE Chipset Support" and stops, so it gets though disk partitioning and copying files etc. will try other stuff you've suggested and get back to yez.

---

### Post by garlicsalt2 on 2008-05-12
> **vivichrist said:**
> I have 384MB of RAM installed and I've had partial success with ctrl+alt+P+R @boot and feisty-desktop, install is ok up until "loading module 'aec62xx' for IDE Chipset Support" and stops, so it gets though disk partitioning and copying files etc. will try other stuff you've suggested and get back to yez.

Ok, that chipset is definitely the IDE of Hard Drive controller. Yes, I know that was stated, but I did some checking, just to be certain. I found a few other people who had this problem. Check the jumpers on the Hard Drive, they should be set for Cable Select, or "CS" for short. This is especially true if you have two hard drives installed. Secondly, check if your cables are snug.

Optional: If you want to completely erase your hard drive, and wipe any failed attempts to install linux, you can do the following.

RED-FLAG-WARNING!!! This will zero-fill the hard drive, and completely OBLITERATE anything there. DO THIS **AT YOUR OWN RISK**

First, read the sticky note at the top of the forum, about Malicious commands. Second, if you have any other drives in the system, unplug them, for the time being. Third, PM me for the command to use, as I'd rather not get myself banned from these forums. You will need to completely boot into Ubuntu, to do this, and you really shouldn't need to do this. Every time you re-partition the drive, it will effectively erase the contents.

Lastly, if you are in the East Los Angeles County, or Northwest Orange County, we can try to work on it together. I have been given a bunch of Blue and White G3 machines, and I have extra Hard Drives, Motherboards, CD Drives, etc., that we can try to swap - *Temporarily*, in order to troubleshoot. I also have a copy of OS X 10.4 Tiger, and OS 9, from which we can try to boot, in order to check for simple problems.

---

### Post by garlicsalt2 on 2008-05-15
Uh, ok. I said very little, in way too many words. I really need to not post messages after 9:00. Too much "verbiage".

VIVICHRIST: Any progress?

---

### Post by vivichrist on 2008-05-18
sorry about the late reply didn't get notice til today. yep trying that right now, I have put a WD1600 160 gig hardrive in but yes I had no jumper (single master) so we'll see. um ... I live in new zealand (south pasific)

---

### Post by vivichrist on 2008-05-18
would I need to adjust the jumper for the dvd-writer also?

---

### Post by vivichrist on 2008-05-20
OK I have switched the HDD and DVDwriter to CS and now HDD is /dev/hdb? but no change. modprode exits abnormally and/or gets stuck which stops the boot process. I think I'm doomed. hardy just freezes during boot. can I disable hardware detection during boot/install?

---

### Post by garlicsalt2 on 2008-05-21
Ok, Ok. I don't really know where to go with this, as I can't visually ispect the machine. Also, although I've been involved in PC repair for many years, I am somewhat new to Macs. The only Macs I've really been "under da' hood" with, so to speak is the Blue and White G3. This model is nearly identical to the G4 "Yikes" platform, also called "PCI Graphics". If you aren't using this model, then the hardware settings might be a little bit different. If your graphics (video) card/adapter is an AGP card, then you're using a hardware platform with which I'm not familiar.

For these reasons, my information is assuming you have the machine I referenced. Newer systems might be the same, or maybe not.

Curious, you say your DVD-Burner is now /dev/hdb??

Wait!!!!

Woah!!

Just thought of something. If you had a system already put together, this would be obvious. Since you say that you put your own hard drive and DVD burner inside, maybe you aren't aware of this.

Are you, by any chance trying to load the hard drive into the bay directly below the DVD-Burner???

Under OS X and classic, you are not supposed to do this. I don't know whether Linux cares. On my system, that bay is for an optional Zip 100 Drive. I'm not certain if the hard drive controller chip is designed to power a Hard Drive there.

Again, assuming that your machine is at least somewhat like mine, The DVD/CD drive and Zip drive go in the front. A different front panel is used if there is a Zip Drive installed.

Look inside the case, on the bottom-rear of the machine. There should be a "u"-shaped bracket thingie. Take your hard drive out, if it is mounted as previously stated, remove it, and mount it into the U-bracket. If you have the original, short, IDE/ATA cable, you should be fine - the Hard Drive is physically near the IDE port. If you don't have that cable, try to find a Cable Select cable for a PC, if no luck, then use a regular cable, but re-do the jumper settings on the Hard Drive back to Master (or Single if it is a Western Digital Drive, or if it has a separate option for single).

I hope this helps.

If you have an OS 9 or OS X disc or disc set, you can try to boot from those. I don't know if they'll work if you don't have an Apple approved CD/DVD-Drive, though. My understanding is, if it doesn't have an Apple Logo, and an Apple ROM chip on it, it won't boot an Apple OS (I think). If I happen to be wrong, feel free to update me.

--Aaron

P.S.: Yeah, I noticed you were listed as being in New Zealand, right after I made the offer. Oops! Sorry.

---

### Post by vivichrist on 2008-05-23
I think th motherboard may be stuffed. after some dusting there was differing behaviour. generic drivers work but hardware specific drivers get stuck with modprobe on ... in particular ohci1394 and IDE. is there any way I could install without hardware detection phase?

---

### Post by garlicsalt2 on 2008-05-24
> **vivichrist said:**
> I think th motherboard may be stuffed. after some dusting there was differing behaviour. generic drivers work but hardware specific drivers get stuck with modprobe on ... in particular ohci1394 and IDE. is there any way I could install without hardware detection phase?

I'm not certain how to do this under Mac PPC. There is a way to bypass HW detection on PC, using a different Linux Distro, called Knoppix. I don't know how under Ubuntu at all, much less on PPC Mac. I do know, that there is a program called MemTest86+, for PC, that will do a thorough diagnostic of the RAM. I don't think it is available for PPC (btw, PPC means PowerPC, if anyone is following this thread, and doesn't know that. It is the type of processor/CPU used in Non-Intel Macintosh machines, starting with the Mac 6100, and includes all G3, G4, and G5 systems).

If you had access to an old, throw-around PC, that took SDRAM, like this Mac, you could pop the RAM, DVD-Burner, and Hard Drive in, and see if you can isolate one of these components as the culprit.

In a PM, you asked me if you could update the firmware, without using Mac OS. The answer is, I don't know, but I don't think so. I have flashed the firmware in mine, but I had to have OS 9 to do so. Even having OS X alone won't work. If someone has come up with a way to do it in Linux, it may work, but I am not aware of any such solution.

Might I suggest, trying the following boot cmd-line:

live-nosplash verbose

That is assuming that you are using the Live CD. I prefer the DVD version, myself, as it has all of the different boot modes all on 1 disc. Live, Rescue, Install, etc.

Be sure to keep an eye out for error messages during the boot procedure, as this will clue you in to possible problems.

You can also try to do an "Expert" install, using the alternate CD or the DVD version:

Expert-nosplash verbose

This will give you more options during the install phase, and with some, experimenting, and a little patience, you might be able to tell it to selectively bypass certain hardware auto-detection, or maybe even tell it which driver to use.

Be creative, and use the forums built-in search features to research if any one else has had similar problems, and their solutions. If your machine is busted, at least take the time to learn as much as you can from it. Also, look on eBay, for a replacement Motherboard. If you are truly using the "Yikes" G4, then a Blue and White MB should work, but try to get a Revision 2 board if possible. You might also need to patch the firmware if you're going to use your G4 CPU on it. Apple has blocked use of G4 chips on Blue and White Motherboards, with there latest Firmware version, but Daystar ([http://www.xlr8.com/](http://www.xlr8.com/)) has a patch available to unblock it.

Happy Mac-Hacking!

--Aaron

---

### Post by HappilySavage on 2008-07-01
Hi Guys. 

Im trying to run the Kubuntu LiveCd on a Powermac g4 'yikes' also. 

when i got the machine it had no hard drive, and i have put some more ram in it.. i noticed that maybe this could be the problem. but the live cd gets going. and then it gets to the point of:

Starting K Display Manager: kdm. 
 * Running local boot scripts (/etc/rc.local) 

then it flashes black, and then it goes back to the screen containing those messages. 

what should i do? ive tried live-nosplash and live-nosplash-powerpc with the same resilt

will try this verbose thing now..

---

