---
title: "Installed update - Now Gutsy won't start"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by pr0lixity on 2007-12-23
Earlier last week, I installed updates for Gutsy - I thought it was just routine. After I restarted my computer, and chose Gutsy from grub, the loading bar would stop loading at the 3rd bar. Then I tried restarting in Recovery Mode, and it went up to "installing hardware drivers..." and the cursor just kept blinking, and would not go beyond that point. 

I have no idea what happened. I install things and tinker with the computer pretty conservatively. I had just installed amarok, wine, and some other programs. What should I do? Just completely purge and reinstall the whole thing all over again?

---

### Post by spiderbatdad on 2007-12-23
could you post some of your computer specs and video card?

---

### Post by pr0lixity on 2007-12-23
HP tx1000 tablet 
Vista / Gutsy
AMD Turion 64 processor
nvidia graphics card
2 GB RAM
150 GB Hard Drive

---

### Post by pr0lixity on 2007-12-23
Oh, and right before I installed updates, I was downloading Frostwire from the terminal, if that matters at all.

---

### Post by spiderbatdad on 2007-12-24
oh boy scary. do you still have other kernel options in grub boot screen? I'm looking at this thread, but it may not specifically address your issue.[http://ubuntuforums.org/showthread.php?t=648201&highlight=gutsy+update](http://ubuntuforums.org/showthread.php?t=648201&highlight=gutsy+update)

---

### Post by pr0lixity on 2007-12-24
yeah, it looks perfectly normal up to a) loading past the 3rd bar on the regular boot screen and b) "Loading hardware drivers..." and the blinking underscore on the Recovery Mode boot screen.

eeep! I was basically done fixing, installing, updating, customizing, and tinkering with Gutsy and was about to make an almost complete switch from vista. Now i'm stuck here and I don't know what to do.

---

### Post by spiderbatdad on 2007-12-24
Hardy is coming soon and it an LTS so you can get that all tinkered up and go with it for (5 years?) I think.

---

### Post by bodycoach2 on 2007-12-24
Things like this are what teach you: Keep your operating system and programs on the computers hard drive, but keep all your personal files on another drive. Or, at least another partition. Windows XP/Vista, OSX, Linux, Solaris/Unix.....doesn't matter. OS's are getting big and hefty, and something is bound to go wrong. 
[Dban the drive]("http://dban.sourceforge.net/"), and reinstall the system.

---

### Post by trippinnik on 2007-12-24
Woah! Hopefully you didn't nuke your machine yet.  If you press ctrl+alt+F1 you should be able to see the bootup info.  You can post what it says here.  Also before you reinstall everything (if that is what you need to do) you can use the live disk to get you data back by copying it to another drive, computer or whatever you have available.  
These are some of the points that make linux attractive to me, the verbose bootup info if needed and a functional live cd with network access, burning access etc.

---

### Post by pr0lixity on 2007-12-24
don't worry, i'm a pretty responsible new user. and don't worry, everything I have is on a separate external hard drive. I haven't put anything important onto Gutsy because, well, I didn't trust it just yet, not until I at least had it and have been running on it entirely for a good number of months.

I haven't nuked anything yet, nor have I completely given up. I haven't done everything I could yet becuase I had left the Live CD back in my dorm. I'm just fishing for anything and anyone that can maybe help out, or if anyone has had similar problems.

Is there a specific way I can copy+paste the bootup info, or do I have to handwrite it or something?

Thank you all for the help! This is definitely one of the big reasons why I chose to switch, which is the big supportive community. I think I've been lurking around for a few months and never have I had to post a problem becuase you all have been so helpful to other people. I only joined a few days ago because this error is really bugging me! You are all so wonderful!

*sheepishly*btw, what does LTS mean?

---

### Post by pr0lixity on 2007-12-24
when/where do i press ctrl+alt+F1?

---

### Post by trippinnik on 2007-12-25
You can hit those anytime.  What it does is bring up the console or terminal in text only mode.  Usually in Ubuntu you don't see the bootup output but this way you can.  You'll get messages about drivers and services that are being loaded and any errors.  You won't be able to cut and paste from there unless you make it to the text login screen.  
LTS stands for Long Term Service, meaning it will be supported under the Canonical support plans for 4 years and should remain more stable while other releases have more cutting edge packages.

---

### Post by meindian523 on 2007-12-25
If what you want is to see the bootup messages,then what you have to do is not to press Ctrl+Alt+F1,you have to edit the kernel line and remove "quiet".....to do that,press e at the Grub screen,scroll to the kernel line,delete quiet and then press b(for boot).....

Also,LTS==Long Term **Support**

---

### Post by terminal on 2007-12-25
I  really think this is due to wrong root= parameter passed to kernel by grub . Normally in gutsy UUID of partition is passed . If possible try pressing 'e' in grub screen then edit kernel line for look like  /boot/vmlinuz-xxx root=/dev/hda1 ro

Replace /dev/hda1 with partition u have ubuntu on .

---

