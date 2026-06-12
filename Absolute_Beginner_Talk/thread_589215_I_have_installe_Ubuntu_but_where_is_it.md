---
title: "I have installe Ubuntu but where is it?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Steve Riley on 2007-10-24
Hi guys,
I am a complete novice at any of the Linux versions but after a lot of reading and watching Youtube videos about how to install Ubuntu, I gave it a shot.
I downloaded the latest version available and followed the instructions to burn the ISO to a CD.
Then I went the whole hog and formatted the C: drive on this laptop.
Yes ... THIS laptop. I'm a believer in playing it safe so I did a fresh install of Win XP using my Dell recovery disks before booting from the Ubuntu CD. I played about with the Linux desktop for a while and then clicked the "Install" icon. 
The partitioning stuff seemed to go OK and so did the actual install process but I must have done something wrong because now, when I start my PC (NO disk in the CD drive) I am given many choices of what OS to boot into.
One is XP which I am using now.
Then there are 3 versions of Ubuntu.
One is a mem check.
One looks like a standard Ubuntu boot
One looks like a safe version.
The problem is that none of the Ubuntu options take me to the Ubuntu desktop.
To be honest, I was expecting to see only 2 options.
"Boot into XP" and be taken to the XP desktop, which is what it does.
"Boot into Ubuntu" and be taken the the Ubuntu desktop, which it doesn't.

Any ideas what I did wrong and how to fix it?
Cheers,
Steve

---

### Post by multifaceted on 2007-10-24
Nothing to fear... the boot loader or "GRUB" is just giving you several options on what to do...

You should automatically boot into Ubuntu after the timer runs out.... if not then, choose "Ubuntu Generic" kernel to start

---

### Post by Mk9 on 2007-10-24
Can you explain what happens when you boot up the machine and choose the default option? It's hard to understand what's happening from your description above.

(NB. Try starting the machine and not making any selection ie. press no keys, and Ubuntu should start automatically)

---

### Post by Steve Riley on 2007-10-24
WOW!! that was quick.
I'll reboot the laptop and make a note of the options I am given.
I dson't think there is a timer on it so just leaving it to do  the default does nothing except leave the options on the screen.
Give me 5 minutes or so.
Cheers,
Steve

---

### Post by Steve Riley on 2007-10-24
OK, that was weird.
I got a pen and paper ready to write down exactly what my options were and rebooted.
I got the list of options up but before I could write anything the screen went black, or rather, dark grey.
I could see there was some hard disk activity so I let it do its thing but nothing happened at all on screen. Then, after 5 minutes, the screen went really black and then the Ubuntu desktop appeared.
I am typing this from Ubuntu, not from Win XP.
Problem solved ...................... I think, lol
Thanks guys.

---

### Post by Sef on 2007-10-24
Evidently it was looking for the video drivers for your system.  Hopefully now, it should just start right up without waiting 5 minutes.

---

### Post by multifaceted on 2007-10-24
Nice... glad to see it booted up for you.

Remember, the LiveCd is roughly 10x slower than it would run of installed on your hard drive. (depending on your computer)

From my experience, Ubuntu runs ***SLOoOoOW*** as a live CD versus from a hard disk on older machines, or one's with limited memory.

---

