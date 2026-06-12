---
title: "Picky O/S??"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by wperez on 2006-04-25
hay just introduced into linux through ubuntu and suse, i installed ubuntu fine when reboot is initated after install i get error 18 when the os attepmts to load i'm thinking ubuntu is picky for h/w i looked for the error code and came up empty handed can anyone give me a hand???

---

### Post by nalmeth on 2006-04-25
Not generally picky I wouldn't say
Is that all you get is error 18?
I know you said you couldn't find a more detailed error, but is that all you see?
Do you see "GRUB" loading at the start? 
After what steps do you see the error 18?
What kind of hardware do you have?
I'm just trying to pick out some more info, for when someone more knowledgable comes around.

---

### Post by cestel on 2006-04-25
Instead of starting a new thread, I thought I would add that I am experiencing the same problem.  I am an extreme newbie to linux but not to computers. I just installed the most current Ubuntu on a partion on my 1.3 Gh AMD Athlon machine.  The whole drive is 160 gig and my linux partition is 26 gigs.  When I had the install load Grub and reboot, I get the 

GRUB loading, please wait...
Error 18

message and then the computer hangs.  I have gleaned from various searches that this somehow involves the size of the hard drive.  I have attempted the fixes that I understood (most of which involved playing with the CMOS settings) but was unsucessful.  Now I cannot boot into either linux or windows.  I am sending this message from my laptop.  Does anyone have any suggestions?

---

### Post by echo $USER on 2006-04-25
To OP:

Grub error 18

Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle. Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range).

I searched google for you.  Sounds like your bios doesn't support a hdd of that size.  [Check this out]("http://www.google.com/search?q=grub+error+18&hl=en&hs=qgU&lr=&client=firefox-a&rls=org.mozilla:en-US:official&start=10&sa=N").

To cestel:

You need to clear your CMOS.  Open your box and look for the CMOS jumper,  consult your motherboard manual if you don't know where it is.  If you dont have a jumper, just remove the little battery that looks like a watch battery on steriods for about 30 minutes, then put it back in.  That will return your BIOS to the default setting allowing you to boot your PC.

Hope that helps.

---

### Post by cestel on 2006-04-26
Thanks for the suggestion echo $USER.  Unfortunately clearing the CMOS did not work.  I still come up with the same error.  Does anyone have any mofre suggestions?

---

### Post by echo $USER on 2006-04-26
[QUOTE=cestel]Thanks for the suggestion echo $USER.  Unfortunately clearing the CMOS did not work.  I still come up with the same error.  Does anyone have any mofre suggestions?[/QUOTE]

Are you still getting grub error 18?  or something else now before that point?

---

### Post by cestel on 2006-04-26
Same error as before

---

### Post by cestel on 2006-04-26
Sorry, yes the Grub Error 18

---

### Post by echo $USER on 2006-04-26
Where is your boot partition and on what block is it located?  Also check out your motherboard manufactorer's website and make sure you have the latest bios installed.

---

### Post by cestel on 2006-04-26
Thanks for all your help.  This has been such a headache just trying to get to where I can get back into my windows partition.  I think that I will hold off on delving into Linux until I can get my hands on a dedicated machine or at least a second laptop.  Thanks again!

---

### Post by steve.horsley on 2006-04-27
You should be able to get windows back by replacing the bootloader with the microsoft one. Search this forum for uninstalling ubuntu.

I don't think you can blame Linux for this. I think the MS bootloader would likeky have problems if the windows partition was placed outside of the area the BIOS can address, too. It's just that windows got there first and got the best real estate. Not that that helps at all. Installing a second hard drive for linux might be a good way round the problem.

---

