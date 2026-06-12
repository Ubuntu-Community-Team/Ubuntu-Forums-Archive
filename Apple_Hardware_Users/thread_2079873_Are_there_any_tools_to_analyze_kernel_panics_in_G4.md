---
title: "Are there any tools to analyze kernel panics in G4 iMac?"
date: 2012-11-02
forum: Apple Hardware Users
---

### Post by este.el.paz on 2012-11-02
Folks:

As I posted over on the "Suspend from sleep" thread I've got a G4 iMac set up to boot OSX & Xu/Lu 12.04 that has been hit with a plague of kernel panics, first it seemed like they were only happening in Xu/Lu, but then they started happening in OSX as well.  I ran the Apple Hardware Test disk several times and it shows OK, I've repaired the disk with Apple's DU, and used Onyx to clean up the system, I've even installed a fresh OSX 10.4.6 on an Ext HD and booted from the Ext HD and the kernel panics continue.  I'm thinking "hardware" but so far nothing has shown to clearly show that.  Would there be some Ubun/Linux tool that could analyze the system such that it might point out what the problem is?  A GUI app might be better for me, but if a CLI app is out there that could be tried with a little help from the forum . . . that would also work.  I'd like to keep the iMac going, it's got ten years of data and it serves to check email and get around the web well enough.  Any thoughts?

Last post from the other thread from earlier in the month, no replies offered:

> @abtabt:

Appreciate the follow-up, just letting you know the latest situation,  looks like my horsie is again pulling up lame and will be a DNF once  again.  I just tried to boot the Xu 12.0.4 system to check on lsmod and  wound up with multiple problems, problems getting Yaboot window to show  up, problems getting gdm log in window to stay, problems with once  getting passed gdm log in then mouse didn't work and no toolbar,  problems then getting passed xubun splash window with subsequent kernel  panic, problem with kernel panic before the Yaboot window . . . problem  with showing a single user window that wouldn't accept my password to  get into CLI . . . went thru 5 cold boots essentially ending in kernel  panic.  Gave up, when I tried to boot OSX, there also was a kernel panic  and had to restart . . . thought it might be the old iMac giving up its  life force, but seems like it's OK for now . . . don't know why kernel  panics in Xubun would carry over to OSX?  But, this has been the history  of trying to get anything in the Linux realm to run on the iMac for  longer than a few months, seems to be doing OK, then the system seems to  start degrading??  kernel panics start and eventually the CLI even goes  away.  There was something about "starting pbbuttonsd 0.7.9 Unknown  powerbook; speech-dispatcher disabled, edit; starting  NTP-server-ntpd-kernel panic 3 or 4" on the Xubuntu splash window.

I did do an update/upgrade on Friday night, couple night back using  "sudo aptitude" and I rebooted then and everything seemed to be OK, I  can't remember if I installed "powerprefs" in the iMac following a  comment in the PPC FAQ about either getting suspend to work, but I  didn't adjust anything in the GUI powerprefs window when it opened . . .  so I don't know if somehow one of the upgrades has messed with my "nv"  driver compilation . . . but once again there is a problem.  Seemed like  Xu/Lu 12.0.4 got me closer to something stable . . . will have to see  on another day if I can get it working, if it's a hardware issue, or  just try what will be the 6th or 7th re-install . . . .  Maybe Tuesday  I'll again have a moment to play around . . . the sound issue goes to  the back burner for now.

---

### Post by powerpcliberation on 2012-11-03
It could very well be the memory.  Don't trust the apple hardware test because it only skims the surface of how to properly test memory.  It's a very weak and incapable utility to say the least.

Use [Remember]("http://www.kelleycomputing.net/Rember/") to fully test your RAM.  It can take 1-2 hours.

Another thing to consider is that you have an iMac and all models from the G4's to the newest Intel machine all sacrifice hardware health and longevity to look pretty.  Because of this the iMacs all tend to die after a few years.  The G4 towers on the other hand live forever because they don't sacrifice hardware health for design.

You would have been far better off using a tower and printing a high res pic of the pretty computer for your wall.  Remember that a computer needs to be a tool before anything else.  When you choose impractical computers like an iMac you're then stuck with all the headaches that come with it.

---

