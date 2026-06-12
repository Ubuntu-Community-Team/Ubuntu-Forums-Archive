---
title: "The best way to install multiple distros?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Xarok on 2008-03-18
So I would like to take my 80GD Ubuntu HDD and add a few more Linux Distros to test out.
The main one I'm interested in right now is openSUSE.

Is there an easy way to just give openSUSE it's own 10GB partition and select it from grub?
Is it easy uninstallation/erasure if I don't like it?

Anything that other distros have that Ubuntu doesn't? 
I've noticed that quite a lot of software I find on the net is offered in RPM style, but I've also heard bad things about RPM, such as dependancy hell...

What do you guys think?

---

### Post by myusername on 2008-03-18
the easiest way is to just use virtualbox it has saved my loads of money in the blank cd department

---

### Post by MockY on 2008-03-18
I would go VMWare or VirtualBox. At least that is what I prefer.

---

### Post by jken146 on 2008-03-18
A VM is an unfair comparison of distros, for some things.

You can just partition off some extra space for SUSE's root to go on, then cross your fingers and hope that GRUB automagically sets itself up properly.  If it doesn't (it most likely will), don't panic, it can be sorted out from a live CD quite easily.

---

### Post by k33bz on 2008-03-18
i would use vmware or use a different computer (test box) totally, which is what i prefer for testing out other distros.

---

### Post by Xarok on 2008-03-18
I actually tried VirtualBox to install openSUSE and it didn't work.

SUSE asked to make a swap partition/file and it wouldn't do anything.

It's also slow 'cause I only got 256 MB RAM

---

### Post by Shazaam on 2008-03-19
The best way depends on if you have Windows installed. If you do have Windows installed, boot to Windows, defrag it a couple of times. Then use what ever partitioner you are partial to (Ubuntu livecd; gparted livecd,etc) to shrink (resize) the Windows partition. Once that is done create an extended partition to enclose the unallocated space. Inside that extended partition add a swap partition (around 500meg, no less). Then go about adding distro's using logical partitions inside the extended partition. When you add them point the installer(s) to the already made swap partition. it's ok to share the swap partition with other distro's.
With only 256megs of ram you may run into problems. Add more if you can.

---

### Post by SneakyBooBoo on 2008-03-24
i agree, using a VM is a bit unfair when trying to compare. The performance on a VM compared to running the OS natively is very different in my experience. Maybe cos i dont have a multi core processor. But as far as i know, any type of emulation is never as fast as the real thing. thats just my opinion tho. if u've run a program better on an emulator, well then more power to you.

---

### Post by angry_johnnie on 2008-03-25
You can install each distro you want on a separate partition, but keep in mind that only four primary partitions are allowed.  So, I think the easier way to go would be to make a big extended partition, and as many logical partitions as you want, inside the extended one. 

All your different distros can share swap, but it's not a good idea to share /home.  Other than that, I would advise to install Ubuntu after all the others, as it will recognize all your other systems and add them to grub's menu.

If you have already installed Ubuntu, and don't want to erase it, you can still add more distros.  But, you'll have to edit your /boot/grub/menu.lst (on whichever distro you install at the end), so that it includes all others.

The same can be done from Ubuntu, if you choose not to let the other distros install their bootloaders.  Again, you'll have to edit /boot/grub/menu.lst.

There have been quite a number of threads posted on how to edit grub.

I just can't seem to find them... :-)

Anyway, it should be simple.  Just copy from each distro's /boot/grub/menu.lst, and paste the contents in Ubuntu's, after the line that says end debian automagic kernels list.

Good luck.  
Multi-booting is lots of fun!

---

