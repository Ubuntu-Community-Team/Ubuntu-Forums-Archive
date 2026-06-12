---
title: "Question about docks..."
date: 2007-08-17
forum: Apple PPC Users
---

### Post by makinasvp on 2007-08-17
I was curious to know if there's a dock such as AWN compatible with Ubuntu Feisty PPC...
If yes, can someone please post a HOWTO on it? Much appreciated...
Best regards,

-Makina

---

### Post by stmiller on 2007-08-17
There is some info here:

[http://awn.wetpaint.com/page/Ubuntu](http://awn.wetpaint.com/page/Ubuntu)

Looks like their repos are only x86 and x64. So for PowerPC you'll have to compile from source. :(

---

### Post by makinasvp on 2007-08-17
That really blows... :(
It's not fair, nobody likes us powerpc users :(:(  I need a hug... :(

---

### Post by aantn on 2007-08-19
Actually, I was planning on making a ppc repository for the git cutting edge version of compiz fusion. I don't mind also putting awn into the repository. You're going to have to wait two or three days because I'm currently on vacation in the U.S. But I'm taking a plane back to Israel on Wednesday, and should be able to have the repo up and running by the weekend. Please tell me if you're interested.

---

### Post by aantn on 2007-08-19
> **makinasvp said:**
> That really blows... :(
It's not fair, nobody likes us powerpc users :(:(  I need a hug... :(

And hopefully, this will be even better than a hug! :)

---

### Post by makinasvp on 2007-08-20
> **aantn said:**
> And hopefully, this will be even better than a hug! :)

You are my new HERO!!!!!!!!!!!! lol 
I have EVERYTHING that I need running on my iBook G4 with the exception of a dock... Beryl is running smooth, my wireless internet is running smooth, everything is great. Now I need a dock. 
Thank you soooooooooo much for doing this! Hope your flight goes well. :)
:)

---

### Post by dark_harmonics on 2007-08-21
> **aantn said:**
> And hopefully, this will be even better than a hug! :)

Nice! I've tried to build the compiz on my own and miserablely failed. I got all the depencies and libraries and it built correctly but i just CANT GET IT TO WORK! Sorry about the yelling but I usually can figure just about anything out if i try hard enough but this one has sunk my ship man! ARGGHHH!! 

Anyways i hope you have a safe flight back  :lolflag:

btw im using a powerbook g4 and just trying to breathe some life into the thing. What a waste of good hardware...

---

### Post by aantn on 2007-08-24
Ok... I'm back in Israel now. I had a nice flight. Anyway, I'm going to try to compile it later today. Right now I'm using OS X for a few things, but when I reboot into Linux I'll start working on it.

---

### Post by makinasvp on 2007-08-24
> **aantn said:**
> Ok... I'm back in Israel now. I had a nice flight. Anyway, I'm going to try to compile it later today. Right now I'm using OS X for a few things, but when I reboot into Linux I'll start working on it.

HOORAY!!!!!!!!!!!!! Thank you so much aantn!!! Glad your flight was ok.

---

### Post by aantn on 2007-08-25
I ran into some problems and got delayed, but it is compiling as I write this. I expect that there will be one more delay because of the x11-xcb issue, but that shouldn't take too long to solve. I'll post again when its done.

---

### Post by aantn on 2007-08-25
It compiled successfully. Thanks to one of Trevinho's patches, I didn't even have to get x11-xcb working.

I'm testing out the debs on my own computer right now...

---

### Post by aantn on 2007-08-25
Hmm... They don't seem to be working with gnome, but I have a feeling that thats a problem specific to my computer. The debs themselves compiled successfully and I think that its only my config thats messing things up...

---

### Post by aantn on 2007-08-26
Woot! I fixed the problem. I'm running Compiz Fusion right now, and its even running smoothly.  Now I'm trying to set up a repository...

---

### Post by makinasvp on 2007-08-28
You are the greatest!!! I can't wait until I can install AWN!! WOOHOO!!!!!

---

### Post by aantn on 2007-08-28
> **makinasvp said:**
> You are the greatest!!! I can't wait until I can install AWN!! WOOHOO!!!!!

Thank you. 

