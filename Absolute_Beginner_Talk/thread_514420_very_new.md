---
title: "very new"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by rjdizz63 on 2007-07-31
I am very new to Linux and in fact i just saw a review in PC World mag and it peaked my interest. if i were to down load the operating system on my current machine that is running windows will it run both operating systems? will windows go a way? will i have to reformat if i dont like it and want to uninstall Ubuntu? How will it work on my net work will it automatically see my other machines? Will it see my storage hard drive in the machine.

sorry for all the questions. just trying to learn.

Dizz

---

### Post by LaRoza on 2007-07-31
Welcome to the forum! 

Your questions are common and there are guides for that, but the quick answer is:

0. You can have both Windows and Ubuntu (on different partitions)
1. The Ubuntu installer makes it easy, but remember to pay attention to the instructions.
2. Your network will probably work fine, and your hard drive will also work fine

See the sticky for the install guide. (The stickies are the posts at the top, that don't move)

---

### Post by lisati on 2007-07-31
You can download Ubuntu from [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu) - the "Desktop" version will work well for most people. If you'd rather not mess around burning CDs, you can also order a free copy.

It is also possible to have both Windoze (or whatever) as well as Ubuntu on your computer. This is known as "Dual Boot". The installation process can guide you through this,

---

### Post by the.phantom on 2007-07-31
ok the easy safe way to try ubuntu

download it and burn the iso disk
then just put that cd in your cdr and boot the computer
it will boot off of a "live cd" and will only use the memory and cd and you can play with it and see how it goes !
you can get the look and feel of it and probably get online !

if you say "hey this is really great stuff" but i don't want to kiss off my security blanket ( windows)

well you can install that disk and dual boot so you still have windows and you also have Ubuntu on your system

---

### Post by rjdizz63 on 2007-07-31
what about Kubuntu?

---

### Post by hammad1337 on 2007-07-31
> if i were to down load the operating system on my current machine that is running windows will it run both operating systems? If your PC already has windows installed, running an Ubuntu installation using a DVD should be fine. Ubuntu will automatically detect the windows installation and set up dual-boot. Try it with a live cd before installation though, this will tell you if all hardware works. Most of the time, it does.> will windows go a way?It won't until you make it go away. :) > will i have to reformat if i dont like it and want to uninstall Ubuntu?Uninstalling Ubuntu is very easy just re-install the XP boot loader using the XP CD and delete/format the Ubuntu partition.> How will it work on my net work will it automatically see my other machines?That doesnot usually work out of the box. your will have to scour the forums for it. But there are many helpful people here who will answer any queries/problems you may have.>  Will it see my storage hard drive in the machine.yes, it will be able to "see" internal/ external hard-drives.


P.S. If you are scared of the idea of repartitioning/reformatting your hard-drive, try wubi [http://wubi-installer.org]("http://wubi-installer.org"). It installs Ubuntu without changing your hard-drive sructure.

---

### Post by LaRoza on 2007-07-31
What about it? 

If you want to try both, you can install Ubuntu first, then run this command:

```

sudo aptitude install kubuntu-desktop

```

This will give you everything Kubuntu has. You will be able to choose which Desktop environment you use when you log on.

---

### Post by dreadlord_chris on 2007-07-31
Let's see....
download the CD - it's a LiveCD, which means that it has a bootable OS on it. Just pop it into your CDROM and reboot (make sure your BIOS is set to boot from the CDROM first). A fully functional OS will load, allowing you to *test-drive* Ubuntu and see if it fits your needs.

".. will it run both operating systems": Most likely, this is called dual-booting
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

"Will windows go away": LOL, not soon enough for my tastes... but seriously, follow the directions in the previous link and you will have 2 fully functional OS' installed

"Will I have to reformat if I don't like it....": yes, if you want to reclaim the space used by Ubuntu.

"How will it work on my network": Linux in general will work fine in just about any network situation.

"...will it automatically see my other machine": Probably not automatically, some configuration will be required - but then this is true of any OS. Assuming your other machines are Windows boxes you'll want to look into Samba:
[https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29]("https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29")

"Will it see my storage drives in the machine": The simple answer to this is: Yes. Ubuntu has built-in support for **reading** NTFS formated partitions, but not for **writing** to them. Writing to NTFS is possible, you would just need to install the support:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28ntfs%29]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28ntfs%29")

---

