---
title: "Feisty beta"
date: 2007-03-24
forum: Apple PPC Users
---

### Post by ssam on 2007-03-24
have you tested the feisty beta yet? it is more important that ever that the community do some testing and file bugs.

the feisty beta cds for powerpc can be found at [http://cdimage.ubuntu.com/ports/releases/feisty/beta/](http://cdimage.ubuntu.com/ports/releases/feisty/beta/)

The desktop cd let you try ubuntu without affecting your hard disk. If you plan to do a test install make sure you have any important data backed up.

if you find bugs then check if they are already reported at [https://bugs.launchpad.net/ubuntu/+bugs](https://bugs.launchpad.net/ubuntu/+bugs) , and if not report them. also post your findings here.

---

i have been running feisty on a spare partition on a ti powerbook g4. the main problem i see is sound not working. this causes loading of gnome to fail. it is the neccisary to CTRL+ALT+F1 to a terminal, and run
```
killall esd
```
to continue.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652)

---

### Post by grazie on 2007-03-24
A fairly major problem that will affect many with certain ATI/Radeon video cards is that X doesn't start up. There are workarounds though.

[Bug #93271]("https://launchpad.net/bugs/93271")

---

### Post by Peter76 on 2007-03-24
Just dist-upgraded from Edgy, no problems at all and everything works great. Going to try desktop-effects next...
My hardware is: ibook g3 900, 640 MB

---

### Post by devils_casper on 2007-03-24
Using and updating Feisty from Herd2. its working grea till now. no problems yet.t

---

### Post by bostoys on 2007-03-24
i just upgraded from dapper drake, and i've had no problem so far except this:

i enabled the 'wobble' desktop effect [which makes windows wobble when you click and drag them...very cool] which worked fine, but immediately after hitting apply and closing the window, when i went back to System->Preferences->Desktop Effects [or any other preference window], the body of the window doesnt show up. terminal works, firefox works, gaim works, file manager works. just not the preferences.

---

### Post by AlphaMack on 2007-03-25
Nautilus is one of those windows that won't show the contents once the wobbling effect is enabled.  The wobbling effect does seem a little choppy, especially with the window contents even though it isn't exactly a 'supported' feature (perhaps a compatibility issue between Compiz and ATI cards?).  BTW I have the ATI Radeon 9600.

The device manager sees the AirPort Extreme card on my PowerBook G4 although I wish that there is an option to grab the firmware (and cutter) similar to the prompt to obtain restricted codecs.

---

### Post by mark on 2007-03-25
I did a clean install (from the Alternate ISO) yesterday and, I must say, I'm excited.  I tried most of the Herd images, but the Beta seems (so far!) very stable, very nice.

When I tried to play one of my usual Internet radio links (MP3) from Rhythmbox, all I got was an error message about not having the correct codec installed.  I logged onto Launchpad to file a bug report and found that this is a feature that's coming.

It detected my parallel-port-connected LaserJet-6P straight away, which Breezy & Edgy had problems with (corrected by adding *ppdev* to /etc/modules).

The *Desktop Effects* are currently a no-go for me - when enabled, window borders are "whited out" and I can't move the silly things!  Oh, well...

Also, I discovered that *Network Manager* can be disabled from the *Sessions* preference, which is good for me as I have a single, wired network connection & prefer the functionality of the *Network Monitor* applet.

All in all, very promising...so promising that it's been promoted to the top of my GRUB menu.  And, I'm casting an eye at my laptop as I write this...<g>

---

### Post by grazie on 2007-03-25
Thanks for your enthusiam Mark, but this thread is for users give feedback and to gauge progress/problems on Feisty Beta for PPC, not x86.

---

### Post by mark on 2007-03-25
Oops...sorry, I missed the PPC tag...now if I can get a mod to move it to the appropriate spot...

---

### Post by eentonig on 2007-03-25
Fresh Edgy install upgraded to Feisty. Just before the Béta was released. I experienced no problems.

That is. Upgrade-wise speaking. I do have a problem with the network-manager not connecting my wireless network. It did connect once, but ever since, it just refuses to connect to the networks available.

---

### Post by woopie49 on 2007-03-25
Problem loading from CD for video on:

Dual 1.42 G4 FW800 2gig/420gig (3HDs - disconnected 2)  Std video Pro 9600 card

ATY,RV250:
 Type:	display
  Bus:	AGP
  Slot:	SLOT-1
  VRAM (Total):	64 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x4966
  Revision ID:	0x0001
  ROM Revision:	113-99702-130


error message read something like .......

Invalid IO Allocation
b: 0xf0000400 e: 0xf00004ff
correcting G

Backtrace
Fatal Server Error 8]
Caught Signal 7
Server Aborting

Going to work now, will have to check post when I get home
6.10 is loaded on 1 of the HDs - no problems - config file modifed for higher resolution

Would rate my skill with Ubuntu as between novice - intermediate user.

---

### Post by Who on 2007-03-25
My experience here:

Smooth install - first time ever doing linux on ppc, worked great first time.
usplash theme is totally distorted (shape fine but colours totally out)

Issues I still have to resolve:
Colour banding
Changing display brightness
Flashplayer
Emulating mouse buttons
Installing Realplayer

---

### Post by Toehead on 2007-03-26
Just about to attempt the install, I'll let you know how it goes!

---

### Post by anders_gud on 2007-03-28
> **ssam said:**
> 

i have been running feisty on a spare partition on a ti powerbook g4. the main problem i see is sound not working. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652)

