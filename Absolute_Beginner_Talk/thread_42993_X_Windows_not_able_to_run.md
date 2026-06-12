---
title: "X Windows not able to run"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-06-20
I have posted a similiar request into the hardware section, sorry but I never saw the beginners section at the bottom of the page! It should be at the top!!!

I have a Intel system, GEV something and the hardware list is compatable with Linux, or so it says on the Intel website. I am running XP and have installed UBUNTU on a spare hard drive. The installation went well, I can choose between the two OS's. 

When I re-start in Ubuntu I was asked to pick my video driver, which unfortunately is not listed under the default selections, so I picked one that sound familiar. Then you get a long list of program updates or something and eventually it asks me for my login. At this stage, I get a message stating "Cannot start X Windows" (What is Xwindows?) The help files have very little info. I find a lot of commands, and not knowing any commands in Linux, I typed in what is listed on internet. I first had to do the "suso" thingy, was asked a new password, did that and it prompts me with the $ sign. 
Typing in the command that is supposed to re-install the video driver, (sorry I don't have the exact command with me at the moment...) it comes back with "Access denied."

I tried changing the video driver by re-installing the whole CD, and then select another video driver, but after all that time it still won't work. I simply don't know any command lines, and was under the impression that Ubuntu was a GUI? But if I got it right from various postings, the GUI comes up only if the Xwindows work. 

The main problem is, how do I get the Xwindows and video driver working? I prefer to use a GUI first and learn the command lines once I am into it. My wife and kids won't be able to learn command lines pretty soon!!!

Before you refer me to some beginners guides, I'm already looking at them, but so far its a dark sinister world. I can run only XP or Ubuntu, so I can't look on the web while using Linux, and while looking on the web using XP. I can't run commands on Linux! And I doubt if a want to print all those files, cause that is the only way I would be able to look at those files for the moment.

Sorry for this VERY long posting. Answers may be short....!!!!

---

### Post by twoseids on 2005-06-20
Hi GrootBrak,

This sounds similar to a problem I had when installing Ubuntu onto my wife's machine very recently.  I'm pretty much a newbie like you.

You can read my question (which I ended up answering myself) [here](http://ubuntuforums.org/showthread.php?t=39734).  I'm not sure what kind of computer you have, so maybe this won't work.

But it's a short answer!

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=GrootBrak]
The main problem is, how do I get the Xwindows and video driver working? I prefer to use a GUI first and learn the command lines once I am into it. My wife and kids won't be able to learn command lines pretty soon!!![/QUOTE]

Sounds like you have a bunk install CD. Ubuntu is very sensitive (more than a music CD) so a bunk install cd will lead to Xserver problems. If you can, try reburning the ISO at lower speeds.

---

### Post by GrootBrak on 2005-06-20
Thanx. I doubt if my system will work, cause the BIOS is from Dell and I have an Intel D915GEV system board. All hardware except for the disks and an extra disk controller is onboard. I have three HDD now, one used just for Linux.

Anyone want to look it up, Intel will show that it is Linux compatible. But, the chipset is unknown to Linux.

Regards

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=GrootBrak]Thanx. I doubt if my system will work, cause the BIOS is from Dell and I have an Intel D915GEV system board. All hardware except for the disks and an extra disk controller is onboard. I have three HDD now, one used just for Linux.

Anyone want to look it up, Intel will show that it is Linux compatible. But, the chipset is unknown to Linux.

Regards[/QUOTE]

I recently had a problem with a Dell with intel graphics. Turned out that when Dell shipped the thing, they hacked XP to work because the BIOS was messed up. A quick reinstall of Windows to update the motherboard firmware, and things worked great in Ubuntu.

---

### Post by GrootBrak on 2005-06-20
[QUOTE=poofyhairguy]Sounds like you have a bunk install CD. Ubuntu is very sensitive (more than a music CD) so a bunk install cd will lead to Xserver problems. If you can, try reburning the ISO at lower speeds.[/QUOTE]
 Thanx, but that is not the problem, my CD rewriter was/is giving me some hassles lately, but the I burned at the Science centre. But to be safe, I will burn at my much slooooower rate of only 16x!!! Everything else seems to have worked great. What is that command that is used to re-install hardware? The one I have is base-config. But there is nothing in there that have anything to do with my video system.

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=GrootBrak] What is that command that is used to re-install hardware? [/QUOTE]

For video hardware:

> sudo dpkg-reconfigure xserver-xorg

---

### Post by GrootBrak on 2005-06-20
[QUOTE=poofyhairguy]For video hardware:[/QUOTE]
 Thanx. Just tried it. Now I get the following reply. "Package Xserver-org is not installed and no info is available. Use DPKG --info **blah blah** ending with xserver-xorg is not installed"

BTW Do you get paid to answer these crazy questions? I sure as heck will be crying on my PC by now if it were not for your attemps to humor me!!!

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=GrootBrak]
BTW Do you get paid to answer these crazy questions? I sure as heck will be crying on my PC by now if it were not for your attemps to humor me!!![/QUOTE]


