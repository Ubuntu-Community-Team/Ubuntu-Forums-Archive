---
title: "[SOLVED] Nuking a computer"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2008-03-08
I nuked one of my old computers using Darik's Nuke and Boot and now when I start it up, the BIOS doesn't show up either. Before I nuked it, it would show me the 'Dell Optiplex' and the option of changing the boot order etc.

Does this mean that DNB nuked the BIOS as well, or am I missing something?

---

### Post by freelinuxhelp on 2008-03-08
I doubt the nuke cd altered or deleted the actual BIOS, but I've seen some HP and Dell machines (and IBM machines did this in the mid 90's) that used a utility partition on the hard drive to store some of the configuration info. Can you boot to a live CD and see what's going on?

---

### Post by Tatty on 2008-03-08
As far as I am aware, the BIOS is stored in ROM on the motehrboard, so you cant remove it.

But dont hold me to that...


Is absolutely nothing showing up when you switch on?

---

### Post by Inxsible on 2008-03-08
> **Tatty said:**
> As far as I am aware, the BIOS is stored in ROM on the motehrboard, so you cant remove it.

But dont hold me to that...


Is absolutely nothing showing up when you switch on?That is exactly what I thought, that the BIOS is in it own little flash memory and not on the drive.

and you are right, when I start up the computer now, it shows me nothing. The screen doesn't even flicker !!

I will try the live CD...if only I can find it soon enough !

---

### Post by Inxsible on 2008-03-08
Ok I tried the Live CD...and nothing happens which is what I thought.

It does not even give me options to boot from the CD...so I hadn't hoped for much.


Any new ideas ?

