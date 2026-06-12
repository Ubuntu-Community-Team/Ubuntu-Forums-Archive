---
title: "Try them all?"
date: 2012-03-27
forum: Any Other OS
---

### Post by Subidubi32 on 2012-03-27
I plan to install multiple Linux systems on my computer, to try them. But I don't know a few things:
-Is it possible, to make only one Linux swap partition for multiple distros?
-How many partitions can I create on one hard disc?
-How many partitions I have to create for optimal performance?... I thin of these mount points /, /var, /home, /temp etc...
-What bootloader would be optimal? Grub2 maybe?

i would like to try Arch, Fedora, Redhat

---

### Post by Pand5461 on 2012-03-27
It's of course possible to use the same swap partition for all distros, just choose it on installation and do not format it.

Moreover, I think it's possible to use one /home partition for sevral distros.

The maximum number of primary partitions is 4 per physical drive, but I don't know if there is a limit on number of logical partitions.

But may I ask you, why do you want to install the distros on the hardware and not to try them in VM? I think the latter is safer and way less problematic.

---

### Post by rk0r on 2012-03-27
> **Pand5461 said:**
> It's of course possible to use the same swap partition for all distros, just choose it on installation and do not format it.

Moreover, I think it's possible to use one /home partition for sevral distros.

The maximum number of primary partitions is 4 per physical drive, but I don't know if there is a limit on number of logical partitions.

But may I ask you, why do you want to install the distros on the hardware and not to try them in VM? I think the latter is safer and way less problematic.

I agree with the VM approach as you can keep the ISO of the distro you want and boot up into whatever flavour of linux/ OS you wish. I have done this and it save a whole bunch of time, if you dont like the distro you just obtained delete the ISO and not your whole file system :).

---

### Post by QIII on 2012-03-27
+1 more for virtualization.

You can throw out the ones you don't care for like dirty diapers.

---

### Post by ranger1021994 on 2012-03-27
Even i wud recommend u to use Virtualization
Use VirtualBox....Its free... :)
I wont recommend messing with GRUB2 or even with HDD..
Keep it simple...Keep it safe :)

---

### Post by cuppsy on 2012-03-30
Another +1 for using VirtualBox. It's not just safer, it'll be a whole lot faster for the sake of testing different distros.

That said, if you are (or eventually) decide to physically install several distributions together, a couple tips:

1) You can use one swap and one /home partition, but make sure each distro has a separate username, so they don't conflict in the /home directory. 

2) From my experience, give each distro a /boot partition and then install GRUB from the last distro on the MBR. Most distros now are good as detecting other distros and configuring GRUB accordingly for you, so it shouldn't be a major task.

3) Depending on your experience level with Linux, and how adventurous you are, I'd recommend reading up on LVM (Linux Volume Management). It's a way of partitioning your hard drive to use "virtual" partitions that can be added/deleted/resized without having to start from scratch, and in a multi-boot system (I've ran upwards of five or six distros at a time before) it's almost essential, since you never know when you'll wanna drop a distro.

Best of luck with however you decide to proceed.

PS - Here's a link for reading up on LVMs. It's from ArchWiki, but it's applicable to basically all distros (and most won't require the terminal commands, for instance, Ubuntu's alternate installer allows you to set up the LVM from a fairly easy menu): [https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

---

### Post by zhogan85 on 2012-03-31
I would like to offer a dissenting opinion to those in favor of virtualization. Virtualization absolutely is a great alternative, but not in every situation. I personally have a triple boot system on my machine.

To answer your questions:

-Yes, you can and should share the same swap partition. Just make sure after you've installed them all, look at the fstab, in each. I've had it happen with certain installers, that for some reason they change the UUID of the swap partition, so make sure the UUID of the swap partition in fstab in each distro is the same.

-As Pand4561 noted, you can have four primary partitions, but unlimited logical partitions.

-This is up to the user. Different people will give you different answers. On my system, I have a shared data partition for all distros, but I have each system on their own partition. While technically you can share a /home partition between distros, this can cause problems if different versions of the same applications are installed on different systems. I think the work around is to have different user names for each system. If you go this route, be sure to read up.

-I like Grub2 and have had no problems with it recognizing additional distros. Install it with the first distro you install, and then skip that step in the other installations.

Hope this helps.

---

