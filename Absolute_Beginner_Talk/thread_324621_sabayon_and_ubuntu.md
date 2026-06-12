---
title: "sabayon and ubuntu"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2006-12-24
Wanting to install Sabayon from the live DVD on my HDD which only has a fresh Ubuntu install on it. Can I do this and have them both on together? Can I dual boot with them as you can with XP?
 
tchoklat

---

### Post by spockrock on 2006-12-24
yes you can.

---

### Post by tchoklat on 2006-12-24
so I just run the DVD and "press" install or the likes and it will self install as Ubuntu did?
 

tchoklat

---

### Post by spockrock on 2006-12-24
> **tchoklat said:**
> so I just run the DVD and "press" install or the likes and it will self install as Ubuntu did?
 

tchoklat

well I have never installed Sabayon so I can't say, but you can install sabayon to a separate linux partition, and you should be ok to dual boot.

---

### Post by tchoklat on 2006-12-29
I have received my Sabayon LiveDVD and want to istall it on my Edgy Ubuntu system. How do I do it p[lease? The loader seems to want to delete the Linux partitions to accomplish it


tony

---

### Post by taurus on 2006-12-30
You need to have an empty partition to install Sabayon.  If you don't have one, better use GParted LiveCD to resize your Ubuntu then...

---

### Post by tchoklat on 2006-12-30
... so I create another partition, say 15Gb and 'tell' Sabayon to install on that partition. Is that the way? I don't know to much about partitions though I do have gparted ..

---

### Post by taurus on 2006-12-30
Yes, you need to create an empty partition first before you can install Sabayon since it will not resize your harddrive for you first...

Again, backup your important files before you do any resizing in case something could go wrong!

---

### Post by crispy_420 on 2006-12-30
I tried Sabayon, didn't like it. Seemed slow to boot, twice as slow as Ubuntu. It has been a bit since I missed with it though. It does look interesting, very cutting edge stuff visually.

Keep in mind if you are a hardcore open source person, this OS is full of propriety drivers and software. Not a problem for me but some won't approve. Also there are is software of questionable legality too, think libdvdcss. Just warning you in advance.

I did this little guide in their forum that looks pretty intriguing: (may give a try myself)

[How to make a Sabayon LiveUSB]("http://www.sabayonlinux.org/forum/viewtopic.php?t=3008")

---

### Post by tchoklat on 2006-12-30
major problems - need urgent help ...

I created a partition on my HDD with GPArted. Sabayon required me to 'make' a boot partition which I did according to the installation program. I installed Sabayon OK but the boot up gave me only one choice - sabayon - no Ubuntu.

I deleted the partition I created an now cannot boot up.!!!!!!

When I reboot, I get a GRUB prompt on the screen - no grub menu, no Ubuntu. What have I done, and more improtantly wot do I do. I am now using the live CD!!!

Tchoklat

---

### Post by robenroute on 2006-12-30
> **tchoklat said:**
> major problems - need urgent help ...

I created a partition on my HDD with GPArted. Sabayon required me to 'make' a boot partition which I did according to the installation program. I installed Sabayon OK but the boot up gave me only one choice - sabayon - no Ubuntu.

I deleted the partition I created an now cannot boot up.!!!!!!

When I reboot, I get a GRUB prompt on the screen - no grub menu, no Ubuntu. What have I done, and more improtantly wot do I do. I am now using the live CD!!!

Tchoklat

I'm not sure whether the live CD has any provisions for this (I always work with the Alternate CD), but you could get a program like testdisk to undelete the Ubuntu partition. If you can't do that using the Live CD, download something like SystemRescue (a bootable Linux with all sorts of programs especially for situations like this one; I have one lying about at all times!) and repair your setup with that.

---

### Post by robenroute on 2006-12-30
Sorry, hadn't read your posting carefully enough.... GRUB (Ubuntu's) was apparently installed to the MBR of your HDD. When you installed Sabayon, the MBR was overwritten. Now you've deleted the Sabayon partition, but your GRUB (in the MBR) still thinks it should boot up Sabayon (which is no longer there). Result: nothing to boot!

I can't remember how to reinstall GRUB (with the correct reference to the partition it should boot) to the MBR. You probably have to download GRUB, make a bootable floppy and reinstall from there. You might be able to do this via the Live CD, I'm not sure.

Good luck.

---

### Post by confused57 on 2006-12-30
> **tchoklat said:**
> major problems - need urgent help ...

I created a partition on my HDD with GPArted. Sabayon required me to 'make' a boot partition which I did according to the installation program. I installed Sabayon OK but the boot up gave me only one choice - sabayon - no Ubuntu.

I deleted the partition I created an now cannot boot up.!!!!!!

When I reboot, I get a GRUB prompt on the screen - no grub menu, no Ubuntu. What have I done, and more improtantly wot do I do. I am now using the live CD!!!

Tchoklat
You can use the Ubuntu live cd(or any live cd) to reinstall your Ubuntu grub to the mbr:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

