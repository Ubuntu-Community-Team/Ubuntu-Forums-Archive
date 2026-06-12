---
title: "Help! Blew everything &amp; cant get past BIOS."
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by ljk on 2007-07-06
Hello,

I did something extremely stupid just when everything was sailing along beautifully.

In "Synaptic"  I selected a package to install but became impatient after a couple of hours of watching a spinning circle (clock???) so I tried to cancel the operation - I couldn't click the cancel button as all buttons were dimmed while the spinning circle just kept on spinning. I tried "esc" by itself and then in combinations with "Alt" and "Ctl" and with "Alt+F4" but, having no luck, I pressed the power on/off key; something I tell others NEVER to do.
 
Now the computer (an NEC La Vie laptop) starts; the usual BIOS screen appears and then a black screen for less than 1 second where the message appears to say "NT undetected" on the lowest of 3 lines (it's so fast that I can't read it all).

I tried using a bootable CD with "Supergrub" on it but was unable to boot into Ubuntu or into Windows XP Home (I had a dual boot system using the Wubi installer).

I then tried the Windows installation CD - apparently there is a "recovery" utility but also failed with that.

The problems are all my fault for doing a stupid thing but I'm sure I have not lost everything. If I can get the laptop to boot then I might be able to salvage and rebuild the OSs.

Can anyone help? Please.

---

### Post by Maxtorm on 2007-07-06
Have you confirmed it isn't a hard drive failure?  The NTLDR (it sounds like) problem would indicate it can't find a boot record, but powering off in the middle of a package update should not cause that problem.  In fact, the interminable installation was probably a symptom of the failing drive rather than the cause.  Can you boot using the Ubuntu live CD?  If so, if you go through the steps as if you are going to install to the hard drive, does it properly detect your hard drive?

---

### Post by swisscow on 2007-07-06
Read somewhere recently about a guy who did a similar thing. Had to remove the power and the CMOS battery, leave it for a few minutes, then put it back together again. The system then seemed to clear itself and all was ok once more. I don't know if this would solve your problem and if even a laptop has a CMOS battery (?????????) or how you could get at it, but it's a thought.

Good luck

---

### Post by moredhel on 2007-07-06
It was probably stuck like that because it needed you to do something - you should of pressed the black triangle to show the details and it was probably a license agreement. :(

---

### Post by cosborn72 on 2007-07-06
Did you use supergrub just to boot, or did you use it to repair GRUB?  When you tried to use it to boot, did it show a list of partitions to boot to?

---

### Post by ljk on 2007-07-06
Thanks to all for your advice.

The [Wubi ]("http://wubi-installer.org/")installer allows you to run Ubuntu without any partitioning and I had Ubuntu running from the same drive as Windows XP home.

I was able to follow some advice I found on the internet and use the Windows install CD to repair the damage. On a previous attempt I was unaware of some the commands I should have used

On restart I checked Windows was running OK. It seems the same as it was before the disaster struck.

Unfortunately, when I re-booted and selected Ubuntu to start, the progress bar on the splash screen stopped shortly after it started and just hung there so I've now uninstalled it and hope to install again sometime soon.

Again many thanks to everyone for trying to help.

---

