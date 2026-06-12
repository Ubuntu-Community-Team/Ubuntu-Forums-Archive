---
title: "[SOLVED] Gutsy freezes frequently"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-11
hello,

I've been using Ubuntu Gursy on an HP Pavillion dv2530 for about one week. Today it froze again (4th or 5th time) for no apparent reason, during normal activity (that is, not after installing/uninstalling a program, for instance, or the like). The mouse just freezes, particularly when I'm browsing the net (on Firefox), and I'm stuck. 

Pressing ctrl+del+delete OR ctrl+del+backspace OR ctrl+del+F1 or the so-called "magic keys" ALT+sys rq doesn't make any difference: only pressing the power button allows me to re-boot the machine. 

I'm new to Linux and don't understand why this happens. I've got plenty of RAM on this laptop, so it shouldn't be a matter of memory (but maybe I just don't know what I'm talking about here)? Can it be a hardware issue? On the other hand, Windows Vista (with all its annoying aspects) never crashed on this machine. 

Any advise will be highly appreciated. Thank you.

---

### Post by PmDematagoda on 2008-03-11
Please do a memory test on the PC using the entry for the Memory Test in the GRUB menu list when the PC is booting. Post the results of that test.

---

### Post by Crooksey on 2008-03-11
Could be an xorg lockup..

Can you post the contents of the file ..

```

/etc/X11/xorg.conf
```

---

### Post by PmDematagoda on 2008-03-11
> **Crooksey said:**
> Could be an xorg lockup..

Can you post the contents of the file ..

```

/etc/X11/xorg.conf
```

It cannot be that because the OP said that the magic sysrq keys do not work, usually if it was an Xorg lock-up then the magic sysrq keys would have had an effect.

---

### Post by smurphy_it on 2008-03-11
What video card is it, an Nvida, Ati, Intel ???  Could try updating the driver (or downgrading).

Could also be a heat issue.  Try using some of the power features to keep a close eye on your temperatures.  Sometimes the fans aren't working properly (or enough) for it.

Did you download ubuntu tweak ?  That has some good profiles in it as well for say performance mode, dynamic mode etc.

Ubuntu tweak can be found on the [getdeb.net]("http://getdeb.net/app/Ubuntu+Tweak") website.

---

### Post by Marianne_S on 2008-03-11
i'm actually experiencing the same problem. and it doesn't seem to be any same connection to with what program or when it happens. sometimes the alt + sysrq - buttons work, sometimes it doesn't. sometimes it is when i am surfing (both with firefox and opera), sometimes when i start a program, sometimes when i haven't started anything. i had the same problem with 7.04 as 7.10

---

### Post by Marianne_S on 2008-03-11
> **PmDematagoda said:**
> Please do a memory test on the PC using the entry for the Memory Test in the GRUB menu list when the PC is booting. Post the results of that test.

btw how do i do this?

---

### Post by deadmnky on 2008-03-11
to do a mem test you resart your computer press esc during the grub boot. highlight the memtest line and pres enter

---

### Post by al.adab on 2008-03-11
Thanks everyone for following this up. 

I'll do the memory test shortly + post the result. 

A few more details might in the meantime help identify the problem: 

- the video card is Nvida, and it's set on "normal" at System>Preferences>Appearance>Visual Effects: shall I set it on "none" instead? 
- the command ctrl+alt+F1 works except when the system freezes (quite annoyingly...)
- the command alt+sys rq (the latter is - on my keyboard - under the key "delete", so I've got to press alt+fn+delete) brings out the window "Save screenshot". There's an R magic word I've come across somewhere (forgotten..): well, I tested that in combination with alt+fn+delete , and the desktop disappeared (but the machine didn't shut down), and had to press the power button in the end. Anyway, alt+fn+delete didn't bring any result whatsoever when the computer froze
- I haven't noticed any abnormal increase of temperature (usually you can feel that on HP Pavillion as the left hand side (near the mouse) tends to become warm if the machine is overloaded, but will try those temperature sensors just in case. What shall I do if they tell me that the temperature is higher than it should?

Anyway, give me an hour or so and I'll try the memory test. Hope to figure out how to do it!

---

### Post by PmDematagoda on 2008-03-11
Actually you can use the magic sysrq keys to get your system back if you do them right.

For example when I face an X-Server crash I kill the X-Server with the I key, switch to a tty using Ctrl+Alt+F1 and then restart the X-Server with:-
```
sudo /etc/init.d/gdm start
```

I have made a guide concerning the magic sysrq keys [here]("http://ubuntuforums.org/showthread.php?t=617349"), you can refer to that from more information.

---

### Post by lloyd_b on 2008-03-11
> **Marianne_S said:**
> i'm actually experiencing the same problem. and it doesn't seem to be any same connection to with what program or when it happens. sometimes the alt + sysrq - buttons work, sometimes it doesn't. sometimes it is when i am surfing (both with firefox and opera), sometimes when i start a program, sometimes when i haven't started anything. i had the same problem with 7.04 as 7.10

I had the same problem with both Fiesty (7.04) and Gutsy (7.10).  I have it solved, but the solution is not for a novice - I compiled a minimal custom kernel, with support for only the hardware that I have in the machine, plus modules for PCMCIA and USB (the machine in question is a laptop).

Note that the machine was rock solid under Edgy (6.10).  After having issues with Fiesty, I downgraded back to Edgy, and ran with that until a few weeks ago.  I ran memtest several times, and it has yet to show any errors.

I'm still not certain exactly what the problem is.  I started suspecting the kernel after I had it lock up while booted to a command line, and running only an FTP program (very low CPU/memory usage). 

One symptom of this lockup - after freezing, the CPU fan would be running at top speed, indicating that something was really pushing the processor (some kind of "endless loop", maybe).

Lloyd B.

---

### Post by Marianne_S on 2008-03-11
> **lloyd_b said:**
> I had the same problem with both Fiesty (7.04) and Gutsy (7.10).  I have it solved, but the solution is not for a novice - I compiled a minimal custom kernel, with support for only the hardware that I have in the machine, plus modules for PCMCIA and USB (the machine in question is a laptop).


yes i read about that somewhere in the forums, but there is no way i am daring (nor have the skills) to try that. i have only recently (september) switched to linux/ubuntu and it was to learn more about computers in general. iow i am definitly a novice still.

---

### Post by al.adab on 2008-03-11
hello everyone
I run the memtest - well, the ten hours later the computer was still "testing" (test no 16, no errors) and had to re-boot it. Hope to hear more on the issue as soon as you've got some possible solution.

---

### Post by holmes85 on 2008-03-13
I'm having the same issue, it usually happens when I'm opening firefox. its crazy bc it never did it before, just recently, like a week ago. its gotta be one of the updates or something.

---

### Post by Marianne_S on 2008-03-13
why is this thread marked as solved?

---