I'm really sorry about the delay. I have some other work to take care of, and I haven't even had enough time to update my own copy of compiz thats running on my own computer, let alone finish experimenting around with a repository. In Israel, we have Fridays off (instead of Sundays) so in the worst case scenario I'll have it done by Friday afternoon.

Btw, you might need to install a compositing manager (like compiz) in order to run awn. Look at the first reply on this page: [https://answers.launchpad.net/awn/+question/11020](https://answers.launchpad.net/awn/+question/11020)

---

### Post by makinasvp on 2007-08-29
> **aantn said:**
> Thank you. 

I'm really sorry about the delay. I have some other work to take care of, and I haven't even had enough time to update my own copy of compiz thats running on my own computer, let alone finish experimenting around with a repository. In Israel, we have Fridays off (instead of Sundays) so in the worst case scenario I'll have it done by Friday afternoon.

Btw, you might need to install a compositing manager (like compiz) in order to run awn. Look at the first reply on this page: [https://answers.launchpad.net/awn/+question/11020](https://answers.launchpad.net/awn/+question/11020)

I have Beryl installed and running :)
I will switch to Compiz if need be...

---

### Post by aantn on 2007-08-31
Its done! The repository can be found at [repository.theesylum.com]("http://repository.theesylum.com"). At this point it only supports Feisty, but if enough people want then I can try to compile for other versions of Ubuntu also. I also don't have a gpg key yet, and there are a few more rough edges to fix up.

Right now it only contains Compiz Fusion. I'm going to add a few more packages (Kiba Dock, AWN, and Ubuntu SE) by the end of the weekend.

To use the repository, simply edit /etc/apt/sources.list and add the following four lines:
```

# The Esylum's Repository for Eyecandy Related Programs.
# Compiled from the latest available code in git, svn, or cvs.
# Supports only the PPC architecture.
deb [http://repository.theesylum.com](http://repository.theesylum.com) feisty eyecandy
```

Apt-get update and then run the following commands:

To install Compiz:
```
sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde
```

To install CompizConfig configurator:
```
sudo apt-get install compizconfig-settings-manager # libcompizconfig-backends-* ?!
```

To install all of the assorted plugins:
```
sudo apt-get install compiz-fusion-*
```

Then start Compiz run the following:
```
compiz --replace
```

Tell me if it works.

---

### Post by makinasvp on 2007-09-02
It works beautiful!! I am vouching to sticky this ASAP!!
Let me know when you're done this weekend so that I can install AWN. :)
Best regards,

-Matt

PS: I don't know how to thank you for your contribution. You are the best!

---

### Post by aantn on 2007-09-02
> **makinasvp said:**
> It works beautiful!! I am vouching to sticky this ASAP!!
Let me know when you're done this weekend so that I can install AWN. :)
Best regards,

-Matt

PS: I don't know how to thank you for your contribution. You are the best!

Thanks, but its really no trouble for me at all. I compile Compiz Fusion anyway for my own computer, and the program Falcon handles most of the work involved in actually creating the repository. I just run 2 commands to update the repo, and then I ftp it to my server.

Anyway, I'm going to begin working on AWN soon. I just need to reboot into Linux. (I still haven't broken off from OS X completely.) I haven't done anything with AWN in a while, so I don't know how long it'll take. It could be compiled and packaged within 10 minutes, but it could also take longer.

Perhaps it would be best to create a new thread about my repository. We sort of hijacked this thread and changed the topic. In case other people need help with Compiz Fusion or something else in the repository, it might be best to start a new thread dedicated to that topic. Tell me what you think. In the meantime, I'll get to work with AWN. Maybe I can even manage to get KibaDock in the repository today.

---

### Post by aantn on 2007-09-02
Sorry, but I had a few problems compiling and I won't be able to have Awn done until tomorrow. I'll keep you updated. Enjoy Compiz Fusion in the meantime.

---

### Post by makinasvp on 2007-09-02
Yes definitely make a new thread and I will vouch for it to become a sticky. You're the best!!
Can't wait for AWN hehe Meanwhile compiz fusion works great! I like it better than Beryl.

---

### Post by aantn on 2007-09-07
I may finally have it done... I'm waiting for the packages to build...

---

### Post by aantn on 2007-09-08
I guess not. The current development version of awn is broken. I'll keep you updated.

---

