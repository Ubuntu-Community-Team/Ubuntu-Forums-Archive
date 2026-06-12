---
title: "Trouble with Live Boot CD and partitioned hard drive"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Driken on 2007-04-30
I've been trying to set up a dual boot system tonight on my laptop,  and using partition magic I set up a separate partition to use for fiesty. The first time I got the boot CD in I started the install process and got to creating my user account before my computer froze up. Since, I've not been able to load the OS from the CD successfully, the furthest I've gotten is the desktop fully loaded then another freeze. I have two copies of fiesty, one mine, the other a friend's both have no errors when run through the check disc utility upon boot. I am unsure why the OS keeps failing to load, or freezing as soon as it does.

---

### Post by Najand on 2007-04-30
Try downloading and burning it using a slower speed. If it was unsuccessful either, then try to install it using the alternative CD:
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)

---

### Post by Pobega on 2007-04-30
Sounds to me like you're going to need the alternate CD; Just download the alternate from Ubuntu.com, compare the md5sums and burn. I had very close to the same problem with my sister's laptop using Edgy, and the alternate CD cleared everything up for her.

---

### Post by Driken on 2007-04-30
New, bigger problem. Got through the install process, now I can't boot to windows or Ubuntu. Still having similar problems with the install CD. Trying to get the alternate downloaded to a separate medium. Whenever I start my computer without the boot CD in, I get "Error loading operating system" :(

---

### Post by Driken on 2007-04-30
Bump. :(  Any ideas how I can fix what I done messed up?

---

### Post by mattmole on 2007-04-30
It sounds to me like the install of GRUB (the boot loader) is corrupt somehow. How is your system setup? Do you have a separate harddrive for windows and ubuntu or are they on the same drive?

What partitions did you choose when you installed?

---

### Post by Driken on 2007-04-30
They are both on the same drive, I split my hard drive into two parts, leaving windows in on partition and putting ubuntu into the other.

---

### Post by mattmole on 2007-04-30
hmmm,

That is the same thing as I did. Do you get any prompt at all, when it boots that would allow you to select an option or type anything in? Im wondering if GRUB is installed at all. 

I think my plan of attack would be to:

1) Use a live disk that doesn't crash your PC. 
2) Create a GRUB floppy disk (I have seen instructions on the web, but I cant remember where (sorry)).
3) From the live disk note down what is written in your /boot/grub/menu.lst
4) Reboot the PC and boot from the floppy
5) using the settings from the menu.lst file you should be able to type the linux options and get your PC to boot into Ubuntu
6) Install GRUB from within Ubuntu

If that sounds like too much work then maybe try installing again from the alternate disk

Matt

PS - Did you remember a SWAP partition during the install or did you let Ubuntu handle the partitioning? (Not that this would cause your problem - I dont think)

---

### Post by Driken on 2007-04-30
I've run across the grub floppy instructions, I'll look into it. I did not remember a SWAP partition. Thanks for all the help so far, I'm slowly figuring some of this out. :)

---

### Post by mattmole on 2007-04-30
Anytime.

---

### Post by Driken on 2007-04-30
Well, I'm out of options for today, I'm out of bandwidth, nearly, and the school's cluster computer thinks that my external is it's own hard drive, and won't let me write the alternate live CD to it.

---

