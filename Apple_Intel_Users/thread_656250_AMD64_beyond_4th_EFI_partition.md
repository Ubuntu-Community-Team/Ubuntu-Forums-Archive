---
title: "AMD64 beyond 4th EFI partition"
date: 2008-01-02
forum: Apple Intel Users
---

### Post by oskarloko on 2008-01-02
*(It's have been passed time from the last time I wrote here )*

Well, I'm now trying to install an **x86-64 Xubuntu **system on my macbook.
I'm stuck with booting scheme, although installation was fine.

I inserted Xubuntu AMD64 Cd on a rEFIT blessed macbook, and it starts perfectly.
I installed the system on **/dev/sda6 **

```

   1:   EFI                      200.0 MB  disk0s1
   2:   Apple_HFS M      29.9 GB   disk0s2
   3:   FAt32                   14.6 GB   disk0s3
   4:   NTFS      14.6 GB   disk0s4
   5:   Linux Swap               1 GB   disk0s5
   6:   ext3                      14.1 GB   disk0s6

```

Well, at the end of installation; on advanced options, I unchecked GRUB install. ( I need a EFI loader, and that is MBR only )

Then I chrooted on the new system, and upgraded with [FONT="Courier New"]apt-get[/FONT]. Also installed [FONT="Courier New"]build-essentials, apt-src[/FONT], etc. to rebuild kernel.

Here started my problems.
I tried to install [FONT="Courier New"]gnu-efi [/FONT] and [FONT="Courier New"]elilo[/FONT] with [FONT="Courier New"]apt-src[/FONT]; as theres no compiled package for now. But a lot of compile-errors were only the result.

So I seek for another solution, and installed [FONT="Courier New"]grub-efi [/FONT]( also know as GRUB2 )
But now I don't know what to do to make it work...

( Also I know I must rebuild kernel with *mactel patches* and EFI support, but thats another war..)

Anyone has tried with **grub-efi** ?

Thanks

Pd. if I conclude a clean Xubuntu installation, I promise a little tutorial here :-) )

---

### Post by oskarloko on 2008-01-02
I know two alternatives will be:
- Use a 32 bit system with ELILO on /dev/sda6
- Use a 64 bit system with GRUB on /dev/sda3

Thanks

---

### Post by cyberdork33 on 2008-01-02
how you have installed is fine, but why are your trying to use grub-efi? There are some limitations...

I think you just have to install grub on a partition < 5, not all of linux...

Also, you can put OSX > 4 as it doesn't care what partition it is.

---

### Post by oskarloko on 2008-01-03
Well, lets see, I almost complete a 6th EFI patition installation on my macbook. 
I already have rEFIT installed ( via macosx )

I installed a 32 bit Ubuntu on my hard disk; on [FONT="Courier New"]/dev/sda6.[/FONT]
Normal installation, just uncheking GRUB install at he end

That's what I done from ivecd after installing

```

*# Chroot*
cd /
mkdir /target
mount /dev/sda6 /target
mount --bind /dev /target/dev ; mount -t proc /proc /target/proc ;
chroot /target su
*# Update system and take what we need*
apt-get update
apt-get upgrade
apt-get install apt-src binutils build-essential gnu-efi fakeroot
apt-get install mc bin86 kernel-package libqt3-headers libqt3-mt-dev
libncurses5 libncurses5-dev doc-base cvs gettext-doc linux-source
kernel-source libdb3-dev libncurses-dev docbook-utils libgcrypt11-doc
gnutls-doc gnutls-bin krb5-doc libqt3-i18n qt3-doc subversion
*# Make a new Kernel*
cd /usr/src/
wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2)
tar -xf linux-2.6.23.tar.bz2
rm -rf linux
ln -s /usr/src/linux-2.6.23 linux
snv co [https://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.23/](https://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.23/)
cd mactel-patches-2.6.23/
./apply /usr/src/linux
cd ..
[I]# Here you will find kernel config files, I used one to macbook
# [http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files/Kernel](http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files/Kernel)
# And saved as file above[/I]
cp kernel2.6.22.12-mactel.config linux/.config
make oldconfig ;  make menuconfig
make-kpkg -initrd kernel_image kernel_headers modules_image
*# Kernel is done, lets set boot*
cd .. ; dpkg -i linux-image-*.Custom_i386.deb ; dpkg -i
linux-headers-*.Custom_i386.deb
*# Edit elilo.conf*
elilo --image /boot/vmlinuz-2.6.23-mactel --label linux-mactel
--install /usr/lib/elilo/elilo.efi --boot /dev/sda1 --root /dev/sda6
--config /etc/elilo.conf -v
```