Maybe I would have to flash the bios again :(

---

### Post by freelinuxhelp on 2008-03-08
Unplug the power and remove the motherboard battery for about an hour, then replace it and try again.

---

### Post by halitech on 2008-03-08
> **Inxsible said:**
> 

Maybe I would have to flash the bios again :(

did you already flash the BIOS once or are you referring to using the nuke and boot cd? Chances are, if you can't see anything on your screen, trying to flash it (or use the nuke and boot cd) isn't going to work. Do you have a spare monitor you can try and see if its the monitor? same with video card as well.

---

### Post by Inxsible on 2008-03-08
> **freelinuxhelp said:**
> Unplug the power and remove the motherboard battery for about an hour, then replace it and try again.Ok. its worth a try. 

But could you please tell me how it will help ?

killing the power will restore the bios? I am confused...sorry !

---

### Post by Inxsible on 2008-03-08
> **halitech said:**
> did you already flash the BIOS once or are you referring to using the nuke and boot cd? Chances are, if you can't see anything on your screen, trying to flash it (or use the nuke and boot cd) isn't going to work. Do you have a spare monitor you can try and see if its the monitor? same with video card as well.
No I didnt try anything with the BIOS. I just used DNB to nuke the drive, since I am trying to give away the computer...but after using DNB (which succesffully erased my drives) I can't get my BIOS to come up at all, which is why I thought that my BIOS probably needs to be flashed ( I havent flashed it yet)

---

### Post by halitech on 2008-03-08
killing the power and removing the battery will force the BIOS default settings back in, just in case it's a wonky setting in the BIOS

---

### Post by jken146 on 2008-03-08
You could try flashing the bios (see your motherboard's documentation for how to do this -- it will involve shorting a jumper somewhere) to reset that to its defaults.

---

### Post by halitech on 2008-03-08
> **Inxsible said:**
> No I didnt try anything with the BIOS. I just used DNB to nuke the drive, since I am trying to give away the computer...but after using DNB (which succesffully erased my drives) I can't get my BIOS to come up at all, which is why I thought that my BIOS probably needs to be flashed ( I havent flashed it yet)

If nothing comes up on your screen, pretty much impossible to get it to boot and flash the BIOS cause you still need to see in order to flash it. when you turn on the power, do you hear any of your fans kick in on the tower itself?

---

### Post by freelinuxhelp on 2008-03-08
That is a way to reset the BIOS.
I just wouldn't think the nuke cd would kill your BIOS.

If the BIOS is actually corrupted or deleted, I don't think you can flash it from a floppy disk, because it won't know to look for a floppy disk.

---

### Post by Inxsible on 2008-03-08
halitech..... yes the fans kick in and i do hear some noises from the tower

freelinuxhelp and everyone else  thanks for your responses

I have unplugged the computer and the BIOS battery and now the wait begins !!!!

---

### Post by halitech on 2008-03-08
so at least we know at this point that the power supply is good. Do you have a spare monitor and video card? It could also be the monitor or the video card.

---

### Post by crjackson on 2008-03-08
> **Inxsible said:**
> halitech..... yes the fans kick in and i do hear some noises from the tower

freelinuxhelp and everyone else  thanks for your responses

I have unplugged the computer and the BIOS battery and now the wait begins !!!!

I hope this works out for you, but I've got tell you something.  Some years back, Compaq starting putting a BIOS loader on a special boot area of their systems.  This loader would boot only enough to run a BIOS configuration utility (which is also a file stored on the HD).  The only thing that would work on these systems without that loader is the floppy drive.  If you (like me) blew away that partition, you have to go to the website and download a floppy image.  Boot from the floppy and it will bring up a utility that will initialize creating the boot utility on the NEW (or blown away) HD.  If this is what happened to you, you will have to obtain that utility floppy image (or perhaps now days it's a CD image) and reinstall the maint. bios partition to the drive.

Good luck, perhaps you didn't get bit by this...

---

### Post by Inxsible on 2008-03-08
> **crjackson said:**
> I hope this works out for you, but I've got tell you something.  Some years back, Compaq starting putting a BIOS loader on a special boot area of their systems.  This loader would boot only enough to run a BIOS configuration utility (which is also a file stored on the HD).  The only thing that would work on these systems without that loader is the floppy drive.  If you (like me) blew away that partition, you have to go to the website and download a floppy image.  Boot from the floppy and it will bring up a utility that will initialize creating the boot utility on the NEW (or blown away) HD.  If this is what happened to you, you will have to obtain that utility floppy image (or perhaps now days it's a CD image) and reinstall the maint. bios partition to the drive.

Good luck, perhaps you didn't get bit by this...
Oh !!!

I hope not !!!

---

### Post by Inxsible on 2008-03-08
> **halitech said:**
> so at least we know at this point that the power supply is good. Do you have a spare monitor and video card? It could also be the monitor or the video card.The monitor is good, because I used it as a spare monitor for my laptop without any hitches.

About the video card, I dont think that would be a problem because it was working well until I tried the DNB. but then again, you never know.

I will try it again after about a couple of hours and see if that works (fingers crossed)

if not, then maybe get a bios update in a floppy as crjackson suggested and if that doesnt work....simply trash the damn machine. Too bad for the person I was going to give it away to  :(

---

### Post by halitech on 2008-03-08
I may be on the wrong track but honestly, if the monitor does absolutely nothing when you turn on the system (ie no beeps from the tower, no flicker) then I'm thinking monitor. Does the light come on showing it is getting power?

---

### Post by Inxsible on 2008-03-08
> **halitech said:**
> I may be on the wrong track but honestly, if the monitor does absolutely nothing when you turn on the system (ie no beeps from the tower, no flicker) then I'm thinking monitor. Does the light come on showing it is getting power?it has the amber light from the power cord....which never turns green even when I switch on the computer. I checked the connections as well...nothing seemed amiss.

As of now I am using the same monitor as an extended desktop on my laptop and it works.

I am just afraid it shouldn't be what crjackson suggested, since I have not had a floppy drive since a very long time now...and I would have to probably beg/borrow/steal/buy(heaven forbid !) the floppies to get the system to work again and even that isn't guaranteed.

---

### Post by halitech on 2008-03-08
ok, so the monitor does work but its not getting any signal from the computer. At this point, if resetting the BIOS doesn't work, I would personally (and I could be wrong) have to say its the video card. It may have become unseated or it may have died. Let us know what happens

---

### Post by Duck2006 on 2008-03-08
Could it be the RAM, i know if you have bad RAM the system may not boot up even in to BOIS.

---

### Post by halitech on 2008-03-08
normally if its RAM the system will sit and beep like mad although if the speaker has been disconnected ....

---

### Post by Inxsible on 2008-03-08
> **halitech said:**
> normally if its RAM the system will sit and beep like mad although if the speaker has been disconnected ....

no beeps from the computer at all.. Speakers were connected.

also, everything worked before...so I am guessing it was probably related to me using the DNB....

well....we'll see !

will report back if things work or don't

---

### Post by halitech on 2008-03-08
before you did the DNB, when you powered on the machine, did it make a single beep? I know mine will beep once then load the boot screen showing the memory test and boot option keys when I first power it on.

---

### Post by Inxsible on 2008-03-08
Alright !!!

I just let it stand and now it works !!

Weird but true !!

Thanks a bunch freelinuxhelp and halitech and everyone else.

I guess it just needed the plain old reset for the BIOS values :)

I am happy now :)

---

### Post by halitech on 2008-03-08
glad to hear you are back up without it being a hardware failure or needing to try and get the BIOS reloaded as was mentioned earlier (sounds like that could be a real pain and makes me glad I build all my own systems)

---

### Post by freelinuxhelp on 2008-03-08
glad to hear it :-)

---

