---
title: "[SOLVED] triple boot problems"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by just learning on 2007-10-30
I have ubuntu gutsy and windows xp on a dual boot . xp is on one hd and ubuntu is on another.
I wanted to try to triple boot with video linux on the same hd as ubuntu.i was able to install it and i think i installed it's boot loader to it's root partition. but when i boot up i get no option in grub to boot video linux. just xp and ubuntu. can someone help please and thank you in advance.:(

---

### Post by Doggles on 2007-10-30
Hi

Sounds to me like you need to manually add an entry into grub for your new install - Grub only detects and adds things in while it's being installed, so your original Grub on your master boot record doesn't yet know that your new install, and it's own copy of grub, exist.

You need get into Gutsy, then open a terminal and type the following to edit the Grub menu:

gksudo gedit /boot/grub/menu.lst

type your password and you should then see the set of instructions that your original copy of Grub is using. Everything that begins with a "#" is inactive, and there just for information. Scroll down and near the bottom you'll see the entries that refer to the boot options for your current system - they'll look like this:

"title    Ubuntu 7.10 blahblahblah...

Now, you need to add an entry to this section in this format:

title  <call it what you want>
root <see example below>
chainloader +1

so, for the title - whatever you put there is what will show up in your grub menu at bootup,

root - you need to specify which partition you new operating system is on, - these count up from zero, so for instance, if it is on the second partition of your first hard drive, then the line you need to include in the above will be:

root (hd0,1)

the chainloader bit just makes this copy of grub kick over to the copy of grub on your new install's root, which will take it from there. This is quite a good way to do it as if you update / change your new system and edit its own (root-based) grub appropriately, the original grub on your MBR will still point to the right place.

There - hope that makes sense ... and I hope I've remembered it right!

Grub is a great bootloader, and will be your friend if you become addicted to trying out new distros - there's loads of info on these forums about it, so I'd take the time to find a decent guide if you can, because it can be annoying if you stuff it up. Remember that if you ever mess up your Grub / MBR, you can use a live CD to get back in and set Grub up again - so even if your system seems wrecked, it might not be!

Cheers matey - best of luck

---

### Post by Doggles on 2007-10-30
...oh yeah, and then save your changes of course...

when you boot up, your new entry should appear in Grub menu

---

### Post by just learning on 2007-10-30
i tried that, and when i reboot i have the option to go to video linux. but when i select it it goes to starting up and never does nothing. Thanks again.

---

### Post by just learning on 2007-10-30
i did a fdisk -lu and here is the output:

Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa74ba74b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    39857264    19928601    7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x26132612

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    87891614    43945776   83  Linux
/dev/hdb2        87891615   156296384    34202385    5  Extended
/dev/hdb5        87891678   151766054    31937188+  83  Linux
/dev/hdb6       151766118   156296384     2265133+  82  Linux swap / Solaris

the one thing i did notice was that /dev/hdb5 has no astrix under boot colum and i am pretty sure that is my video linux. so maybe i put the bootloader for it in the wrong place b/c i know i installed it. any ideas would be great.thanks!

---

### Post by Doggles on 2007-10-30
OK then, so we're successfully saving changes to your grub menu, but now it sounds like they're pointing to the wrong place perhaps, or as you say, where they're pointing to doesn't have a grub of its very own...

You usually just get the option to install the bootloader either to / or to the MBR, if you'd picked the MBR the I don't think your problems would be the same as described, so if you've installed grub for your videolinux at all,  it must probably have gone on /

I'm a n00b myself by the way, so apologies for any unintentional misinformation! - just doing my best...

looks like you're using extended partitions on hdb, so that might make the numbering confusing too...

so, just to check, in the "root" bit of the grub menu entry, I think you might need this?:

root (hd1,4)

If that's what you've got, then maybe we do need to check whether grub is in the right place. Luckily, there's an easy way to find where your grub bits'n'pieces are. Open a terminal in Gutsy and type this:

sudo grub

then this:

find /boot/grub/stage1

This should return all of the places that grub is installed - hopefully your videolinux partition will be among them? - you can then make sure that your menu.lst is pointing to the right place.

(also, you could maybe try mounting that partition in Gutsy, and browse to its /boot/grub folder, if that's there and it contains its own menu.lst file, you could even copy the correct grub entries from there into your own menu.lst - never tried to do it that way though, so no idea if that will work... presume this would need to be done as root)

Now, as for the boot flag, I'm not sure if it's necessary (like I said, total n00b myself...), but I'm pretty sure that you can flag a particular partition as "bootable" using gparted running off a live CD. So the boot flag is not necessarily indicative of Grub being there. Don't do this one until you've tried everything else of course...

I think that your last resort in a case like this will be to reinstall VideoLinux, then when prompted, install its Grub to the MBR. Some distros recognise that other distros are present at this point, and set up Grub to see them all, so then at least you'll be able to get into videolinux and Gutsy. HOWEVER - bear in mind that this might get rid of your menu.lst file's references to windows, and you might have to edit to get windows back - there are good guides to that effect on this forum though - and as you've already set up a dual boot, then you clearly know what you're doing in that regard, so that may be less of a problem. Maybe take a note of the entries for Windows in your current menu.lst, then just pop them in later to get Windows back (as windows appears to be on a different disk, there might be some remapping lines required?). ALSO - this will then make the MBR Grub refer to the menu.lst of the VideoLinux partition, so if you later decide to delete videolinux, you'll need to tell grub to resume referring to your original Gutsy menu.lst - I think I've got instructions for doing that at home (I'm at work at the minute...)

So - to summarise - make sure you're referring to the correct partition, and verify whether Grub is actually installed on that partition.

Keep on chipping away at it, you'll get there... :)

---

### Post by Doggles on 2007-10-30
By the way - post the content of your menu.lst file and I'll have a look at that and compare it with mine when I get home - maybe there's something obvious in there that we're missing... :)

---

### Post by just learning on 2007-10-31
Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa74ba74b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    39857264    19928601    7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x26132612

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    87891614    43945776   83  Linux
/dev/hdb2        87891615   156296384    34202385    5  Extended
/dev/hdb5        87891678   100920329     6514326   83  Linux
/dev/hdb6       151766118   156296384     2265133+  82  Linux swap / Solaris


thats the output of fdisk. through me reading in the last couple of days, i think i know where the bootloader is (units=sectors of 1*512=512 bytes). i notice that ubuntu and xp have it but videolinux doesn't.Anyhow thanks for the help doggles i am just going to try the updated version of videolinux live cd.ciao!

---

### Post by Doggles on 2007-10-31
OK - best of luck matey

One other thing - I've noticed that some entries in my own menu.lst use "rootnoverify (hdx,y)" rather than "root (hdx,y)" ... don't know if that makes a difference - I think it's used when grub is not going to recognise the system that it is handing over to - like windows for instance. Not sure that will help in this case.

Anyway, let me know how you get on with the new videolinux cd - once you have it set up and working, it would be nice to compare the menu.lst files of videolinux and your original Gutsy version - just to see what the correct grub entry for you videolinux system actually is, and see how close we got!

Finally - not sure if you're aware of this one: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
might come in handy...

Cheers

---

### Post by just learning on 2007-10-31
it must have been an install error on my part b/c i did a fresh install of dreamlinux in the videolinux partition and blamo! everything works. i can now triple boot. i actually wanted to try dreamlinux as well so thats great.maybe when videolinux comes out with a more stable version i will give it another shot. thanks for all your help doggles. ciao!

---

### Post by Doggles on 2007-11-01
YAY!

Glad you got it sorted.

:guitar:

---

