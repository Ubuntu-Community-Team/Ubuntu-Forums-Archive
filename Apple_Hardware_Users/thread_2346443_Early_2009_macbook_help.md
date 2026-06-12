---
title: "Early 2009 macbook help"
date: 2016-12-14
forum: Apple Hardware Users
---

### Post by warwickben on 2016-12-14
I installed ubuntu 16.04 on my old MacBook 4gigs of ram and stock hd . 
after reading as much as I could find , and I am having some trouble . It takes for ever to boot .

All I did was save the few files on my Mac I wanted to keep to my google drive . Shut my Macbook off , put USB stick in , hit the power button and held the option key down , then Wiped the drives and finished the install. Swited to the drives that where recommended

When I start up now it dose the Mac chime sound . Grayish screen for a few . Then black screen for a long long long , time some times a Nivida splash screen shows. 
Ubuntu login shows up . Screen goes black then comes back . 

Any help or advice would be great .

---

### Post by g33zr on 2016-12-14
How did you install Ubuntu with a DVD or with the USB stick? If with the latter, how did you format the USB stick? Did you wipe Mac OSX completely or are you dual booting? How did you partition the HDD during the install? 

With the Ubuntu install, the boot partition should be 300-500 MB and configured /boot/efi and the boot flag esp
Your other partitions are likely / and /home and a swap partition.

---

### Post by warwickben on 2016-12-14
I used a USB stick , I set the USB stick up on my windows pc .  I forget the program I used but its made for making  live USB sticks, has a se lotion for what flavor linux your going to install etc . Worked fine when I used it to setup my dual boot setup on my pc. 
I wiped out my OS X . 
The partition was the preset for wiping out the hard drive 

Sda1 efi fat32 /boot/efi 512.00mib boot,esp
Sda2      Ext4 /              107.54gib
Sda3.      Linux-swap.     3.75 gib

---

### Post by g33zr on 2016-12-16
^Your partitions look okay. You should be able to boot. You might want to install [Etcher]("https://etcher.io/") on you dual-booted PC and burn the ISO onto the USB stick with it and reinstall Ubuntu using the same partition setup.

---

### Post by warwickben on 2016-12-17
Sorry if I confused you . I can boot it just takes for ever todo so . 
I'm going to swap to a ssd in a week or two so maybe that will help . 

Besides a really long time to boot , only other thing I need help with is the fan . I'm not 100% sure it's work correctly . When I was running it on OS X at times the fan would get extremely loud .

---

### Post by g33zr on 2016-12-17
OK, your MacBook is getting a little long in the tooth, but an SSD should help and perhaps more RAM wouldn't hurt either. Another thing to try is installing a distro or Ubuntu flavor that demands fewer resources. I'm running Ubuntu MATE 16.04 on my aging laptop and it performs better than Unbuntu Unity 16.04. :)

---

### Post by warwickben on 2016-12-23
> **g33zr said:**
> OK, your MacBook is getting a little long in the tooth, but an SSD should help and perhaps more RAM wouldn't hurt either. Another thing to try is installing a distro or Ubuntu flavor that demands fewer resources. I'm running Ubuntu MATE 16.04 on my aging laptop and it performs better than Unbuntu Unity 16.04. :)

I just got my new ssd. I was using gnome flash back as a desktop . 
I was thinking about installing mate 16.04 but was little confused about some of the Mac fixes like getting the display brightness keys working etc . Is mate 16.04 basically just ubuntu 16.04 with the mate desktop environment and all the stuff not needed to run mate removed ?  I'm still new to Linux , so I figure it's a dumb question lol. 

Just as I finished typing this ubuntu finished installing with the new ssd. 

Boot time was extremely faster then befor . 
I currently have 4 gigs of ram installed . I've read I can put 6-8 gigs in this machine even tho Apple says it only works with 4. 
Can I get 6 or 8 gigs ? And what's a cheap ram set I can buy (this machine is old so why tho a bunch of money at it ) I've tried searching but only foun 4 gig sets .

---

### Post by g33zr on 2016-12-23
It appears that your MacBook is doing fine with SSD and 4 GB of RAM. If Ubuntu Unity runs well with what you've got, then stick with that. My laptop runs better and uses less resources (i.e., battery) with MATE. I guess you can mark this thread as solved. :D

---

### Post by warwickben on 2016-12-23
> **g33zr said:**
> It appears that your MacBook is doing fine with SSD and 4 GB of RAM. If Ubuntu Unity runs well with what you've got, then stick with that. My laptop runs better and uses less resources (i.e., battery) with MATE. I guess you can mark this thread as solved. :D
If I go with ubuntu mate would you recommend the 32 bit version ?

---

### Post by g33zr on 2016-12-24
No, your laptop can handle 64 bit. Moreover, if you update to 17.04 in the near future, you won't have 32-bit support.

---