I installed Sabayon with the live cd a few weeks ago, and it didn't require me to use a separate /boot partition, however, it didn't give me an option of where to install grub...it automatically installed grub to the mbr & didn't add an entry to boot Ubuntu.  I used the Ubuntu cd to reinstall Ubuntu's grub to the mbr, then install Sabayon's grub to it's root partition...then I added an entry to Ubuntu's grub to boot Sabayon, using chainloading, e.g.
title   Sabayon
rootnoverify  (hd0,3)    #use your root partition here
chainloader +1

I've since deleted Sabayon and installed Gentoo, thought it'd be better to learn a little about Gentoo before going back to Sabayon.

---

### Post by macogw on 2006-12-30
Boot from your Ubuntu live cd.  Open a terminal
sudo mount /mnt /dev/hda1
chroot /mnt
sudo aptitude install grub-install

That should put grub back on your Ubuntu install.  Change /dev/hda1 to say wherever your Ubuntu is installed.  I'm pretty sure that's all the steps I went through to fix some borked installs.  Still don't know why my GRUB says the Ubuntu hard drive is hd1 but then boots it from hd0.  That means every time a new kernel is added, it changes GRUB and tries to boot from the wrong hard drive, which doesn't work and gets a "no OS found" error.  I edit menu.lst each time now, but if my family tries that...eesh...that'll be bad.

You could also boot into your Sabayon install and edit GRUB to include a space for Ubuntu so that it's on the GRUB menu too.

---

### Post by confused57 on 2006-12-30
> **macogw said:**
> 

 That means every time a new kernel is added, it changes GRUB and tries to boot from the wrong hard drive, which doesn't work and gets a "no OS found" error.  I edit menu.lst each time now

You might want to check this out:
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

---

### Post by tchoklat on 2006-12-30
No improvement -


ubuntu@ubuntu:~$ sudo mount /mnt /dev/hda1
mount: /mnt is not a block device
ubuntu@ubuntu:~$ 


tchoklat

---

### Post by taurus on 2006-12-30
> **tchoklat said:**
> 
ubuntu@ubuntu:~$ sudo mount /mnt /dev/hda1
:confused: 

```
sudo mkdir /mnt/temp
sudo mount /dev/hda1 /mnt/temp
```

---

### Post by macogw on 2006-12-30
er...switch /dev/hda1 and /mnt  i might've typed those backwards..

---

### Post by tchoklat on 2006-12-30
Hi,

fixed and thanks guys - it is so reassuring that assistance for we mere mortals is out there at the touch of a mouse button - so to speak.

To 'confused57' (whose link to another forum fixed my problem) or others, I obviously did something wrong when trying to install Sabayon - I would like to persevere, can you detail the steps I go through if you have the time and the inclination?

I have a clean Ubuntu install with the minimum number of partitions as set up automatically by the installer from the liveCD

I have Sabayon on a live DVD.


Tony

---

### Post by confused57 on 2006-12-30
> **tchoklat said:**
> Hi,

fixed and thanks guys - it is so reassuring that assistance for we mere mortals is out there at the touch of a mouse button - so to speak.

To 'confused57' (whose link to another forum fixed my problem) or others, I obviously did something wrong when trying to install Sabayon - I would like to persevere, can you detail the steps I go through if you have the time and the inclination?

I have a clean Ubuntu install with the minimum number of partitions as set up automatically by the installer from the liveCD

I have Sabayon on a live DVD.


Tony
The best way to learn linux, is to try & persevere...you'll make mistakes along the way, believe me I did.

The first thing I would do is download the latest gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Boot up the gparted live cd, then resize your Ubuntu root partition to free up enough space to make an ext3 partition to install Sabayon to(make a note of the partition #,hda3,etc of the new partition).

You might want to read the information on the Sabayon site, especially the wiki, although the info is rather sparse at the moment...also, you'll definitely want to check out the Gentoo website, read over sections for Portage, USE flags, etc...although Sabayon has Kuroo, which is a GUI for portage(gentoo's version of synaptic package manager).  The Sabayon & Gentoo forums are excellent reading.

I don't remember all the steps of the Sabayon install...but, be sure to update the installer before you begin...during the install you can always "go back", if something doesn't seem right...if there's a checkmark for installing a separate /boot partition, just remove it...be sure to select the partition where you want root installed(e.g. /dev/hda3).

As I mentioned in my other post, the Sabayon live cd automatically installed it's grub onto the mbr(overwrote the Ubuntu grub)...it didn't add an entry to boot Ubuntu.

It's easy to reinstall Ubuntu's grub, using the link I gave in my previous reply.
```
find /boot/grub/stage1
```
should return something like:
root  (hd0,0)
root  (hd0,2)

using the directions in the link, you would setup Ubuntu's grub to the mbr:
```
root  (hd0,0)
setup (hd0)
```

then reinstall Sabayon's grub to the root partition:
```
root (hd0,2)
setup (hd0,2)
```

then reboot your computer, & add the Sabayon entry to Ubuntu's grub(using chainloading).  Adjust the above to your actual partitions.  By the way, you can use the same swap partition for both Ubuntu & Sabayon.
Don't hesitate to ask if you have any questions...good luck.

---

