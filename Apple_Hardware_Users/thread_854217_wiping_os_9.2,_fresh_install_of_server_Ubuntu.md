---
title: "wiping os 9.2, fresh install of server Ubuntu"
date: 2008-07-09
forum: Apple Hardware Users
---

### Post by AngelusLocke on 2008-07-09
Hello veteran and fellow newbie Ubuntu users. This is my first time installing Ubuntu using a Mac OS system. The current computer I am using for the OS is an iMac with OS 9.2. It's not a very powerful machine (I think at most a 533mhz processor) but I am not planning on overstressing this thing too much. My plan is to use it as a file server for a small website that won't be expecting too much traffic. I need your help. I made a start up cd/dvd with the Ubuntu ISO on it. The Mac recognizes it when the OS starts up, but for the life of me I cannot figure out how to get the darned thing to start up from the optical drive. I want to completely wipe the existing software off of the drive with a fresh install of Ubuntu. The Ubuntu version I downloaded and plan on installing is the server version (since.. well it *is* going to be a server). Any help will be greatly appreciated. thank you very much.

---

### Post by cyberdork33 on 2008-07-09
hold c at startup to boot from cdrom.

I would check the information about running Ubuntu on PowerPC hardware first though just to make sure there are not major problems with it on your hardware.
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by stream303 on 2008-07-09
Just be sure you are burning to CD-R, and at a low(ish) speed like 4x or 8x, as an iso image and not just copied over.

If holding down the "C" key upon boot doesn't work, try holding down that key very quickly after powering up, and long enough to hear it booting from CD.

When it comes time for guided partitioning, just let it "use the entire disk", and it will automatically wipe out everything and create the special Apple partitions along with the necessary Ubuntu partitions for you.

Depending on your exact model, you may run across a 128gb partitioning limitation, which means that you could either just create a 125gb partition (to play it safe) to hold the whole install, and use the rest as a general data partition.  Your other option if you like to slice up your /home /var /usr partitions yourself, is to make sure that the special apple partitions and boot and root are also under that 125gb limitation, whereas the rest can go outside it.  Again, this depends on your model, so try just using the entire disk first.

A 500mhz G3 is roughly equivalent to a 1ghz Intel box, so that should make for a fine lightweight server, and even a nice desktop if you have enough ram.

Sometimes you may run across the date-bug, so keep this handy too:

[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

---

### Post by AngelusLocke on 2008-07-10
does burning it to a DVD make any difference as opposed to using a CD-R? my iMac has an aftermarket DVD drive in it. also i am restarting the computer and holding C but all i get is a flashing folder, it flashes a smilie face then a question mark then back to a smilie... does that for about 10 seconds then boots to the OS. i bet i did something wrong =/.

---

### Post by AngelusLocke on 2008-07-12
hello? anyone else care to try and help me out with this? =/

---

### Post by oswaldkelso on 2008-07-12
Dont use a CD-R. A plain old cd burnt at a low speed. The flashes and smilie face with a question mark mean it failed to see the OS (CD-R disk in this case).

---

### Post by grundygreen on 2008-07-12
> **oswaldkelso said:**
> Dont use a CD-R. A plain old cd burnt at a low speed. The flashes and smilie face with a question mark mean it failed to see the OS (CD-R disk in this case).

I concur. hit c as soon as you hear the boot chime.
You should get a grey screen 1st.
You could wipe with the pwerpc version of dban. <a href="http://downloads.sourceforge.net/dban/dban-2.0.0_powerpc.iso?download">Download Link</a>
At which point all you get will be the folder icon.
At that point it will boot fronm any bootable cd you shove in.
I have an old lime iMac giving me fits. So far net install disk or mini disk has been the best. The slot loading cd drive seems twitchy.
Yeah G3's scream from shell.

---

### Post by AngelusLocke on 2008-07-16
awesome, thanks i will try out Boot and Nuke. i have no reason to keep this iMac with any other OS on it except Ubuntu. I already have a mac with OSX and a PC with Vista Ultimate 64bit, so i am good on those fronts. hopefully that program will solve some that boot issue (pretty much forcing the computer to boot from the dvd drive). I dont have one of those slot drives that come with typical iMacs, mine has a after-market installed DVD drive.

---

