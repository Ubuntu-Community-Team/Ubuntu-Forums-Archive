---
title: "Is Feisty  really a stable OS?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-06-19
It keeps freezing up on me and I keep having to reinstall. Getting to be a real pain. I'm about ready to go back to Edgy and live with the notice in Update manager there is an upgrade to Feisty.

---

### Post by starcraft.man on 2007-06-19
> **captgadget said:**
> It keeps freezing up on me and I keep having to reinstall. Getting to be a real pain. I'm about ready to go back to Edgy and live with the notice in Update manager there is an upgrade to Feisty.

I'm rock solid when not using Beryl (admittedly it crashes the odd time but I find it acceptable most times).

What is the hardware on your machine? Did you do anything special with the install or directly after getting Feisty in? Did you check the burn to make sure the disk had no errors? Maybe try using the alternate installer, its never failed me so far... You have to give more details.

---

### Post by vexorian on 2007-06-19
Just as much you'd probably find a guy whose edgy was less stable than feisty, it could be some hardware specific thing, or perhaps you just installed Feisty over Edgy or had a malformed installation.

There isn't much to do besides trying to find a pattern to what is causing the freeze and reporting the bug, and switching back to edgy since it is not broken for you.

---

### Post by jimrz on 2007-06-19
> **captgadget said:**
> It keeps freezing up on me and I keep having to reinstall. Getting to be a real pain. I'm about ready to go back to Edgy and live with the notice in Update manager there is an upgrade to Feisty.

has been for me on 4 machines + a couple of others that I setup for friends

i, too, have not been using beryl or compiz.

---

### Post by Crafty Kisses on 2007-06-19
I think Feisty is a solid OS, I have never experienced really any major problems, besides when I try to install my video card drivers.

---

### Post by Zzl1xndd on 2007-06-19
No issues except when Running Beryl but even those are few and far between.

---

### Post by bone43 on 2007-06-19
Nothing but minor problems on two machines, most crashes or problems Ive had are with programs and those have been fixed for the most part with codex and some tweaking.

Beryl and Emerald can be a little weird at times with missing buttons and messed up text but has never crashed at least yet.

---

### Post by captgadget on 2007-06-19
I built the machine with a Maxtor 80GB hard drive, a new Intel Pent 4 processor, a new MSI motherboard and 1.2GB of Ram. I had everything the way I wanted it and when I was trying to set up Evolution the cursor moved to the status bar at the bottom and it was locked up. So I did a reset and the rest is history. Keeps happening so I guess I'll go backwards.

---

### Post by Bachstelze on 2007-06-19
Depends on what you consider "stable", it's not with Feisty that you'll have 200 days of uptime :p

---

### Post by old_geekster on 2007-06-19
With my configuration (See Signature), Feisty is 100% stable.  I even have my CPU and memory overclocked.  I use Beryl continuosly and have never had a freeze that I didn't cause myself.

As stated earlier in another post, I believe Feisty is more stable than Edgy on my rig.

---

### Post by phr0ze on 2007-06-19
I understand it locks up for people but why do you have to reinstall? That might be a bit more serious.

---

### Post by captgadget on 2007-06-20
When it locks up I have to do a reset and when I do the reset it doesn't restart and like this last time it ran fsck and found a bunch of errors. The screen just sat there while the hard drive ran and gave all these error messages for usb 2-1. At that point I figure I have no option other than do a install. At that point I lose all my data.

---

### Post by Zzl1xndd on 2007-06-20
> **captgadget said:**
> When it locks up I have to do a reset and when I do the reset it doesn't restart and like this last time it ran fsck and found a bunch of errors. The screen just sat there while the hard drive ran and gave all these error messages for usb 2-1. At that point I figure I have no option other than do a install. At that point I lose all my data.

Might suggest running some Ram and Hard drive tests.

---

### Post by Arinux on 2007-06-20
Yup so far it's working good. I got a Dell laptop and its working flawlessely. For more trouble shooting , please post your rig components and any specific error messages!

---

### Post by Calash on 2007-06-20
Been very stable on 3 systems, one a minimal install for MythTV, one an iBook, and my main that I tweek out (Beryl, Kibi-dock, Fluxbox for games)

