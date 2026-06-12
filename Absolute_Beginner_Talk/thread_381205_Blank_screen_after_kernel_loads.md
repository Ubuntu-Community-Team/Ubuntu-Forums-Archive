---
title: "Blank screen after kernel loads"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by templeofstone on 2007-03-10
UPDATE: 

I just tried booting from the LiveCD with NO hard drives connected, to see if it could boot to the mini desktop. 

Same results!

So it doesn't seem to have *anything* to do with the hard drive linux was installed onto, it seems the LiveCD has just spontaneously developed a conflict with my hardware!

===
Original post:
---
I'm having a tricky problem. :confused: 

I downloaded the 6.10 liveCD and burned it (admittedly at a fast burn setting). No problem. Booted to the LiveCD - no problem, brought up the Ubuntu install menu. Ran the verification on the cd to make sure it was intact, and the report said there were no disk errors (bad sectors, I think were the exact words). 

Ok, no problems so far so I ran the installer. Everything installed properly, I successfully ran the install program on the little mini desktop, got Ubuntu properly installed and booted to ubu on the hard drive under its own steam. 

By the way, let me stop right here to give some five-star kudos to the dev team for the mini-desktop during install... I blew a few minds by sending them an MSN message telling them I'm talking to them through the installer. Also, web-browsing and email during your OS install process... Mega-props guys!! Ok, back to the topic at hand...

