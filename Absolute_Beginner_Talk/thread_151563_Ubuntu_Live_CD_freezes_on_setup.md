---
title: "Ubuntu Live CD freezes on setup"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Over Haze on 2006-03-28
Hello, my Ubuntu Cds arrived this morning but I’m having a problem. When I in stall one of the live Cds (64 or PC) the setup process freezes on “running/ect/hot plug/usb.rc

Looking true the wall of text displayed before that I found the following “BIOS handoff failed” then “continuing after BIOS Bug”

Anyone got any advice? I was looking forward to trying Ubuntu.

---

### Post by Over Haze on 2006-03-28
Bit of help, please?

---

### Post by BlaineM on 2006-03-28
are you talking about the first splash screen after you have run all the way through the install, or is this still during the install?

---

### Post by Over Haze on 2006-03-28
During the install.

---

### Post by BlaineM on 2006-03-28
I had what sounds like that problem, if it was with the live cd.  But it doesn't technically install anything, just run off of the cd. all I hit was ctrl+c to cancel that process.  I dont know about during the install of anything with that though.  Mine was during the main first splash screen (says Ubuntu in the background and brown color, and the list below that also says stuff like syncing clock and setting clock, alsa 0...) is this what you are talking about?

---

### Post by Over Haze on 2006-03-28
No I never made it that far. My problem is on a black screen with nothing but text.

---

### Post by BlaineM on 2006-03-28
I did some quick searching in the forums and all I could find for now was [http://ubuntuforums.org/showthread.php?t=149882&highlight=ubuntu+live+cd](http://ubuntuforums.org/showthread.php?t=149882&highlight=ubuntu+live+cd)   I hope that this solves the problem,  if not sorry man, keep waiting, someone else might know.

---

### Post by Over Haze on 2006-03-28
Thanks for the help.

---

### Post by Over Haze on 2006-03-28
I am completely new to this so I am slightly out of my depth, so if anyone recognises this problem and knows how to do something about it please give me some advice.

Thanks.

---

### Post by Over Haze on 2006-03-28
I’m going to bump this. I am determined to use this live CD.

---

### Post by IDipSkoalMint on 2006-03-28
Try the Knoppix live CD ... I never had an issue with that one.

---

### Post by Over Haze on 2006-03-28
No I really want to try Ubuntu. The point of using the Live CD is to see how well it detects my hardware before I try a duel boot. 

I have a mid range PC, I have the Live CD, there must be some way of getting it to run.

---

### Post by Mustard on 2006-03-28
When you start up the live CD I believe there are options that you can run the live CD with.  These options are accessible by hitting the function keys at the prompt.  You can try running it with the noapic nolapic options.

What type of graphics card are you using?

---

### Post by Over Haze on 2006-03-28
Intergrated radeon Xpress200G. As I’m say I’m completely new to this so please don’t assume I know anything ;)

---

### Post by Mustard on 2006-03-28
[QUOTE=Over Haze]Intergrated radeon Xpress200G. As I’m say I’m completely new to this so please don’t assume I know anything ;)[/QUOTE]

Hmm..Ok, sometimes ati cards are a problem.  You can also try the 'vga=771' option **if** you have a problem with your display.  This is assuming you get past this hotplug freeze issue.  Hotlug is loading a lot of different modules and any one of those modules could be where the problem is occuring.

Do you know if you have the latest BIOS upgrade for your system?

I know mine never gets upgraded.  Flashing BIOS is one of those computer tasks that I have an inherent fear of and never do. :)

---

### Post by Over Haze on 2006-03-28
I have no idea if they are up to date but I know they are Phoenix (Award) PnP Flash ROM BIOS

Just so I know when I’m trying this again how long does the boot process take the first time? I don’t want to go panicking because its taking longer than I THINK is normal.

---

### Post by Over Haze on 2006-03-28
Just so this is completely idiot  proof. Could you please tell me exactly what boot command I should enter?

So its boot: (what?)

---

### Post by Mustard on 2006-03-28
[QUOTE=Over Haze]Just so this is completely idiot  proof. Could you please tell me exactly what boot command I should enter?

So its boot: (what?)[/QUOTE]

It's been a while for me since I have used the live CD, so I know I was being a bit vague. :)

I think its something like this at the boot prompt type..

```
linux noapic nolapic
```

Don't quote me on that though. ;)  The part that most people miss is the 'linux' part at the front of the boot options.

---

### Post by Over Haze on 2006-03-28
Thank you, I'll give it a try.

---

### Post by Mustard on 2006-03-28
[QUOTE=Over Haze]I have no idea if they are up to date but I know they are Phoenix (Award) PnP Flash ROM BIOS

Just so I know when I’m trying this again how long does the boot process take the first time? I don’t want to go panicking because its taking longer than I THINK is normal.[/QUOTE]

The process does take a little time, but it should be fairly obvious when something is happening.  Certainly any long stretch of staring at the screen for over a minute or two without anything happening on the screen would be considered unusual and in need of some user interaction ie rebooting and trying again.

---

### Post by Over Haze on 2006-03-28
Nope, that didn&#8217;t work. &#8220;Cannot find Kernal image Linux&#8221;. I&#8217;m starting to think I will never know the pleasure of starting a PC and not seeing the windows logo.

Any other ideas?

---

### Post by Over Haze on 2006-03-28
*bump*

---

### Post by IDipSkoalMint on 2006-03-28
[QUOTE=Over Haze]*bump*[/QUOTE]

On-topic: Is this a live CD that you ordered and paid for or one you downloaded and burned the .iso/.img to a disc? If it's the latter, try burning another copy.