### Post by makinasvp on 2007-09-09
> **aantn said:**
> I guess not. The current development version of awn is broken. I'll keep you updated.

Can't wait for the updates. :)
Thanks again for everything that you're doing...

---

### Post by aantn on 2007-09-19
You can expect an update of Compiz Fusion tonight, and maybe even AWN.

---

### Post by aantn on 2007-09-20
Falcon is giving me problems, but you should be able to download the packages from [http://repository.theesylum.com/pool/feisty/eyecandy](http://repository.theesylum.com/pool/feisty/eyecandy)

---

### Post by aantn on 2007-09-20
Its done.

To install Awn just apt-get update and install the package avant-window-navigator

Your settings may not carry over when you update Compiz Fusion. There have been a lot of changes lately.

Tell me if it works.

---

### Post by aantn on 2007-09-22
I just updated cf and awn again. 

Btw, you also might want to install the package awn-manager for the settings manager.

---

### Post by frog_pilot on 2007-10-09
Hello aantn. I installed compz-fusion as you pointed out here [http://ubuntuforums.org/showpost.php?p=3285700&postcount=17]("http://ubuntuforums.org/showpost.php?p=3285700&postcount=17")
During install there was an error message that any driver was created by compiz and could not be overwritten. Thats why compiz-gnome could not be installed and there were several problems with depedencies between the packages.

To solve this problem I uninstalled default-compiz from my feisty install. This broke the whole metapackage ubuntu-desktop. But i didn't mind that.

After this your instructions worked well. I adjusted my xorg.conf like this (only the 3d related parts:
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"gbe"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"	"false"
	Option		"NoInt10"	"yes"
	Option		"AGPMode"	"4"
	Option 		"AGPFastWrite" 	"true"
	Option		"DRI"		"true"
	Option		"GARTSize"	"64"
        Option		"DisableGLXRootClipping" "true"
	Option		"AddARGBGLXVisuals"	"true"
        Option          "XAANoOffscreenPixmaps"
        Option		"AllowGLXWithComposite" "true"
	Option 		"EnablePageFlip" "1"
	Option 		"ColorTiling" 	"1"
	Option		"RenderAccel"	"true"
EndSection

Section "Monitor"
    Identifier     "P110"
    DisplaySize     402    302
    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 160.0
    Option         "DPMS"
EndSection

Section "Screen"
	Identifier	"CRT"
	Device		"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Monitor		"P110"
	DefaultDepth	24
   SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		"CRT"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

When I execute - after restarting the xserver - 
```
mpunk@PUNIX-G4:~$ compiz --replace
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
and something like that (I have to translate):
windowmanager-warning: »« found in configuration library is no admissible (acceptable) value for the shortcut (key combination) »toggle_shaded«

```
After it, there is no new prompt coming up/ nothing. After executing compiz --replace, the window-frames disappeared for short and then appeared as they were before.

Although I adjusted everything for 3d, when I issue ```
glxinfo | grep rendering
```, I get ```
direct rendering: No

``` confusing....

I'm on G4 Dual 1,25 GHz with Radeon 9000 pro (64 MB) as you can see in my xorg-file. Do you have any suggestions?

---

### Post by frog_pilot on 2007-10-09
btw: Desctop-Effects on the feisty-ppc-desktop-cd ar working fine... :(

There is a conflict between copiz-gtk and compiz-gnome. I can only install one of them.

---

### Post by aantn on 2007-10-10
Weird...

I'll get back to you about this.

---

### Post by aantn on 2007-10-10
There is a similar bug on launchpad. [I also found this on the compiz fusion forums.]("http://forum.compiz-fusion.org/showthread.php?t=3350&page=2") Are you using xgl or aiglx? Also, you might want to ask for help in #compiz-fusion.

---

### Post by frog_pilot on 2007-10-10
thanks for your help!

I figured it out. It wasn't because of the conflicting dependencies. It was an option in my xorg.conf's driver section.
```
	Option		"GARTSize"	"64"
```
This setting retards direct rendering (on my system). I found it anywhere in the web and pasted it to my xorg.conf :( my failure!
This Option provides RAM for the GPU, but I have VideoRAM on my video card...

But there is another Problem. When I open Emerald-Manager, there are no themes displayed. I installed Emerald from your repo. Anywhere there are options to fetch themes under GPL and without GPL. When I hit the button for GPLed Themes. There comes a progress bar and after this - nothing...

What's the matter? Where can I get the basic themes?

//Edit: I'm using aiglx, as you recommended. It runs a little bit stuttering (on dual G4 1,25 with 2 GB RAm and 64 MB Radeon 9000, it should run smoothly, i think). But I try to adjust a little bit with xorg.conf's options.

---

### Post by aantn on 2007-10-10
Just install the themes package. :)

You might want to try disabling some of the plugins and see if that improves the speed. For me, the water plugin really slows things down.

If I get around to it, I'll update the packages for cf and awn today.

---

### Post by frog_pilot on 2007-10-12
Hi aantn, thank you so much for your patient support :KS

I really forgot to install emerald-themes :)

Now without the water and snow plugin compiz is ronning fast. But there remains one problem. When I start compiz, the 2d speed will decrease immensely. It is no longer possible to scroll - e.g. a website in firefox -  in realtime. It starts to scroll shortly after moving the scrollwheel and then it hangs and stutters a little bit. I will search the web for explanations of my xorg-options here
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"	"false"
	Option		"NoInt10"	"yes"
	Option		"AGPMode"	"4"
	Option 		"AGPFastWrite" 	"true"
	Option		"DRI"		"true"
#	Option		"GARTSize"	"64"
        Option		"DisableGLXRootClipping" "true"
	Option		"AddARGBGLXVisuals"	"true"
#        Option          "XAANoOffscreenPixmaps"
        Option		"AllowGLXWithComposite" "true"
	Option 		"EnablePageFlip" "1"
	Option 		"ColorTiling" 	"1"
	Option		"RenderAccel"	"true"
EndSection
```
maybe here are some possibilities to tune 2d acceleration. Did you ever mention similar things?

///edit: btw, the default compiz switcher under "system" -->  "settings" --> "desktop effects" isn't compatible with 'our new version' of compiz-fusion?? There is no gui-way to start this compiz-fusion. I can only go the way ```
compiz --replace
```??

---

### Post by rhetoric on 2007-10-14
thanks much aantn. care to make a .deb for [fusion icon]("http://ubuntuforums.org/showthread.php?p=3163821") also?

---

### Post by aantn on 2007-10-15
I'm going to upgrade to gutsy sometime this week. As soon as that's done I'll continue updating the repository and I'll try to set up a vm for edgy. 

Yes, I can and will include fusion-icon.

---

### Post by rhetoric on 2007-10-15
What about awn-curves? I've already compiled and installed it from bzr. Are you familiar? I hope it's incorporated into the AWN project soon.

---

### Post by aantn on 2007-10-15
> **rhetoric said:**
> What about awn-curves? I've already compiled and installed it from bzr. Are you familiar? I hope it's incorporated into the AWN project soon.

I thought of including it in the past and then I decided to just wait until it got into the trunk.

---

### Post by rhetoric on 2007-10-19
aantn: Are you going to stop making Feisty packages once you upgrade? I'm hesitant to move to Gutsy since everything is working fine in Feisty ([thread]("http://ubuntuforums.org/showthread.php?t=579927") re:this)... but if I need to upgrade to keep updating compiz/awn I guess I will.

---

### Post by aantn on 2007-10-20
> **rhetoric said:**
> aantn: Are you going to stop making Feisty packages once you upgrade? I'm hesitant to move to Gutsy since everything is working fine in Feisty ([thread]("http://ubuntuforums.org/showthread.php?t=579927") re:this)... but if I need to upgrade to keep updating compiz/awn I guess I will.

I just upgraded. It depends on how difficult it will be to do so. I'll post again when I know what I'm doing.

---

### Post by rhetoric on 2007-10-21
> **aantn said:**
> I just upgraded. It depends on how difficult it will be to do so. I'll post again when I know what I'm doing.

Cool. If I can learn how to make the packages and I decide to stick with Feisty maybe I can help.

---

### Post by aantn on 2007-10-21
> **rhetoric said:**
> Cool. If I can learn how to make the packages and I decide to stick with Feisty maybe I can help.

Its really simple actually. :)

I just use an automated script. I'll see if I can use your help.

---

### Post by rhetoric on 2007-10-22
New compiz fusion released.

---

### Post by aantn on 2007-11-06
Sorry about the delay...

I'm working on the repository right now.

---

### Post by aantn on 2007-11-06
I've changed things around a bit. The Feisty repository is exactly the same as before and hasn't been updated. The Gutsy repository is split into two parts- compiz-fusion and eyecandy.
Right now, the eyecandy section only contains awn. I still plan on adding other packages when I get a chance.
The compiz-fusion section contains the git packages for compiz-fusion. They're built from the latest source code and are therefore slightly less stable than the default packages in Gutsy. All packages are tested first.
Right now, there's a small problem in the versioning schema that the compiz-fusion packages use. If you want to install the packages you'll first have to remove all of the official packages. You can remove them with:
```
echo "aptitude -y remove" `sudo dpkg -l | egrep '(beryl|emerald|compiz)'| awk '{print $2}'` | sudo bash
```
Then install all of my packages and just ignore update manager's claim that there are newer packages.

---

### Post by frog_pilot on 2007-11-07
It's a great pity that you have already upgraded to gutsy :) I hoped you will keep the feisty packages up to date. But don't be bothered by me, your feisty packages are still running fine for me. Thanks a lot...
I don't want to upgrade to gutsy yet. I'm happy with a stable feisty install on my mac and I am worrying that an upgrade could harm my system, because the ppc branch of ubuntu isn't that technically mature as the x86 branch...
Maybe now - the hope for burning hot compiz updates is gone - I will backup my system and have a shot at a gutsy gibbon :lolflag:

---

### Post by aantn on 2007-11-07
> **frog_pilot said:**
> It's a great pity that you have already upgraded to gutsy :) I hoped you will keep the feisty packages up to date. But don't be bothered by me, your feisty packages are still running fine for me. Thanks a lot...
I don't want to upgrade to gutsy yet. I'm happy with a stable feisty install on my mac and I am worrying that an upgrade could harm my system, because the ppc branch of ubuntu isn't that technically mature as the x86 branch...
Maybe now - the hope for burning hot compiz updates is gone - I will backup my system and have a shot at a gutsy gibbon :lolflag:

I wouldn't burn that cd yet. I completely understand your reluctance to update (my system was a bit borked up, so I just used Gutsy as an excuse to do a fresh install) and I agree that Gutsy is less stable than Feisty. If you give me a few more days, I'll see if I can work something out. I still have my Feisty partition intact (albeit a bit cluttered up), and I wouldn't mind building a few new packages once or twice a month for you. Do you use awn? (If you don't than you should.)

---

### Post by frog_pilot on 2007-11-07
fine :) I'm looking forward for cutting edge cf + awn on feisty 

> **aantn said:**
> Do you use awn? (If you don't than you should.)

Yes, of course I'm using awn. For mac-users there is no other way to start programs as through a animated dock-icon and terminal-comads are a mystery... :guitar:

---

### Post by aantn on 2007-11-07
> **frog_pilot said:**
> Yes, of course I'm using awn. For mac-users there is no other way to start programs as through a animated dock-icon and terminal-comads are a mystery... :guitar:

Just checking. As a soon to be applet developer, I'm always looking for new users to convince. :)

---

### Post by rhetoric on 2007-11-13
I'm still around and checking your repository, but I'm still in Feisty also (why fix what isn't broken right? ;p)

---

### Post by smackswell on 2007-11-13
> **aantn said:**
> Falcon is giving me problems, but you should be able to download the packages from [http://repository.theesylum.com/pool/feisty/eyecandy](http://repository.theesylum.com/pool/feisty/eyecandy)

I get a "403 Error- Forbidden"


Help?

---

### Post by holmrun on 2007-11-14
OK, I removed all of the stock compiz stuff with the command on page 5 and then redid the step by step posted early in the thread. This time it installed fine, however, when I attemp to run compiz --replace I receive the following errors:

$ compiz --replace
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/home/joey/.gtkrc-2.0:20: error: invalid string constant "000000", expected valid string constant


Any ideas?

---

### Post by aantn on 2007-11-15
The first bunch of errors don't matter. You can ignore them. I'm not sure about the others. I'm going to update the repo soon and that my fix some things.

---

### Post by holmrun on 2007-11-15
thank you, aantn. Looking forward to the updates.

---

### Post by aantn on 2007-11-15
Alright, I'm working on it...

I played around with Trevinho's script and I'm now repacking all of the debs for gutsy. Hopefully the version numbers will have been fixed.

I've updated the debs for feisty and I'll upload them along with the Gutsy ones as soon as the script finishes running...

:guitar:

---

### Post by aantn on 2007-11-15
It works!

:popcorn:

I'm uploading the repository... I'll tell you when I'm done.

---

### Post by aantn on 2007-11-15
Done.

Tell me if it works.

I updated the cf packages for gutsy and feisty. I'll work on awn next week.

---

### Post by aantn on 2007-11-15
[I've added a howto on my blog.]("http://theesylum.com/2007/11/15/repository-for-ubuntu-updated/") Tell me if it works...

---

### Post by holmrun on 2007-11-15
Wow, thanks. I'll check it out after work tonight. Thanks again for all of your hard work!

---

### Post by frog_pilot on 2007-11-16
Wow! When I started my mac this morning I got a message from update manager and found that you updated the cf packages. THANK YOU AANTN :). Now I'm up to date and will see if everything works fine. Until now it does. :guitar:

---

### Post by Pokefan on 2007-11-16
After running everything I get the error:

Fatal: compiz can't be ran using VESA of VGA divers.

Any suggestions?

---

### Post by holmrun on 2007-11-16
OK, so I still can't get this to work. After running compiz --replace I get this:

/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/home/joey/.gtkrc-2.0:20: error: invalid string constant "000000", expected valid string constant

This is running on a 15" G4 powerbook 1.67Ghz, 1.5GB ram, radeon 9600 128mb card.

---

### Post by frog_pilot on 2007-11-16
> **Pokefan said:**
> After running everything I get the error:

Fatal: compiz can't be ran using VESA of VGA divers.

Any suggestions?

the vesa display driver wont support direct rendering or any other 3d stuff.
supposably you have a ati video card. most likely a radeon. for most older cards (which we have on older ppc machines) the free ati-driver will support the whole 3d stuff. choose this driver in your xorg.conf.

---

### Post by holmrun on 2007-11-16
> **holmrun said:**
> OK, so I still can't get this to work. After running compiz --replace I get this:

/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/home/joey/.gtkrc-2.0:20: error: invalid string constant "000000", expected valid string constant

This is running on a 15" G4 powerbook 1.67Ghz, 1.5GB ram, radeon 9600 128mb card.

OK, so after some more testing compiz will run fine as long as I don't activate the window decoration plugin. As soon as that plugin is activated I get the error above and it quits. Any other ideas? All settings in that plugin are stock. (all compiz settings are stock as a matter of fact)

---

### Post by Pokefan on 2007-11-17
> **frog_pilot said:**
> supposably you have a ati video card. most likely a radeon. for most older cards (which we have on older ppc machines) the free ati-driver will support the whole 3d stuff. choose this driver in your xorg.conf.

I've got an nVidia GeForce FX Go5200. I haven't even had a chance to get in and look at drivers since I can't even boot up right now but do I need to download a driver or is there an option for this in the xorg.conf?

---

### Post by frog_pilot on 2007-11-17
> **holmrun said:**
> OK, so I still can't get this to work. After running compiz --replace I get this:

/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/home/joey/.gtkrc-2.0:20: error: invalid string constant "000000", expected valid string constant

This is running on a 15" G4 powerbook 1.67Ghz, 1.5GB ram, radeon 9600 128mb card.

Did you install the following packages? ```
libdecoration0
emerald
emerald-thems
libemeraldengine0
```

---

### Post by frog_pilot on 2007-11-17
> **Pokefan said:**
> I've got an nVidia GeForce FX Go5200. I haven't even had a chance to get in and look at drivers since I can't even boot up right now but do I need to download a driver or is there an option for this in the xorg.conf?

You can access the xorg.conf also when there is no X-Server started yet via the comandline. If you have already installed ubuntu, there is also a package with the free display-drivers installed.  But I think you won't be lucky. The free nvidia-driver "nv" also won't support the 3d effects.

If you have gutsy installed IMHO you won't be able to boot up, since the 3deffects are enabled as default. Could you ever start up 7.10 successfully?

---

### Post by holmrun on 2007-11-17
> **frog_pilot said:**
> Did you install the following packages? ```
libdecoration0
emerald
emerald-thems
libemeraldengine0
```

I did not have emerald installed so that fixed the window decorations... My only other concern is that windows now go under the top panel. On my other fiesty install (x86) the top panel is always on top and nothing can go over/under it. Is there a setting for that somewhere or is it just a part of being installed on PPC?

Thank you for all of your help so far.

---

### Post by Pokefan on 2007-11-17
Thanks Frog, I have been able to boot into 7.10 up until I tried to install all of this. I think I'll probably just completely reload it any way my PB was running to slow for it to be worthwile so it's no big deal. Thanks for the help. I should be building my new computer soon I'll deal with it later.

---

### Post by frog_pilot on 2007-11-17
> **holmrun said:**
> I did not have emerald installed so that fixed the window decorations... My only other concern is that windows now go under the top panel. On my other fiesty install (x86) the top panel is always on top and nothing can go over/under it. Is there a setting for that somewhere or is it just a part of being installed on PPC?

Thank you for all of your help so far.

Here the windows can be moved above the top panel. I don't know if there is a difference between compiz-fusion on ppc and on x86. On my machine it's normal since using compiz-fusion. btw. it remains the same when you turn off the wobbly windows plugin.

If the top bar of a window disappears under your panel, there is no problem. You can move these windows as usual with the top bar by holding ALT-Key while klicking and dragging it on any other point.

---

### Post by holmrun on 2007-11-17
Thanks frog. It isn't a problem and I know I can move the windows around, it just seemed odd that there would be a difference. Very happy with the end results, thanks so much for assisting with the PPC stuff. It is a world of difference after everything going so smoothly on the x86 side.

---

### Post by jlotempio on 2007-11-18
Hi, I am having a little bit of trouble getting compiz to work.  Although I have read that Nvidia cards don't support 3D on the macs, I thought I would take a chance with this guide.  I have the same card as Pokefan and receive the same error.  I know this guide probably works beautifully for ATI, but is there really no hope for the Nvidia people.  I have an Nvidia card in my desktop pc, and can run compiz-fusion perfectly.  Does anyone have any advice for getting the desktop effects going on my PB G4 with an Nvidia card, or is all hope lost?

---

### Post by frog_pilot on 2007-11-18
> **jlotempio said:**
> Hi, I am having a little bit of trouble getting compiz to work.  Although I have read that Nvidia cards don't support 3D on the macs, I thought I would take a chance with this guide.  I have the same card as Pokefan and receive the same error.  I know this guide probably works beautifully for ATI, but is there really no hope for the Nvidia people.  I have an Nvidia card in my desktop pc, and can run compiz-fusion perfectly.  Does anyone have any advice for getting the desktop effects going on my PB G4 with an Nvidia card, or is all hope lost?

[http://ubuntuforums.org/showthread.php?t=616061]("http://ubuntuforums.org/showthread.php?t=616061")

---

### Post by jlotempio on 2007-11-18
frog_pilot:

Thanks for the quick response.  I was afraid that would be the answer to my question.  As far as the Nouveau project goes, what is the hold up.  It seems that I have read oodles of posts that date back to last year that say they are really close to releasing the drivers.  Why so long with little to no progress, at least as far as releases goes?

---

### Post by frog_pilot on 2007-11-18
I really don't know anything about Nouveau projekt. Please post your question on the other thread, I redirected you to. Maybe Auria knows a little more. :)

---

### Post by aantn on 2007-11-18
> **holmrun said:**
> I did not have emerald installed so that fixed the window decorations... My only other concern is that windows now go under the top panel. On my other fiesty install (x86) the top panel is always on top and nothing can go over/under it. Is there a setting for that somewhere or is it just a part of being installed on PPC?

Thank you for all of your help so far.

Thats a bug in emerald as far as I know. If it really bothers you than you can use Metacity with compiz.

For those of you having problems that aren't specific to my repository, you should ask for help on the compiz forums. I'll do my best to help either way, but you'll probably get help faster on the compiz forums.

---

