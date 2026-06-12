---
title: "Sleep (suspend?) freezes mac"
date: 2012-09-18
forum: Apple Hardware Users
---

### Post by scognito on 2012-09-18
Hi,
I'm using an iMac (12,2) with Ubuntu 12.04 64 bit, standard kernel (3.2) and latest AMD drivers (downloaded from AMD site).
Sometimes when monitor turns off (because it went in sleep after x minutes) I can't turn the monitor on anymore.
Sometimes it works (moving mouse), sometimes don't. I don't know if it is related to some level of "sleep": seems (but didn't verify) that if it is in sleep mode for 5 minutes, I can wake it up, but if it is in sleep for an hour or so, I can't.
Also ALT-F1/F2/... doesn't switch to virtual console.
I've installed ssh to see at least if it is a display problem or a completely freeze of machine, just trying ssh'ing into, I'll let you know.
I don't remember to have this problem using opensource Radeon driver, so this seems related on these drivers.
Does this problem happen to you too?
Thanks in advance.

---

### Post by este.el.paz on 2012-09-18
@scognito:

I can confirm the issue with, is it just Mac's?, failing to revive from "suspend" . . . I've posted questions about this and have yet to receive any solutions, but it seems like a Linux or Debian issue as I've had a number of different Debian based systems on three computers, an iMac G4 w/XuLu 12, iBook G4 w/Debian Wheezy, and a MBPro w/LMDE all set up dual boot with OSX.  Whenever I'm finished using the Xu/Lu, or any of the Linux side partitions I have to restart and boot back into OSX, otherwise I have to shut the computers down.  The PPC FAQ sections on this problem make it seem like it is a deficiency of RAM that is the problem, but the MBPro has plenty of RAM and still "Suspend" is not something that can "wake up" with the tap of a key or click of a mouse.  It would be nice to see if there is a simple solution to this problem.

On the "F-keys" not working, I saw a post here yesterday where somebody said that the "new aluminum Apple keyboard doesn't do the F-key commands" . . . I can confirm that as well, as I have the newer aluminum keyboard on my G4 iMac . . . and have yet to get the F-key commands to work as advertised . . . .

e.e.p.

---

### Post by scognito on 2012-09-19
As for the F-keys they works like a charm. What I mean is that they don't work when the machine freezes.
I'll investigate further, thanks!

---

### Post by este.el.paz on 2012-09-19
@scognito:

Ah, OK, well anyway, the main problem is this failure to revive from suspend, it's less important whether all or none of the keys work if all you/I can see is a black screen that is unresponsive to any inputs except the "Off" button . . . requiring re-booting each time that the Linux side is used . . . .  And that makes it "slow" . . . yes?

e.e.p.

---

### Post by c4c on 2012-09-19
[FONT=Arial]It[/FONT][FONT=Arial]’[/FONT][FONT=Arial]s not just Mac. Many machines have problems with both suspend and[/FONT] [FONT=Arial]hibernate[/FONT][FONT=Arial].[/FONT] Granted, I am setting up 5-10 year old computers for the most part; but it definately crosses through AMD, Pentium, PowerPC... [FONT=Arial]I[/FONT][FONT=Arial]’[/FONT][FONT=Arial]ve taken to r[/FONT][FONT=Arial]emov[/FONT][FONT=Arial]ing[/FONT][FONT=Arial] both options from the Power Menu[/FONT][FONT=Arial] so there is no chance anyone will accidently do either.[/FONT]

```
gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.upower.policy
```


[FONT=Arial]There are only two sections in this file; the first for Suspend, the next for Hibernate.[/FONT]
  [FONT=Arial]Almost at the end of each section is a line that reads:[/FONT]**[FONT=Courier New][SIZE=2]<allow_active>yes</allow_active>[/SIZE][/FONT]**[B]
[FONT=Arial]Change "yes" to "no" in the 1st section to disable the Suspend option.
[/FONT][/B]**[FONT=Courier New][SIZE=2]<allow_active>[/SIZE][/FONT]****[FONT=Courier New][SIZE=2][COLOR=#006600]no[/COLOR][/SIZE][/FONT]****[FONT=Courier New][SIZE=2]</allow_active>[/SIZE][/FONT]**[B]
[FONT=Arial]------------
[/FONT][/B]**[FONT=Courier New][SIZE=2]<allow_active>yes</allow_active>[/SIZE][/FONT]**[B]
[FONT=Arial]Change "yes" to "no" in the 2nd section to disable the Hibernate option.
[/FONT][/B]**[FONT=Courier New][SIZE=2]<allow_active>[/SIZE][/FONT]****[FONT=Courier New][SIZE=2][COLOR=#006600]no[/COLOR][/SIZE][/FONT]****[FONT=Courier New][SIZE=2]</allow_active>[/SIZE][/FONT]**
  [FONT=Tahoma][SIZE=2][COLOR=#000000]
Suspend and/or Hibernate will be gone out of the Power menu whenever you restart. If you want to change back, just change the no to yes again.
[/COLOR][/SIZE][/FONT]

---

### Post by este.el.paz on 2012-09-19
@c4c:

I'm not sure if the OP wants to turn off the feature, but as the SP (second poster) I appreciate the reply and the insights . . . certainly the iMac & iBook are in the 5 - 10 + year range . . . .  Personally, I'd like to "fix" the suspend feature . . . but since I now know that "suspend" probably doesn't work I can just not click on it . . . .

e.e.p.

---

### Post by 2blue on 2012-09-20
12.04 is the first time suspend and hibernate works flawlessly for me in both Ubuntu and Lubutu. (I`m no dual booting though). I know these functions can be fuzzy, but you have to make a generous swap for them to work.

---

### Post by este.el.paz on 2012-09-20
@2blue:

Thanks for the post, glad to hear that Suspend is working for somebody; I do have 12.0.4 Xu/Lu on the iMac, but I guess it's not meeting the criterion for "generous swap" or swap that is enough to get suspend to work??  It has 512??MB of RAM so I have 1 GB of swap, but no joy in terms of Suspend.  And, the machine where I have lots of GB's of swap, 7 or 8 I believe, it must be an area where Ubun/Xubun/Lu has dealt with the problem of Suspend successfully but LMDE/Debian is leaving that for another day?  No joy for Suspend revival there . . . so close, but . . . .

e.e.p.

---

### Post by 2blue on 2012-09-21
My iBook orginally had 512MB RAM and lubuntu installer made 1.5GB swap by default. Advice vary on how much swap is needed, but in this case it is three times RAM. A few days ago I installed 1GB RAM extra and swap/hibernation still works fine. System still hardly ever use more than 400-500GB RAM regardless of applications running. 

I have previously wondered if swap partitions can be randomly accessed by whatever os you boot, and sort of  mess up a bit? I know live CDs can grab swap partitions if there are any, which surprised me a bit.

Just in case: You have activated and set powermanager to work with suspend? I just remembered I had messed with the settings for battery and screen before it all worked properly.

---

### Post by este.el.paz on 2012-09-21
> **2blue said:**
> My iBook orginally had 512MB RAM and lubuntu installer made 1.5GB swap by default. Advice vary on how much swap is needed, but in this case it is three times RAM. A few days ago I installed 1GB RAM extra and swap/hibernation still works fine. System still hardly ever use more than 400-500GB RAM regardless of applications running.

This post is pretty interesting, agreed, it doesn't seem that the advice on swap is "standardized" as it seems that the Debian based installers that I've mostly used are going for 2x RAM, but, in watching the System Monitor I actually don't recall seeing much if any swap being used . . . the line just flopped along slightly above zero.

> I have previously wondered if swap partitions can be randomly accessed by whatever os you boot, and sort of  mess up a bit? I know live CDs can grab swap partitions if there are any, which surprised me a bit.

Yeah, this also is interesting in terms of dual-booting, some things good and some things odd.  When I was running MintPPC on my iBook I didn't have too many problems because it uses the "radeon" video driver, but, during one update/upgrade I got a flash of an error screen saying "Low Disc space--148MB available" . . . something like that, and I had a small partition to begin with, 6 GB, split between root/home and swap, but I didn't understand why there was "no room" . . . checked GParted or Disc analyzer and "somehow" a "small" 250 MB partition had been cut off the root/home . . . and that was my wiggle room for space . . . and, I couldn't get that partition to meld back using GParted . . . had to wipe the HD and re-install; I went with straight Wheezy at that point because it shaved an hour off the install, and haven't had any issues yet.  Possibly that might have been a "side effect" of dual booting?????  Don't know.

> Just in case: You have activated and set powermanager to work with suspend? I just remembered I had messed with the settings for battery and screen before it all worked properly.[/QUOTE]

This might be most relevant to my problem--set powermanager????? to work with Suspend?????  I probably have not done that in the Xu/Lu system since it's still very new and I haven't had time to mess with it . . . no Linux system has lived in the iMac for longer than a couple of months before it either imploded or an upgrade took out the video driver . . . .  I'll try to look at that in the next few days and if it doesn't seem obvious maybe the SP will post back asking for a "handout" on how to set the powermanager to work with Suspend.  That would be great if it would be a simple fix and the system would revive with a click of the mouse . . . thanks for the idea.

e.e.p.

---

### Post by tumutanzi.com on 2012-09-21
> **scognito said:**
> Hi,
I'm using an iMac (12,2) with Ubuntu 12.04 64 bit, standard kernel (3.2) and latest AMD drivers (downloaded from AMD site).
Sometimes when monitor turns off (because it went in sleep after x minutes) I can't turn the monitor on anymore.
Sometimes it works (moving mouse), sometimes don't. I don't know if it is related to some level of "sleep": seems (but didn't verify) that if it is in sleep mode for 5 minutes, I can wake it up, but if it is in sleep for an hour or so, I can't.
Also ALT-F1/F2/... doesn't switch to virtual console.
I've installed ssh to see at least if it is a display problem or a completely freeze of machine, just trying ssh'ing into, I'll let you know.
I don't remember to have this problem using opensource Radeon driver, so this seems related on these drivers.
Does this problem happen to you too?
Thanks in advance.

I have never used iMac, so do not have any info for you. Good luck. You are really a Ubuntu fan.

---

### Post by 2blue on 2012-09-21
I cannot remember exactly what I did, but suspend didn`t work on first boot ups after install. I didn`t pay much attention to it at the time, mostly focusing on making battery monitor working in lxde (which it sort of arguably does now), but at least after some simple config setup under "power manager preferences" it has worked fine since. 12.04 has been stable as long as I have had it. No update or change to the system has caused any horror with drivers or graphics luckily. I have some smaller issues I haven`t yet manage to iron out, but I am working on them. I think we have to stick with lubutu or whater distro we choose to figure out the fixes and work arounds, not to mention feedback and bugreports to developers. 

In relation to RAM and swap; I wasn`t sure it would make any difference adding more RAM since I never could make the system use all 512 what ever applications I ran simultaneously. Swap kicked in but I don`t think I ever noticed more than 30-100 MB used. My theory now is system some free ram space to have optimal usage of it. When system doesn`t have to incorporate swap when running it runs a tad bit smoother and lighter. Swap should probably ideally only be for suspend and hibernation mode.

Edit: When waking up from suspend I sometimes have to click twice on enter (any key really) to get a login window asking for password before session runs again. Sometimes I get desktop directly, not sure why there is an inconsistency but I never have to reboot or anything like that.

---

### Post by este.el.paz on 2012-09-21
@2blue, et al:  

I did take some time to fiddle with the powermanager, in this case the "xfce powermanager" even though I've been using lxde in the iMac . . . and I could set the buttons, "If I click on Suspend what should I do?" and "Nothing" is the default, so I changed it to "Suspend" . . . .  There was another button there that was checked by default--"Disable Display Power Management Signaling" and when I moused over it the window said, "(DPMS) e.g., don't attempt to switch off the display or put it in sleep mode."  When I unchecked it I saw the display kind of flash, so something must have happened, but I checked it again.  But,after doing those steps when I "suspended" the iMac the screen went black but the hardrive kept spinning and then did not revive . . . .  Would that or should that DPMS button be unchecked?

On a more interesting front, I ran "update/upgrade/dist-upgrade" in the iBook, didn't check before, but after I rebooted I tested the Suspend and revive from Suspend and it actually revived, checked twice reviving with mouse-click and it worked, and one time I had to use the keyboard space bar to get it to revive.  The iBook has always been able to figure out what Linux is trying to do better than the iMac . . . right now as I said the iBook is dual-boot OSX & a straight, no chaser, Debian Wheezy OS . . . so that is very helpful, now if I can just get the iMac thinking along the same lines . . . .

e.e.p.

---

### Post by abtabt on 2012-09-22
hello 

este.el.paz

can you post your xorg.conf for imac and ibook

---

### Post by scognito on 2012-09-22
My iMac was not used for 4 hours and when switched back moving mouse it didn't hang.
Probably it didn't hybernate, I don't know. I don't even know if it hybernates after some hour of not using...I'm a bit confused :)
I'm using KDE, don't know if it could be useful.

---

### Post by 2blue on 2012-09-23
It should be easy to know if the white iBook suspends: the blinking light in the front goes on (i think all computers have some kind of blinking light indicator), screen goes black, fans and all sounds are off. When  you reasume something "clicks" in and you might even have to log in with password. 

When you hibernate comptuer in all apparence shuts down, and you have to press on/off button to reasume, but you continue with what ever aps you had running. It takes a bit longer to get back to the running desktop than suspend. A full shut down kills all aps. 

At least that is how it behaves here.

---

### Post by scognito on 2012-09-23
I have an iMac, not macbook...and it doesn't have any led :/

---

### Post by este.el.paz on 2012-09-23
> **abtabt said:**
> hello 

este.el.paz

can you post your xorg.conf for imac and ibook

@abtabt:  Thanks for your interest, busy weekend . . . the iMac has a simplified xorg.conf file, set up to run with the "nv" driver, which so far is the only extant driver that runs the display, fbdev was removed from the kernel not too long ago.  The iBook has a longer xorg.conf file, but right now seems like "suspend" might be working, so rather than get the iBook out right now, I'm just posting the xorg.conf file for the iMac, it's easier and possibly relates more to the OP scognito's problem with the iMac . . . .

e.e.p.

---

### Post by abtabt on 2012-09-24
i hola  este.el.paz

try this xorg.conf


rename to xorg.conf and copy to /etc/X11

and see if this will solve our problem

---

### Post by este.el.paz on 2012-09-24
> **abtabt said:**
> i hola  este.el.paz

try this xorg.conf


rename to xorg.conf and copy to /etc/X11

and see if this will solve our problem

@abtabt:  hola back atcha . . . and thanks for the xorg.conf file . . . but, I'm a little hesitant to change the file since getting the display working on the iMac has been a lot of work, and the xorg.conf file I have posted is the one that works.  Also, the "nouveau" driver so far has not worked with the iMac, the "fbdev" driver did work, but was removed from the kernel . . . .  

But, what part of your xorg.conf file do you feel would help with the "suspend" function, and perhaps that part could be added in to what I've got now?  I know I could always change it back, but, this process has been going on since Dec. '11 and for the most part the Xu/Lu option has been good, and fine tuning the Suspend function is just the gravy . . . but I don't want to give up my GUI display for a little gravy.  BTW, I tried to get the iBook xorg.conf file opened and posted, but in Wheezy "there is no application to open it" . . . and I tried a few tricks, but they didn't work--anyway, revive from Suspend is working in Wheezy iBook system.

e.e.p.

---

### Post by abtabt on 2012-09-26
este.el.paz

this xorg.conf file comes from a imac 800 like ours

with lubuntu 12.04 and will not break our imac if so 

only go back to the old one 


in debian have you tried  

code
sudo nano /etc/X11/xorg.conf
 
or use filemanager to copy and put .txt after xorg.conf

like xorg.conf.txt and post it

abtabt

---

### Post by este.el.paz on 2012-09-26
> **abtabt said:**
> este.el.paz

this xorg.conf file comes from a imac 800 like ours

with lubuntu 12.04 and will not break our imac if so 

only go back to the old one 


in debian have you tried  

code
sudo nano /etc/X11/xorg.conf
 
or use filemanager to copy and put .txt after xorg.conf

like xorg.conf.txt and post it

abtabt

@abtabt:  Thanks very kindly for the follow-up . . . I'll try to play around with it a bit, but the next 3-4 days I'm going to be away from the iMac so it probably won't be right away.  I have to brush up on my Terminal commands as far as moving new xorg.conf into place and then moving it back out if I want to revert, etc.  It's not a big deal I know, but it's just the fiddling . . . right now I'm trying to get LM13 to boot up on my MBPro . . . GRUB seems to have taken a dive lately????

e.e.p.

---

### Post by este.el.paz on 2012-09-30
@abtabt:

Haven't forgotten about this, but too much work this week . . . brain fry . . . spent the extra effort getting GRUB directed to the right "dev" . . . LM13 MATE is now running on my MBPro!!!!!  I'll get back to this next week . . . probably just try the xorg.conf file you posted, see if that fixes suspend.  I'll post back when I have something actually done.

e.e.p.

---

### Post by scognito on 2012-10-06
I don't know what happened, but since my last post it didn't happen anymore :)
Maybe some fix on some kernel/X update? :)

---

### Post by este.el.paz on 2012-10-06
@scognito:

That's great, I just realized today that tomorrow I'm having to work so I won't be able to play around with the xorg.conf file or other stuff . . . but, as of a few days ago Suspend is not something that my iMac can wake up from . . . yet . . . even did some upgrades . . . .  Anyway, I'll just have to push the investigation(s) down the road . . . .  In the meanwhile I took a few minutes to try to get sound working following the PPC FAQ . . . started by deleting the /modprobe.d/blacklist local file which contained a list of blacklisted sound drivers??? . . . a deleted a "snd" item from /etc/modules . . . as one of the options in the FAQ suggested . . . didn't seem to provide sound, so I'll be adding the blacklisted items back and adding the snd back into modules . . . and then trying to get suspend going, lots to do for the iMac . . . .  : - ))))

e.e.p.

---

### Post by abtabt on 2012-10-07
Este.el.paz

Post our lsmod file please

---

### Post by este.el.paz on 2012-10-07
> **abtabt said:**
> Este.el.paz

Post our lsmod file please

@abtabt:

Appreciate the follow-up, just letting you know the latest situation, looks like my horsie is again pulling up lame and will be a DNF once again.  I just tried to boot the Xu 12.0.4 system to check on lsmod and wound up with multiple problems, problems getting Yaboot window to show up, problems getting gdm log in window to stay, problems with once getting passed gdm log in then mouse didn't work and no toolbar, problems then getting passed xubun splash window with subsequent kernel panic, problem with kernel panic before the Yaboot window . . . problem with showing a single user window that wouldn't accept my password to get into CLI . . . went thru 5 cold boots essentially ending in kernel panic.  Gave up, when I tried to boot OSX, there also was a kernel panic and had to restart . . . thought it might be the old iMac giving up its life force, but seems like it's OK for now . . . don't know why kernel panics in Xubun would carry over to OSX?  But, this has been the history of trying to get anything in the Linux realm to run on the iMac for longer than a few months, seems to be doing OK, then the system seems to start degrading??  kernel panics start and eventually the CLI even goes away.  There was something about "starting pbbuttonsd 0.7.9 Unknown powerbook; speech-dispatcher disabled, edit; starting NTP-server-ntpd-kernel panic 3 or 4" on the Xubuntu splash window.

I did do an update/upgrade on Friday night, couple night back using "sudo aptitude" and I rebooted then and everything seemed to be OK, I can't remember if I installed "powerprefs" in the iMac following a comment in the PPC FAQ about either getting suspend to work, but I didn't adjust anything in the GUI powerprefs window when it opened . . . so I don't know if somehow one of the upgrades has messed with my "nv" driver compilation . . . but once again there is a problem.  Seemed like Xu/Lu 12.0.4 got me closer to something stable . . . will have to see on another day if I can get it working, if it's a hardware issue, or just try what will be the 6th or 7th re-install . . . .  Maybe Tuesday I'll again have a moment to play around . . . the sound issue goes to the back burner for now.

e.e.p.

---

