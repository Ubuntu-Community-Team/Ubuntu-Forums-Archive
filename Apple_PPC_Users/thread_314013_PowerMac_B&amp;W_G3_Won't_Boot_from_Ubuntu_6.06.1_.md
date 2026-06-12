---
title: "PowerMac B&amp;W G3 Won't Boot from Ubuntu 6.06.1 Server"
date: 2006-12-06
forum: Apple PPC Users
---

### Post by alexroche on 2006-12-06
Hi There

Trying to boot this ISO on my B&W G3.
ubuntu-6.06.1-server-powerpc.iso

I believe it's a Rev A B&W G3, 350Mhz, 256MB RAM (4x64MB). It's got Mac OS 9.2.2 on it right now... I'm just putting the Ubuntu CD in and holding down C while restarting. It reads the disk (the light on the CD drive goes on) for about 30 seconds.... then just ends up booting Mac OS.

Any ideas?

Thanks,
Alexandre

---

### Post by Rent New Tampa on 2006-12-07
I have had similar problems with my G3 B&W, with Ubuntu and other distros. I believe the CDROM does not read CDs written at high speeds very well, so if you burned at 40x or higher, that could be the problem. I do not recall what the speed rating of the B&W CDROM drive is, but before doing anything else, you should try burning the CD at 16x (or slower if you know the limit and it is less then this).

---

### Post by alexroche on 2006-12-07
Ok thanks, I'll try that. I put the disc in my powerbook, and it booted off of it fine.

Did you ever get it to work on your B&W?

---

### Post by alexroche on 2006-12-07
Just burnt 6.06.1 server at 4x... no dice. Does the same thing as before.

I was thinking I could try 5.10 Breezy Badger... but I can't find it anywhere on the internet. I've also downloaded the desktop version of 6.06.1... gonna give that a shot too.

Seems like a lot of people have trouble with this machine..

Alexandre

---

### Post by Rent New Tampa on 2006-12-07
Yeah, I have not problem getting it to work, I have actually installed and reinstalled 6.10 server several times. (noob with the server stuff and since it installs rather quickly, I keep giving myslef a fresh start when I mess up enough configurations...)

I remember going through something similar and burning a few disks before it would work. Any chance the drive isn't working or is dirty? I had many frustrations with this machine in the past, causing me to ignore it for quite some time. Others kept telling me it was the disk and I couldn't believe it because I tried so many times...and they worked on other machines. Eventually that was what worked though, I have about a dozen disks burned and only a handful will actually boot AND install on this machine. Once you get past the boot part, you will find out sometimes the CDROM drive can't read the whole disk and you will be burning yet again...

Keep trying, I think the machine is worth it (I hope). I will be posting my current project on here shortly (LAMP Server with ssh and ftp for testing out my php/mysql websites in house prior to putting them online...). I am a noob at Linux servers and web development, so it should be entertaining...

---

### Post by Rent New Tampa on 2006-12-07
You are using the PPC iso, right? Don't mean to insult, just want to make sure we didn't overlook the obvious...

---

### Post by alexroche on 2006-12-07
yes, i am using the PPC.

I'll try burning at 1x. I may also try using the alternate install disc.
The drive works... because it boots off of a Tiger install DVD no problem (and it's a burnt disc).

---

### Post by Rent New Tampa on 2006-12-07
> **alexroche said:**
> 
I'll try burning at 1x. I may also try using the alternate install disc.

I'm not sure 1x is necessary... I burned at 16x I think... if you don't mind going through disks, try it at 16x with "verify" enabled. You may also want to try burning it from another computer if possible. I'm not sure if the software you use to burn makes a difference, I usually use Nero on Windows...

---

### Post by alexroche on 2006-12-07
Ok... so i just got it to boot...
I did it by booting into open firmware:
- hold down option-command-o-f when you hear the chime
- open firmware loads up... then type:
- "boot cd:,\install\yaboot"

that will force it to boot off the CD.
Got the info here:
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html)

I'll let you know if I succeed in installing.

---

### Post by alexroche on 2006-12-07
Ok... ran into problems..

Get it to boot into yaboot
I press return
Then it gets me to select language
Then keyboard layout
Then it does this detect hard thing

Then it brings me to a screen that is all blue, with a text area at the very bottom. Nothing written.

I left it for like 15 minutes... and eventually it told me that it couldn't mount the install cd. Try again?

I said YES. Now it's trying again (same blue screen).

