---
title: "Clean reinstall of 7.10."
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by RossAndGarfunkel on 2008-03-26
I I run a single-OS Ubuntu 8.04 laptop. There are just too many issues to be had when using 8.04 (which I expect will all be ironed out a month or so after release) and I just need to completely wipe it clean and put 7.10 back on there. I already have all my music and other important files backed up elsewhere, and I have a copy of 7.10 on a CD. What exactly do I need to do to start completely fresh and install 7.10?

---

### Post by jan quark on 2008-03-26
I guess you can use gparted during the live session when you have booted with the gutsy cd to wipe the hardy partitions 

then install as usual 

you can of course select "use entire disc" during the partitioning process of the installation 
then your drive will be formated, wiped clean

but you won't have a separate home partition

---

### Post by spiderbatdad on 2008-03-26
Run the live cd. When the desktop loads, click the install icon. During the installation you will be offered options for using unused space, guided partitioning, or using the entire disk. Choose, Use Entire Disk.

---

### Post by RossAndGarfunkel on 2008-03-26
I have the live CD in my drive, but it doesnt auto-run anything, and I cant find anything but Windows executables.

---

### Post by jan quark on 2008-03-26
> I have the live CD in my drive, but it doesnt auto-run anything, and I cant find anything but Windows executables.
:confused:
so your ubuntu live CD does not boot you into the live session is this correct?

where do you see windows executables?

---

### Post by spiderbatdad on 2008-03-26
Is this your own 7.10 live CD? Have you used it before?
If not, I was tinking it may not be an iso image.

---

### Post by RossAndGarfunkel on 2008-03-26
It doesnt start a live session. I see "start.exe" and "wubi-cdboot.exe" in the main folder on the disk.

---

### Post by jan quark on 2008-03-26
> It doesnt start a live session. I see "start.exe" and "wubi-cdboot.exe" in the main folder on the disk.

nah, you cannot boot with an exe file
download the gutsy iso from here
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)
and burn the iso to the CD but as an iso image not as data CD
then boot with it

---

### Post by RossAndGarfunkel on 2008-03-26
and when I boot the disk on a Windows XP system it starts a live session.

---

### Post by spiderbatdad on 2008-03-26
That's the 8.04 disk.

---

### Post by jan quark on 2008-03-26
yes because wubi is an installer for windows
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by RossAndGarfunkel on 2008-03-26
Well it's definitely not an 8.04 disk.

You know, you'd think it would be easier to just do a clean reinstall. :/

---

### Post by RossAndGarfunkel on 2008-03-26
well I still cant figure it out; like I said, it works fine in Windows, but it just wont do anything on ubuntu 8.04.

---

### Post by AndyCooll on 2008-03-26
It's not currently simple because it sounds like your using the wrong CD for a clean Ubuntu install.

At the top of this page there is a link called Products. If you click on that one of the options is "Download". As mentioned, download the 7.10 iso and burn it to a CD (as an iso image). 

Reboot your pc with that cd in the drive, and provided you've got your bios set to bootable from the CD-drive first it should then start up the live cd. 

On the Live CD is an option to "Install". Again as mentioned, follow the instructions until the partitioning stage. If you choose "Use whole of drive" that will wipe everything that's already   there and install a completely clean version of Ubuntu on to your hard-drive.

Simple.

:cool:

---