### Post by tchoklat on 2006-12-31
Hi and thanks for your offer to help.

This is what I propose to do;
1.  using GPartEd, create a 20gig empty partition on my HDD
2.  boot the Sabayon disk and then install it onto this partition
3.  I will then have a GRUB that will only allow me to boot to Sabayon - what are the steps I take then please to set up dual boot on the MBR?

Question will each of the OS's allow access to each others' files?

PS - happy new year.


Tony

---

### Post by confused57 on 2006-12-31
> **tchoklat said:**
> Hi and thanks for your offer to help.

This is what I propose to do;
1.  using GPartEd, create a 20gig empty partition on my HDD
2.  boot the Sabayon disk and then install it onto this partition
3.  I will then have a GRUB that will only allow me to boot to Sabayon - what are the steps I take then please to set up dual boot on the MBR?

Question will each of the OS's allow access to each others' files?

PS - happy new year.


Tony
After completing your steps 1 & 2....

See my last reply about using the live cd to (re)install grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
It's really quite easy and effective...install Ubuntu's grub to the mbr, Sabayon's grub to it's root partition.
Add an entry to Ubuntu's grub to boot Sabayon(using chainloading):
Boot up Ubuntu, open a terminal(Applications---Accessories---Terminal),enter(copy&paste) each line one at a time, pressing enter after each line:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
At the very end of the file, enter your entry to boot Sabayon, e.g.
```
title     Sabayon
rootnoverify  (hdx,x)
chainloader +1
```

Here's some screenshots, using the gparted live cd to resize partitions(guess I should have placed this at the top of this reply):
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

After you're able to boot both OS, using Ubuntu's grub, you'll need to mount the other OS to be able to access files:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Good luck...and a Prosperous New Year

---

### Post by cotcot on 2006-12-31
chroot from the liveCD (ubuntu) into your ubuntu environment and re-install grub.

Here is some guiding : [http://www.ubuntuforums.org/archive/index.php/t-24113.html]("http://www.ubuntuforums.org/archive/index.php/t-24113.html")

Sabayon is an installer for gentoo, as well as Kororaa.

---

### Post by ferebee on 2006-12-31
A twenty gig partition is a good idea for Sabayon. I installed it on a 15 gig partition,and it took up almost nine gigs of it. In Sabayon's partitioning tool, if I remember it right, you've got to mark your chosen partition for install as root (/).

When I installed, the option to install grub to the root partition instead of the MBR was under Advanced boot options, at least in 3.2. You might need to boot back into Ubuntu to add Sabayon to Ubuntu's Grub menu.lst

I haven't had trouble accessing files from one distro to another. Ubuntu to Sabayon or vice versa. Some distros differ as to the location of the mounted partitions. Some of them put them in /mnt, some in /media. I'll have  to boot back to Sabayon to check where it puts them .

Edited to add:
In Sabayon kde, mounting from the command line told me mty partitions weren't found in fstab. However, opened Konqueror , and clicked on Storage Media and there they were. They mounted as /media/disk, /media/disk-1 etc. Perhaps this is a gentoo related difference?

---

### Post by tchoklat on 2007-01-03
I have installed Sabayon on /dev/hda3. Can anyone tell me the script I need to put into the Ubuntu GRUB menu.lst to allow me the option to start Sabayon as a GRUB option at start-up?

tchoklat

---

### Post by confused57 on 2007-01-03
> **tchoklat said:**
> I have installed Sabayon on /dev/hda3. Can anyone tell me the script I need to put into the Ubuntu GRUB menu.lst to allow me the option to start Sabayon as a GRUB option at start-up?

tchoklat
You could still boot using chainloading, by booting up with the Sabayon live dvd(cd?), select upgrade or rescue system...then select to install grub to the Sabayon root partition(make sure the "Advanced..." option is selected for installing grub).  Then the entry added to Ubuntu's grub would be:
title  Sabayon
rootnoverify (hd0,2)
chainloader +1

When I boot up Sabayon in the next few hours, I'll post my grub entry, I used the 3.2 live cd to install so it may be same kernel...

You could also try mounting your Sabayon partition, using your Ubuntu live cd, and opening your Sabayon boot menu to get the exact entry needed to boot:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

With Sabayon, it may be /boot/grub/grub.conf, instead of /boot/grub/menu.lst?

Here's my grub entry:
title    Sabayon
root  (hd1,5)
kernel  /boot/kernel-genkernel-x86-2.6.18-gentoo-r5 root=/dev/ram0 ramdisk=8192               real_root=/dev/sda6 quiet init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1
initrd  /boot/initramfs-genkernel-x86-2.6.18-gentoo-r5

(note:vga=791 is just a continuation of the kernel line)

Check out "Configuring the Bootloader" from the Gentoo handbook:
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10)

Adjust to your partitions, i.e.  root (hd0,2) on real_root=/dev/hda3...your vga option may be different from mine(it's for framebuffer support in the console), you can probably safely omit it for now.

---

### Post by tchoklat on 2007-01-04
done and working, the chain loading did the trick now I can boot into either. I now need to learn to use Kuroo amongst other programs.thanx dude


Tony

---

