---
title: "CDROM wont mount"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by masooga on 2006-05-07
Okay, I'm running Dapper and I just updated the kernel to 2.6.16.  When I put a CD in the CD drive it trys to recognize it for quite some time but then gives up.  If I try to manually mount it I get:

mount: special device /dev/scd0 does not exist

Any ideas?

---

### Post by louis_nichols on 2006-05-07
Try using /dev/scd instead of /dev/scd0 in all mount comands.

A number is usually assigned to a partition, which cd's don't have.

---

### Post by masooga on 2006-05-07
Still doesn't work. :(

---

### Post by louis_nichols on 2006-05-07
What's in your fstab? Please post here the contents of /etc/fstab

And I'm thinking this happens with more than one cd, right?

---

### Post by masooga on 2006-05-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


Yes, it happens with all of my CDs.

---

### Post by punkybouy on 2006-05-09
try mount /dev/cdrom.  It worked for me but points out the shortcomings of linux. Everytime I have to do something I have to go to a terminal and either edit a file or type some manual command.  It's the reason why linux is still behind windows in ease of use.   CDROM's should mount automatically.  They do in Windows and have for years whether they are ide scsi usb whatever.

---

### Post by punkybouy on 2006-05-09
By the way I try Linux every few years starting with Red Hat 4.something and it does get better and better.  Ubuntu is the best distro I have tried so far.  It recognized my PCI-X SCSI card running in a 32 bit slot without a hitch.  Suse 10 crashed when I tried to set the date and time and Red Hat Fedora latest version 5 I think crashed after it did an automatic update.  No time to trouble shoot so I tried Ubunutu.  Very nice. Kudos to those who contribute.

---

### Post by ComplexNumber on 2006-05-09
>  Everytime I have to do something I have to go to a terminal and either edit a file or type some manual command. thats just as necessary in windows from my experience. in fact its a lot easier and less painful in linux. try getting such software such as mobile phone software without going into the registry and doing a long winded registry edit or editing ini files.i can give you a massive long list of just a handful of the windows programs for which this is required.  i've been there and done that, and so have many others. believe it or not, that is the norm in windows. it is very rare for software to work out of the box without a tweak under the hood here and there in windows.

---

### Post by masooga on 2006-05-09
$ mount /dev/cdrom
mount: can't find /dev/cdrom in /etc/fstab or /etc/mtab

I'm pretty sure it's a bug with the new kernel.

---

### Post by uzi09 on 2006-05-09
can you also just type:
mount

and let us know what it prints out for ya. maybe it's already mounted somewhere o_O. it is really weird tho :S

---

### Post by masooga on 2006-05-10
~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by punkybouy on 2006-05-10
Ok, I'll take another stab at it.  Is there a hardware conflict (IRQ)?  Do you have the CDROM set for master, slave or CS (cable select) and is this something you changed before you installed Ubuntu. Some boxes need to have the CDROM set for cable select for the bios to detect them.  Does Ubuntu have a Hardware list of approved CDROM's? Hit the Pause/break key when you see your bios screen and see if the bios detects the CDROM or maybe go into the bios and check.

---

### Post by masooga on 2006-05-11
I doubt there's a hardware conflict, if I switch my kernel back it works just fine.

---

### Post by macdo on 2006-05-11
try ```
mount /media/cdrom0
```
Because it's defined in fstab, your system should know **what** it should be mounting...

---

### Post by masooga on 2006-05-12
$ mount /media/cdrom0
mount: special device /dev/scd0 does not exist

---

### Post by macdo on 2006-05-12
Okay, I'm guessing here...
have a look in /dev/, and see if there's anything called either CDROM or hda, hdb,, hdc, etc. (other than your hard drive). If so, it *might* be that you need to change your fstab to say hd* or CDROM.

---

### Post by Bionic_Beefpile on 2006-06-09
I'm having this exact same problem...

Some sort of kernel issue maybe?  I'm totally stuck

If I try mount cdrom or mount cdrom0, I get the error "mount: special device /dev/scd0 does not exist"

there is no scd0 in my /dev either (or anything else that looks like a CDROM drive)

If I go to System==>Administration==>Disks, it shows a "Hard Disk" at /dev/scd0, but everything else is "unknown" or blank...

---

### Post by Bionic_Beefpile on 2006-06-11
I hate to bump this, but I'm still stuck...  I haven't had any luck reconfiguring my kernel, because that quits with errors when build the .deb file.  I'd love to wipe the system and do a clean install, but I need to get my data off, which isn't easy without a working CD burner

---

### Post by Bionic_Beefpile on 2006-06-12
Ok, so I did a clean install of Dapper today, and I get this problem whenever I upgrade to the 2.6.16 kernel, even without any patches applied

I can't use the 2.6.15 kernel because that one can't mount the root filesystem.

This is incredibly frustrating...

::EDIT::
[http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_cdrw_dvdrw_multi_burner](http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_cdrw_dvdrw_multi_burner)
says to add
libata.atapi_enabled=1
to the kernel command line

I'll give it a shot tomorrow

---

### Post by Bionic_Beefpile on 2006-06-13
I think that did it!

Following the instructions at the link above, I did
```
sudo gedit /etc/mkinitramfs/modules
```
and added the line
```
libata atapi_enabled=1
```

Then I did
```
cd /boot/
sudo /usr/sbin/mkinitramfs -o initramfs_2616 2.6.16 #Note: change the last 2.6.16 to match your kernel
sudo mv initramfs_2616 initramfs_2616.img-2.6.16
```
For some reason it didn't like to make the file in one step, I had to do the mv step at the end...

Ok, so finally, in the boot options for my 2.6.16 kernel, I added the line
```
initrd /boot/initramfs_2616.img-2.6.16
```

The first time you can do that boot option by hand, but after that (assuming it works), you should
```
sudo gedit /boot/grub/menu.list
```
and add it to the 2.6.16 and recovery mode entries

---

### Post by dan4444 on 2006-06-16
Running your exact commands (with just a minor mod on my 2.6.16 directory name) fixed my cdrom inaccessability prob also.

Thank you "Bionic_Beefpile", for documenting these steps in a centralized location. You saved me a lot of time and trouble. Maybe I will go though those commands later and try to make better sense of em all. Anyway, thank you.

---

### Post by nitricacid on 2006-06-16
ingore this
My bad for not reading all the posts.

---

### Post by Bionic_Beefpile on 2006-06-17
[QUOTE=dan4444]Running your exact commands (with just a minor mod on my 2.6.16 directory name) fixed my cdrom inaccessability prob also.

Thank you "Bionic_Beefpile", for documenting these steps in a centralized location. You saved me a lot of time and trouble. Maybe I will go though those commands later and try to make better sense of em all. Anyway, thank you.[/QUOTE]
Really glad to hear it worked for you.  This was a problem that was bugging me for a while, and was getting on my nerves.
I'm not totally sure what the fix does, but here is what it says on the site I linked (where I found the instructions):
The DMA support doesn't work because the drive is connected to the SATA controller.  The ATAPI support on SATA just has to be enabled in the kernel.

I'm willing to bet that there is a way to build this right into the kernel, bypassing all of the boot option alterations I've listed above, but I tried that about 4 times and never did get it to work.  I'm sure I just didn't find the proper check box in the config.  For now, this solution does the job, and the next time I compile a kernel I'll look closely for the option there.

---

### Post by Tamatoa on 2006-06-17
This is the line that gets added when I type "moount" after inserting a CD into my system.


/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=blahblah)

---

