---
title: "Will I be okay running the Server version of Ubuntu?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Shiny Fork on 2006-10-05
I got a copy of Ubuntu from my Comp. Prof. at school, but I believe the version he gave me is meant for networks (the CD shows up as Unbuntu Server 6. in Windows; its a copy he had burned). I want to set up a dual boot on my laptop, a 750Mhz, 256MB Dell. I could use the copy of Desktop Ubuntu I am downloading for this, but it will take a while and I want to get started right now. Will I be okay with the Server version? 

Also, I have read through this: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Is it really that easy to install? I have bad luck with this type of stuff; somehting always comes up and I have to spend a few hours researching to fix it, if I even can. I am currently defraging my HD, but am also worried about how much space this will need. The guide said 10 GB, but my HD is only 20. I had planned on closer to 5 GB, as I will still be using Windows for a lot of stuff and have already collected 11 GB of stuff. How easy is it to switch OS's? Do I have to pick every time, or can I set it to automatically chose?

---

### Post by Mr Pink57 on 2006-10-05
You can however Server Editon doesnt install a GUI, so you may just wanna get the full ubuntu version.  I suggest getting it thru a Torrent file as its a much faster DL.  Also if you can burn the DVD version vs the CD version.

pink

---

### Post by robinl on 2006-10-05
Well as long as your Windows is not "unusual" GRUB should find it and you should have no problem dual-booting. The server version doesn't come with a Desktop Environment so you will be stuck with the command line. I suggest you wait for your Desktop CD unless you are using it as a Server.

---

### Post by Shiny Fork on 2006-10-05
No GUI? OK, I happen to have a CD-RW around that I can put the Desktop version on. I know that Grub is the tool used to dual boot, but is it included w/ Ubuntu? Or is it another thing that I have to go and look for?

Also, I have been defragging my HD and noticed that the graphic used to show where the data is has it all scattered throughout the drive, even though its no longer fragmented. Will this cause a problem with the partition?

---

### Post by Mr Pink57 on 2006-10-05
> **Shiny Fork said:**
> No GUI? OK, I happen to have a CD-RW around that I can put the Desktop version on. I know that Grub is the tool used to dual boot, but is it included w/ Ubuntu? Or is it another thing that I have to go and look for?

Also, I have been defragging my HD and noticed that the graphic used to show where the data is has it all scattered throughout the drive, even though its no longer fragmented. Will this cause a problem with the partition?

GUI = Graphical User Interface.  That means command line...

pink

---

### Post by az on 2006-10-05
If you are in a hurry, install the server version and then log in and run

sudo apt-get install linux-386 ubuntu-desktop

and after it fetches and installs the packages, you will have a desktop version.

Installing from the desktop cd takes about 15 minutes and doing it from the server (or alternate - text mode -) installer takes over an hour because they use a different strategy.

---

### Post by az on 2006-10-05
> **Shiny Fork said:**
> No GUI? OK, I happen to have a CD-RW around that I can put the Desktop version on. I know that Grub is the tool used to dual boot, but is it included w/ Ubuntu? Or is it another thing that I have to go and look for?


Grub is installed and configured automatically by the Ubuntu installer.
> **Shiny Fork said:**
> 
Also, I have been defragging my HD and noticed that the graphic used to show where the data is has it all scattered throughout the drive, even though its no longer fragmented. Will this cause a problem with the partition?


The installer uses a partitioner that can usually move the data.  If it has the slightest doubt, it will balk and not go ahead.  Just be sure that you chose the option to shrink a partition but not the USE ENTIRE DISK option!

If the installer refuses to do anything with the partition, try defragmenting it again and start over.

---

