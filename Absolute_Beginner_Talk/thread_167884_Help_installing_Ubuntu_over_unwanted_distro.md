---
title: "Help installing Ubuntu over unwanted distro"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by dannzo on 2006-04-29
Thinking of installing Ubuntu 5.1 on HDD that already has a swap partition plus 3 other partitions with different distros already installed on each. I want to remove one of the other distros and try out Ubuntu 5.1, although I'm not 100% sure how to do this. 

I'm using GRUB as boot loader from when I installed Suse 10, which I edited to also boot Windows (on separate HDD) if required.

Ideally I'd want to install Ubuntu leaving GRUB in place and then try and edit menu.lst file through Suse to allow booting into Ubuntu.

Any help much appreciated.

---

### Post by Eversmann on 2006-04-29
First of all, make a backup ;-)

As i see, maybe i'm wrong, you only have to install ubuntu on the partition of the distro you want to overwrite (removing the partition before doing that, or whatever, you know). Ubuntu should add the entry to grub during installation.

Then later edit the grub file to remove the reference to the other distro and re-sort everything if you see so.

---

### Post by dannzo on 2006-04-29
> Ubuntu should add the entry to grub during installation.

Do you mean if I install GRUB again (which I'd rather not) when installing Ubuntu? Otherwise I can't see how it will update the GRUB from Suse which I'm using and would prefer to keep.

---

### Post by Rinzwind on 2006-04-29
danzzo print out the grub you have now on suse.

Install Ubuntu.
That way you can (if it goes wrong) add suse to your Ubuntu Grub.

---

### Post by AndyCooll on 2006-04-29
As it stands, installing Ubuntu into a partition is quite straightforward. When it comes to the partitioning section of the install select "Manual partition". Then choose the partition you would wish to install Ubuntu onto, saying yes you wish to format it.

What an install normally also does by default is to make the Ubuntu "menu.lst" the default one on boot-up. Now ...you have couple of options!

Firstly you could accept all those defaults, allow the Ubuntu grub install, it will find all the other installed OS's, and then simply edit that one when it's finished. Even using that one it is then possible to make Suse the default install by changing one of the settings.

Secondly (I've not tried this with Suse, but it works with Ubuntu). Again go through the install process. When it's finished boot into the OS you wish to make default and type:

```
sudo grub-install /dev/hda
```

Or, at least the Suse equivalent command. What happens there is that it makes the menu.lst of the operating system you are currently in the default one. So for me, I install Ubuntu first, then another OS (e.g Suse). The Suse menu.lst becomes the default one. Rebooting I select Ubuntu from the Suse menu list. This boots me into Ubuntu. I then type the above command. Now the Ubuntu menu becomes the default one. I then update the Ubuntu menu.lst to include Suse as an option (since clearly the Ubuntu menu.lst is still the same one peior to the Suse install)

I believe there are other options, such as having /boot on it's own partition. I simply find the above easiest to work with.

:cool:

---

### Post by dannzo on 2006-04-29
Thanks for the replies.

Decided to just install GRUB again whilst installing Ubuntu, reduced the timeout and shuffled the order about to suit.

All working fine. :-D 

Cheers

---

