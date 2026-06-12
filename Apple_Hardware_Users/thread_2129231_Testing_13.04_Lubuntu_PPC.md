---
title: "Testing 13.04 Lubuntu PPC"
date: 2013-03-25
forum: Apple Hardware Users
---

### Post by phillw on 2013-03-25
Hi folks,

the beta 1 of the Desktop for PPC got passed [http://iso.qa.ubuntu.com/qatracker/milestones/261/builds](http://iso.qa.ubuntu.com/qatracker/milestones/261/builds) We are now approaching the beta 2 testing, this is the usual call to anyone who can test (The current daily images can be found via [http://iso.qa.ubuntu.com/qatracker](http://iso.qa.ubuntu.com/qatracker) which will also host the testing of beta 2). Yes, some of the long suffering bugs are still there. On the bright side, I've now been made aware of a mystical beast called the PPC kernel team. Whilst this revelation came too late for 13.04, I am hopeful that once 13.04 is out we may be able to lay to rest [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1066435](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1066435) which would be nice. In the meantime, we need to get a release out so the we can go nag the developers to look at some of the bugs that seem to rumble on, release after release.

Please have a read of [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing) and [https://wiki.ubuntu.com/Lubuntu/Testing/PPC%26Mac64](https://wiki.ubuntu.com/Lubuntu/Testing/PPC%26Mac64) If you are able to test, please add your machine specifications to the area pointed to on the second link and ensure you record your tests on the iso-tracker!

Regards,

Phill.

---

### Post by str8bs on 2013-04-05
@Phil,
You mentioned desktop ISO.
Do you have a preference of alternate vs. desktop iso being tested? (20130403 vs. 20130403.1 currently)

---

### Post by phillw on 2013-04-05
> **str8bs said:**
> @Phil,
You mentioned desktop ISO.
Do you have a preference of alternate vs. desktop iso being tested? (20130403 vs. 20130403.1 currently)


Hi, only the desktop iso made it to beta2. The dailies will resume tomorrow. Hopefully both will make final, but that depends on people testing them!

[https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes/Beta2/Lubuntu](https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes/Beta2/Lubuntu)

Regards,

Phill.

---

### Post by este.el.paz on 2013-04-08
> **phillw said:**
> Hi, only the desktop iso made it to beta2. The dailies will resume tomorrow. Hopefully both will make final, but that depends on people testing them!
[https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes/Beta2/Lubuntu](https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes/Beta2/Lubuntu)
Phill.

@Philw:

I will try to test this beta2 on my PPC iBook G4 as the desktop DVD/CD in the next few days . . . and see if it boots, etc.  Don't have a spare place or time to go for the install.  Will this 13.04 be the next LTS system?

e.e.p.

---

### Post by phillw on 2013-04-08
> **este.el.paz said:**
> @Philw:

I will try to test this beta2 on my PPC iBook G4 as the desktop DVD/CD in the next few days . . . and see if it boots, etc.  Don't have a spare place or time to go for the install.  Will this 13.04 be the next LTS system?

e.e.p.

13.04 is not an LTS for any team, next one on the horizon is 14.04. The email thread on lubuntu-quality, I do endeavour to keep updated. But, for forum users, I will sumarise it below.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

> [FONT=arial]as I've previously mentioned, this is something that needs fixing at kernel level. As the reason ppc iso is over sized is due to having lots of kernels in it, I had entered early discussions so that lubuntu-ppc-desktop (and alternate) only ship with the kernel(s) needed for the various desktops we support. It is very unlikely that this will be resolved before 13.04 lands (we've passed too many freezes and it is not a minor undertaking -- although it has not been ruled out for 13.10). when this is done, we may even find out which kernel(s) to alter for which chipset!
[FONT=Verdana][/FONT]
[/FONT]

Regards,

Phill.

---

### Post by este.el.paz on 2013-04-14
@Philw:

Not too much time to figure out how to register my iBook G4 with radeon driver, so posting here.  Downloaded the Beta2 desktop for PPC today, burned in xfburn . . . and then tried to boot it . . . not too successful.  First time used "live" . . . got to the lubuntu 13.04 splash window . . . good resolution . . . then after a minute it tried to load and got the "instruction dump" stuff, ending with "fixing recursive fault but reboot is needed."  Restarted and used "live-powerpc driverupdates-powerpc" . . . and got the same result.  3rd time used "live video=ofonly" . . . got a low resolution splash, much like when trying for something on the iMac before the xorg.conf file was loaded . . . and then it went to a black screen . . . the CD drive was not working . . . so it probably KP'd it . . . .  No more time for it today.

There was a "software detected, would you like to open this using 'package manager'?" . . . didn't know if that's what I should have done, just went for reboot holding C key to boot the CD/DVD as I've usually done with LiveDVD . . . .

e.e.p.

---

### Post by michiganmac on 2013-04-14
> **este.el.paz said:**
> @Philw:

Not too much time to figure out how to register my iBook G4 with radeon driver, so posting here.  Downloaded the Beta2 desktop for PPC today, burned in xfburn . . . and then tried to boot it . . . not too successful.  First time used "live" . . . got to the lubuntu 13.04 splash window . . . good resolution . . . then after a minute it tried to load and got the "instruction dump" stuff, ending with "fixing recursive fault but reboot is needed."  Restarted and used "live-powerpc driverupdates-powerpc" . . . and got the same result.  3rd time used "live video=ofonly" . . . got a low resolution splash, much like when trying for something on the iMac before the xorg.conf file was loaded . . . and then it went to a black screen . . . the CD drive was not working . . . so it probably KP'd it . . . .  No more time for it today.

There was a "software detected, would you like to open this using 'package manager'?" . . . didn't know if that's what I should have done, just went for reboot holding C key to boot the CD/DVD as I've usually done with LiveDVD . . . .

e.e.p.

I use the following at the yaboot prompt to boot my 12" iBook G4, 1.33Ghz, 1.5GB ram, ATI Mobility Radeon 9550:

live video=radeonfb:1024x768-32@60

For my Powermac G4, MDD FW800, 2GB Ram, Radeon 9800 Pro (flashed PC card) 1920x1080 monitor:

live video=radeonfb:1920x1080-32@60 snd-powermac.blacklist=yes

Hope this helps.

---

### Post by este.el.paz on 2013-04-15
> **michiganmac said:**
> I use the following at the yaboot prompt to boot my 12" iBook G4, 1.33Ghz, 1.5GB ram, ATI Mobility Radeon 9550:
live video=radeonfb:1024x768-32@60
For my Powermac G4, MDD FW800, 2GB Ram, Radeon 9800 Pro (flashed PC card) 1920x1080 monitor:
live video=radeonfb:1920x1080-32@60 snd-powermac.blacklist=yes
Hope this helps.

@Michimac:

Thanks for the boot params . . . I'll give it a try later, so far I haven't had to use any boot params to get the iBook booted up for a number of systems.  The iMac, however, I needed them, plus other stuff . . . .

e.e.p.

---

### Post by michiganmac on 2013-04-15
You're very welcome!

---

### Post by powerpcliberation on 2013-04-15
I have been running 13.04 since late January and have always been impressed.  I abandoned 12.10 for it.  12.04 will be my main squeeze for a while yet but 13.04 is very promising on the horizon.

---

### Post by este.el.paz on 2013-04-16
@Philw:

Testing report:
Thanks to michiganmac's boot parameters I was able to boot the Lu 13.04 Beta2 desktop for powerpc in my iBook G4 933MHz with 646? MB RAM burned what listed as 800MB .iso file to DVD . . . .  Took awhile to get passed the black screen after the splash window . . . got to the new? LXDE desktop image . . . it was very dark across the top of the screen, but the windows that launched on top of it were fine.  Launched Audacious . . . one of the few problems that showed: error:  ALSA error--no mixer element found & snd_mixer_attach failed--no such file or directory.

Abiword--OK, able to save a document.  Terminal--OK, ran update/upgrade OK.  Firefox--OK, but the color in the browser was off to the blue side, i.e., no red fox in the FF icon--it was blue.

Wired connection was OK, but, no surprises--no wireless.  Otherwise, fonts clear, icons look good.  File manager worked well.  Overall looks nice . . . .

e.e.p.

---

### Post by phillw on 2013-04-23
Hi folks, a bit of good news! the iso's for ppc desktop and alternate should now be CD sized. Please do test, file and update the known bugs. [http://iso.qa.ubuntu.com/qatracker/milestones/269/builds](http://iso.qa.ubuntu.com/qatracker/milestones/269/builds)
 
This may not seem like a massive step forward, but it was only achieved by the number of people testing who proved that PPC is not dead. There is also an over-sized ISO available via kubuntu, if it gets tested the kde team are willing to release it.

Your fate is in your own hands. For any testers coming in, please have a read of the quick guide to testing at [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing) and register your machine on the Mac / ppc area at [https://wiki.ubuntu.com/Lubuntu/Testing/PPC%26Mac64](https://wiki.ubuntu.com/Lubuntu/Testing/PPC%26Mac64)

Thanks,

Phillw.

---

### Post by dgsa on 2013-05-02
Hello all, I'm new to linux on mac/ppc but I was reading about it some on [http://ppcluddite.blogspot.com](http://ppcluddite.blogspot.com) and elsewhere so I thought I'd give lubuntu a try.  I didn't get very far.  On my 12" powerbook I can't get past a blank black screen.  I've registered a few new accounts and mailing lists today and spent quite a while searching and reading documentation online.  I'm guessing there is some problem with the graphics drivers.  I created a bug here:

[https://bugs.launchpad.net/bugs/1175736](https://bugs.launchpad.net/bugs/1175736)

For grins I put the same 13.04 CD I burned in my g4 mac mini and it got further.  It looks like it booted up into some kind of GUI desktop.  I can see a mouse pointer that moves with the mouse but the colors are all jumbled and I can't read anything or really tell what it's doing.

This info is probably not a lot of help to those working on it, but I thought I'd share my experience.  Thank you to those who are trying to keep the ppc platform alive!

---

### Post by phillw on 2013-05-02
> **dgsa said:**
> Hello all, I'm new to linux on mac/ppc but I was reading about it some on [http://ppcluddite.blogspot.com](http://ppcluddite.blogspot.com) and elsewhere so I thought I'd give lubuntu a try.  I didn't get very far.  On my 12" powerbook I can't get past a blank black screen.  I've registered a few new accounts and mailing lists today and spent quite a while searching and reading documentation online.  I'm guessing there is some problem with the graphics drivers.  I created a bug here:

[https://bugs.launchpad.net/bugs/1175736](https://bugs.launchpad.net/bugs/1175736)

For grins I put the same 13.04 CD I burned in my g4 mac mini and it got further.  It looks like it booted up into some kind of GUI desktop.  I can see a mouse pointer that moves with the mouse but the colors are all jumbled and I can't read anything or really tell what it's doing.

This info is probably not a lot of help to those working on it, but I thought I'd share my experience.  Thank you to those who are trying to keep the ppc platform alive!

Hi, as you are trying out lubuntu, I'd ask that you do ask the lubuntu-ppc team directly. I do not have a machine to test on. As the Team Leader for the lubuntu testing team I assure you that the testers on there will be more helpful than certain comments on here.

[https://wiki.ubuntu.com/Lubuntu/Testing/PPC%26Mac64](https://wiki.ubuntu.com/Lubuntu/Testing/PPC%26Mac64)

It does involve joining the mailing list, but as a person wanting to use ppc on lubuntu, you will be welcomed.

Regards,

Phill.

---

### Post by este.el.paz on 2013-05-04
> **dgsa said:**
> Hello all, I'm new to linux on mac/ppc but I was reading about it some on [http://ppcluddite.blogspot.com](http://ppcluddite.blogspot.com) and elsewhere so I thought I'd give lubuntu a try.  I didn't get very far.  On my 12" powerbook I can't get past a blank black screen.  
For grins I put the same 13.04 CD I burned in my g4 mac mini and it got further.  It looks like it booted up into some kind of GUI desktop.  I can see a mouse pointer that moves with the mouse but the colors are all jumbled and I can't read anything or really tell what it's doing.

This info is probably not a lot of help to those working on it, but I thought I'd share my experience.  Thank you to those who are trying to keep the ppc platform alive!

@dgsa:

Welcome to Linux. If you just want the screen that has a working  desktop, you probably have to find out which "Boot parameter" will work  for your computer, and then that needs to be typed into the Yaboot  screen, I believe it's after the flashing underscore cursor that's after  the the word "Boot"??? You'll have to find your way to the "PowerPCFAQ"  which is part of the ubuntu wiki for PPC, and read fully the  suggestions that would apply to your computer, it's very complete set of  instructions. However it is a bit strange if you don't have any CLI at  all, and just go the black screen . . . it would be a different deal if  you got the Yaboot boot window and then got a log in screen . . . which  went to a black screen.

Also, it seems like the Lubuntu 12.04 for PPC might be the better choice  for easy boot . . . so you might try that version first to get the hang  of it.


e.e.p.

---

### Post by gusduenas on 2013-05-04
I have tested the alternate cd and though it installs normal, I cannot go to the desktop and it stalls at the terminal, so far nothing...using a g5 dual 2.0ghz nividia geforce 6600....

---

### Post by str8bs on 2013-05-07
@dgsa Thanks for trying out the install and sharing. People testing on real PPC hardware is really helpful.

Sounds like you've tried quite a bit. As e.e.p mentioned, you may find 12.04 a little easier to get going if you are new to Linux and want a break from troubleshooting.
My advice: The most common trouble on PPC is related to your video card. I would look up your model numbers on apple or everymac web site and then start a thread for each with the name of your video card in the title prefixed with PPC. This makes it easier for people that might have the same hardware know if they are able to help.

Keep in mind that it is all about the community helping each other. None of us are experts and people willing to help will do so where and when they can.

Str8

---

