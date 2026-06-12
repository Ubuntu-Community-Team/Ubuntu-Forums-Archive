---
title: "Random freezing"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by MrShmoo on 2007-06-14
Hi all,

First time Linux user here. I recently installed Ubuntu 7.04 on a dual-boot system with Windows just to try it out. I like it a lot so far and have managed to tinker with it to get my sound card working and my ATI video card working with two monitors.

Except there is one small problem... it randomly freezes quite a bit. Usually this happens between 10 minutes and an hour of when I initially log in but I've had it both stay up for longer and crash within 2 or 3 minutes of logging in. It seems to happen more when I'm playing multimedia of some sort (using Rhythmbox, watching videos on YouTube), though this is just a hunch. Sometimes when it freezes I am still able to move the cursor around, but nothing responds on the screen and the keyboard does not work so I think that it's not totally a hardware problem. There is also a weird "cracking" noise that I am getting recently through the headphones even when Ubuntu is up and working fine. I am using the open source "ati" drivers as opposed to the propietary "fglrx" ones for my video card, as I had much difficulty getting the correct resolutions on both my monitors with the fglrx drivers.

Here are my system specs:

P4 2.6 Ghz
1024 MB RAM
ATI Radeon 9700 Pro
Soundblaster Audigy 2

Built this system for myself a few years ago, but I don't know the motherboard off the top of my head.

I'm running Feisty Fawn and in the boot menu I chose the 2.6.20-16-generic kernel. I also do not have the slightest idea on which log file might be helpful to look at to diagnose the problem so any insight on that count would be helpful as well.

All assistance is greatly appreciated. Thanks!

---

### Post by Gmbrdilos on 2007-06-14
question 1: do you have beryl or compiz enabled?

question 2: did you check the inside of the case for heavy dust or heat?

---

### Post by MrShmoo on 2007-06-14
> **Gmbrdilos said:**
> question 1: do you have beryl or compiz enabled? 

Nope..hadn't gotten that far yet

>  question 2: did you check the inside of the case for heavy dust or heat?

I just did..found nothing remarkable. I can check the system temp in the BIOS so I'll keep an eye on if it's high the next time I freeze.

---

### Post by Gmbrdilos on 2007-06-14
Last time this happened to me was a bout a year ago, my fan got clogged with dust so heat was building up. It might not look much but it never hurts to spray it with a can of concentrated air. Did the trcik for me.

---

### Post by BHelts on 2007-06-14
a good idea might be to boot into the LiveCD (if you installed with the LiveCD) and test the memory.
another good idea would be to download [Ultimate Boot CD]("http://ultimatebootcd.com") and run your hard drive manufacturers test.

{EDIT}  if you didn't install with the LiveCD... UBCD has a memtest on it as well, a few actually.

---

### Post by MrShmoo on 2007-06-14
> **BHelts said:**
> a good idea might be to boot into the LiveCD (if you installed with the LiveCD) and test the memory.
another good idea would be to download [Ultimate Boot CD]("http://ultimatebootcd.com") and run your hard drive manufacturers test.

{EDIT}  if you didn't install with the LiveCD... UBCD has a memtest on it as well, a few actually.

Hmmm...about 60% through the memtest my motherboard (? I think) started making an awful beeping noise (but there were no errors). I stopped the test and my CPU was really hot. So I'm thinking it might be a heating problem? 

Any idea on why this would be happening and solutions which don't include going out and buying fans? I'm not running anything particularly intense in Ubuntu and I have no overheating problems at all in XP.

---

### Post by BHelts on 2007-06-14
make sure all the fans in your case are spinning.  blow out any dust from the case and specifically the heat sink.  if you use compressed air, be very careful, it'll blow water if you aren't careful.  finally, if the cpu (heatsink) is still getting hot, remove the heatsink and wipe off the thermal compound from the heat sink and the processor, it is probably too dry.  when you do this, use a dry kleenex or papertowel.  Reapply thermal compound (should be able to get it at most computer shops).  the key here is to not use too much, you want to have a dollop that is a little smaller than a pea.  reattach the heatsink and that should help with the over heating.

---

### Post by MrShmoo on 2007-06-14
Gave the fans and CPU heatsink a few more sprays of compressed air and then went through some of the CPU throttling guides on ubuntuguide.org and this seemed to improve things vastly (though it still crashes occasionally). The weird thing about when it crashes is that I don't see any corresponding spikes in the temperature monitor I've put up...

