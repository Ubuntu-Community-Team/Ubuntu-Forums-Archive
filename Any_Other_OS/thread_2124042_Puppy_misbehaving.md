---
title: "Puppy misbehaving"
date: 2013-03-09
forum: Any Other OS
---

### Post by Markup 001 on 2013-03-09
Can anyone give me a little guidance or point me in the right direction please?

I have an eeE PC 4GB SSD It’s [full specs are here]("http://www.cnet.com/laptops/asus-eee-pc-4g/4507-3121_7-32466960.html") and it has an xanmdros operating system from 2007 installed. At some time a previous owner installed windows XP but I suspect it was a somehow stripped down version as it never behaved properly and displayed several bugs that made it practically unworkable. So I managed to get the files off the original recovery disc that came with the machine from new. I loaded the files onto a bootable USB and reinstalled Linux Xandros.

Because I liked the way Linux worked in comparison to my poor version of Win XP and owing to the fact that I could not, in any circumstances, get an internet connection of any kind to do updates, I joined the forum here and some friends guided me to Puppy Linux. Again using my formatted and bootable USB I downloaded an .iso file called pup-431.iso and after getting advice from coldraven here on the forum I used Unetbootin to pick up the file from my downloads and make it bootable on my USB stick.

All went well and I loved the way my new version of Linux worked, so much so that I wanted to do a full install rather than boot from USB every time I logged on. So I set about reading up on how to do this and set to work. Unfortunately I had booted a few times with the USB and had made a save at some point, which meant I had created a pupsave file, this has given me many headaches when trying to figure out how to do an install of Puppy Linux over my old version of Xandros. I have followed very carefully this [HOW TO]("http://murga-linux.com/puppy/viewtopic.php?t=29653") do a full install guide even though there are some differences I thought, how hard can it be to improvise...? But when I get to the actual install Puppy kicks me out.

I have been back twice and restored the machine to its factory state and deleted all data from my USB stick, using unetbootin I have picked up the iso file from my downloads again tried again a couple of times to reinstall Puppy, but every time I have tried it is somehow picking up the settings from the previous installs (on my desktop there is a little yellow circle over my sda1 folder) which must mean that the machine is not going back to its factory state – even though it takes me through all of the set up steps at install each time.

The end result is that I have ended up dizzy and am not sure if I am making some glaringly simple error that I am not seeing because of my over enthusiasm in wanting to have Puppy Linux sit on my machine and boot with the convenience of a windows OS. I do intend to persevere as the Puppy users I read of are so enthusiastic so I know I am making errors that I can correct with some help.
Can someone point me in the direction of the knowledge to go back to absolute zero and remove Xandros from my machine completely so that I can pick up the pup-431 file and try again at a full install to a totally clean drive.

Thank you, I’m sorry for the drawn out post but want to try to give as much background as possible in the hope that someone will recognize my problem and know how to assist me, or even advise me that by installing Puppy I am trying to run before I can walk. If this is so can someone recommend something that will give me the Linux experience and set me on the learning curve that will lead to Puppy at a later date, when I am more proficient in working with Linux please?

Thanks very much,
Mark

---

### Post by papibe on 2013-03-09
Thread moved to **Other OS/Distro Talk**.

---

### Post by cheatos on 2013-03-09
Have you formtted the drive you install to before installation?
If not, do so. It should remove all old files (so do a backup of important data before you format)

---

### Post by Markup 001 on 2013-03-09
Thanks cheatos

I did format the drive using the gparted tool from within the usb loaded puppy installation, I created a partition and allocated it a size etc. Everything seemed to go well at the time even though I could not delete the sda1 because as I say I had previously saved some data to the pupsave file so the installation process would not allow me to completely remove that and my limited knowledge of Linux prevented me from forcing the issue, one difference I noted (and chose to ignore) was that catdude who was doing the "how to" of the install was working with hda1, hda2 etc whereas my system was showing the files as sda1, sda2 etc.

I am assusming that when I created the partition with gparted and set it up successfully the formatting of said partition was automatic, am I right to assume this?

---

### Post by cheatos on 2013-03-20
uhh, sorry I can't give you a qualified response to this...
maybe someone else can help you?

But what is it with all these pupsave and cat stuff you are talking about?
With a live-usb you should be able to completely remove all partitions on your hard drive (probably sda in your case) and all its partitions (i assume these will be sda1 to sda"n") with n your given number of partitions.

---

### Post by ManamiVixen on 2013-03-20
Puppy Linux isn't supposed to be installed to a hard disk. It was designed to run off a USB or CD and all Save PUPS saved to the USB or on a empty, but formatted hard disk partition. There are ways to install it to a disk, but the creator of Puppy strongly suggest NO as it can and will mess up Puppy in some way, especially with it's Pupplets and saves.

---

### Post by mips on 2013-03-20
Why do you want to use puppy? It's a pita to install, I tried a few times and gave up in frustration.

Have you looked at distros like Slitaz, Crunchbang, Lubuntu etc

[http://www.slitaz.org/](http://www.slitaz.org/)
[http://crunchbang.org/download](http://crunchbang.org/download)
[http://www.lubuntu.net/](http://www.lubuntu.net/)

You want the x86/32-bit versions for your cpu.

---

### Post by leclerc65 on 2013-03-20
Puppy 431 is a bit outdate. Try Puppy Lucid or Precise.

---

