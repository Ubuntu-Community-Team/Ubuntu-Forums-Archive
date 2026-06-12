---
title: "Second Dual Boot Dapper question"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by richbarna on 2006-06-11
I,ve just used gparted to wipe out an old Dapper partition,
|
|
v
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=11068&stc=1&d=1150060947[/IMG]

I want to install another Dapper in the free space, but after having some major problems trying to get two installations of Dapper to be recognised at boot, I am a bit dubious about this one.
I've just got Dapper set up and running sweet on hdc3.

Does anybody think that I will have any problems with this? I really don't want to reinstall for a third time.
The last time I tried I only got access via GRUB to the newest Dapper install.
I thought it would be the same as an XP/Dapper dual boot where both OS's get added to the boot loader.

Thanks

---

### Post by richbarna on 2006-06-11
Ok no problems, I found this :-

**HOW TO DUAL BOOT MULTIPLE LINUX DISTROS**

All the Linux flavors I have tried have no problem dual-booting with Windows, but how do you boot multiple Linux flavors, like Fedora and Ubuntu? This is a great way to have your favorite distribution on the first drive (hda) and experiment with the hundreds of others on a second drive (hdb). I found many procedures by Googling, but most of them concentrated on booting two distros on the same hard drive. However, this is a very simple procedure.

I have found that if you try to dual-boot Linux with Linux, the second flavor that you install overwrites the existing boot loader and the first distro seems to vanish. To solve this problem, don't install the boot loader of the second distro. You should be able to find an option for this as you go through the install process.

I know what you're thinking -- if I don't install the boot loader, how will I boot the system?

Let's assume that the bootloader is on the first hard drive (hda) from your original distro. You need to copy certain files from the /boot directory of the hdb drive to the /boot directory of the hda drive. To do this, you must first mount the hdb drive while logged in as the root user. Since this is only a temporary mount point, I just use the floppy directory:

mount/dev/hdb1 /mnt/floppy

Some of the newer distros now use the /media directory for mount points, so if the above command doesn't work, try:

mount /dev/hdb1 /media/floppy

You should see an icon appear on the desktop that looks like a diskette. Enter that drive, and cd /mnt/floppy/boot or cd /media/floppy/boot.

There are three files you need to copy to the /boot directory of the first hard drive (hda). The first is System.map, which will look something like System.map-2.6.9-1.6_FC2 (which is the System.map for the 2.6.9.-1.6 kernel from Fedora Core 2). The other two files will have identical numeric suffixes, after prefixes of vmlinuz and initrd. Once you locate these three files, copy them to the /boot directory of the first hard drive (hda). When copying the initrd file, make sure to copy it exactly as you see it, including the .img extension that will be someplace in the name of the file.

Now cd /boot to change to the /boot directory of your first hard drive (hda). You should see the three new files added to the directory.

Now there's only one step left -- add a stanza to GRUB, the boot loader file. Change to the /boot/grub directory and open the file menu.lst in your favorite text editor. Scroll down a few lines and add the new stanza under the one for your existing distro, skipping a line between them. It should look something like this:

title "whatever you want to call your new distro"
        root (hd1,0)
        kernel /boot/vmlinuz"Your Kernel Number" ro root=LABEL=/
        initrd /boot/initrd"Your Kernel Number".img

Note that this is a case-sensitive and space-sensitive document. That means that root=label is different from root=LABEL, and there is no space after the "=".

If you've done things right, you can now reboot your machine and you will see your new entry in the boot menu. Select it and you will boot into your new distro.

---