### Post by este.el.paz on 2012-11-03
Folks:

The continuing saga . . . I got a hint to try booting the Lubuntu 12 LiveDVD which I was able to do last night and the computer ran for well over an hour . . . I got into DU and ran the "self-test" and it cam eback with "Two bad sectors" . . . .  The problem is that the screen resolution is probably at 8 and it's very difficult to read words that are in boxes.  Can someone help me out with some boot parameters that might improve the screen resolution, so that I might be able to find where the "Repair bad sector" function might be?  I used "videoofonly=0???? (whatever is listed) and "nouveau.modeset=0" . . . .  It's interesting that the machine ran OK in the DVD, but doesn't from the int HD, I have SMARTReporter in the OSX side and it still shows OK.  Mousing over some of the "Self-test" results in Lubun DU, showed phrase, "Failure means imminent demise of the HD due to old age . . . " . . . something like that . . . but I couldn't tell if that meant that failure was indeed imminent, or if the word "Failure" had to be listed as a result--which it wasn't . . . just two bad sectors.  In OSX DU has been run from the clone to "repair disk" . . . would a "bad sector" possibly survive that repair work, or would a bad sector in Xu/Lu "reach" over and cause crashes in the whole computer?

e.e.p.

---

### Post by este.el.paz on 2012-11-03
> **powerpcliberation said:**
> It could very well be the memory.  Don't trust the apple hardware test because it only skims the surface of how to properly test memory.  It's a very weak and incapable utility to say the least.

Use [Remember]("http://www.kelleycomputing.net/Rember/") to fully test your RAM.  It can take 1-2 hours.

Another thing to consider is that you have an iMac and all models from the G4's to the newest Intel machine all sacrifice hardware health and longevity to look pretty.  Because of this the iMacs all tend to die after a few years.  The G4 towers on the other hand live forever because they don't sacrifice hardware health for design.


@powerliberation:

I was in the middle of typing out my last post and missed yours, thanks for your time . . . it might well be RAM, although I did run Rember and could only get thru one round before the computer crashed, but in the LiveDVD last night we lasted over an hour until I got tired.  On the "design" . . . right, it was my first foray into computers, but it has lasted ten years, so I can't complain . . . .  Any thoughts for the screen rez in the LiveDVD??

e.e.p.

---

### Post by rsavage on 2012-11-04
At the yaboot prompt type: 
 