And then I rebooted.
rEFIT shows me a new Linux entry, first of all. 
A linux icon with [FONT="Courier New"]Boot EFI/ubuntu/elilo.efi [/FONT], label bellow
But when I'm about to boot, it throws an error. :(
[FONT="Courier New"]
Starting elilo.efi
Error: Load Error returned from elilo.efi
[/FONT]

I tried to redo the [FONT="Courier New"]/usr/lib/elilo/elilo.efi [/FONT],with [FONT="Courier New"]elilo --efiboot,[/FONT] from chrooted terminal. 
But I have the *[FONT="Courier New"]efivars not loaded[/FONT]* message 

I think I need to make the [FONT="Courier New"]efivars[/FONT] module and load it on the livecd kernel ( [FONT="Courier New"]kernel 2.6.22.14 [/FONT]); but I was unable to do...

¿ Anybody has an idea ?

---

### Post by oskarloko on 2008-01-05
( I think this thread is becoming a blog more than other thing... )

I 've used[FONT="Courier New"] elilo.efi [/FONT]from [http://www.madingley.org/macmini/]("http://www.madingley.org/macmini/")

```

Starting elilo.efi
Setting always-power on behaviour via 82801GBM LPC:
   82801GBM LPC found at 0:1F.0
   AC make with power was off, RTC battery is good and has been good.
   Setting AC wake with power... done
   AC wake up with power is now on
ELILO
Loading file \EFI\ubuntu\initrd.img...done
EFI legacy vga patch (c) 2006 James McKenzie
EFI legacy vga patch (c) 2006 James McKenzie
   $Id: 
   params at 0x3C61A010
Searching for ROM in 0x38728B10-0x40728B10
signature match at 0x3DC6102C
checksum is 0xE6866BEC or should be 0x3A233DEF
signature match at 0x3DC72030
checksum is 0xE6866BEC or should be 0x3A233DEF
signature match at 0x3DC8494C
checksum is 0xE6866BEC or should be 0x3A233DEF
Failed to find ROM
VGA rom not found
Failed to find VGA ROM so can´t initialize it.
sleeping for 30 seconds
```



And it hangs....

---

### Post by cyberdork33 on 2008-01-05
Since you are trying to boot from EFI, there are not many here that can help you. I do hope you know that there are some limitations...

Also, try to use code tags to make your posts more legible.

---

### Post by oskarloko on 2008-01-05
Yes, I know EFI ( specially on macbooks ) is a new ground on Linux, but I saw other trying. ( Benazo I think )

So far, I decided to give it a try and comment here if there was a path to solve it.