Ok up to this point everything worked properly, so I tried installing Beryl. (I'll mention right now - this isn't a Beryl-related problem, I'm only mentioning it to give as complete a background/history to the problem as possible.) Beryl installed properly - everything reported OK and I logged into a session using XGL, but when I tried to load the Beryl Manager, it tried to load and immediately defaulted back to GNOME. No other problems - GNOME still worked properly and all the little applications Ubuntu comes with were working properly. 

I tried rebooting as one of my attempted fixes/solutions. It didn't work, but I thought I'd mention it to illustrate that I was still able to successfully reboot at this point and get back into GNOME.

Anyway, through the course of fiddling with Beryl I disabled the option to load the fallback window manager (GNOME) if Beryl crashes. Predictably, Beryl crashed. I was left with an orange screen and no interface widgets. I tried all the standard keyboard shortcuts every Windows user is familiar with - CTRL-ALT-DEL, CTRL-SHIFT-ESC, but nothing did anything. Also, nothing during the Ubuntu install process gave me any indication that there are special system-wide hotkeys that work for Ubuntu (or Linux in general) so I was left with no choice but to walk across the room and hit the reset button on the computer.

THIS IS WHERE THE PROBLEM REALLY STARTS

When I tried rebooting it got as far as the GRUB menu, but when I tried loading either the entry for 6.10 or 6.11 (the 6.11 entry appeared after the automatic-update thing finished when I loaded Ubuntu from HD for the first time.) the screen would go blank, everything would stop and no user input would work - I had to manually get up, walk across the room, and press the reset button again every time.

I tried booting to the 6.10 and the 6.11 recovery mode options and every time it would get part way through the list of things being loaded then just stop at some random place every time, not loading anything else and not accepting any user input.

Side note - at this point I booted to GRUB and tried to select the Windows XP option so I could check forums and knowledge-bases for some clues, but when XP tried to load it brought up the blue loading screen (same screen as chkdisk and the login screen, not the blue screen of death) and said that it was missing a couple files.. hung on that screen for a few seconds, then spontaneously rebooted itself. It continued to do that every time I tried to load XP.

So, GREAT. Not only did Ubuntu hoop itself, but it hooped my fallback OS as well. I wouldn't be pissed off if it was because of something I had done, but there doesn't seem to be any indication that it's my fault. Beryl said it installed properly, and even though Beryl wasn't functioning properly it didn't seem to be affecting the operability of the rest of the system while GNOME was loaded. I didn't make any changes to the system's hardware or OS configuration, and it just suddenly stopped behaving properly. Thank you linux, for ruining my whole system. At least all my important data is on a different drive :P

So anyway I tried everything I could think of (including removing every hard drive except for the one linux is instsalled/being re-installed onto) and eventually decided to nuke the partition and start over from scratch. However, now when I try to load up the installer, I encounter the same problem as when I was trying to boot to the Ubuntu that was installed on the hard drive - I choose the "Start/install Ubuntu", it says "Loading linux kernel..." then the screen goes blank and everything stops.

Same results when I try loading the installer using Safe Graphics mode or whatever it's labeled as.

So...
- I know it's not a hardware issue as the problem started without me making any changes to the hardware configuration. 
- I know it's not a problem with the LiveCD as it managed to properly install Ubuntu once already yesterday. 
- I know it's not a problem with Beryl or the previous installation of Ubuntu for two reasons - 1) I followed all the instructions to the letter for both the Ubuntu and the Beryl installations, and 2) I've completely NUKED the partition that had Ubuntu on it. There is no such thing as linux on that hard drive anymore, so it can't possibly be what's preventing the LiveCD from performing its duties.
- It seems the problem was caused by pressing the reset button on the computer while Ubuntu was loaded, but Beryl and GNOME weren't. I don't understand why it would prevent me from being able to load Ubuntu, or why it would frack-over my XP, or why it would prevent me from being able to even properly install Ubuntu onto a newly-paved partition... But that's the only catalyst I can detect for my problem.

Also - and this is weird - yesterday before I did my first install I ran the "Test CD integrity" option (or whatever it's labeled as...) and had good results - it ran the test properly and reported that there were no bad sectors. Today when I run the "test cd" option, the same thing happens as when I try to install - gets as far as clearing the "Loading linux kernel..." screen, then everything goes blank and the system becomes unresponsive and inactive.

One last note (in case it helps) - the blank screen isn't entirely blank, there's a command-line cursor in the top left. Not a full prompt, just the cursor/underscore. Also when it gets to the lock-up point, pressing NumLock doesn't toggle the indicator light like it does when things are running properly.

I tried burning another copy of the LiveCD at 4x burning speed as it seemed to solve some other peoples' problems, but I get the exact same results.

Am I going to have to do a low-level format on the drive to completely wipe out any other partitions the drive might have?

(in other words, am I going to have to buy a new hard drive to back up my data before said low-level format? linux is supposed to be free, not cost me more money than windows vista!!)

:confused:

I've already re-installed XP on a new partition in order to get on here and ask for some form of help... (I've installed it onto the partition that Ubuntu WOULD have been installed onto if it had worked properly. Take that, Ubuntu! You've got a WINDOWS sleeping in your bed!)

Does anyone see any potential solution that won't defeat a large part of the whole purpose of going Linux? Or is everyone as confused about this as I am?

---

### Post by Bachstelze on 2007-03-10
> **templeofstone said:**
> 
By the way, let me stop right here to give some five-star kudos to the dev team for the mini-desktop during install... I blew a few minds by sending them an MSN message telling them I'm talking to them through the installer. Also, web-browsing and email during your OS install process... Mega-props guys!! Ok, back to the topic at hand...

You know what ? Right now, I'm installing Gentoo, not from the mini-desktop of a Live CD but from my fully-configured Debian desktop, meaning that I can not only browse the web or chat via IM/IRC but also watch a movie, listen to music, play my favourite games and so on. The Gentoo installation just takes a tiny terminal window ;)

Anyway, back on topic :

Whenever the Live CD fails on someone's machine, for whatever reason, I ask them one thing : did you try the Alternate CD ? The Alternate CD is the "old-school" text-based installer. So you won't get the fancy desktop while Ubuntu is installing but it is far more reliable. I honestly have no clue about what is preventing the Live CD to work but it is very possible that it will be no problem for the Alternate so I'd advise you to try that first.

---

### Post by templeofstone on 2007-03-10
> **HymnToLife said:**
> Whenever the Live CD fails on someone's machine, for whatever reason, I ask them one thing : did you try the Alternate CD ? The Alternate CD is the "old-school" text-based installer. So you won't get the fancy desktop while Ubuntu is installing but it is far more reliable. I honestly have no clue about what is preventing the Live CD to work but it is very possible that it will be no problem for the Alternate so I'd advise you to try that first.

I didn't try the Alternate cd, I'll give it a whirl, thanks :)

---