No I do it for fun. I like Ubuntu and this is my part in the whole thing.

Try this command:

> sudo apt-get install ubuntu-desktop

tell me what it does.

---

### Post by GrootBrak on 2005-06-20
[QUOTE=poofyhairguy]No I do it for fun. I like Ubuntu and this is my part in the whole thing.

Try this command:



tell me what it does.[/QUOTE]
 I have re-burned and just finsished re-installed a CD for a much slower approuch as you suggested. Now it looks a bit different, but Xwindows still is not running. I just used the command as above, and I get a screen full of "Depends: **program** is not going to be installed"
The last line ends as such.
"E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)."

I AM SO LOST.... I get the hunch I should take my whole PC to Mark Shuttleworth...

Any more ideas?

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=GrootBrak]I have re-burned and just finsished re-installed a CD for a much slower approuch as you suggested. Now it looks a bit different, but Xwindows still is not running. I just used the command as above, and I get a screen full of "Depends: **program** is not going to be installed"
The last line ends as such.
"E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)."

I AM SO LOST.... I get the hunch I should take my whole PC to Mark Shuttleworth...

Any more ideas?[/QUOTE]


Sure. Lets try what it says to do:

> sudo apt-get -f install

I'll stay with you on this thing....

---

### Post by GrootBrak on 2005-06-20
[QUOTE=poofyhairguy]Sure. Lets try what it says to do:



I'll stay with you on this thing....[/QUOTE]
 It show "unpacking evolution (from ..../evolution_2.0.2-ubuntu1_i386.deb) .....
then a few "hdb: ide_intr: huh? expected NULL handler on exit"
This process takes quite a while.
Then I get "dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error"
A few more lines saying more or less the same thing follows.
Near the end I get this
"Errors were encountered while processing:
/cdrom/pool/main/e/evolution/evolution_2.02-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Sorry for being such a sorry ass, but how will I know the problem is not with my copy of Ubuntu? Though I still doubt it. I toke some notice of the messages the last time I installed the complete CD, the only error (non OK) I got was something in the line of "modprobe fatal error" but it was too fast to get everything.

I checked under the base-config and found a lot of the "installed" programs is also listed under the "not installed" programs as well. Where on earth have I lost it?

Any ideas would be exremely helpfull, so far I have learned more than on any website or from the Ubuntu CD, but alas, I still come short!

Thanx

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=GrootBrak]
Any ideas would be exremely helpfull, so far I have learned more than on any website or from the Ubuntu CD, but alas, I still come short!

Thanx[/QUOTE]

I'll keep helping you...quick question 

Do you have broadband?

If you do I suggest this.

Put in the Ubunu install cd. At the first screen instead of hitting enter type "server" and hit enter.
Then go through the install as normal. It will do an Ubuntu base install and take you to the command line.

There enter this command:

sudo pico /etc/apt/sources.list

A file will come up. Put two pound sighs (#) before the first line you see that begins with the phrase "deb." Later in the line it says something like "hoary cd"

Then you will notice other lines that begin "deb" with pound signs in front of them. Delete those pound signs.

You all telling Ubuntu to use the server to setup your box, not your CD.

Then hit the control button and "x" and the same time. Tell it to save.

Enter in these lines:

> sudo apt-get update

sudo apt-get install ubuntu-desktop

Then you will notice

---

### Post by GrootBrak on 2005-06-20
[QUOTE=poofyhairguy]I'll keep helping you...quick question 

Do you have broadband?

If you do I suggest this.

Put in the Ubunu install cd. At the first screen instead of hitting enter type "server" and hit enter.
Then go through the install as normal. It will do an Ubuntu base install and take you to the command line.

There enter this command:

sudo pico /etc/apt/sources.list

A file will come up. Put two pound sighs (#) before the first line you see that begins with the phrase "deb." Later in the line it says something like "hoary cd"

Then you will notice other lines that begin "deb" with pound signs in front of them. Delete those pound signs.

You all telling Ubuntu to use the server to setup your box, not your CD.

Then hit the control button and "x" and the same time. Tell it to save.

Enter in these lines:



Then you will notice[/QUOTE]
 No broadband. I am using my PC to install Ubuntu to and my work laptop to read this mail with XP. I use a cellphone for internet access. Sorry for the hassles. 

Thank you SOOOO much for your effort tonight. (You do know its evening already in SA?!!!)
Will have to sign off now. Will try and be online tomorrow night as well.
Regards

---

### Post by GrootBrak on 2005-06-21
[QUOTE=GrootBrak]No broadband. I am using my PC to install Ubuntu to and my work laptop to read this mail with XP. I use a cellphone for internet access. Sorry for the hassles. 

Thank you SOOOO much for your effort tonight. (You do know its evening already in SA?!!!)
Will have to sign off now. Will try and be online tomorrow night as well.
Regards[/QUOTE]
 I am back at my office. Where can I download the files? I do not have Linux at the office. I have SUSE and Debian as well on CD's. Is there anyway I could use those in stead of Ubuntu or re-downloading the complete files? Not that I do need XP as well for the time being.
Regars

---

