---
title: "HOWTO Customize oversize ubuntu-9.10-desktop-powerpc.iso (Karmic Koala) for 700 MB CD"
date: 2009-11-23
forum: Apple Hardware Users
---

### Post by tiresia on 2009-11-23
To install Ubuntu 9.10 (Karmic Koala) is advisable to use ubuntu-9.10-alternate-powerpc.iso to download [here]("http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-alternate-powerpc.iso") 

To install it booting from the LiveCD you need to burn it to a DVD, because the size of the iso-image is bigger than 700MB CD. If a CD-ROM does not support burning or reading from DVD, you can follow [this]("http://ubuntuforums.org/showthread.php?t=1333829") thread to force iso-image to fit in a 700MB CD in MacOSX (but it should also possible in Linux using wodim with the option -overburn)

Here I describe a way to reduce the iso-image's size, just removing data (Kernel and Intrd) that are not needed for my architecture. When you mount the iso-image, you will notice that they are stored in /casper/powerpc (powerpc32) respectively in /casper/powerpc64.

:!: *Try it at your own risk!* :!:

 

Download ubuntu-9.10-desktop-powerpc.iso to the directory ~/Downloads (or wherever you prefer)
```
$ cd Downloads
$ wget http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-desktop-powerpc.iso
```
Checksum the downloaded iso-image
```
$ md5sum ubuntu-9.10-desktop-powerpc.iso
```
fa2c5eb18dfb2e82fffa661fac75a240


Download hfs.map to ~/Downloads. We'll need it to create a bootable powerpc iso-image
```
$ wget http://people.ubuntu.com/~cjwatson/hfs.map
```

Mount the iso image
```
$ sudo mount -o loop -t iso9660 ubuntu-9.10-desktop-powerpc.iso /mnt
```

Exit Downloads
```
$ cd ~
```

Create a directory ~/custom-ubuntu (or whatever) where to copy ALL the content of the mounted CD
```
$ cp -ra  /mnt custom-ubuntu
```
**[COLOR="Red"]For PowerPC 32-Bit Users (G3 and G4)[/COLOR]**
```
$ sudo rm custom-ubuntu/casper/powerpc64/initrd
$ sudo rm custom-ubuntu/casper/powerpc64/vmlinux
```

[COLOR="Red"]**For PowerPC 64-Bit Users (G5)**[/COLOR]
```
$ sudo rm custom-ubuntu/casper/powerpc/initrd
$ sudo rm custom-ubuntu/casper/powerpc/vmlinux
```
Generate an hybrid bootable iso-fs with genisoimage
```
$ genisoimage -hfs -part -map /home/~/Downloads/hfs.map -no-desktop -hfs-volid "Ubuntu 9.10" -hfs-bless /home/~/custom-ubuntu/install -pad -l -r -J -v -V "Ubuntu 9.10" -o custom-ubuntu-9.10-desktop-powerpc.iso /home/~/custom-ubuntu
```

(Do not forget to change '~' to your user name) 

You should get in your /home/~ directory a new .iso image called 'custom-ubuntu-9.10-desktop-powerpc.iso' SMALLER than 700 MB. My image for ppc64 is 692 MB.

Burn the generated .iso image with your preferred application or with wodim
```
$ sudo wodim -sao custom-ubuntu-9.10-desktop-powerpc.iso
```
Unmount the downloaded .iso image
```
$ sudo umount /mnt
```


Reboot to check if it works as expected. As always, be patient when you boot a LiveCD, it can take longer than expected. At the yaboot prompt, hit TAB to see all possible options. Of course only those for your architecture are available. Choose live-nosplash-powerpc or live-nosplash-powerpc64 to see what happens when booting.
Please, don't forget that *you can use the custom CD ONLY on the appropriate architecture (either ppc32 or ppc64)*.

---

### Post by vodsonic on 2010-02-23
Thanks for the tutorial. It was easy to follow. All went well until I tried to use the new CD to boot the PowerBook. I can get into the Mac's boot menu, but it doesn't present this CD as an option for booting, as it does with the PPC alternate install CD I've got. After 15 minutes or so, the CD still doesn't appear in the boot menu, so I'm stuck. Tried burning it twice on two different burners & OSes.

---

### Post by tiresia on 2010-02-23
How did you burn it?

---

### Post by vodsonic on 2010-02-23
With Disk Utility on a Mac, and with Brasero on a Xubuntu system using a USB CD burner. 

Meanwhile, I did finally get a direct download of 9.04 PPC to complete, so at least that will start to boot the PowerBook in question.

---

### Post by tiresia on 2010-02-23
I guess you know that you should burn the iso image, not just the files.
Anyway checking if you can boot 9.04 is a good idea to understand if the problem has to do with the custom cd or with the burning process

---

### Post by vodsonic on 2010-02-23
I did burn the iso image, not the files.

The 9.04 image worked once I burned it.

Thank you again for your suggestions. I'm not sure why the iso I created didn't want to boot, but I did get where I needed to go in the end.

---

### Post by ritalin153 on 2010-02-27
Thanks for the HOWTO. I followed your guide on reducing the size of the ISO. It worked okay for me, now booting Ubuntu on my trusty Powerbook. :-)

---

### Post by tiresia on 2010-02-27
> **ritalin153 said:**
> Thanks for the HOWTO. I followed your guide on reducing the size of the ISO. It worked okay for me, now booting Ubuntu on my trusty Powerbook. :-)Glad to hear it! Let me please know if you had any trouble during installing

---

### Post by OzzyFrank on 2010-03-16
For those wondering how to do this in Ubuntu, with this or any other .iso a bit over 700Mb, open it with K3b, and it will automatically burn it using wodim. If you haven't already got K3b, install it, and then right-click the .iso, choose to add a new app to the list of choices, pick K3b from the list supplied, and away you go.

---

### Post by dlkolegaev on 2011-05-22
Hi.
Unfortunately after doing everything in HOWTO .iso is not bootable :(

Tried twice.

Maybe for Natty this guide is not working.

Any suggestions?

Thanks

---

### Post by OzzyFrank on 2011-05-23
Did you try burning it with K3b as advised?

---