I find this, however, not enough:
[LIST]
[*][http://www.mythic-beasts.com/resources/macmini/walkthrough.html](http://www.mythic-beasts.com/resources/macmini/walkthrough.html)
[*][http://www.madingley.org/macmini/](http://www.madingley.org/macmini/)
[*][http://elilo.sourceforge.net/cgi-bin/blosxom](http://elilo.sourceforge.net/cgi-bin/blosxom)
[*] and good information on this fourms... (thaks to all )
[/LIST]

I've been searching, but as I've read [I]making elilo.efi is an obscure art
[/I]




Pd. comments edited to make it more readable, thanks; and excuse me if I've been a little intensive...

---

### Post by cyberdork33 on 2008-01-07
there is also grub for EFI:
[http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)

---

### Post by oskarloko on 2008-01-10
Thanks, I think it's now done

[http://packages.ubuntu.com/gutsy/admin/grub-efi]("http://packages.ubuntu.com/gutsy/admin/grub-efi")

I'll try with this...

---

### Post by oskarloko on 2008-01-11
I tryed with grub-efi or grub2 package, but error is shown

```
 grub-mkimage -d . -o grub.efi gpt hfsplus fat 
grub-mkimage: error: cannot open ./moddep.lst
```

I tried to buikd it from GNU Savannah CVS
[http://cvs.savannah.gnu.org/viewvc/grub/grub2/](http://cvs.savannah.gnu.org/viewvc/grub/grub2/)
but I don't know how to make CVSROOT on* cvs checkout *

:oops: :( :(

---

### Post by oskarloko on 2008-01-13
Well, now I have a GRUB2 working with rEFIT, but I doesn't boot anything
See from
[LIST]
[*][http://grub.enbug.org/TestingOnX86](http://grub.enbug.org/TestingOnX86)
[*][http://grub.enbug.org/TestingOnEFI?highlight=%28Testing%29](http://grub.enbug.org/TestingOnEFI?highlight=%28Testing%29)
[/LIST]

From a LiveCd, I have installed Ubuntu on[FONT="Courier New"] /dev/sda6[/FONT] - with kernel recompiled, see post above - without any boot.

 ```

*Chroot*
sudo -s
cd /
mkdir /target
mount /dev/sda6 /target
mount --bind /dev /target/dev ; mount -t proc /proc /target/proc ; chroot /target su
* Update system and take what we need*
apt-get update
apt-get upgrade
apt-get install apt-src binutils build-essential gnu-efi fakeroot
apt-get install mc bin86 kernel-package libqt3-headers libqt3-mt-dev libncurses5 libncurses5-dev doc-base cvs gettext-doc linux-source kernel-source libdb3-dev libncurses-dev docbook-utils libgcrypt11-doc gnutls-doc gnutls-bin krb5-doc libqt3-i18n qt3-doc
* Get Grub2 and compile it*
apt-get install build-essential binutils cvs bison autoconf
cvs -z3 -d:pserver:anonymous@cvs.savannah.gnu.org:/sources/grub co grub2
cd grub2
sh ./configure --with-platform=efi
make 
make install
./grub-mkimage -d . -o grub.efi gpt hfsplus fat ext2
*  Mount EFI partition*
mkdir /Volumes; mkdir /Volumes/efi
mount /dev/sda1 /Volumes/efi
mkdir /Volumes/efi/efi/grub
cp grub.efi *.mod fs.lst command.lst /Volumes/efi/efi/grub
*  Write down grub.cfg as you see*
cat /Volumes/efi/efi/grub/grub.cfg
[COLOR="Gray"]
timeout=10
@ "Mac" {
  # Set the root device for Mac OS X's loader.
  root=(hd0,2)
  # Load the loader.
  chainloader /usr/share/standalone/i386/boot.efi
}

@ "Linux" {
  # Set the root device for GNU/Linux.
  root=(hd0,6)
  search --set /vmlinuz
  # Load the kernel and initrd.
  linux /vmlinuz 
#video=imacfb:mini acpi=force libata.atapi_enabled=1 init=/linuxrc root=/dev/ram0 pcboot=cdrom gpt
  initrd /initrd
}[/COLOR]

```

The result: on rEFIT, the GRUB entry appears.
When I select GRUB, it loads GRUB loader, and
```

grub(rescue mode)> boot Linux
no kernel loaded
>


```

...I am missing something....maybe...

Pd note: from the GRUB2 web
*But, beware GRUB 2 counts partitions from 1 and not from 0 like GRUB Legacy! *

---

### Post by cyberdork33 on 2008-01-13
> **oskarloko said:**
> ...I am missing something....maybe...

Pd note: from the GRUB2 web
*But, beware GRUB 2 counts partitions from 1 and not from 0 like GRUB Legacy! *

I think you have to create a config file similar to menu.lst to avoid loading like that... if you plan to load from the command prompt, then you have to load the kernel, etc first before using the "boot" command, as was done in legacy grub. I think was done in the same order as a menu.lst entry... set the root partition, set the kernel line, set the initrc line, then boot.

---

### Post by oskarloko on 2008-01-13
I'm starting to loose the faith 

Well, I tried something like this
( note than efi partition is mounted on [FONT="Courier New"]/Volumes/efi[/FONT] and we are on the *chrooted* enviorement on [FONT="Courier New"]/dev/sda6[/FONT] )

```
 ./grub-mkimage -d . -o grub.efi gpt hfsplus fat linux ext2 search gpt
cp grub.efi *.mod fs.lst command.lst grub.cfg /Volumes/efi/efi/grub2
cp /boot/initrd.img-2.6.23-mactel /Volumes/efi/efi/grub2/initrd.img
cp /boot/vmlinuz-2.6.23-mactel /Volumes/efi/efi/grub2/vmlinuz
```

Well, now when I got into grub's rEFIT menu, normal GRUB2 console appears
And I try

```
set root=hd0,6
linux /grub2/vmlinuz
 [ Kernel.... *ok loaded*]
initrd /grub2/initrd.img
 error: no free pages
```

¿¿¿ :confused: ???

---

### Post by cyberdork33 on 2008-01-13
got me, but it looks like you are making progress!

---

### Post by chillman88 on 2008-01-14
Well... i'm not sure about this, but the code you are using seems to be for a mac mini, and you said your using a macbook. The code might be causing the problems, just an idea, so dont quote me on it, but I think I read somewhere that the code you are using is mini-specific

---

### Post by chillman88 on 2008-01-14
whoops, sorry, i just re-read it, and you arent using the elilo image any more are you? Sorry, that was what threw me for a loop

---

### Post by oskarloko on 2008-01-14
Ok, I know it's a large and confusing experience. I'll make a summary.

I have a Macbook C2D. with rEFIT as primary boot loader.
I (want to) have a triple boot system.
I want to install Linux onto a EFI partition, a 6th primary partition ( [FONT="Courier New"]/dev/sda6[/FONT] ). As a little experiment, to see if it is possible to boot by this way  
Because EFI is not the classic partition schema, no classic GRUB nor LILO are compatible to boot this linux.

I installed without problems Ubuntu on [FONT="Courier New"]/dev/sda6[/FONT], without any bootloader; from LiveCd. But i neeed to install a new bootloader EFI-compatible.
So lets search and try.

Firts I tried with [ELILO]("http://sourceforge.net/projects/elilo"), the EFI boot loader
[LIST]
[*]On AMD64  I was unable to compile/find ELILO boot loader. I used x86 ubuntu instead
[*]On x86 I found ELILO, it installed well on . But the problem was the binary loader[FONT="Courier New"] elilo.efi[/FONT]: the one that uses elilo by default doesn't boot.
[*]I searched for other, but no one work.
[*]I tried to redo [FONT="Courier New"]elilo.efi[/FONT] with elilo, but a kernel module was required. I don't know how to build and *modprobe *the [FONT="Courier New"]EFI_vars[/FONT] module on kernel on a LiveCd
[/LIST]
So, as ELILO migth work - the entry appears on rEFIT menu.But the problem was on [FONT="Courier New"]elilo.efi[/FONT], it was unable to load kernel. 




Then I tried with [GRUB2]("http://www.gnu.org/software/grub/grub-2.en.html"), the new bootloader from GNU boys.

[LIST]
[*]Althougth the package was on Ubuntu repositories, it didn't work well
[*]I downloaded last version from CVS and [compiled]("http://grub.enbug.org/TestingOnEFI?highlight=%28efi%29") it well. Also the installation appears to be succesfull.
[*]But when I try to load [FONT="Courier New"]initrd.img[/FONT],on GRUB2 console, an error appears... don't know why
[/LIST]

And here I am, a little stuck...
¿ Any ideas ?

---

### Post by cyberdork33 on 2008-01-14
> **oskarloko said:**
> I tried to redo [FONT=Courier New]elilo.efi[/FONT] with elilo, but a kernel module was required. I don't know how to build and *modprobe *the [FONT=Courier New]EFI_vars[/FONT] module on kernel on a LiveCdSo, as ELILO migth work - the entry appears on rEFIT menu.But the problem was on [FONT=Courier New]elilo.efi[/FONT], it was unable to load kernel. Well you are going to have to compile your own kernel that is capable of booting via EFI before it will work with either elilo or grub2. if you installed a system on the hard drive already, you can boot the Live CD, and chroot into the installed system, and compile a kernel with the EFI booting capability. There is some good info on this from Gentoo:
[http://gentoo-wiki.com/Gentoo_MacOSX_MacBook_Pro_Dual_boot](http://gentoo-wiki.com/Gentoo_MacOSX_MacBook_Pro_Dual_boot)

---

### Post by oskarloko on 2008-01-14
I've recompiled a vainilla kernel with mactel support ( on chrooted partition )
Both 2.6.23 version

I've checked these options on kernel configuration ( among others):
```

Proccesor Type And Features --->[INDENT]
[*] Boot from EFI support

Firmware Drivers --->[INDENT]
[*] EFI Variable support via sysfs
[/INDENT][/INDENT]
File systems  --->
[INDENT]
Partition Types  --->[INDENT]
[*] Advanced partition selection

[*]   Macintosh partition map support

[*]   PC BIOS (MSDOS partition tables) support

[*]   EFI GUID Partition support

[/INDENT][/INDENT]

```

These doesn't apply to LiveCd, of course...
¿ Can I boot [FONT="Courier New"]/dev/hda6[/FONT] kernel from LiveCd ?

---

### Post by cyberdork33 on 2008-01-14
> **oskarloko said:**
> Can I boot [FONT=Courier New]/dev/hda6[/FONT] kernel from LiveCd The link I gave seems to imply that you can use the efi executable off a USB drive to boot the system. I don't think it would be too far fetched to think you could do it from CD too. I don't think that will solve the problem though. I am willing to guess that there is something about the kernel that is preventing it from loading for some reason.

You might want to ask for help on the mactel-linux mailing list???

---

### Post by oskarloko on 2008-01-14
Not exactly... but reading it is a great idea.

Use the generated kernel and files from Mactel proyect to use rEFIT ( no elilo nor grub2 used ) to boot directly kernel. 

( The USB stick is used to copy files between the created Linux partition and MacOSX - where rEFIT lives )

I'll try and post.

---

### Post by oskarloko on 2008-01-20
Well, I've installed Ubuntu on [FONT="Courier New"]/dev/sda3[/FONT] to try my build 2.6.23 kernel - to see if this was the cause of my booting problems. 

*To renember: I installed Ubuntu on a [FONT="Courier New"]/dev/sda6[/FONT] EFI partition ( it is a primary partition, a different schema from classic 'PC' MBR ). I also build a kernel with EFI enabled ( on livecd ). Then  I tried elilo, grub2, directly with rEFIT to boot this installation, with no luck.*

As I was writing, I installed again Ubuntu, but on[FONT="Courier New"] /dev/sda3[/FONT]. I copied my *old* compiled kernel and setup grub on /dev/sda3.

It booted well ( very fast ) so I've seen the problem is not on kernel compilation.

Futhermore, grub on new Ubuntu installation recognized the old installation; anb wrote it on grub configuration menu.  Also booted it well;  little strange messages are shown, and a little slower... I think it is graphic acceleration with EFI system.

I'll try a little more with grub2. 

But I think the main problem is on EFI loader ( [FONT="Courier New"]e.efi [/FONT]file ), the binary bootloader. 
It is unique for a type of computer ( chipset, motherboard, graphic card ) and it's very hard to build one.

---

### Post by cyberdork33 on 2008-01-20
As far as I know graphic acceleration does not work after booting from EFI (except some Mac Minis) so that is consistent. It is odd that it is booting ok from sda3 and not sda6 though.

---

### Post by Halligalli on 2008-01-21
> **oskarloko said:**
> Well, I've installed Ubuntu on [FONT="Courier New"]/dev/sda3[/FONT] to try my build 2.6.23 kernel - to see if this was the cause of my booting problems. 

*To renember: I installed Ubuntu on a [FONT="Courier New"]/dev/sda6[/FONT] EFI partition ( it is a primary partition, a different schema from classic 'PC' MBR ). I also build a kernel with EFI enabled ( on livecd ). Then  I tried elilo, grub2, directly with rEFIT to boot this installation, with no luck.*

As I was writing, I installed again Ubuntu, but on[FONT="Courier New"] /dev/sda3[/FONT]. I copied my *old* compiled kernel and setup grub on /dev/sda3.

It booted well ( very fast ) so I've seen the problem is not on kernel compilation.

Futhermore, grub on new Ubuntu installation recognized the old installation; anb wrote it on grub configuration menu.  Also booted it well;  little strange messages are shown, and a little slower... I think it is graphic acceleration with EFI system.

I'll try a little more with grub2. 

But I think the main problem is on EFI loader ( [FONT="Courier New"]e.efi [/FONT]file ), the binary bootloader. 
It is unique for a type of computer ( chipset, motherboard, graphic card ) and it's very hard to build one.
So you´ve managed to boot your MB using EFI? Do you notice any differences compared to booting the usual way?

---

### Post by benanzo on 2008-01-21
Hi **oskarloko**,

You are embarking on a journey which after more than three months I failed miserably at.  I'll try to save you some of the trouble I went through (though it seems you've already encountered most of it.)  First, Apple's EFI implementation differs greatly from Intel's original specification, which is what the kernel support was designed for.  The most obvious symptom of this is the lack of accelerated graphics support.  I did finally get my MacBook to boot Ubuntu in EFI, but only manually from the rEFIt shell, and only in 800x600 with the vesa driver, which made the system unusable for daily tasks.  It would actually only boot 1 out of 5 times without a kernel panic.  Also, there's absolutely no support for Suspend/hibernation and access to the USB subsystem was hit or miss, depending  on the device.  For instance, my USB mouse worked all the time but my thumb drive never did and my Logitech webcam appeared but never worked.  All these devices worked perfectly out of the box booting via GRUB, so EFI definitely seemed to be the problem.

If you're looking for a way to have more than 4 partitions on your disk I recommend changing the whole disk to MBR and booting everything, including Mac OS X, via GRUB.  That way you can have your four primary partitions, but also as many extended partitions as you want for swap, storage, other OSs etc.  Mac OS X will refuse to *install* to an MBR disk, but will happily live on one if you move the OS X install to it after it's installed.  I achieved this by installing OS X normally to the whole disk, then booting the Ubuntu live cd and making a tarball out of it and moving it to another disk.  Then use parted/gparted to repartition the disk as MBR.  The gentoo wiki has a good article on booting OS X via GRUB but I can't seem to find it right now.  I'll keep looking.


Good Luck!

---

### Post by oskarloko on 2008-01-23
> after more than three months I failed miserably at
Don't be rude to yourself, you have tried and thats good enough.

> First, Apple's EFI implementation differs greatly from Intel's original specification
Ok, as usually: apple way of making things.... 

As I see on [James blog]("http://www.madingley.org/macmini/"), a lot of patches are needed to make a totally functional boot. Now I know why. 

I will try a little more with GRUB2, with little hope.

But it isn't critical . I wanted to install linux on [FONT="Courier New"] /dev/sda6[/FONT] to make [FONT="Courier New"] /dev/sda3[/FONT] an interchange FAT32 partition ( between Mac, Linux, Win )

I can make this work on [FONT="Courier New"] /dev/sda6[/FONT] and keep linux on [FONT="Courier New"] /dev/sda3[/FONT]. Only Win will not acces to [FONT="Courier New"] /dev/sda6[/FONT] FAT32; Linux and Mac will. I already have swap partition on [FONT="Courier New"] /dev/sda5[/FONT] and it works well.

I know it's possible and easy to use MBR with MacOsX, but firmware updates ( which are not frequent ) won't work. Regular MacOsX updates I don't know. And it seems theres a file-by-file method to update MacOsX ( as downloading .deb's on Ubuntu ), but I don't  know details.

Thank you, Benazo

---

### Post by cyberdork33 on 2008-01-23
> **oskarloko said:**
> But it isn't critical . I wanted to install linux on [FONT=Courier New] /dev/sda6[/FONT] to make [FONT=Courier New] /dev/sda3[/FONT] an interchange FAT32 partition ( between Mac, Linux, Win )You can put the OSX partition beyond #4 without issue...

---

### Post by hajk on 2008-01-24
> **cyberdork33 said:**
> You can put the OSX partition beyond #4 without issue...
Interesting thread! Does this also hold for Linux swap and partitions like /home, /var etc? As long as the legacy *boot* partition is numbered either 2, 3 or 4?

---

### Post by cyberdork33 on 2008-01-24
> **hajk said:**
> Interesting thread! Does this also hold for Linux swap and partitions like /home, /var etc? As long as the legacy *boot* partition is numbered either 2, 3 or 4?
yep pretty much... but to a point. windows cannot see ANY partition that is beyond 4, so if you want to be able to access your home partition in windows, then it cannot be greater than 4, but for linux-only use (or mounting in OSX), it will work just fine.

Technically, you only have to have a /boot partition in the first 4, you can put the whole root filesystem (/) beyond 4 (or anywhere. This is how many people put Ubuntu on an external hard drive).

---

### Post by oskarloko on 2008-01-25
> You can put the OSX partition beyond #4 without issue...

I didn't know that... 
¿ From installation DVD or from a MacOsX image ?

> Technically, you only have to have a /boot partition in the first 4, you can put the whole root filesystem (/) beyond 4 (or anywhere. This is how many people put Ubuntu on an external hard drive).
Without graphic acceleration if linux is beyond 4th partition 
( at least in my experience )

---

### Post by cyberdork33 on 2008-01-25
> **oskarloko said:**
> I didn't know that... 
¿ From installation DVD or from a MacOsX image ?
Install for the disk (or restore from an image... either should work). I personally had an install of tiger in partition2 and leopard in partition6 for a long time and could easily boot either.

> **oskarloko said:**
>  Without graphic acceleration if linux is beyond 4th partition 
( at least in my experience )no, booting in legacy mode where Graphic Acceleration works, you can put your root partition beyond #4 (with a boot partition in the first 4). The Graphic Acceleration is only hampered if you boot via EFI.

---

