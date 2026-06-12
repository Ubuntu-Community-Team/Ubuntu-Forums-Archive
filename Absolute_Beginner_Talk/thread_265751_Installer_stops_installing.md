---
title: "Installer stops installing"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by JamesWP on 2006-09-26
Hi there, decided last night that Windows had bored me, so i thought I'd give linux a go, asked around and was told that ubuntu was probably the best distro for me to ease into, so i backed up my junk, formatted my C: and removed all partitions.

First i gave the live CD (AMD64) a go, had a little trouble with graphical glitches, so i ran it in uhm, safe graphics? (or whatever its called :P), got to the desktop, had a play around and found that i liked it.

So I click the 'Install' button, go through the wizard, get past the 'copying files'part, and it crashes at setting the clock, i thought i'd give it another go, and atleast 5 times, it crashes at any random stage after copying files. 

So i decide to give the 'alternate' ISO a go (AMD64), I get to the part where it does the 'select and install software' stage, and once again, it randomly crashes =\.

I'm probably doing something entirely wrong, and you'll probably fix it in one post, but thanks :)

Here is my setup (to the best of my memory, usually use windows to check up on it without taking it apart :p).

AMD64 3800 2x Core, set at 2.0ghz
DFI Lanparty UT nF4 SLI-D
nVidia 7800GT
1GB of OCZ gold stuff, with 2-2-2-6 timings?
200gb Western Digital SATA-II HDD

Thats probably as accurate as my memories gonna serve, any help is appreciated :)

---

### Post by hellmet on 2006-09-26
he he..i like your sportiveness..but welcome to Dapper..
I've had problems like these 'n' times..
but for me each time it got stuck at different places..on different places.

But the same place when it came to the same computer..
anothe place for another computer..
even alternate cds failed me..
I finally installed Breezy into those computers to get going..

Its a bug in dapper..

this is my experience...

Well, some one mite be knowing a solution to this

---

### Post by JamesWP on 2006-09-26
Downloading breezy now, any disadvantages to this, and can i upgrade to the latest version of ubuntu once breezy is installed?

---

### Post by bigken on 2006-09-26
I would give the 386 iso a try or even  edgy knot3 a try ;)

---

### Post by petri on 2006-09-26
Those crashes could be a result of an corrupt CD download, did you check the md5 sums?

---

### Post by JamesWP on 2006-09-26
Checked the checksums on both cds, both passed

Will look into edgy now :)

---

### Post by JamesWP on 2006-09-26
For some reason, both Dapper and Edgy both crash at "Configuring language-pack-en-base", im wondering wether i should try the 386 iso or breezy next, any ideas? =\

---

### Post by Dinerty on 2006-09-26
> **JamesWP said:**
> Checked the checksums on both cds, both passed

Will look into edgy now :)

64 bit is known to be more picky then it's 386 brother. I recommend you try Dapper 386

---

### Post by JamesWP on 2006-09-26
Downloading 386 dapper now :)

---

### Post by Jukey on 2006-09-26
And if that doesn't work, try the alternate install cd :)

---

### Post by JamesWP on 2006-09-26
Gone straight for the alternate this time :)

---

### Post by JamesWP on 2006-09-26
Ok, the 386 version of dapper installed perfectly, except for one problem, whilst using the live CD, the screen glitched at the splash screen unless i used 1280x1024 or 'safe graphics' mode, now after i enter my password, the splash screen tries to come up, but glitches, i'm assuming this is due to me not having the latest nVidia drivers installed, any way to either install the drivers, enter 'safe mode' or change screen resolution without logging in? :)

Thanks

---

### Post by bigken on 2006-09-26
log into single user mode (safe mode ) and type sudo dpkg-reconfigure xserver-xorg from here you can select your video drivers and screen resolutions ;)

---

### Post by JamesWP on 2006-09-26
Tried the 'sudo dpkg-reconfigure xserver-xorg' thing, found the uhm 'wizard?' a little wierd, it didn't do what i wanted, and i had to enter adresses and stuff i didn't know, even when i told it i wanted it to do it automatically, so i tried filling it in, used 'reboot' and found that i'd entered it wrong, so i messed around and found out how to restore backups, opened the backuped file and added Option "NoAccel"? to it, restarted and found out it works super now i added that :).

As i found the 'wizard' confusing, is there a way to add resolutions that i want to use via the nano /etc/X11/xorg.conf file? Or is the GUI capable of doing such things?

---

### Post by bigken on 2006-09-26
to add resolutions just run the dkpg-reconfigure again and use the up and down arrows and space bar to select which 1s you want ;)

---

### Post by JamesWP on 2006-09-26
Thanks for the help Ken :)

Just downloading the updates, and the latest nVidia drivers, gonna puzzle myself over installing them and then i'll give the dkpg thing another whirl :).

Oooh, last question (for now ;p)

As i've installed a '32 bit' kernal, i'm assuming the system will still make use of BOTH of my cores? Windows XP did, but linux is a whole new world from what i've seen so far :)

---

### Post by bigken on 2006-09-26
no you should use the AMD K7 SMP ;)
take a look [here ]("http://www.ubuntuforums.org/showthread.php?t=85917&highlight=AMD+K7+SMP")
well im off to bed coz its late

---

