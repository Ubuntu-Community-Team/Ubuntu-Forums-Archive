---
title: "OldWorld PB G3, BootX"
date: 2008-09-01
forum: Apple Hardware Users
---

### Post by sourman on 2008-09-01
Hi!

I've been searching everywhere but still haven't found the answer.
I have a PrettyDarnQuick PBG3 and I'm trying to get the Ubuntu on it.
First time a succeeded to get it install the ubuntu, but it failed the timezone config and later when verifing the CD it hanged on 98%.
Ok, so I did a hard reboot and thought that maybe the install CD is corrupt. So I downloaded a Debian businesscard iso, burned it and tried to boot it.
The kernel is loaded but after the line MMU exit it hangs and after some minutes it boot into OS9.
The same goes on with Ubuntu CD.

I haven't got a clue what is going on.

Ant help?

---

### Post by tiresia on 2008-09-01
Have you ever changed anything in the hardware? Please, give more informations about your mac (HD, memory), and how did you burned the installer (which version of ubuntu, which version of debian?).
Do you have OS9 installed?
When I installed Debian/Ubuntu on OldWorld Machines, I had such problems, because I had an USB PCI-Card.

---

### Post by sourman on 2008-09-04
it's a PDQ 333MHz, 320MB RAM, an internal original 6GB! HDD and an original CD-ROM.
I haven't made any changes in hardware. I have a basic OS9 installation and I have three burned CDs all burned in OSX from .iso (Ubuntu Live, Debian 4.0 businesscard iso and a Ubuntu 6.06 LTS .iso)
The Ubuntus stop at arch exit line (or smth like that).

that else?

---

### Post by tiresia on 2008-09-04
Sorry for my question, but are you sure that it is a PDQ Powerbook g3?
According to Mactracker, there is no PDQ Powerbook with a processor at 333MHz.
Do you have a Floppy Disk Driver? If not, it is for sure not a PDQ Powerbook 
If it is a Lombard, it should be NewWorld, and you can/must start the Ubuntu or Debian Installer just by pressing C at boot.

---

### Post by sourman on 2008-09-04
you're right. the fastest PDQ is 300MHz, but mine has a 333MHz G3 dunno how. But it's definetly an PDQ because I had to use the XPostFacto to install the Panther and it doesn't have any USB ports. Pure oldskol machine... and it has  the metal cover covered with rubber.

still looking for a brainstorm on this problem

---

### Post by tiresia on 2008-09-04
Can you, please, tell me how did you set up BootX?
Have you run the GrabG3CacheSetting, and have you enabled the G3 cache (the BootX checkbox for G3 cache must checked)?
Sometimes it helped me to delete the 'preferences'

---

### Post by sourman on 2008-09-04
can't check the G3 cahce. All other options are checked. No video drivers also checked. 
the main issue is that I got it to boot at two first tries, but then the cd check freezed. After trying booting w/ Debian CD i got that symptoms. Maybe I need to reinstall OS9 and BootX?

---

### Post by tiresia on 2008-09-04
No, you don't need to reinstall OS9.
Just try to delete the BootX Preferences (they are in the Preferences Folder), then open BootX so that it recreats its Preferences Document, then run GrabG3CacheSetting. After that open again BootX, now you should be able to check the G3 Cache. Let me know what happens

---

### Post by sourman on 2008-09-04
I'll try it. But I'll be back to U maybe on Saturday.

---

### Post by SpicyPanda on 2008-09-04
Are you sure that you are using the PPC versions of Ubuntu?  As a G3 CPU are PPC based..

---

### Post by cyberdork33 on 2008-09-04
> **SpicyPanda said:**
> Are you sure that you are using the PPC versions of Ubuntu?  As a G3 CPU are PPC based..
Yea that was what I was leaning toward as well at first... especially after this part:
> **sourman said:**
> The Ubuntus stop at arch exit line (or smth like that)

---

### Post by sourman on 2008-10-04
Hi everybody!

Of course I'm using PPC version.... duh! :D... I have only a 4 year experince w/ Apple's computers but I know quite a lot about the specs of these machines ;) 

Some weeks have past. We'll my PDQ PB still isn't booting.... amazing
tried to "reinstall" bootX but still the same.

---

### Post by hellrazordude on 2008-10-04
hi guys,,,,,
i just got a imac g3, i try to install ubuntu 7.10 but and the end i wont boot after i install the software. got a error code "initramfs" please help

---

