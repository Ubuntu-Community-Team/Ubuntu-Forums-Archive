---
title: "i have ubuntu iso: now what?"
date: 2007-05-28
forum: Apple PPC Users
---

### Post by platinum on 2007-05-28
i have the ubuntu iso. how do i burn it to a cd so it is bootable on my mac? my mac doesn't have a cd burner or any os, so i need to burn it on my pc.

thx

---

### Post by reh4c on 2007-05-28
I use Roxio Creator Classic on WinXP.  Select "Burn from Disc Image File" to make the bootable iso CD.

---

### Post by platinum on 2007-05-28
don't have roxio.

i'll use nero. thx

---

### Post by platinum on 2007-05-28
okay

i burned it.

i press and hold option key to get to the boot menu and select the cd drive, and i do. but when i click on the cd drive, it loads to a white screen, and then back to the boot menu with all the colors messed up. it does this with an external usb CD drive. it doesn't even mount with the internal cd drive. it buzzes and hums and what not, then stops.

---

### Post by platinum on 2007-05-28
ugghhhh.

i'm doomed to forever not use this imac.

it's such a waste of a machine.

i'll check back to this post and hope someone can help me [-o<

---

### Post by stmiller on 2007-05-28
What kind of Mac do you have? Some (iMacs in particular) have trouble with the Live CD. Read the PPCFAQs at the link below for some possible tips.

---

### Post by Alterax on 2007-05-29
There is an extension that microsoft made (but does not support) for burning the ISO to a disc.  Don't try to just drop the file on a cd; doesn't work that way since ISO is an actual filesystem, not just a file.

Search on Microsoft's site for the .iso cd burning extension.  Right-click on the ISO once that is installed and it'll give you the option of burning a CD from the image.  Burn that, then boot it in your mac.

After that, good times will be had by all.

--Alterax

---

### Post by EuroCity on 2007-05-29
It's this one:

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

(a so-called Power Toy, but unofficial).

---

### Post by platinum on 2007-05-29
okay, i'll try that.

but i did the same thing in nero (i don't just burn the file as a file. i know how to burn an iso.) i've tried the burn disc image and burining the contents as a bootable disc using USA boot locale and it still doesn't work. i'll try that tool, and that faq. i'll post back with my findings

edit: the faq mentions an imac g3 not booting properly, and to configure x when you are booted, but mine doesn't boot at all! it just hangs, spins the disc inside, and if i try to click on it in the system picker, it inverts the colors on the screen, and doesn't work. i've booted off of a mac os 9 disc before, why won't this work?? (btw, mac os 9 is OLD, so i thats why i want linux) :)

---

### Post by pxwpxw on 2007-05-29
If you are unable to get the imac to boot from the CD drive,  it is possible to do an hd-media install from the downloaded iso on your macos partition, using hd-media install images.

There is an explanation here:

Howto Install/rescue with no cd drive - O/F booting