And it still strikes me as odd that I (and many others, according to [https://launchpad.net/ubuntu/+bug/22336](https://launchpad.net/ubuntu/+bug/22336)) have these overheating problems in Ubuntu without any corresponding problems in XP. Hopefully the developers can fix this in future versions as I'm having great fun with Ubuntu :)

---

### Post by MrShmoo on 2007-06-15
Upon further investigation I'm thinking it may not be an overheating problem..I continue to have these lockups...even when the computer is sitting completely idle and I typically see no spikes in temperature preceding the freeze.

I'm kind of at a loss of what to do now

This is kind of interesting though...when I run "sudo sensors" I get the following

```

w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +1.50 V  (min =  +0.00 V, max =  +4.08 V)              
VCore 2:   +2.58 V  (min =  +0.00 V, max =  +4.08 V)              
+3.3V:     +3.30 V  (min =  +2.82 V, max =  +3.79 V)              
+5V:       +5.03 V  (min =  +1.83 V, max =  +0.86 V)       ALARM  
+12V:     +11.98 V  (min =  +8.82 V, max = +11.67 V)       ALARM  
-12V:      -7.01 V  (min = -14.09 V, max =  -3.48 V)              
-5V:       -3.69 V  (min =  -1.28 V, max =  -7.71 V)       ALARM  
V5SB:      +5.46 V  (min =  +0.43 V, max =  +0.43 V)       ALARM  
VBat:      +3.25 V  (min =  +0.00 V, max =  +0.00 V)       ALARM  
fan1:     2812 RPM  (min =  332 RPM, div = 16)                     
fan2:        0 RPM  (min =  332 RPM, div = 16)              ALARM  
fan3:        0 RPM  (min =  332 RPM, div = 16)              ALARM  
temp1:       +33°C  (high =   +32°C, hyst =    +0°C)   sensor = thermistor   ALARM   
temp2:     +40.0°C  (high =   +85°C, hyst =   +80°C)   sensor = diode           (beep)
temp3:     +39.0°C  (high =   +95°C, hyst =   +90°C)   sensor = thermistor           (beep)
vid:      +0.000 V  (VRM Version 9.0)
alarms:   
beep_enable:
          Sound alarm enabled

```

Are these ALARMs anything special?

edit: also installed a new BIOS today just to make sure this wasn't it. My motherboard is an ABIT IS7

---

### Post by Captain Flamingo on 2007-06-15
I seem to be having a similar problem.

I recently installed Ubuntu and I've been having random moments where the system would "freeze" but my mouse would still be functional. This happens usually during surfing the internet via Firefox. Anyhow, I don't mean to take anything away from this thread, but I will keep an eye on it.

---

### Post by Gmbrdilos on 2007-06-16
I ran into similar problem just yesterday, and I can say for sure its heat.

Problems are clogged fans and heatsinks, especially the CPU and VGA fans.
My CPU heatsink had more dust under it than the entire contents of my house.
Cleaned it with a dry cloth and let it cool for a while.

another important think I noticed was the heat of the videocard. make sure it is properly cooled. decent cards get a tendancy of getting hot.

---

### Post by orb9220 on 2007-06-16
Also your power supply voltages are way out of spec. And may be the main culprit.

Usually when a power supply voltages start varying more than 10% then it is time for a new power supply.

---

### Post by Captain Flamingo on 2007-06-16
I really don't think it's the heat that causes the freezes. In my case, i wasn't even running anything substantial; my laptop was very quiet (if it was to be hot, the fans would surely be running very loudly), and the bottom of it was cool.  

P.S. Just to add, mine often freezes when i multitask.,

---

### Post by Captain Flamingo on 2007-06-16
I think this thread might be useful:
[http://ubuntuforums.org/showthread.php?t=412125&highlight=system+freeze](http://ubuntuforums.org/showthread.php?t=412125&highlight=system+freeze)

Coincidently, one of the members (se2131) had the same computer as me and I have tried what worked for him. However, it hasn't been long enough yet to come up with anything conclusive. I'll probably have a result by tomorrow.

To quote what se2131 did,

[QUOTE=se2131]
First do:

Code:

> sudo nano /boot/grub/menu.lst

and scroll down until you see the line: ## ## End Default Options ## ##

After this, you will see lines that begin w/ title, root, kernel, initrd, and maybe quiet or savedefault.

What you need to do is find the kernel that you are using and edit the "kernel" line.

This is what my edits look like:

> Code:

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c8d81b8b-4a0a-4acb-b18f-6aa156583253 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

Make sure that you edit the kernel that you are planning to use. If anyone knows how to make this option stick for all kernels, please provide your insight.[/QUOTE]

---

### Post by Gmbrdilos on 2007-06-17
k now mine started to crash. I am thinking this might be because of an update.

---

### Post by Captain Flamingo on 2007-06-17
The solution I posted above seems to be working so far. I've managed to go a few hours doing the things that usually lead to a freeze but everything is alright.

I'll keep you guys udates

---

### Post by wtruong on 2007-06-19
I've been getting random freezes too, i just installed some ram so i thought it might be the ram but i ran memtest and it was fine.  If you guys have problems too then, I'm sure we can pinpoint it to something.

I'm running

beryl
firefox
nvidia gfx driver
conky
etc..


So it's not the ati drivers for sure.  But maybe it's the heat,

---

