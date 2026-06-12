---
title: "Cannot install to HDD!"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by benh088 on 2007-06-28
Alright, so I find this old Dell Dimension 4100 out by my dumpster with some pretty kickass hardware (for it's era), including (but not limited to) a full 512MB RAM, a decent graphics card, a 160GB HDD, DVD-ROM, CD-RW, and a 1.0GHz Pentium III processor, but come to find out I can NOT install Ubuntu onto the freshly-formatted Hard Disk drive!

Here's where the frustration begins;

I had a bit of hardware issues, but I work at a used PC parts store, so those were VERY easily fixed. Come to find out my DVD-ROM was bad.

Then, when I FINALLY boot to the beauty of Ubuntu for the first time (by means of the LiveCD), I mess around with it for a bit.

Well, I decide I really want to make it a Linux based machine instead of a barely-passing-requirement Windows XP machine, so I double click the install icon and wait.

And wait.

And wait.

Mind you I have a KVM switch so waiting isn't so much of a thing.

So, I wait more. And more. And I try double clicking the icon again. Still nothing.

Then I go to the System menu, then Administration, then Install. And wait. And wait. And nothing!

I can't get this damn OS to install and I want to mess with it SO bad!

What can I do to install it, or fix it so it will install from the desktop? Help me!

By the way, if it makes a difference, I have the HDD formatted as an NTFS drive, but I assumed that Ubuntu installation will format the hard drive with it's own file system.

Regardless, I NEED HELP, PLEASE!

---

### Post by alienexplorers on 2007-06-28
You might want to try the Alternate install CD.

---

### Post by Nythain on 2007-06-28
my advice... download the ubuntu alternate install iso via bittorrent (if you must http or ftp make sure you get the checksum and verify the file after downloaded) then burn at the SLOWEST possible speed known to man, 1x, 4x, would go much higher, maybe 6x... this will ensure an accurate burn... then try again.

i've enountered a few downloads and a few burns that werent quite all right.

i had a LiveCD burn that booted livecd, ran great, started the install process, made it really frar, passed gparted, passed installing the system, then hung for infinity when it was setting up apt or some jazz... tried it again and it hung infinately towards the end of the install... reburnt the EXACT iso at 4x instead of 40x and voilla, never had a problem again

---

### Post by hartz on 2007-06-28
Hi,

During bootup from the CD, select the option to install Ubuntu, don't even boot to the desktop.

Oh wait, I never use the LiveCD, I only use the Alternate Install disk (The LiveCD is a waste for me because the default Xorg settings does not correctly identify my graphics card and gives me a black screen) .... so I am unsure ; maybe the LiveCD does not have this option in the startup menu.

Try it, if the option is there, run the installer.  If not, download the AlternateInstall disk image, burn that to a CD, boot from it, check it for defects, and then install to hard drive.  

Note: The alternate install CD does not have LiveCD functionality - you can use it in Console mode to recover a system, or you can install Ubuntu from it to the hard drive.

---

### Post by rillip on 2007-06-28
Not to sound dumb, do you hear the drive spinning?

Try opening the console and running 

```
 top
``` to see if the install program is actually trying to run. Maybe it's not actually double clicking right, or there's a ram error killing it, or the dvd drive is still having issues.  As Alienexplorers suggested you could try the alternate CD, which is a text based installer and would probably give a better idea of what was happening if it wasn't working.  

You might also try checking the disk for errors before boot with the checksum option.

---

### Post by Nythain on 2007-06-28
livecd does in fact have the option of not booting the os, its called install in text mode...

---

### Post by hartz on 2007-06-28
Nathan - you beat me to it.

But some comments:
1) It has been proven that the burn speed is not the issue (I read an article on this a few days ago actually, though I can't find it now).  This is almost ALWAYS an issue of quality of the media.
2) Both cksum the disk image AND check the disk from the boot menu for defects.

Cheers

---

### Post by benh088 on 2007-06-28
> **Nythain said:**
> livecd does in fact have the option of not booting the os, its called install in text mode...
Awesome!

So I'm wondering how to do this. I'm assuming I boot from the CD then push F6 for 'Advance Options' and type in something to the little text field that comes up; am I right?

If so, what should I type?

By the way, thanks to everyone for replying, I really appreciate it.

---

