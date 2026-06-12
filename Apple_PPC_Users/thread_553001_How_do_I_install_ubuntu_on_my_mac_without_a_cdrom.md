---
title: "How do I install ubuntu on my mac without a cdrom?"
date: 2007-09-17
forum: Apple PPC Users
---

### Post by OscarWabbit on 2007-09-17
hi

i am trying to install ubuntu as a 2nd OS on my imac g4 but my cdrom drive is buggered.

how can i do this?

i have a spare external hard drive but it seems the desktop version of ubuntu is setup to install from cdrom..

i would really appreciate some help

thanks

---

### Post by pxwpxw on 2007-09-17
**OscarWabbit**
You can do a network install or hd-media install, depending on wha you have there.
You dont use the Desktop install cd.
Have a look at Section 4 and 5 of the Install Guide, and my post here:

[http://ubuntuforums.org/showpost.php?p=2887410&postcount=4](http://ubuntuforums.org/showpost.php?p=2887410&postcount=4)

---

### Post by OscarWabbit on 2007-09-17
hi pxwpxw

that looks like just the info i am searching for.

thanks, i will see how i get on with that.

i'll report back here if i get stuck... :D

many thanks, your help is appreciated.

Oscar

---

### Post by OscarWabbit on 2007-09-24
hi

ive tried to follow these instructions but got completely lost.

im using an imac g4 ppc - is this a New Age mac or an Old Age mac?

the instructions seem to be for a new age mac.

ive got an external free fireware 125GB disk and i want to install from that.

i copied the feisty 704 iso files to that disk along with what i thought were the right boot files but when i select to boot from that disk i get a big X on the screen and the computer just halts.

could anyone advise me please how i install from an external firewire drive, i want ubuntu to be on that drive too, not on my main os x boot disk.

cheers

---

### Post by Falx on 2007-09-24
Hm, this is also what I'm looking for, it seems.

I'd like to install Xubuntu on an old PowerMac 7500 with a G3 500Mhz upgrade processor. The disc drive is wee bit wonky so a network install may be my best bet for getting it to work. It might seem like a chore but it's something I'd like to get working as a backup machine, etc.

Thanks for the info, pxwpxw.

Now to scrounge up some additional RAM...

---

### Post by pxwpxw on 2007-09-24
> **OscarWabbit said:**
> hi

ive tried to follow these instructions but got completely lost.

im using an imac g4 ppc - is this a New Age mac or an Old Age mac?

the instructions seem to be for a new age mac.

ive got an external free fireware 125GB disk and i want to install from that.

i copied the feisty 704 iso files to that disk along with what i thought were the right boot files but when i select to boot from that disk i get a big X on the screen and the computer just halts.

could anyone advise me please how i install from an external firewire drive, i want ubuntu to be on that drive too, not on my main os x boot disk.

cheers

iMac g4 is  a NewWorld. But  there is a problem doing the hd-media  install FROM an external drive.

I tried  to install from an external, and there was (a) the problem of booting the install kernel from there and then (b) with the installer finding the iso on the external. I could do (a) from open firmware, but the installer got lost  with (b). It is the hard way to do it.

The install should work if you can put the installer kernel and initrd and the iso on the INTERNAL drive for the install to the external firewire drive. But there is a fixup needed with external firewire to get it to boot after the install finishes (same problem arises if you used a normal install CD), and you can use the internal stuff in rescue mode to sort this out.
Works best if you can provide a boot partition on the internal.

Sounds difficult? You need to be enthusiastic, but the external firewire system works well for me with g4 and g5, I use a Apple_Bootstrap partition on the internal drive to boot it, as wel as Macosx and linux on the internal, but can also boot from Apple_Bootstrap partition on the external. But usb external is another story.

---

### Post by OscarWabbit on 2007-09-24
my apologies, im actually on an IMAC G5 (not G4 doh!)

all i want to do is install ubuntu on this external firewire drive.

i have already installed Tiger on this firewire drive before with no problem by doing a "Restore" to the firewire drive of the install CD and then pressing Alt on bootup which gives you the firewire bootup menu where you can pick which disk you can boot from.  or you can select that disk in the Preferences application so it automatically boots from that disk.

so with Panther, i installed from the firewire drive to the firewire drive which is exactly what i want to do with ubuntu.

is this not possible?




also, i do have a couple of USB drives, one 5gb which i could wipe and use for the install, but im sure ive read that it is not possible to boot an imac g5 from usb, but the ubuntu instructions say you can. i tried to follow the ubuntu install instructions from usb and it didnt work.



im going to give up soon, this is too much like hard work. :(

---

### Post by pxwpxw on 2007-09-25
**OscarWabbit**

Sorry, I missed your post. 
No you cant do ubuntu like macosx on external firewire, it is just a different system.

If you have a cdrom drive and the ubuntu install cd, you just run the installer and install to the external firewire drive.
Now, there is a catch with the ubuntu (and others) installer because the yaboot bootloader does not get installed properly at the end of the install when everything else is installed,  
There are 2 ways to fix this. If you are very happy with command line installers, there is a patch I have for the yaboot installer which will get yaboot correctly installed, but you have to run the patch during the install. 
The other way is to let the standard install finish and fix up the yaboot boot loader partition afterwards, which you can do mostly from MacosX if you have it.
I hope I have the story right this time.:confused:

Edit, except that this thread is about  NO cdrom drive.:confused::confused:

---

