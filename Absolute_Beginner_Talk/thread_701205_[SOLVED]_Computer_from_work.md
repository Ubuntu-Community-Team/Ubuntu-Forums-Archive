---
title: "[SOLVED] Computer from work"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by carterrocks on 2008-02-19
My sis got a computer from work which has XP professional, its also connected to a network (suppose to be).  Its an RM computer and my intial idea was to install UBUNTU however when I tried to get into the boot menu it freezes.  I tried several times but it just kept freezing.  So I accepted defeat and tried to get into safe mode (back to windows) however that kept freezing.  I need help guys, I want UBUNTU!

---

### Post by hyper_ch on 2008-02-19
if she got it from work, I doubt she got the permission of altering the OS on there.

---

### Post by carterrocks on 2008-02-19
Well my understanding is "they gave her the computer, in doing so allowing her to make any changes to it she wanted to, she gave it me, allowing me to make any changes to it I want to."   Oh and the computer was being thrown away anyway so I don't think they really care what happen to it.

---

### Post by hyper_ch on 2008-02-19
I dunno why you can't enter the bios but before trying, make sure she can really do what she wants to the computer.

---

### Post by carterrocks on 2008-02-19
> **hyper_ch said:**
> I dunno why you can't enter the bios but before trying, make sure she can really do what she wants to the computer.

I think the fact that they were throwing it away kinda suggests they don't care. I've tried getting into the BOOT menu and safe mode but when I try it just freezes.

---

### Post by Iceni on 2008-02-19
> **carterrocks said:**
> I think the fact that they were throwing it away kinda suggests they don't care. I've tried getting into the BOOT menu and safe mode but when I try it just freezes.

Bios or boot menu? Does it make any beeps when booting?

There's a chance some hardware is dead - likely the memory, the psu or the mobo.

If it has two ram sticks you can test a little by removing one of them and boot.

Also try to go into the bios and reset to bios defaults in case someone has been messing around.

---

### Post by carterrocks on 2008-02-19
> **Iceni said:**
> Bios or boot menu? Does it make any beeps when booting?

There's a chance some hardware is dead - likely the memory, the psu or the mobo.

If it has two ram sticks you can test a little by removing one of them and boot.

Also try to go into the bios and reset to bios defaults in case someone has been messing around.

I don't think it does make any bleeps.  I've been trying to get into boot, and have tried with getting safe mode.  It freezes.  I'll  try resetting the BOIS and if that doesn't work I'll open her up and see about her ram.  Thanks for the help- i'll keep you updated!

---

### Post by seventhc on 2008-02-19
Which boot menu, the one thats already on the computer or the menu from the live cd?

---

### Post by philinux on 2008-02-19
Did it work when you got it?

Put the live cd in and see if that boots up.

---

### Post by bumanie on 2008-02-19
What are the computer specifications? If it is an old system say with 256mb ram or something, the latest ubuntu will be hard pressed to run off the live cd or install. May be the bios/cmos needs resetting. As it was a work computer, some settings may have been passworded and haven't been removed properly. As said above, it could also be the hardware is past its best. May be your sister's work got rid of it because it had problems.

---

### Post by carterrocks on 2008-02-19
> **seventhc said:**
> Which boot menu, the one thats already on the computer or the menu from the live cd?

The one already on the computer.  

> **philinux said:**
> Did it work when you got it?

Put the live cd in and see if that boots up.

It works.  I can turn it on and Xp pro starts and (since its was connected to a network) it asks for a username and password.  My sister has tried putting in hers, didn't work, guessing you have to be connected to the network.  I put the live CD in and nothing happened.

> **bumanie said:**
> What are the computer specifications? If it is an old system say with 256mb ram or something, the latest ubuntu will be hard pressed to run off the live cd or install. May be the bios/cmos needs resetting. As it was a work computer, some settings may have been passworded and haven't been removed properly. As said above, it could also be the hardware is past its best. May be your sister's work got rid of it because it had problems.

All I know is that it has a pentium 4 (an improvement on my current PC :D ).  When or if i get into the boot menu I'll see how ubuntu looks, may end up using xbuntu but hey.  I'm gonna try and get into the BOIS when i get home and i think the computer works fine since xp pro loads.

---