Your description sounds like a harddrive issue as noted earlier in the thread.  There are some nice CD based utilites to check the hard drive and mark bad sectors.  If there are too many, you may want to look into getting a new hard drive.

---

### Post by Golyadkin on 2007-06-20
Feisty Beta sometimes crashed on me, but that was to be expected. Now I have been running Feisty final stable since the day it was released.
AMD64 X2 4200+, 1GB Dual Channel DDR2-5400, HIS X1650XT Ultra and a bunch of Western Digital disks.

---

### Post by dptxp on 2007-06-20
Why not post your hardware details, maybe someone can help.

I use 32 bit and 64 bit on different machines. Not a single problem yet.

---

### Post by captgadget on 2007-06-20
Here is the hard ware

---

### Post by Jimmyfj on 2007-06-20
No issues what so ever on my part. Not on Feisty itself nor on Beryl - Ubuntu is rock solid on my sys

---

### Post by sailor2001 on 2007-06-20
I agree with the old geezer... Fiesty is very stable on my box. Only time I ever have any problem is when I push it too hard and have way to many things going on at the same time

---

### Post by captgadget on 2007-06-20
OK, as I read most of the replies most everyone agrees it's pretty stable. Now, let me ask this question. If it freezes and the cursor won't move, you can't do a crtl-alt-backspace then how do you recover from this and not have restart problems?

---

### Post by MrShmoo on 2007-06-20
I and many other people have had the same problem. Seems like a pretty big bug left in Feisty. I've filed a bugreport on Launchpad but have no clue how long it will take to be resolved.

---

### Post by WHICKS on 2007-06-20
Running very stable.  No problems after first 24 hours.  New kernel upgrade had no effect.

---

### Post by hsweet on 2007-06-20
A couple of things to try if your system freezes before you hit the reboot key.

Ctrl/Alt/Backspace will get you out of a locked gnome session
Ctrl/Alt/F1 will take you to a terminal.  From there you can ctrl/Alt/delete to a restart or ```
sudo shutdown -r now
``` to a clean reboot.

There is a way to go to a lower runlevel but I forget how.

finally, you can connect remotely if you are on a network.  Use a Putty terminal to send the shutdown command.  This can work from windows or linux.  There are good free putty apps.

Beats screwing up the system and reinstalling

---

### Post by orb9220 on 2007-06-20
Yep I also had random lockups on my older p4 1.3ghz intel board and now on my new AMD 3500+ K8N Neo2 would Totally Hard Lockup anywhere from 1hr to 8hrs it would Lockup.

Some said it was the kernel.  Some say it was Beryl. Some say it was firefox. Some even say it was a bug in networking layers.

Latest upgrades from a couple of days ago and have had zero lockups so far. Been going now 11hrs this session no lockups.

---

### Post by AusIV4 on 2007-06-20
I've had some freezes similar to what you're talking about, turned out to be some bad RAM. Run Memtest + from the Grub menu and see what it gives you.

You might also have similar problems if you're hard drive is bad and is corrupting your filesystem for whatever reason. Sounds more like hardware than software to me.

---

### Post by Nezing on 2007-06-20
Feisty seems fine.Sunday last,there was a power fluctuation in my local power supply (not my fault),which wrecked my download of Virtualbox,and refused me access to Synaptic,so a reinstall had to be done.So unless flames are coming from the cpu,everything is fine.
Running beryl,Firefox,and Rythmbox music player at the moment.No freeze up's yet.:D

---

### Post by MichaelLerch on 2007-06-20
I've found that on some systems - Feisty is having small problems.  However, with a little bit of diagnosing it's easily fixed.  I haven't had really any problems [so far] with Feisty.  

If you're having random lock ups upon upgrading to Feisty, make sure you uninstall and reinstall your video card drivers using Envy.

---

### Post by Golyadkin on 2007-06-20
> **hsweet said:**
> 
There is a way to go to a lower runlevel but I forget how.

Isn't that the command "init" ? 
> 
sudo init 3

for switching to the third runlevel (no X).

---

### Post by capecove on 2007-06-20
Ubuntu has been 100% stable for me. The only time something goes wrong is when it's "pilot error". :)

---