Any ideas as to why that would happen?

---

### Post by stream303 on 2006-12-07
This might not be related to your setup, but when I ran the Alternate install on my iMac, I had to disconnect the mouse, and not let it auto-detect my keyboard layout.  I just chose it manually during setup.

Maybe this will get you a bit farther...

---

### Post by alexroche on 2006-12-07
Yeah, I've been doing both those things.

I'm downloading alternate right now and i'm gonna try that.

---

### Post by alexroche on 2006-12-09
Ok so I just tried alternate... It boots when I hold down C!

I successfully did an install.. but when it boots it says "not enough video RAM".

All I want is the server version... how can I install that from the alternate install (6.10)? I don't see an option.... I also never get to see the install screen with the Ubuntu logo....

Any ideaS?

---

### Post by stream303 on 2006-12-09
Hmm..  you could download the server version which is purely text-based.

Can you get to a shell? (ctrl-option-f1).  If so, I wonder if you drop the default color bit depth (DefaultDepth 24) from 24 down to 16 in /etc/X11/xorg.conf might just squeak it in.  Reboot or restart gdm...

---

### Post by alexroche on 2006-12-09
Yeah I've already tried the server version.. doesn't install. Keep running into problems.

I can get into a shell within the installer...

I actually don't really care about the graphical install... what I really want is to be able to install the server version from the alternate disc. It's puzzling how I can't get to the main install menu with the Ubuntu logo though... because that's where you select server install I think.

---

### Post by alexroche on 2006-12-11
OK so I FINALLY got it to work the way I wanted it to. It now works flawlessly. Here's what I did.

I read on a messageboard archive (some other site) that the Optical Drives that come in the B&W G3s are a little wonky, and one person reported success after swapping in a new one. So I went to my local cheap computer store and picked up a refurbished HP 48X CD-ROM for $10. Took out the DVD-ROM in the PowerMac, and swapped in the new CD-Rom.

Then I put the server CD in (6.10 Ubuntu). Before, this CD wouldn't boot when holding down C. Only the Alternate disc would. With the new drive, the server disc booted perfectly. 

I had already formatted the drive as UNIX (i think) with the MAC OS X 10.4 CD... using Disk Utility. So when I went into the partition table, the Apple Boot portion was there. I didn't touch that... just told it to automatically partition free space. 

It then went through the install process... rebooted, and everything appears to be working great. It boots as though Ubuntu were its native OS.

So, for those having problems installing Ubuntu Server on their B&W G3s.... just put a new CD drive in and it should do the trick.

Thanks to everyone for their help and effort!
Alexandre

---

### Post by dirkb on 2006-12-20
> **alexroche said:**
> OK so I FINALLY got it to work the way I wanted it to. It now works flawlessly. Here's what I did.

I read on a messageboard archive (some other site) that the Optical Drives that come in the B&W G3s are a little wonky, and one person reported success after swapping in a new one. So I went to my local cheap computer store and picked up a refurbished HP 48X CD-ROM for $10. Took out the DVD-ROM in the PowerMac, and swapped in the new CD-Rom.

Then I put the server CD in (6.10 Ubuntu). Before, this CD wouldn't boot when holding down C. Only the Alternate disc would. With the new drive, the server disc booted perfectly. 

I had already formatted the drive as UNIX (i think) with the MAC OS X 10.4 CD... using Disk Utility. So when I went into the partition table, the Apple Boot portion was there. I didn't touch that... just told it to automatically partition free space. 

It then went through the install process... rebooted, and everything appears to be working great. It boots as though Ubuntu were its native OS.

So, for those having problems installing Ubuntu Server on their B&W G3s.... just put a new CD drive in and it should do the trick.

Thanks to everyone for their help and effort!
Alexandre

heh. while reading through this thread...i was thinking, "that sounds like a bad CD drive...."

---

### Post by ckom on 2007-01-19
> **alexroche said:**
> Ok... so i just got it to boot...
I did it by booting into open firmware:
- hold down option-command-o-f when you hear the chime
- open firmware loads up... then type:
- "boot cd:,\install\yaboot"

that will force it to boot off the CD.
Got the info here:
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html)

I'll let you know if I succeed in installing.

this is the fix i've been looking for all night!

---

### Post by alexroche on 2007-01-20
You may run into issues.

What ended up doing it for me was buying a new CD ROM drive (a used one) to replace the DVD ROM in the G3.

Alexandre

---

