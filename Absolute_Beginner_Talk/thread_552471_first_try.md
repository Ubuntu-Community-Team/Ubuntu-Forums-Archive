---
title: "first try"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by tractorman on 2007-09-16
hi there, as a newbie to Ubuntu i just tried to install a version of 7.04 but keep getting the message application failed to initiate 0xc0000006 on K-meleon.exe i am running XP on a Athlon xp-2000 any ideas on where to go?

---

### Post by wpshooter on 2007-09-16
Please describe how it is that you are trying to do installation ?

---

### Post by tractorman on 2007-09-16
thanks for the prompt reply, i set my system to boot from the CD and not much happened so i thought i'd try from Windows and this is when i have the message come up. CD works fine but for some reason the installation freezes

---

### Post by n3tfury on 2007-09-16
> **tractorman said:**
> thanks for the prompt reply, i set my system to boot from the CD and not much happened so i thought i'd try from Windows and this is when i have the message come up. CD works fine but for some reason the installation freezes

not sure how you can say the Cd works fine if you can't boot from it.  have you changed your bios settings to boot from CD?

---

### Post by dppowell on 2007-09-16
When you put the CD in the drive and powered up the machine, what happened?  Were there any error messages then?  As the other poster suggested, you may just need to ensure that your machine is configured to boot from CD.

---

### Post by tractorman on 2007-09-16
CD was checked out on another computer so i am assuming it is fine??? yes i changed my bios setting to boot directly from the cd

---

### Post by caravel on 2007-09-16
Most BIOS's support the F8 key as a means to load the boot device menu.  You can then select the CD to boot from.  This is better than going into the BIOS and selecting the CDROM as the first boot device.

---

### Post by tvrg on 2007-09-16
we still don't know how far you've gotten or what the error was (if any)

---

### Post by Celegorm on 2007-09-16
Did you use the checksum to make sure your download wasn't corrupted?

---

### Post by dppowell on 2007-09-16
Yes, it sounds like the disc is fine...but we really need to learn what error messages (if any) your machine gave when you actually tried to boot.  There may be a problem with your BIOS setup or maybe something else entirely (e.g. Linux barfing on your hardware or whatever).  We can only guess until we find out what happened on boot.

---

### Post by forestpixie on 2007-09-16
if you've set up the bios correctly as you say and it won't boot - did you actually burn the disc as an iso?

---

### Post by dppowell on 2007-09-16
> **forestpixie said:**
> if you've set up the bios correctly as you say and it won't boot - did you actually burn the disc as an iso?

He said the disc worked on another machine, so I think it's probably fine.

---

### Post by forestpixie on 2007-09-16
he also said he'd tried from windows  - just making sure ;) - I've seen more than one 'how do I unzip the file to burn it' thread

---

### Post by tractorman on 2007-09-16
ok, just to clarify,, i booted from the CD directly i get the options screen fine and select either option 1 or 2 things seem to go ok then the screen just freezes. So, then i try to install from windows things seem to go ok till i get a bluewindows box pop up with K-meleon.exe application failed to initialise 0xc0000006

i have seen that other problems are happening with faster cpu's than mine but i do have 1gb ram and 750gb hdd

---

### Post by dppowell on 2007-09-16
> **tractorman said:**
> ok, just to clarify,, i booted from the CD directly i get the options screen fine and select either option 1 or 2 things seem to go ok then the screen just freezes.

It sounds like there might be a hardware component that it's choking on.  What's the last thing printed on the screen before things freeze?

---

### Post by tractorman on 2007-09-17
just tried one more time and i am getting a disk error 80,ax=4200,drive 9f
if that makes any sense

---

### Post by Celegorm on 2007-09-17
It might be worth it to give the alternate cd a try, since this one isn't working. I don't know what else to suggest at this point.

---

### Post by dppowell on 2007-09-17
What Celegorm said--I think that's a read error from the CD.  Maybe the CD drive in the other machine was able to read it, but your drive must be more sensitive.

---