[http://ubuntuforums.org/showthread.php?t=390770&highlight=hd-media+install+apple](http://ubuntuforums.org/showthread.php?t=390770&highlight=hd-media+install+apple)

---

### Post by deeteesbeard on 2007-05-29
> **platinum said:**
> okay, i'll try that.

but i did the same thing in nero (i don't just burn the file as a file. i know how to burn an iso.) i've tried the burn disc image and burining the contents as a bootable disc using USA boot locale and it still doesn't work. i'll try that tool, and that faq. i'll post back with my findings

edit: the faq mentions an imac g3 not booting properly, and to configure x when you are booted, but mine doesn't boot at all! it just hangs, spins the disc inside, and if i try to click on it in the system picker, it inverts the colors on the screen, and doesn't work. i've booted off of a mac os 9 disc before, why won't this work?? (btw, mac os 9 is OLD, so i thats why i want linux) :)

Just burning the iso with nero should work as it's an image of a disc that you are burning, it worked for me.
I have a powerbook G4 ti that I installed 6.1 onto. I booted by holding down the c key on startup. Just make sure it's the ppc iso you have downloaded ;)

---

### Post by platinum on 2007-05-29
well, i tried that a few times. it just buzzes and hums a bunch of times with the internal disc drive, so i use an external one that is KNOWN to work. and it mounts the disc fine in the system picker, but when it goes to boot off of it, it inverts the colors, and goes back to the system picker.

when i hold c, it inverts the colors, and goes to a question mark flashing on a folder, and just sits there, then boots too the hard drive.

that install guide for computers without a cd drive doesn't make a lot of sense. i've already downloaded the iso images of the full install cd, so i'm guessing i need to use the hd-media thing. but all i see is configurations for machines that have os x. this thing has os 9.2.2. so i really have no idea what to do.

so let me try this once more in nero: can you tell me exactly what you did in nero to burn it (like step by step)? i have nero 6. does it help to burn at a slow speed?

thx guys! you've been a good help so far!

---

### Post by platinum on 2007-05-29
i think i know what part of the problem is (and even this is stupid)

i used md5 checksum on this image (on three different downloads), and there are 45 errors before i even burn it. i burned it slow, 45 errors

i'll keep trying

---

### Post by platinum on 2007-05-29
agghhhh!

so i try booting from the disc.

after several tries and several discs, i get to a command prompt. i press enter to boot, it tries to load the ramdriver, and a file is corrupt.

so, i am going to attempt to download from a different mirror, and hope that it passes the checksum

---

### Post by pxwpxw on 2007-05-29
> **platinum said:**
> 
that install guide for computers without a cd drive doesn't make a lot of sense. i've already downloaded the iso images of the full install cd, so i'm guessing i need to use the hd-media thing. but all i see is configurations for machines that have os x. this thing has os 9.2.2. so i really have no idea what to do.
!

This one:
[http://ubuntuforums.org/showthread.php?t=390770&highlight=hd-media+install+apple](http://ubuntuforums.org/showthread.php?t=390770&highlight=hd-media+install+apple)

Thanks, you are quite right, it is for macosx and a NewWorld mac, I will add a note.

However it should be possile to do a hd-media + iso , or a netinstall on and OldWorld with macos9, as outlined in the same thread.

---

### Post by deeteesbeard on 2007-05-30
> **platinum said:**
> well, i tried that a few times. it just buzzes and hums a bunch of times with the internal disc drive, so i use an external one that is KNOWN to work. and it mounts the disc fine in the system picker, but when it goes to boot off of it, it inverts the colors, and goes back to the system picker.

when i hold c, it inverts the colors, and goes to a question mark flashing on a folder, and just sits there, then boots too the hard drive.

that install guide for computers without a cd drive doesn't make a lot of sense. i've already downloaded the iso images of the full install cd, so i'm guessing i need to use the hd-media thing. but all i see is configurations for machines that have os x. this thing has os 9.2.2. so i really have no idea what to do.

**so let me try this once more in nero: can you tell me exactly what you did in nero to burn it (like step by step)? i have nero 6. does it help to burn at a slow speed?**

thx guys! you've been a good help so far!

From memory as I'm at work and don't have a copy of nero handy.
First download the .iso image and make sure it matches the md5 checksums
Then fire up nero (I also use version 6), cancel the window to start a project if that comes up, then click burn image (I think it's in the File menu), browse to where you saved the iso, select it and click ok, accept the burning defaults and click burn, put your blank cd in.

I hope once you get a good .iso image your install problems end, good luck :)

---

### Post by platinum on 2007-05-30
okay.

i've done exactly what you said, and i verified that the iso has no errors (ZERO ERRORS! :D )

i put it in the cd drive, it buzzes, hums, tries to load, then doesn't.

i put it in the external drive, and the thing loads, then inverts the colors, goes back to the system picker, and tries to load again.

i don't get it. i can't even select this as a startup disk in os 9.

maybe i should just get os 10 and go from there, because this thing is starting to piss me off. would resetting the open firmware fix this?

anyway, you guys have been extremely helpful. i'm gonna figure this damn thing out one way or another

thx

---

### Post by deeteesbeard on 2007-05-30
What mac do you have again?
Does the cd mount ok in os9?

---

### Post by luckyd on 2007-05-30
Try an alternative install cd.

---

### Post by deeteesbeard on 2007-05-31
> **luckyd said:**
> Try an alternative install cd.

That sounds like a very good idea to me.

---

### Post by platinum on 2007-06-01
it's an imac G3, 400mhz, 40gb, 512mb ram, ati 8mb, slot loading cd.

i've tried 3 different ubuntu discs from 3 different mirrors, and same problem: it mounts, then the colors invert, goes back to the system picker, and mounts again.

it mounts my os 9 disc fine (only on the external drive tho. i wonder if i could take a normal cd drive and manufacture it into the imac (taking out the slot loading one and replacing it). it would be cheaper than buying a new one. i'll see how much they are first. maybe a laptop one will work?

we'll se

---

### Post by dwingojr on 2007-06-01
I used the ISO Recorder mentioned earlier, but had the same problem with my G3. I ended up buying a new CD/DVD and replacing the old CD unit. Worked perfectly. With that old machine, it could still be a hardware issue. I, too, was able to mount the OS9 CDs, but found that the install failed on one or two of the discs. All was well once I replaced the hardware that I got on Ebay for about $15US.

Good luck!

---

### Post by bijan588 on 2007-06-02
well when i get to install it says blablaqbla.dat is corupt:o

---