Off-topic: I'm sure it's just out of frustration and eagerness to get this working for you, but I think showing a little more patience (e.g. not constanly "bump"ing your thread) wouldn't hurt ;)

---

### Post by jason.b.c on 2006-03-28
> **IDipSkoalMint]On-topic: Is this a live CD that you ordered and paid for or one you downloaded and burned the .iso/.img to a disc? If it's the latter, try burning another copy.

Off-topic: I'm sure it's just out of frustration and eagerness to get this working for you, but I think showing a little more patience (e.g. not constanly "bump"ing your thread) wouldn't hurt  said:**
> 

No, i think he said that he just got them in the mail.;) 

I read in the january 2006 issue of maximum pc , an article on build a $300 pc where the guy's that buit it had a similar problem with there ubuntu install,..

In the the small section labled " Operating System> Ubuntu Linux " they wrote,


[QUOTE]There's a small incompatablity with onboard video and ubuntu, but luckily the fix is easy: Just edit a single file before you start the GUI.  The first time boot after the install completes, press ESC during the boot process and go into the ubuntu recovery console.
From there, type:*nano /etc/x11/xorg.conf* and scroll down to the line that says **Device "ATI"**. Replace **Device "ATI"** with **"Vesa"** , press ctrl-o, then ctrl-x, and restart your computer, after that you should be good to go..

I don't know if this can help you or not,( i hope it does ), but it might, or at least send you in the right direction..:) :confused:

---

### Post by Mustard on 2006-03-28
[QUOTE=Over Haze]Nope, that didn’t work. “Cannot find Kernal image Linux”. I’m starting to think I will never know the pleasure of starting a PC and not seeing the windows logo.

Any other ideas?[/QUOTE]

I would suggest hitting the functions keys when you get to the boot prompt and reading the instructions on how to use the boot parameters in there then.  My own recollection is hazy.

---

### Post by Over Haze on 2006-03-29
Okey dokey, I got past the lock up using boot: live noapic nolapic (hurrah!) BUT the process froze again later on during the installation process (Brown screen, directly after hardware detection), It froze at 20%. This goes for both the PC and 64 Bit versions so its not a disc problem.

At least we are making progress! Any advice on this?

---

### Post by Over Haze on 2006-03-29
I still haven’t got past 20%, anyone got any ideas.

---

### Post by Mustard on 2006-03-29
[QUOTE=Over Haze]I still haven’t got past 20%, anyone got any ideas.[/QUOTE]

More options would be choosing the vga=771 option as well as the others you are already using.  You could also try the acpi=off option.  You can also try looking in your BIOS settings to disable some options relating to acpi.  You could also try unplugging any USB devices that are not essential to have connected during the startup.

The reasons why the lockups occur are many and varied, so it's a bit of a crapshoot trying to find them.

---

### Post by Over Haze on 2006-03-30
No that didn't work, vga=771 made the setup crash and with acpi=off its locked up where it did originally, I did however manage to jot down what is freezing on at 20 %. **Lebic6-udeb** if that helps any.

---

### Post by Mustard on 2006-03-30
[QUOTE=Over Haze]No that didn't work, vga=771 made the setup crash and with acpi=off its locked up where it did originally, I did however manage to jot down what is freezing on at 20 %. **Lebic6-udeb** if that helps any.[/QUOTE]

I'm starting to lose hope. :)  How are you going?  I'm wondering whether you should wait for the next version of Ubuntu to come out and try the new live CD, or even try a live CD from another distro. It would at least be interesting to know whether another live CD distro detects your hardware better than the Ubuntu live CD does.

---

### Post by jason.b.c on 2006-03-30
[QUOTE=Mustard]I'm starting to lose hope. :)  How are you going?  I'm wondering whether you should wait for the next version of Ubuntu to come out and try the new live CD, or even try a live CD from another distro. It would at least be interesting to know whether another live CD distro detects your hardware better than the Ubuntu live CD does.[/QUOTE]


Ya I feel for him too :( ,  It sucks when you try and try and still can't get anything going..:( :mad:

---

### Post by Over Haze on 2006-03-31
I think I might give Knoppix a try, but right now im walking away from Ubuntu (But I will order the next release). For now I&#8217;m going to relax and play Oblivion for a while. 

Thanks for all you help.

---

### Post by Mustard on 2006-03-31
[QUOTE=Over Haze]I think I might give Knoppix a try, but right now im walking away from Ubuntu (But I will order the next release). For now I&#8217;m going to relax and play Oblivion for a while. 

Thanks for all you help.[/QUOTE]

No problem.  I'm disappointed myself that you couldn't get it going and hopeful that whatever issue was causing your problem will be fixed in the next issue which is due June 1st, IIRC.

I found Kanotix a bit more polished than Knoppix.  The only issue with Kanotix is that it's very German orientated atm.  When I popped into the Kanotix help channel on IRC, everything was in German. :)  If you install Kanotix to your hard drive, it becomes a pure Debian distro (with KDE interface).  I'm not sure if that is the case for Knoppix or not.  I've installed Kanotix to a spare partition so I could play around with a pure Debian install and explore the 'roots of Ubuntu'. :D

So far my list of live CD's consist of:
1. Knoppix
2. Kanotix
3. Mepis
4. AnonymOS
5. Ubuntu (Breezy Badger, Hoary Hedgehog, Dapper Flight 4)
4. System Rescue CD
5. Puppy Linux (CD and Multi-Session DVD)
6. Damn Small Linux (DSL)
7. Super Grub Disk

I think thats all of them. I'd like to add Gnoppix to that list soon.  I quite like collecting them.  :)

---

