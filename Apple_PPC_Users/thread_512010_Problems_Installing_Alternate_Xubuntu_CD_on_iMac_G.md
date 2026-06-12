---
title: "Problems Installing Alternate Xubuntu CD on iMac G3"
date: 2007-07-28
forum: Apple PPC Users
---

### Post by YarisPCA on 2007-07-28
I need some help. I have a tray loading iMac G3 and since it cant install from either Ubuntu or Xubuntu LiveCDs, I decided to get the alternate install disk. I read one of the guides on these forums and tried to follow it, but every time the I get to the point where the HDD is being formatted, the mac restarts and tries to boot from the hard drive. What can I do?

---

### Post by bodycoach2 on 2007-07-28
How much memory does this G3 have?

---

### Post by YarisPCA on 2007-07-28
It has 256 MB of RAM.

---

### Post by YarisPCA on 2007-07-29
BUMP


I really need help. Could it be a bad HDD?

---

### Post by bodycoach2 on 2007-07-29
Possible, but unlikely.
Obviously, the install process is starting. At the moment, I'd guess you have a bad burnt CD. I had this problem on my iMacs. The CD needs to be burnt at the lowest possible speed. 

What speed did you burn the CD?

---

### Post by YarisPCA on 2007-07-29
I used disk utility and burnt it on maximum speed. I didn't really think it would matter that much, but I will burn it slower when I get the chance.


Thank you very much. I'm really glad I got some help.

---

### Post by YarisPCA on 2007-07-29
Okay, I tried this and he same thing happened. I had burnt the CD a the lowest speed possible (8x)

My hard drive is 4 GB, maybe that's not enough? What options did you choose when formating the HDD?

---

### Post by pxwpxw on 2007-07-29
> **YarisPCA said:**
> Okay, I tried this and he same thing happened. I had burnt the CD a the lowest speed possible (8x)

My hard drive is 4 GB, maybe that's not enough? What options did you choose when formating the HDD?

Could be. What Macos have you got on the drive and how much disk space is it using?
If you want to keep Macos and dual boot linux, you will need to resize the Macos partition (assuming you do have Macos on there).

---

### Post by YarisPCA on 2007-07-30
All I know is that when I got the iMac, booting from the hard drive would get me the flashing system folder icon. I tried reinstalling OS 9,  but I couldn't update the firmware from the CD. So, I decided to try Ubuntu. I just want Ubuntu on there, not a dual boot.

---

### Post by pxwpxw on 2007-07-30
OK, well when you get to the partitioning stage, you should have an option to use the whole disk with automatic partitioning, or guided partitioning, or to use manual partitioning. Do you get those? Which have you tried?

---

### Post by YarisPCA on 2007-07-30
I chose the one that formats the entire drive guided I think. Should I try the others?

---

### Post by pxwpxw on 2007-07-30
If that is what you want, yes Guided use whole disk - then it should have shown you next screen, the disk to select and then the partitions it will write, did it get that far? When did it fail?
You could run thru it again to make sure.

---

### Post by YarisPCA on 2007-07-30
Yes,as soon as I select the disk and confirm it, I am shown a screen with a progress bar, as soon as it shows up, it is on 33% and stays hat way for about 5 minutes and then reboots. I've tried at least three times and this is all I get.

---

### Post by pxwpxw on 2007-07-31
In the installer menu, check your CD for errors.

When you get to the partitioner, select Manual, it will display what is existing on the disk, make a note of it. Then delete it all, that should show your 4GB as one big free space.

Then go back to Guided, whole disk, and when you get to the final Confirmation to Write, go back. That should show a list of the partitions and their sizes.

Should be 4, adding up to about your disk size (4GB)

- Apple partition map (small)

- NewWorld boot - about 1MB

- / Root - the main partition.

- Swap - about 500MB.

Note the settings.

Then go back to Manual Partitioning and just leave the partitions as above and go from there. It might give a different result with manual partitioning, and at least you will have some more information. 

You should be using Feisty704 Alternate install CD, or Server install.

---

### Post by radicalspud on 2007-08-02
i had some HD trouble on my powerbook G3, trying to install Feisty and Edgy both. i have a 15GB drive that is a little flaky (Mac OS X didn't like it all that much), but it has passed all the manufacturer tests (DOS boot floppy) including a low-level format, and i was able to re-install OS X on it, which has been working fine.

however, attempting to install Ubuntu on this drive failed every time, with both alternate-install and net-install CDs. the installer would hang anywhere from booting to partitioning to installing the base system. random crashes over and over. i finally gave up on that drive.

i have installed Edgy on a 4GB drive from the alternate-install CD. 4GB is only a limitation after you have installed everything including Gnome. that will fill it nearly full. (there was 159MB left on mine after installing "ubuntu-desktop" package.) so you might try to get your hands on a larger HD (ebay is a good place) if you want to run Ubuntu and have room for more apps than the basic ones, plus data.

---

