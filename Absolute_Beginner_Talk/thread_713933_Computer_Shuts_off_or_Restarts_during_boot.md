---
title: "Computer Shuts off or Restarts during boot"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by bacardee on 2008-03-03
Hi, I've been trying to install Ubuntu 7.10 for a while now. I have tried 3 different versions, 64bit, 32 bit, and 32 bit alternate(text installer).

My problem is, that when I select start or install ubuntu, it loads, gets to the orange colored screen, plays the login sound and then my computer abruptly shuts off. So I tried installing it with the text installer, worked fine and then when I went to login to ubuntu, computer just shuts off.

I should probably note that this is not only an ubuntu issue, I had the same exact problem when trying to install vista from a boot cd. It would get to the graphical loading bar, and then shut off. I DID actually get it part way installed, then it restarted to finish the installation, but of course it would just shut off when I tried getting past the loading screen. For some reason I can install windows XP perfectly fine. I just reformated about a week ago. Media center edition, works great but I would love to test out ubuntu and possibly vista

thanks in advance for any help

Specs: everything is about 2 months old

Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+, MMX, 3DNow (2 CPUs), ~3.0GHz
Memory: 2046MB RAM
DirectX Version: DirectX 9.0c (4.09.0000.0904)
Card name: Radeon X1950 Pro 512.0 MB 256mb interface
Hard Drive: WDC WD2500KS-00MJB0 250 GB


By the way temps are fine, so its not a heating issue, cpu is at a constant 35-40 celsius

---

### Post by dstew on 2008-03-03
> when I went to login to ubuntu, computer just shuts offI take it that you were able to install Ubuntu using the text-based installer, but when you boot the Ubuntu system, it shuts off at the point you begin to log in. This is probably a conflict with your graphics display adapter. Can you boot Ubuntu in recovery mode (that is, get to a working command line)? If so, you can from there do **sudo dpkg-reconfigure xserver-xorg** to set up your graphics display. Choose the vesa driver. Then, reboot. You should get a functional but perhaps clunky desktop. If you do, look in System --> Administration --> Restricted Drivers Manager and see if you can install a restricted driver for your display adapter.

---

### Post by {BzF}~JOKesTER on 2008-03-04
Clarify: The Screen Goes Off Or The Tower Itself Shuts off?

If It's Just The Screen - Go Into Your Bios And Change The Primary Display Adapter To You ATI Radeon Instead Of Onboard Graphics.

---

### Post by slughappy1 on 2008-03-04
I have a problem very close to this. But my problem was that Vista would do what you said. On the loading screen, the progress bar would get about half way across one time, freeze, blue screen of death, crash my system, and then reboot. I could never get Vista to load properly. I also had Ubuntu installed using the Alternate CD (so I could encrypt my hdd). I followed the guide [here]("http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html") to create a partition for Vista and to also encrypt Ubuntu. I installed Vista first. It was able to get installed almost all the way but then when it was rebooting so I could enter my username and password, it would freeze. I took the DVD out and rebooted and Vista was able to finish installing and load properly. I then followed the guide above and installed Ubuntu. But I still had the Vista problem. I was able to get around this by when Vista crashed, I will load Ubuntu until it gets to the screen where I enter my encryption passphrase. I did NOT enter my passphrase, instead I have to hold the power button until my computer turns off. Then I am able to load Vista and it works. 

After updating Vista fully and using this method several time. Vista has started to work properly (it actually loads most of the time), but when it doesn't I do what I said above and it works every time.

I am not sure this will help, but I thought I would share my experience and hope it does. I was able to get Ubuntu and Vista too dual boot with a problem that sounds similar to yours.

Edit

I couldn't install XP on my computer. It never worked properly because it wasn't designed for it so the drivers weren't very good. I have a Dell Inspiron 1420n by the way

---

### Post by WildeBeest on 2008-03-04
I had exactly the same problem as you, but XP installed fine.

Never did get it resolved. Still have two open threads on it.
[Thread1]("http://ubuntuforums.org/showthread.php?t=641427")
[URL="http://ubuntuforums.org/showthread.php?t=639135"]Thread2
[/URL]
So I gave up on it. Left that machine with XP on it and gave it to my wife.

I have another machine with the exact same HW set and the Live CD runs on it. Didn't do the install on it for a variety of reasons.

---

### Post by bacardee on 2008-03-08
> **{BzF}~JOKesTER said:**
> Clarify: The Screen Goes Off Or The Tower Itself Shuts off?

If It's Just The Screen - Go Into Your Bios And Change The Primary Display Adapter To You ATI Radeon Instead Of Onboard Graphics.



The tower ( or I should say box )  shuts off completely, sometimes it stays off sometimes it reboots


[IMG]http://www.pro-clockers.com/images/review/apevia%20qpack/X-QPACK-AL-1_500.jpg[/IMG]

---