```

live video=offb:off nouveau.modeset=0 single

```
This will freeze or give you a blank screen. You will have to judge blind when the machine has finished booting which can be longer than you think. Type the command (you won't see what you type): 
 
```
modprobe nvidiafb
```
 
Text should now appear on the screen.
 
If it doesn't reboot (type reboot), but this time use:
 
```
modprobe rivafb
``` 
 
You can start the desktop with 
```

start lightdm

```
 
EDIT: In 12.10 you may have to force a higer colour depth. For example "modprobe nvidiafb mode_option=1024x768-16"

---

### Post by este.el.paz on 2012-11-04
@rsavage:

Thanks for your attention to my problem . . . it looks like you are providing a way to run the Lubun LiveDVD in such a way that the screen resolution will be improved????  Rather than giving me a way to somehow analyze or repair the "2 bad sectors"???  Certainly if I can see the screen more clearly it might help, but then are there any tools loaded in the LiveDVD that can "analyze" why the kernel panics are happening in both the internal HD running Xu/Lu 12 and the OSX side?  If I could somehow "deep clean" the HD would that fix the kernel panics?  

I can certainly try out your commands from the LiveDVD and that might get me to a read-able GUI and then I might find the DU "repair problems" tab???  It's not that I'm looking to run my computer from the install DVD all the time, but how to figure out why it's crashing ?????  HD dying or "bad sector"????  Don't know . . . but, thanks for the guidance . . . so far the Xu/Lu has been the best in the iMac G4 . . . but, again, now some issue with kernel panics.

e.e.p.

---

### Post by este.el.paz on 2012-11-04
@rsavage:

Ran those commands using my Lubun 12 install DVD, waited until no more Op drive sounds, entered the "modprobe" . . . nothing happened . . . tried the second modprobe rviafb . . . nothing, no text.  Then I typed "start lightdm" the Op drive made a few sounds . . . .  I'm looking at a greyish screen with three vert lines, two yellow, one blue on the left third of the screen . . . .  Is there a flashing boot prompt?  Can't see it.

e.e.p.

---

### Post by rsavage on 2012-11-04
Corrected.  Forgot to turn off KMS.

---

### Post by este.el.paz on 2012-11-04
@rsavage:

OK, that worked and got me into a clean GUI . . . and I checked DU and ran the "self-test" and it came back with #5 WARNING-reallocated sector count" . . . "2 bad sectors" . . . .  But, as originally posted I don't know how to repair the bad sectors if that is possible??  Problem is the partition is split . . . and kernel panics happening on both sides, but is there a way to "repair disk" as there is with OSX, but doing it from the Lubuntu install disc?  Interestingly, I tried your edited commands the first time, got to DU and when I clicked on the "self test" button the app crashed and the toolbar fell off the screen . . . .  I tried again and got back to DU and was able to run the self test; I tried the Benchmark option but "operation failed."

e.e.p.

---

### Post by este.el.paz on 2012-11-12
et al:

The latest update on the kernel panics . . . is that they seem to have abated . . . for reasons that don't entirely make sense.  I was on the track that it is/was a hardware problem, finally got around to unplugging the ethernet while simultaneously running "applejack" from the OSX side, thanks to some help from the Apple discussion forum.  That managed to get many hours of run time on the iMac yesterday w/o ethernet, and then plugged it in and had no problems.  I even rebooted into Xu/Lu and got an error message telling me that "a crash was detected now or recently" . . . other than that no problems.  The only issue was that w/o the ethernet plugged in I couldn't get the wireless to work in either OSX or Linux side.

But, this brings me back to this forum and my question about whether there are any apps that do "deep cleaning" on the Linux side, as perhaps applejack has done from the OSX side?  Is there some "fsck" command that would clean cache?  I'm not sure if I'm out of the woods on this problem, but previously it was hard to run it longer than 15 mins., but considering that before the kernel panics were happening in both OSX & linux it's not clear why running applejack in OSX will let both sides run??  It's been cooler here and there might have been some problems with hot weather in the previous weeks.  I did see how kernel panics do something so that the chances of kernel panics is increased, but how is it that the Linux system seems to have gotten over the problem . . . seemingly w/o any "deep cleaning"???

e.e.p.

---

### Post by este.el.paz on 2012-11-15
Folks:

Bumping this up since there hasn't been any response to the latest question or even to the title of the thread asking about tools or utilities for Linux that could either do "deep cleaning" like "applejack" or that can diagnose issues that would be causing kernel panics in two separate partitions . . . ??????

I can't conclude that it isn't necessary, because both the Linux side and the OSX side were plagued with kernel panics for quite awhile . . . .

e.e.p.

---

### Post by este.el.paz on 2012-11-16
Folks:

Thanks for the kind attention, very much appreciated . . . latest update is that I decided to try to experiment with the iMac a bit by plugging the FW connection to the ext HD back in again and then doing a cold reboot into OSX since my knowledge of how to fix Linux is limited . . . .  Just after logging in I again got the classic greyed screen with the chilling words . . . "You need to restart your unit" . . . .  Unplugged and tried the other FW port with same results . . . .  Then tried to run "AJ AUTO" but each time it got to the "repair permissions" phase there was a violent kernel panic that rocked the process . . . tried to run that 4 or 5 times, then remembered that previously I started with "AJ auto" . . . but the kernel was again violently "panic-ed" . . . .
 
So, the paroxysms of KPs have returned, possibly having to do with the FW port, possibly not . . . since unplugging the FW cable did not stop the KPs . . . .  But, right now, we can't get through running AJ . . . it might just be there was a brief flash of trouble-free computing after running AJ, but in running the computer the last breath was spent . . . ?????  : - ))) 
 
I'll try again until hopefully the full AJ process can be run . . . if there is some Linux utility that could clean the system or analyze why kernel panics are happening might be worthy of running from the Xu/Lu side . . . .

e.e.p.

---

### Post by este.el.paz on 2012-11-19
To whom:

In the interest of science I'm posting the latest updates on the KP situation and its effect on the Xu/Lu partition . . . .  After plugging in the FW and getting several KPs in OSX and trying to run AJ and not being able to complete it w/o a KP, I tried to boot into Xu/Lu and could not get to a GUI . . . I just got a black screen, and I believe the mouse cursor could be seen . . . .  Thinking that AJ may have somehow wiped the Yaboot items I tried to boot into a Super Grub 2 CD using the C key . . . and that also did not work, we just went back into OSX w/o the Yaboot screen showing up at all . . . I tried to leave the CD in and boot using the option key, but the CD did not show up to choose from . . . .  So, the Linux partition does show up in the Option OSX boot manager window, but just goes to a black screen, can't get into SG2 . . . .

I'd still be interested in hearing about utilities that could be used to help Xu/Lu recover from the KPs . . . that are possibly related to the FW port?????

e.e.p.

---

### Post by abtabt on 2012-11-20
one suggestion is to disassemble and replace the hard drive
and NOT use the Firewire make it clean inside and reconnect cables and Memory etc.

because it sounds like a hardware fault (dirty, heat, age)

the CD player can provide these problems

usually self-extension cables and pull it through the CD cover so that with an easier way to access the
switch / disconnect the hard drive or CD

you can also run the Live CD without the hard drive plugged in if you have enough memory

and to format the hard drive completely

I guess you tried to remove the battery, sappat PRAM, and CUDA



badblocks can be one thing to identify the sectors but it is a temporary solution (a computer that I have is one of a number of bad blocks, but which has been isolated and has served for three years in daily use)

[http://linuxpoison.blogspot.com.ar/2008/01/howto-check-disk-drive-for-errors-and.htm](http://linuxpoison.blogspot.com.ar/2008/01/howto-check-disk-drive-for-errors-and.htm)

or doing a ILAMPA

goodluck

---

### Post by este.el.paz on 2012-11-20
@abtabt:

Many thanks for your post . . . agree that it seems like a hardware problem, right now I'm focusing on the FW, but have yet to plug back USB or speakers, etc.  So far I haven't done any "surgery" on the HW end . . . .

I did manage to get into "single user" and tried to do "fsck" but I obviously didn't know what I was doing, but I did manage to get the GUI fired up and it ran w/o crashing, but it did show me a "crash report" error window, so there might be a crash log to read.  I'll have to read through the Linux Poison links, I did find one of them in a google search.

Right now, the problem is that the wired connection through Network Manager is not working and won't let me connect, and this has been a traditional problem in Linux on this computer, so I ran a few commands to try to get it back, but none responded.  I don't have Disc Utility loaded in Xu/Lu, I think I tried to get it installed awhile back when it was cashing every five-seconds, but it didn't work--I wanted to try to see if DU could "repair the disk" from the GUI . . . .  So. I'm back in OSX typing this post, there has been a little progress in terms of reviving the Linux side, now I would just need to test for bad blocks or try to learn how to run fsck . . . but it seems like if I could just get the ethernet back up the system might be OK.

But thanks for the suggestions about running a stripped down machine, that's kind of amusing; it may get there.  I'd have to read through your post a few times; I get the "clean stuff off" idea, but I didn't understand the: "_usually self-extension_ cables and pull it through the CD cover so that with an easier way to access the
switch / disconnect the hard drive or CD" . . . that doesn't seem to be translating well in English . . . anyway, no worries, right now I don't have time to break open the iMac . . . .  It's just been a series of issues that keep cropping up as far as keeping a Linux system running on the iMac . . . now we're back to the basic ethernet connection--in the past, running "sudo modprobe sungem" was enough to bring it back, that isn't working now . . . .

Thanks for the reply though,

e.e.p.

---

### Post by abtabt on 2012-11-21
If Network Manager is not working well 

i do like this

code

nano /etc/network/interfaces

and add follow in interfaces

auto eth0              # or eth1 or what yours is
iface eth0 inet dhcp   # or eth1 or what yours is


and then 

code

sudo /etc/init.d/networking restart

and off course this will work when you boot normally 

and if you want back to basic hash the lines

about cables out off CD what i mean was take a longer ide and power cable then you can try different HDs or CD players

and i will suggest  LUBUNTU CD 12.04 for test badblocks ,fcsk.etc 

btw sound will work and Suspend too (if you use UBUNTU 12.04 CD it will not work with out some tweaks

:guitar:

---

### Post by este.el.paz on 2012-11-21
@abtabt:

Thanks again for the follow-up and details . . . although I did most of those steps which perhaps we discussed many moons ago on the MintPPC forum . . . I even did the "ifup" gambit, the network/interfaces looks like you've mentioned . . . I logged out and in . . .  The applet says something like "Network Manager is not available" . . . bit of a sticket wicket, eh?  If I'd want to download some update I'd need the internet, etc.  Sort of interesting that this problem has followed along in all the Debian-based systems I've had installed in the iMac . . . some system problem, kernel panic would then break the internet connection, making it that much more difficult.  I'll have to try to find the threads where I was posting that problem, but previously after doing all the other steps you've mentioned it was the "modprobe sungem" that fixed it before--this time that isn't working . . . yet . . . . 

> and i will suggest LUBUNTU CD 12.04 for test badblocks ,fcsk.etc 

I'm assuming that you mean to boot the install CD and use that to repair the disk . . . OK, again, as I mentioned I was having a problem booting the CD drive . . . .  And as far as sound goes, right, I originally did the Xubuntu installation, but then added the LXDE desktop, and then I think you posted your xorg.conf file in a thread, which I have; but right about that time is when the KPs started happening and the main push has been to just get the iMac working . . . so, the continuing saga continues . . . the basic computer functions are more or less working, now for the Xu/Lu side the next step is internet connection . . . and then later suspend & sound.  

Thanks for being there, much appreciated.

e.e.p.

---

### Post by este.el.paz on 2012-11-25
Gents:

"Network Manager is not running" is what the error message is saying . . . I've tried all the suggestions on the "networking restart" listed by abtabt, I've read through and ran the UbuntuPowerPC wiki that links to the Lubuntu wiki for "network manager is unmanaged" . . . ran those commands . . . .  Nothing.  And, very strange, I've tried booting up in the Lubuntu and Kubuntu LiveDVDs . . . to try to run fsck, and when I follow the rsavage method to boot into a clear screen using the LiveDVD . . . it fails.  If I enter the boot parameters with a space between  ```
video=offb: off
```

"offb:" and the "off" there is a frenzy of activity recognizing an error, and then it boots into the 8hz screen . . . barely readable . . . .

I'd like to try to fix the ethernet connection so I could download "disc utility" or something to try to repair the disc to see if that will fix the problem(s), or update the system to see if that would fix the ethernet connection . . . I even tried to boot a SuperGrub 2 CD to try to repair the partition, but it isn't being recognized.  Could I boot up in the Xu/Lu system with some LiveDVD loaded in the tray, and then somehow use the Terminal to boot or select the DVD as "mounted" and then run fsck?  I tried to follow some advice on booting into "single" user and then "umount" the home partition, but it said, "device is busy" . . . .

Seems like a perfect storm of karmic interference on getting a Linux system to run in the iMac for longer than a few weeks . . . clearly there is a hardware issue going on, but now on the OSX side, the computer runs fine, connects to the ethernet w/o a problem, etc . . . .  Back in Xu/Lu the system boots OK and I can run Terminal and do stuff, but it just won't connect to the net.  Running "sudo ifconfig"  just shows the "lo" info, but not the "wlan0" . . . .  Any thoughts would be appreciated.

e.e.p.

---

### Post by este.el.paz on 2012-12-01
> **abtabt said:**
> If Network Manager is not working well 
i do like this
code
nano /etc/network/interfaces
and add follow in interfaces
auto eth0              # or eth1 or what yours is
iface eth0 inet dhcp   # or eth1 or what yours is

and then 

code
sudo /etc/init.d/networking restart
and off course this will work when you boot normally 



@abtabt:

A few days ago I was re-re-reading your post and realized that I actually didn't have exactly what you had typed in /etc/network/interfaces . . . I had "allow hot-plug eth0" . . . and we had some rainy weather here in SoCal so instead of going for a bike ride I played with the iMac Linux partition . . . took a few times of trying different code, but wound up taking out the "#Network Manager" line and just putting what you have put in your post pasted above . . . and then ran "sudo ping google.com" and indeed the internet is still working this morning . . . !!!!!  So I ran update/upgrade last night, it still is taking a long time to boot the Xu/Lu side, I'm still getting "Crash report" error window, the Network Manager applet of course is showing an "X" . . . but, I'm typing this in Xu/Lu 12.04 Firefox . . . . .  As I mentioned previously, I've had problems getting the Lu Live DVD to boot in any readable form, so it's made it hard to try to "repair disk" from the Live DVD . . . perhaps I'll again try to boot to "linux single" and see if I can run "fsck" . . . not sure how to "test for blocks" from the CLI .  I also tried to install "disk utility" from the CLI, but it came back "utility not found" . . . .  Looking for a utility that can run from the GUI to repair the system . . . so far no advice on what apps might do that . . . .  It's interesting that straight Wheezy installed in my iBook has a Disk Utility app, but Xu/Lu doesn't seem to show it???????

Anyway, thanks for your post, it did help to fix the immediate ethernet problem, now maybe I can try to switch the xorg.conf file to get Suspend to work . . . but it still seems like the system is detecting the kernel panic damage, but doesn't seem to be able to repair it in spite of multiple reboots in and out of Xu/Lu . . . . 

e.e.p.

---

### Post by abtabt on 2012-12-02
hallo i suggest you to reinstall with Lubuntu CD not DVD to get a clean install



if not CD drive work cant you use firewire or if you are a handy man 
change the hard drive 

its good to read tings twice

---

### Post by este.el.paz on 2012-12-02
> **abtabt said:**
> hallo i suggest you to reinstall with Lubuntu CD not DVD to get a clean install
if not CD drive work cant you use firewire or if you are a handy man 
change the hard drive 
its good to read tings twice

@abtabt:

Thanks for the follow-up, I do appreciate your help . . . so far as it goes I have not been a "handy man" with computers . . . it's only been the last 1.5 years of messing around with Linux that I have started to "look under the hood" in terms of software, hardware is another story . . . .  We'll see how it goes, without FW ports any back-up is now going to be very slow . . . and is it the HD that is starting to go, or is it motherboard, so far even on the Apple forums no one was able to point me in a direction as far as testing goes beyond Apple HD Test . . . which shows everything as OK . . . .

Still looking to see if there is some way to repair the software or as the title asks, a way to analyze KPs on the Xu/Lu system . . . it keeps showing the Crash Report error window . . . have yet to be able to run any tests or find a utility to repair the disk like there is in Wheezy . . . but, internet is working and so I can do updates . . . I'm still trying to avoid the 3-4 hour reinstall process since there probably is some physical hardware impending doom in the near or medium short term future . . . .  I'm just trying to keep what is going, going, for as long as the computer is working; maybe I'll try to burn an install CD, but what would be the difference between the CD and the DVD as far as installing the system goes?  Still not sure why the CD drive seems to work in OSX, but not in Linux??  Is Linux more the "early warning" canary in the mineshaft than OSX??  : = )))

e.e.p.

---

### Post by este.el.paz on 2012-12-04
@ et al:

Latest update . . . seems like the KP thing has stabilized since unplugging the FW port to the ext HD, and after getting the internet connection working again and running updates, I was able to use Synaptic to find a "gnome-disk utility" app and install it, ran a few tets there and it showed "Disk has a few bad sectors" . . . so I googled that phrase and it took me to some threads about installing "smartmontools" . . . so I did that, and then I read a thread about using "GSsmartcontrols" as a GUI interface for smartmontools . . . so being a GUI guy, I did that and ran the test . . . and it shows I have "Two bad sectors" . . . and showing a "pre-failure" status for a few line items . . . .  So, compared to some posts tha I saw were saying they had 1107 bad sectors, I guess 2 is "better"???  So, a mild sense of impending doom remains . . . was still looking for some kind of app that could "repair the bad sectors" . . . following a line of thought on going to the HD manufacturer site and getting their tools . . . but nothing seems to be for Mac . . . although there was a "legacy" system for Linux CLI to test the HD???  A bit busy, but perhaps it will lead somewhere . . . .

e.e.p.

---

