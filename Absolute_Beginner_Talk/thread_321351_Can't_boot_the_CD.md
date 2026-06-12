---
title: "Can't boot the CD"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by lesty on 2006-12-18
I Just downloaded Ubuntu 6.10 to try for the first time i downloaded it checked the checksum it was good burnt it and booted it to the main menu selected the first option. It shows the bar bounce back and forth then the bar starts loading from left to right loads all way, then blinks like its changing resolutions or getting ready to boot then a big mess of scrolling text comes with "SQUASHFS" and "Zlib_fs returned an unexpected result" with numbers and letters before and after them. Then it clears the screen and says "user not known to the underlying authentication module" a few times and then just has the blinking "-" sign. (the text is still there the "-" is at the bottom) I've tried both option 1 and 2 (the special gfx one). Each one does the same thing. 

My hardware
Pentium 4 1.5ghz "Willamette" core ( socket 478 )
256mb of SD RAM (PC-133)
Evga Geforce 5200 FX (128mb vram) (Running at AGP 4x)
Asus P4B motherboard with Intel i845 chipset.
Award Medallion BIOS v6.0
D-Link DFE-530TX Ethernet card

I really hope theres some way i can get this to run on my PC.

---

### Post by crazedgremlin on 2006-12-18
I don't think that the Live CD works for everyone.

Try the alternate install cd.
Good Luck :)

---

### Post by lesty on 2006-12-18
Is this a command-line install and if so whats the command to install I'm downloading the alt version now. Oh, and does it give you an option to delete partitions and format drives?

---

### Post by Kapre on 2006-12-18
Try burning ISO again at a lower speed...say 6X...

K

---

### Post by lesty on 2006-12-18
The lowest i can burn at is 10x is that OK?(I'm using a DVD burner and thats the lowest speed). I burnt it at 16x before. I'm using Nero express would it be better if i used the free ware program Ubuntu recommends?

---

### Post by crazedgremlin on 2006-12-18
> **lesty said:**
> Is this a command-line install and if so whats the command to install I'm downloading the alt version now. Oh, and does it give you an option to delete partitions and format drives?

It is an installation cd, but there is no live cd functionality

you boot off of the cd and navigate with the enter and arrow keys


> The lowest i can burn at is 10x is that OK?(I'm using a DVD burner and thats the lowest speed). I burnt it at 16x before. I'm using Nero express would it be better if i used the free ware program Ubuntu recommends?

This makes me think that maybe you burned it too quickly the first time.  Try burning your original cd at the slowest speed possible.

---

### Post by lesty on 2006-12-18
I just burnt it with the program that ubuntu recommends (can't remember the name) at 10x (the slowest i could because of the DVD burner). It gave me the same error ](*,) . I did though try it on my other computer a Pentium 3 running at 1000mhz with 256mb and it works well on here I'm typing this message right now using the live CD. i guess I'll have to use the alternate CD. But what are the chances it would work on my PC if the Live CD didn't? I also noticed the Geforce 5200 wasnt on the supported hardware list but the 5100 and 5500 were. could that be the issue?

Edit: i have an old crappy Geforce 2 MX in the closet i might try and see if that works

---

### Post by macogw on 2006-12-18
DVD burners can go slower than that.  Trust me.  It's the app that determines the speed of the burner.  For instance, the Nautilus cd burner won't let me go below 9x, but I installed GnomeBaker which goes down to 1x.  I use 4x when I burn install cds.

---

### Post by lesty on 2006-12-18
O i thought since 1x dvd seed = 10x speed that would mean thats how slow it could write but i don't think thats the issue since it works on this computer and not on my other one.

---

### Post by lesty on 2006-12-18
Tried the geforce 2 still doesn't work. I have to back up a lot of stuff to try the alt install version. If anyone has any other ideas let me know I'm stumped

---

### Post by balloons on 2006-12-18
there are other live cds. Any of them work? DSL? Knoppix? Puppy? If one works, and the other doesn't we know it's a live cd problem on ubuntu's end. If none work, than more than likely you aren't getting a good burn.

---

### Post by lesty on 2006-12-19
Knoppix runs fine on my machine

---

### Post by lesty on 2006-12-19
I'm using Damn Small Linux right now it has been sometime since i used knoppix (no hardware chnages though) so i though i'd double check and try DSL (which is based on knoppix apernetly). works well but i really wanna get the live version of Ubuntu to run before i format and try to install it

---

### Post by rccharles on 2006-12-19
> **lesty said:**
> Knoppix runs fine on my machine

Perhaps the x11 configuration is incorrect/messed up.

Try copying the x11 configuration from knoppix to your Ubuntu install.

Here is the X11 file to copy:

/etc/X11/xorg.conf

You need to copy it to floppy or some other writable device. Maybe you could define another partition on your harddrive for this file.  I'd use vfat/fat32 so any os can read the file.

Boot up ubuntu.  Let it run until it fails.

press 

control alt f1 

to get into the console. You may have to try several time.

replace the X11 file

sudo cp /floppy/xorg.conf /etc/X11/xorg.conf

control alt f7

#gets you back to x11

control alt backspace

#reloads x11

If the above doesn't work try...

control alt f1 

sudo init 1
init 2


Robert

---

### Post by lesty on 2006-12-19
Very complicated but i understand. but can i use that file from DSL instead of Knoppix because i don't have a copy of it lying around since i havnt used it inawhile

---

### Post by lesty on 2006-12-19
Well my floppy is messed up and not working i think I'm just gonna back-up what i can and use the alt CD for the full install. Can Ubuntu format one partition as opposed to 1 drive and without creating its own. I want to convert the  winblows partition but want to keep the other partition. i gotta change that partition to FAT32 aswell

---

### Post by macogw on 2006-12-19
Yes, it can just format one partition if that's what you want it to do

---

