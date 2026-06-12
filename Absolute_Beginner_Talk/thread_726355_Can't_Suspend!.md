---
title: "Can't Suspend!"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by EJacqmain on 2008-03-16
My Dell Inspiron 1501 laptop will not go into suspend mode completely. When i tell it to suspend, it shows part of a compiz animation as if it is closing a window, and the screen goes blank. The hard drive and wireless card turn off, but the fan keeps going and the power light stays on. It cant be revived from this state. all i can do is hold the power button and force kill it. 

When i first installed ubuntu (7.10), it went into suspend **just fine**. I have an _ATI radeon Express 1150 graphics card_. It took a while, but i eventually got desktop effects to work on it, and as soon as that happened is when this started happening.   I;m thinking that the problem has something to do with my graphics card or compiz.  HELP!

---

### Post by Oldsoldier2003 on 2008-03-16
> **EJacqmain said:**
> My Dell Inspiron 1501 laptop will not go into suspend mode completely. When i tell it to suspend, it shows part of a compiz animation as if it is closing a window, and the screen goes blank. The hard drive and wireless card turn off, but the fan keeps going and the power light stays on. It cant be revived from this state. all i can do is hold the power button and force kill it. 

When i first installed ubuntu (7.10), it went into suspend **just fine**. I have an _ATI radeon Express 1100 graphics card_. It took a while, but i eventually got desktop effects to work on it, and as soon as that happened is when this started happening.   I;m thinking that the problem has something to do with my graphics card or compiz.  HELP!

try turning off desktop effects and going into suspend, this will verify if its a compiz issue.

---

### Post by EJacqmain on 2008-03-16
I just tried that, no luck...

---

### Post by steveneddy on 2008-03-16
[From this thread:]("http://ubuntuforums.org/showthread.php?p=3900319")

> 
The files you will modify are /boot/grub/menu.lst and /etc/default/acpi-support. If you open them with the privileged gedit I described above, make sure to save a backup before modifying them.

You will be adding a kernel parameter to the grub menu list. In the last section, you will see the various menu entries and their parameters. Each of these correspond to the boot menu options you should see when you power up your computer, especially if you dual boot. For more details go to the "grumpymole" link I have provided. At the end of the "kernel" line for the boot session you wish to enable suspend in, add the following to the end of that line :
"acpi_sleep=s3_mode" without the quotations if you use the Proprietary drivers, or
"acpi_sleep=s3_bios" if you use the vesa drivers.
make sure you include a space before you add this.

Now on the the acpi-support file. These should be modified regardless of the driver you are using. Rather than adding options, you will simply be changing their values. What I did was comment out the relevant line as it was originally and duplicate it with the new value below. That way, it's easy to change back by just switching which one is commented. The values to change are:
SAVE_VBE_STATE=false
POST_VIDEO=false

Now suspend to RAM should work. It did for me!! Sorry if this was too long winded, but for newbies like me, the more detail the better. For more details I would definitely recommend checking out the grumpymole link below, it taught me a lot.

Sources:
[http://grumpymole.blogspot.com/2007/...arameters.html](http://grumpymole.blogspot.com/2007/...arameters.html)
[https://bugs.launchpad.net/ubuntu/+s...rt/+bug/139089](https://bugs.launchpad.net/ubuntu/+s...rt/+bug/139089)


This continues to work for me.

---

### Post by EJacqmain on 2008-03-16
ubuntu must have some serious issues with my graphics card, it's been a hassle.    

 After installing (dual boot with XP Pro), i enabled the restriced driver and restarted, worked fine. I could run all the screensavers and things, suspend, ect easily.  But if i tried to enable desktop effects, i would get a message about the "composite extention". It seems that many other people have had the same problem with ATI cards. I eventually stumbled upon a solution on one of the forums.

 I don't remember exactly what i did... it had something to do with "xserver".     All i had to do was type a couple things into the terminal, hit <Ctrl, Alt, Backspace>,login, enable desktop effects, and compiz things started working, BUT NO SUSPEND. 

Is there any hope for a cure in the next ubuntu release?

---

### Post by EJacqmain on 2008-03-17
i tried **hibernating** and WHOA...  everything but the motherboard and graphics card turned off,  and the screen remained on while showing _a mess of color-changing lines and shapes_. 

SO, obviously the graphics card is NOT SHUTTING OFF (not a compiz issue), and its probably not using the ram.    When i try to **suspend** it does the same thing, but the screen shuts off.        

I'm having to use XP right now because i need to suspend a couple times a day, rather than keeping the computer on all day or rebooting.  The only way i can use ubuntu is to boot and shut down.  I LOVE UBUNTU, but this is really my ONLY serious problem.             

Ive installed ubuntu on this laptop three times: first time was when i got fed up with Vista, all went well but i couldn't get effects to work. I came across some things to type into the terminal (I was REALLY a noob then), bad idea, messed it up and reinstalled.  That install went fine too, but i (being unfamiliar with the art of manual partitioning) attempted to but xp on it also, bad idea, messed up ubuntu and eventually had to have my hard drive wiped COMPLETELY.   

I had XP Pro installed FIRST this time, and then used guided partitioning to put ubuntu on. SUCCESS! 

But i still had issues with the eyecandy (main reason i like ubuntu, second to the fact that it is far more stable than Vista).  

So, as ive said in earlier posts, i dug around and found some step by step directions to get things working on my machine.      I only had to type in a couple things, but obviously screwed something up.

I need some step by step help.

---

### Post by EJacqmain on 2008-03-18
The problem is definately the driver for my ATI card. If the restricted driver is **not enabled, suspend works**.  BUT, before i got compiz working, suspend worked even with the driver active.       

**I'm very confused**...   After installing ubuntu, i was propted to install the restriced driver, which I did.  At that point, i could suspend/hibernate but could'nt enable desktop effects. If i tried, i would get a message "The composite extention is not available" (compiz not installed?).   I don't exactly remember what i did, but i installed compiz fusion and, during the install, must have tweaked the driver.

I hear there are two different drivers i can use for my card (ATI Radeon Xpress 1150):
 OPEN SOURCE and CLOSED SOURCE.        

 Which did the restriced driver manager install? 
 Would i have better luck with the other one?  
 Is there a way i can reverse everything i did/ start over as far as my graphics driver is concerned???

  If i disable the driver, does it uninstall it?    And when i re-enable it, does it reinstall it...  because it seems so?     Therefore, if I disable and re-enable the driver, is it "fixed"?  (haven't tried yet)

---

### Post by EJacqmain on 2008-03-18
I"m going to compile everything ive just said above into a new post... 

"ATI driver, Can't Suspend/Hibernate"

---

