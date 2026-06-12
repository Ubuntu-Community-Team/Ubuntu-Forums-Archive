---
title: "Has ANYONE got a burned CD to boot on an older new world mac?"
date: 2006-11-06
forum: Apple PPC Users
---

### Post by fisherdmin01 on 2006-11-06
I have followed every FAQ and instruction I can find regarding burning Ubuntu-PPC isos from my PC for installation on my Powerbook G3 (Lombard).  I have bit-torrented, standard downloaded, alternative downloaded, checked MD5s, used Nero, used ImgBurn as suggested in the FAQ.  I have burned as slowly as I can which is 4x.  Nothing works except to use my shipit cds.  This is a pretty common theme on this forum and I'm sure that many are rolling their eyes, thinking some noob cannot figure out how to burn an image.

Has anyone successfully accomplished this feat and if so, what did you use for cd-media, burning application, etc.

Thx

---

### Post by 3rdalbum on 2006-11-07
In terms of an older New-world Mac:

I burnt using a version of Toast that works on OS 9. Burning the image wasn't the hard part; the hard part was that the computer's CD-ROM drive doesn't like burnt discs. Maybe your Powerbook's drive is the same.

I ended off burning at 8x onto a Mitsubishi disc, but really if you have any burnt CD-Rs that read in your Mac, those are the brands to look for.

---

### Post by dualusbibook on 2006-11-11
I had success using Verbatim cd-r's.  I burnt using Toast under 10.3.

I agree with 3rdalbum.  It probably isn't the disc but the CD drive.  Some older drives were not sensitive enough to read burnt discs.  What you could try (provided you have the extra hardware) is connect an external CD drive.

I had issues with a G4 Sawtooth (rev2 logic board) that would only read commercial DVD's and CD's.  It would selectivity read burnt CD's.  Using a rev7 logic board no problems as Apple used a different cd drive manufacturer.  May be the same problem for you - my solution was I used an external drive as I have a few lying around.

Good luck

---

### Post by CadTeach on 2006-11-11
I am running on an  original iMac G3, 233 Mhz.  I burnt the CD on a windows machine, and was able to install, although it involved a bit of extra work. AIs the disk readable at all on any machine?  I booted after essentially opening a terminal window at start up .  There are threads describing similar problems. Post again if your still having problems.

---

### Post by iomicifikko on 2006-11-11
hi Cadteach, what do u exactly mean ? im on a imac g3 333mhz, the cd is read, is booted, i can see the splash screen with the line going right and left, while the cd is read and read again, but after a few minutes, the monitor seems to go in standbye mode (with the power button yellow lighted) and nothing happens anymore. I'm using a desktop cd.  Any idea?

Thanks! byez

---

### Post by Radiolad on 2006-11-12
Hi, I'm new to this but have had the same problem on my iMac. The very helpful reply (from **Linear **member )I had is copied below and worked:-

[COLOR="SeaGreen"]The LiveCD does not set up xorg.conf correctly for the iMac G3. The fix, after you get to that blank screen, is to drop to a shell prompt and edit xorg.conf.

If you don't know how to do this:[COLOR="SeaGreen"][/COLOR]

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. Modify "HorizSync" to 58-62 and "VertRefresh" to 75-117. Both are in the monitors section.
4. Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo killall -HUP gdm (return) to restart Gnome
[/COLOR]

[COLOR="Black"][/COLOR] Hope this helps you also, Regards Radiolad.

---