Running the LiveCD on a Tibook:
1. No sound..
2. No sleep/powermanagement (pbbuttonsd running)
 
Has anyone got Feisty working properly on a Powerbook yet (by upgrading alsa-libs maybe)?

---

### Post by Toehead on 2007-03-28
I have a 1.33 ghz powerbook G4, just installed Feisty. So far, EVERYTHING works. I have beryl up and running, and sound works very well. No crashes to report so far either, except one where the system hung when i was trying to select a screensaver.

---

### Post by domino on 2007-03-31
PowerBook G4 TI 15" 1.33GHz 1gig sodimm ATI 9700. Dual boot Tiger 10.4.9. Desktop install was flawless. No noticable hardware failure after reading and installing from airport how-to. Beryl official package from synaptic works well. No crash as of yet. Overall CPU time nominal and not overheating. Power Managment works well as far as I know. Although I never go on standby or sleep. Display sleep is all I use to prolong LCD use.

Feisty total uptime ~20hrs. I'll get a better evaluation when I have her running more than 4 days without reboot.

---

### Post by anders_gud on 2007-03-31
> **anders_gud said:**
> 
2. No sleep/powermanagement (pbbuttonsd running)
 
Silly me, suspend needs swap. 

Audio issue still here...

---

### Post by Toehead on 2007-04-01
I found one problem, Sleep doesnt appear to work. I click hibernate, and it goes blank then the unlock password prompt comes up right away.

---

### Post by jvc26 on 2007-04-04
No issues here for me.
Il

---

### Post by indica on 2007-04-15
has anyone out there dist upgraded from edgy to feisty on an ibook g4 800? just out of curiosity, i want to know what my odds will be

---

### Post by old_geekster on 2007-04-15
I just returned to Edgy.

I upgraded to Feisty -Herd 5 from Edgy a week ago.  Everything was going great (Beryl worked fine.) until the update to -14.  It would not boot into x server.  Then, the -15 update and the same happened.  So, I did some trouble-shooting with no positive results.  Now, it is back to Edgy.

I downloaded two 64-bit ISO's and one 32-bit ISO for Feisty, but none of them would install.  The install would get to "Step 6 of 8" and simply continue to percolate.  I finally went the upgrade route.

Update: Well, I upgraded to Feisty 2.6.20.15 generic.  It is running great with Beryl.  Now, if they just don't mess it up again.

---

### Post by stmiller on 2007-04-16
Installing shortly on an G4 867Mhz Tibook. Live CD picked up all hardware fine [edit] but gnome wouldn't start. Trying a daily release alternative cd.

---

### Post by grazie on 2007-04-17
A word of caution.

I've just updated a version of Feisty Xubuntu Beta to the latest Feisty which is now frozen and should effectly be the Feisty Release if there are no problems found. However the machine now no longer boots with the updated kernel or the old backup kernel either. Haven't got to the bottom of the problem yet, but spent no time trying.

Just thought I'd mention it.

---

### Post by Maelvon on 2007-04-17
> **eentonig said:**
> Fresh Edgy install upgraded to Feisty. Just before the Béta was released. I experienced no problems.

That is. Upgrade-wise speaking. I do have a problem with the network-manager not connecting my wireless network. It did connect once, but ever since, it just refuses to connect to the networks available.

I've the same problem here, have you find a solution to take the network card back ?
Local network is working, but internet is off ! :( 

How can I downgrade ?

Thanks,

Maelvon

---

### Post by stmiller on 2007-04-17
> **Maelvon said:**
> I've the same problem here, have you find a solution to take the network card back ?
Local network is working, but internet is off ! :( 

How can I downgrade ?

Thanks,

Maelvon

This network manager bug is well known, and will be fixed for the final release.

---

