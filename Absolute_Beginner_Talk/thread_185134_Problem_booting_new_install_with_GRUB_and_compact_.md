---
title: "Problem booting new install with GRUB and compact flash"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by dan_99503 on 2006-05-31
I am building a breezy server and cannot get it to boot properly after install. 

/dev/hda is a 128MB compact flash with IDE adapter (looks like a 128MB HD)
/dev/hde is an 80GB HD
/dev/hdg is an 80GB HD


I have installed /boot with boot enabled on /dev/hda

I have setup a softraid mirror on the other two drives. 

Each drive has three partitions in three mirrors
/dev/md0   -- /
/dev/md1   -- /var
/dev/md2   -- swap

I have this same configuration running on another system and I must have missed this problem. 

When the sytem reboots after installation it comes up to display the word

GRUB 

on the screen and then does nothing else. 


I have already tried grub-install /dev/hda1, it accepted the command but nothing changed. 

One thing I should mention is that the two harddrives are on a built-in promise IDE raid controller but I'm not using the raid hardware setup. The OS and BIOS recognize the drives and can use them without setting up a raid in the BIOS.

I have already tried using the hardware raid and after our trouble and reading about the lack of support for 2.6 hardware raid we gave up on it and decided to go with the compact flash for the boot device. 

Any suggestions are greatly appreciated. 

- Dan

---

### Post by dan_99503 on 2006-06-02
I just tried Dapper Drake with the same results. 

Does anyone even know what GRUB is missing when it hangs after GRUB?

- Dan

---

### Post by dan_99503 on 2006-06-08
Update:

Drives hde and hdg are on a promise IDE softraid controller. I am not using the raid functionality since it is software based and Linux doesn't seem to recognize it. The compact flash IDE adapter does show as (hd0) /dev/hda. 

I have got the system to successfully boot to the GRUB prompt but it's not picking up any of the config files. When I'm at the prompt GRUB see the two harddrives (hde,hdg) just fine and can boot from them to the OS. What is doesn't see is the /dev/hda. If I boot the OS it will see /dev/hda (hd0) fine but not after booting to the prompt with grub. The filesystems on hda (hd0) is ext2 and the others are ext3. 

It looks like that it can boot to the prompt from the compact flash but then fails to recognize it as an IDE device when GRUB starts. I'm not sure if it's initializing too quickly or it's a compatibility issue with the hardware I'm using and the CF card. 

I was a newbie to GRUB and bootloaders when I started this but now I understand much more. I'm thinking about trying lilo instead to see if it has the same problem recognizing the IDE device on boot. 

Any tips are very appreciated 8). 

- Dan

---

### Post by freddyg on 2006-06-17
I am looking to install ubuntu on a compact flash card, i am running an experiment right now with the card installed in a usb adapter. I am curious to see if i have the same issues.
from my research online it appears that there may be future issues with the amount of  writes performed on a compact flash unit. are you doing anything about this issue, or are you doing a custom install of any type?

---

### Post by dan_99503 on 2006-06-18
I am only putting the /boot filesystem on the flash and after I'm done I will set it to read-only. The problem you mention is a real one and  it will limit the number of writes but it's still fairly high. 

I gave up trying to get it working properly on that hardware 8(. There is definitely a bug/hardware compatility issue holding it back.  Even when not installing with the compact flash it was still running into the same problem. 

I tried installing it on a different motherboard with the same hardware and it installed flawlessly. 

The other hardware that was giving me trouble was a TYAN 1U server. After al the trouble I've had with it and it's fakeraid I will buy SuperMicro next time 8). 

- Dan

---

### Post by catlett on 2006-06-18
ACTUALLY, I JUST REREAD THE FIRST POST. ARE YOU GETTING A GRUB PROMPT OR JUST A WORD GRUB? iF IT IS NOT A GRUB PROMPT THEN DISREGARD EVERYTHING THAT COMES NEXT.


You do not have a grub menu created for some reason. You have to enter each line to boot from grub i.e.
```

grub>root  (hd0,0)
grub<chainloader  +1
grub< boot
```
That is a generic entry to boot the first partition of the first drive. You do each of these indicvidually. At the grub prompt, enter "root  (hd0,0)" press enter. You get the grub prompt again, you enter "chainloader +1)", etc....You get the point. The entries that are normally in your grub menu.lst  have to be entered manually one line at a time. This is grub. It is in your system. It just hasn't been totally configured with a menu list.

Try this for starter, see what comes up and if there is an error we'll try and create the proper entries.

---