### Post by seventhc on 2008-02-19
Ok if it's asking for a user name and password, there might be an arrow in one of those boxes and you can choose not to join the domain.
So since you won't be logging into their network you may be able to go in as just a regular user not on their network.
Also, if you want to install ubuntu you won't need the windows password. Just get rid of windows. ;)

---

### Post by philinux on 2008-02-19
> **carterrocks said:**
>  I put the live CD in and nothing happened.

All I know is that it has a pentium 4 (an improvement on my current PC :D ).  When or if i get into the boot menu I'll see how ubuntu looks, may end up using xbuntu but hey.  I'm gonna try and get into the BOIS when i get home and i think the computer works fine since xp pro loads.

Once in the bios you need to change the boot order to put boot from cdrom at the top. Then the live cd will run.

---

### Post by carterrocks on 2008-02-19
> **philinux said:**
> Once in the bios you need to change the boot order to put boot from cdrom at the top. Then the live cd will run.

So I don't need to go into the boot menu?  I can just change the order and restart the computer, with the CD rom in? Then just change it back (all of this assuming i can get on to the BIOS menu) 

> **seventhc said:**
> Ok if it's asking for a user name and password, there might be an arrow in one of those boxes and you can choose not to join the domain.
So since you won't be logging into their network you may be able to go in as just a regular user not on their network.
Also, if you want to install ubuntu you won't need the windows password. Just get rid of windows. ;)

i don't think there is an arrow and i cant install ubuntu without getting into the boot or bois, but thanks :)

---

### Post by seventhc on 2008-02-19
If the bios is password protected your gonna have to pull the battery for a while so it resets. It looks like a watch battery, then you'll be able to get into the bios.
So you take out the battery, let the computer sit for a while then put the battery back in. If it doesn't reset right away, then leave the battery out for at least an hour and it will reset.

When I was on a computer that was part of a domain, I remember there being a choice. I can't remember the exact wording, but one I would enter UID/PW and join the domain, the other it would just go into the computer and not a part of the network.

---

### Post by dhtseany on 2008-02-19
I'd verify that the memory (RAM) was good in it. Then I'd try running an XP setup off of the install CD and try to format the drive. However, I do agree that it could be a problem with the boot order. Some laptops offer the option to hit F12, F1, F5, etc. to load the boot menu. Also, try removing the HDD then try and boot to the LiveCD. If it then lets you it could be a toast HDD.

---

### Post by bumanie on 2008-02-19
seventhc is correct. I would add that there is some pins next to the battery with a jumper on it. You should also remove the jumper as well eg, if presently on pin 1&2, move it to pin 2&3. Move jumper back to its original position just prior to reinstalling the battery.

---

### Post by carterrocks on 2008-02-20
> **seventhc said:**
> If the bios is password protected your gonna have to pull the battery for a while so it resets. It looks like a watch battery, then you'll be able to get into the bios.
So you take out the battery, let the computer sit for a while then put the battery back in. If it doesn't reset right away, then leave the battery out for at least an hour and it will reset.

When I was on a computer that was part of a domain, I remember there being a choice. I can't remember the exact wording, but one I would enter UID/PW and join the domain, the other it would just go into the computer and not a part of the network.

I researched the computer model (RM) and, thankfully they didn't reset the default password.  

> **philinux said:**
> Once in the bios you need to change the boot order to put boot from cdrom at the top. Then the live cd will run.

THANK YOU SO MUCH!!!!!!!!  I reseted the BOIS so it boots from CD-ROM and...it worked!!!!  I'm eager to find out the computer's hardware.  I ran the ubuntu live cd and usually people say the CD runs a little slow- it was super fast!

---

### Post by SteveHillier on 2008-02-20
What model RM machine is it.  Some of them are pretty ancient and sometimes have non standard hardware.
Ok, if no beep during bios boot try removing ALL RAM.  If if then sings like a bee then at least you know the M/B is alive.  If Multiple RAM sticks try single sticks and check.  
If running Bios gets nowhere try removing the battery and let CMOS discharge.  You sill then have to run though full bios set up thereafter.  
If need be try disconnecting various drives inside.  Are you sure you are getting power though from the PSU.
Have you got a spare CD ROM drive you could use.  Quite often CD Drives decide not to work for no apparent reason.  They are so cheap now that I just put a new one in and get on with life. I have known them even from new not to work and the cost of sending them back under warranty is more than the cost of scrapping them.
Hope some of this helps

---

