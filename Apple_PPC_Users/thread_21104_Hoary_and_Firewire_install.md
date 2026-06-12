---
title: "Hoary and Firewire install"
date: 2005-03-20
forum: Apple PPC Users
---

### Post by matthis on 2005-03-20
Will Hoary make install and booting from external firewire easy?
In warty, installation failed at the yaboot step, and the initrd didn't include firewire support.... so, will this work in hoary?

EDIT: no reply to this... its a shame as many people would like to install ubuntu without having to change their current internal hd partitions...

---

### Post by matthis on 2005-04-09
So, has anyone tested it? \\:D/ OK, I just tested it, and it doesn't work. Too bad.  :-?

---

### Post by Huxley on 2005-04-11
Hi all
I hope this will work soon -any help with FW code from YDL and Mandriva Linux?

---

### Post by scramblejams on 2005-04-13
I've gotten along a ways using this guide:

[http://lists.terrasoftsolutions.com/pipermail/yellowdog-general/2003-October/010501.html](http://lists.terrasoftsolutions.com/pipermail/yellowdog-general/2003-October/010501.html)

I've got it starting the boot off my Firewire drive, now I'm fiddling with my initrd to make it mount the root partition. This may not be an option for you if you don't already have a yaboot installation on your internal drive as I'm modifying my internal drive's yaboot.conf to make it work.

I'll post any updates on my progress here.

Steve

---

### Post by matthis on 2005-04-14
Sure please let me know if you succeed. As for the yaboot, I've managed to install it on the firewire drive and boot from it, but I get stuck at a mounting error of the root filesystem. Maybe we need to compile a kernel with firewire modules?

---

### Post by dendave on 2005-04-14
Tried it and the install cd doesn't "see" the fw drive. I am also in the search for this option as I want to keep osx on my internal drive. Yellowdog sells drives that boot but apart from an obnoxious howto I cannot find out if there is an "easy" way to this and / or whether the linux ppc community is at current working on a scripted install for this. YD looks like anaconda installer script with some patches in the kernel.  It feels like linux on x86 three years ago... LOL!!

---

### Post by scramblejams on 2005-04-14
[QUOTE=matthis]Sure please let me know if you succeed. As for the yaboot, I've managed to install it on the firewire drive and boot from it, but I get stuck at a mounting error of the root filesystem. Maybe we need to compile a kernel with firewire modules?[/QUOTE]
I've been modifying the initrd image to make it load the relevant kernel modules, but I'm still stuck on mounting the root filesystem. It sees the Firewire drive, and attaches to it. It gets as far as /sbin/init in the initrd, and all the way down to where it has to do mknod, but it says Operation Not Permitted, so something's wrong either with the way it's got the RAM disk mounted, or it expects to have the root filesystem mounted by then. Can't quite figure it out... I really shouldn't spend the time, but my iBook is mocking me! :-D

---

### Post by scramblejams on 2005-04-14
[QUOTE=dendave]Tried it and the install cd doesn't "see" the fw drive.[/QUOTE]
Hrm, not sure what to tell you about that. The installer saw it fine for me, no fiddling necessary. Maybe there are other devices on your FW chain that could be removed?

In other news, I'm a step closer. See, when I unpacked the initrd image in /boot, since it's a cramfs image, I can't modify it. So I copied the contents into another directory. When I did that, it warned me that it couldn't copy a bunch of hard links. It wouldn't let me do hard links using "ln", so I substituted symlinks, thinking it'd be all right.

It's not. I tried the same procedure on my Debian box, and the symlinks are killing the boot. So now I've got to figure out why my system isn't letting me make hard links, even though I'm root.

---

### Post by khc on 2005-04-14
I don't have a firewire drive, but I see this as something interesting. Just to make sure, you know that you cannot make hardlinks across partitions right?

---

### Post by scramblejams on 2005-04-14
Okay, a little further now. I'm still not sure why I can't make hard links (even tried using tmpfs), but based on another thread here ([http://ubuntuforums.org/showpost.php?p=42546&postcount=14)](http://ubuntuforums.org/showpost.php?p=42546&postcount=14)), I just decided to replace them with empty directories. Well, the earlier errors went away, and it seems to mount the filesystem, but now it dies with a whole bunch of "sbp2: sbp2util_node_write_no_wait failed" error messages. Not sure yet what that's about...

---

### Post by scramblejams on 2005-04-14
[QUOTE=khc]I don't have a firewire drive, but I see this as something interesting. Just to make sure, you know that you cannot make hardlinks across partitions right?[/QUOTE]
Yes. In this case, I can't seem to make a hardlink inside the same directory. Even tried booting into single user mode and trying to do the work on tmpfs, but it wouldn't work.

I'm not sure how mkinitrd does it when it makes the initrd image.

---

### Post by scramblejams on 2005-04-14
Well, I'm going to have to give up on this for today. But for anybody who wants to try, here's an overview of what I did:

Assumptions: The root partition on my firewire drive is on sda3. I've mounted it under /mnt/firewire. And I've got an existing Linux (Debian Unstable) installation on my internal drive which is what I'm working off of. Any distro should work, though, as long as it has a reasonable up-to-date yaboot installation. I'm doing all my yaboot stuff with my internal partition for now.

1. I installed Hoary to the firewire drive using the normal install procedure. When it choked on the yaboot install, I told it to just ignore it and continue. Then I added an entry like this into my internal drive's yaboot.conf:

image=/boot/vmlinux-2.6.10-5-powerpc
	initrd=/boot/initrd-new.img
	device=/pci@f4000000/firewire@e/node@0010100500000a71/sbp-2@4008/disk@0
	partition=3
	label=fw
	boot=/dev/sda3
	root=/dev/sda3
	read-only

initrd is set because of what we'll do below. partition=3 because of the root partition being on sda3, and the device line is info you should get from doing this (make sure to strip the foregoing path of what this command gives you, what you paste in should start with "/pci..."):

# find /proc/device-tree/ -name disk@\* | grep -i firewire

Now we've got to modify the stock initrd image So I went into the FW drive, where the Hoary installation lives, mounted the initrd image somewhere, then made a copy of its contents:

# mkdir /mnt/initrd /mnt/initrd-new
# mount -o loop -t cramfs /mnt/firewire/boot/initrd.img-2.6.10-5-powerpc /mnt/initrd
# cp -pR /mnt/initrd/* /mnt/initrd-new/
# umount /mnt/initrd
# rm -Rf /mnt/initrd

During the copy it should throw a bunch of errors about hard links, do this:

# cd /mnt/initrd-new
# mkdir devfs keyscripts mnt proc scripts sys tmp var

Now clean up after ourselves...

# umount /mnt/initrd

Now, the problem is that the stock initrd doesn't include the ohci1394 module. So we'll fix that.

# cp /mnt/firewire/lib/modules/2.6.10-5-powerpc/kernel/drivers/ieee1394/ohci1394.ko \
    /mnt/initrd-new/lib/modules/2.16.10-5-powerpc/kernel/drivers/ieee1394/

Okay, so now the right drivers live in our new initrd image. Now we have to get the initrd image to load them, so modify your /mnt/initrd-new/loadmodules to look like this:

modprobe -k unix 2> /dev/null
modprobe -k sd_mod
modprobe -k ieee1394
modprobe -k ohci1394
sleep 2
modprobe -k sbp2
modprobe -k sr_mod

Wait, you say! Initrd has no sleep command! You're right. Gotta copy that too. So copy it from your Ubuntu install's /bin directory into your initrd's bin directory. But wait, sleep has library dependencies. Well, do "ldd /mnt/firewire/bin/sleep" to see what it depends on, then copy those from your Ubuntu install into your initrd's lib directory. Now it should be able to sleep.

Now we've got to install the new initrd image on your fw drive. So do:

# mkcramfs /mnt/initrd-new /mnt/firewire/boot/initrd-new.img
# ybin

With that you should get at least as far as I do. Reboot, enter "fw" into yaboot to boot into firewire mode, and it should at least hit the part where the driver chokes.

I'd be VERY interested in somebody else trying this and seeing what happens.

---

### Post by scramblejams on 2005-04-14
BTW, I'm doing this on an iBook G3, so I'd be particularly interested in somebody trying this with different hardware.

---

### Post by scramblejams on 2005-04-14
Well, this bug here ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=302806)](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=302806)), which sports a bunch of the same errors I'm getting, makes me wonder whether this is a kernel bug. However, booting off the Live CD allows me to mount the same drive just fine (points off gnome-volume-manager here, it mounted it, opened a window with its contents, but it failed to make an icon on my desktop!), so I'm not sure what the deal is, as the LiveCD uses the same kernel as the installer CD.   ](*,)

I sent an email to the author of sbp2, hopefully that'll turn up a clue.

---

### Post by scramblejams on 2005-04-21
Ha, y'all are lazy slacks!   :razz: 

Didn't get a reply from the driver author, and nobody here joined in, so I gave up and installed Hoary on the internal drive. Anybody who wants to boot off Firewire will have to pick this up and run with it on their own.

Steve

---

### Post by interrupt on 2005-04-26
I have successfully managed to boot off external firewire drive:

[see this post](http://www.ubuntuforums.org/showthread.php?t=29837)

---

### Post by scramblejams on 2005-04-27
[QUOTE=interrupt]I have successfully managed to boot off external firewire drive:

[see this post](http://www.ubuntuforums.org/showthread.php?t=29837)[/QUOTE]
Very cool, I'll have to give it a try. Thanks for the tip!

---

### Post by basilarchia on 2006-10-12
> **scramblejams said:**
> Okay, a little further now. I'm still not sure why I can't make hard links (even tried using tmpfs). I just decided to replace them with empty directories. 

That's correct. mkcramfs makes the empty directories look like hard links so you can't copy them. Making new empty directories for the missing ones is the correct thing to do. When you recreate your initrd with mkcramfs, they will again show up like hard links.

---

