---
title: "Crazy things are happening with live disk..."
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by jeremycollins08 on 2008-04-06
Ok, my buddy is wanting me to help him with ubuntu installation. He's doing a dual boot with win xp. I am going to act as i am him, and tell you the problem:

I have the ubuntu live cd, and i put it in and booted up the computer. Ok, so, my ram wasn't at the requirement. The live cd ran ok, but it was very slow, and you couldn't install ubuntu. But, it did load up the gnome desktop with everything fine. One week later, today, I have a wopping 736mb ram now! Now, i put in the live cd, and it came up to the loading bar, and i clicked on Start/Install Ubuntu. It gets all the way to the orange desktop background, and the curser appears, and then the screen goes black, but the ubuntu music plays. Then, the monitor's light goes from Green (on) to Orange (standby). I started up Windows, and it works fine. I just now installed the ram, and started up windows and was amazed at the speed of my computer now. That shows that my monitor does work. But i don't know about the ubuntu. I ran the disk check for errors, and it came out clean. Can someone help me with this?

Here are the specs of my computer:

```
Compaq Presario

3000+*
AMD Sempron TM processor

736MB PC2700
DDR SDRAM memory

80GB 7200RPM
Ultra DMA hard drive

CD-ROM/DVD-ROM 
combo drive
48x32x16x48x max. speed

Processor speed 2.00GHz, 512KB
L2 cache, 333MHz Front Side Bus



```

---

### Post by Bölvaður on 2008-04-06
what about graphic card?

---

### Post by jeremycollins08 on 2008-04-06
> **Bölvaður said:**
> what about graphic card?

VIA/S3G  UniChrome IGP
Internal 32MB

---

### Post by Bölvaður on 2008-04-07
it sounds very strange

the only thing that comes to my mind is that you might be able to fix it by changing the booptup paramters that state the screen resolution.

try run the live cd in save graphic mode with 800x600 resolution.
When I installed 7.04 I had problem the first time because of similar problem.. the monitor was turned off but ubuntu was running (heard the startup music). What I did was change the resolution to maximum by the command  vga=791 I think.

You can try any one of those :


640x480 800x600 1024x768 1280x1024 1600x1200 Ask user at boot
8 bits vga=769 vga=771 vga=773 vga=775 vga=796 vga=ask
16 bits vga=785 vga=788 vga=791 vga=794 vga=798 vga=ask
32 bits vga=786 vga=789 vga=792 vga=795 vga=799 vga=ask

This code : vga=(a number) is supposed to be added at the end of the bootup parameter thingy. Not sure how to get there, could be advanced options. Should be easy to google it.

---

### Post by dstew on 2008-04-07
Yes, the best thing to try is booting in Safe Graphics Mode (press F6 at the opening menu).

---

### Post by Dazed_75 on 2008-04-07
just FYI, you did not say WHICH livecd you were trying (e.g. ubuntu 7.10, kubuntu 6.06, etc) which would be a good idea generally.

I have done a LOT of installs and found a new problem with the 7.10 release which happens on quite a few systems.  The symptoms sound a lot like what you describe.  I know it sounds silly and you probably would have tried this, but ...

It APPEARS that 7.10 livecds may invoke incorrectly a power saver feature on a monitor while booting into the livecd.  The screen goes blank and the monitor shows it is not receiving a video signal.  The solution when this happens is simple; just press the space bar.  The monitor comes back on and everything proceeds normally.

My educated guess is that whatever memory location contains the power saver flag  and/or its coundown timer data is either uninitialized or is initialized to a value such that the power saver is incorrectly invoked soon after the GUI is started.

---

### Post by jeremycollins08 on 2008-04-07
I am running 7.10...and the spacebar worked!!! Wow. That was the easiest fix i've ever had...lol.

Thanks!!!

---

### Post by Bölvaður on 2008-04-07
this is the funniest bug fix I've ever seen

---

### Post by dstew on 2008-04-07
Great job Dazed. Thanks.

---

