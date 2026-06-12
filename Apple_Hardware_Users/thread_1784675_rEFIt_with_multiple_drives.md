---
title: "rEFIt with multiple drives"
date: 2011-06-17
forum: Apple Hardware Users
---

### Post by Fasopus on 2011-06-17
I don't know if anybody can help me but I have a question about rEFIt and its behaviour, you'll have to forgive me, I'm sorta new to this whole multiple OS thing. So right now I have rEFIt on my mac pro and when I load it all 4 drives I have installed appear, one drive for OSx and then the windows formated drives I have (Windows 7, Windows Vista, and a storage drive). Right now everything is working fine but I'm looking to reformat my Vista drive and install Ubuntu on it. I didn't setup the computer originally (All I've personally done is bootcamp the windows 7 drive) but I know bootcamp doesn't support linux distros as an option. So I'm wondering, since rEFIt sees the Vista drive already, if I completely wipe the drive and install Ubuntu on it, what happens? I know rEFIt can boot linux paritions, so will it just bring up the options as it does now, except with the linux partition? All the solutions I've found online have been for macbooks and relate to using 1 hard drive with 3 partitions as opposed to 3 drives.

---

### Post by MacHackers on 2011-06-17
> **Fasopus said:**
> I don't know if anybody can help me but I have a question about rEFIt and its behaviour, you'll have to forgive me, I'm sorta new to this whole multiple OS thing. So right now I have rEFIt on my mac pro and when I load it all 4 drives I have installed appear, one drive for OSx and then the windows formated drives I have (Windows 7, Windows Vista, and a storage drive). Right now everything is working fine but I'm looking to reformat my Vista drive and install Ubuntu on it. I didn't setup the computer originally (All I've personally done is bootcamp the windows 7 drive) but I know bootcamp doesn't support linux distros as an option. So I'm wondering, since rEFIt sees the Vista drive already, if I completely wipe the drive and install Ubuntu on it, what happens? I know rEFIt can boot linux paritions, so will it just bring up the options as it does now, except with the linux partition? All the solutions I've found online have been for macbooks and relate to using 1 hard drive with 3 partitions as opposed to 3 drives.
If you are using intel, boot up a Ubuntu Intel disk (hold down the C) key... 
 
When Ubuntu fully boots, Call to the command prompt (Accessories > Terminal).
 
Type in:         sudo apt-get gparted
 
If it says you need to run dpkg, type this in the terminal.
 
Type in: (if it says run dpkg)         sudo dpkg --configure -a
 
It should get done. Now, if you had to run dpkg, run the sudo apt-get gparted   command again..
 
Now, navigate to: System> Administration > GParted. Type in your password and hit the enter key. Choose your device from over on the right and find the windows partition... should be formatted one of the FAT formats or NTFS. Choose it and hit the delete button near the top.... MAKE SURE IT IS THE WINDOWS Partition..... Now, click the Check key and wait.... If it pulls up an error message, please reply back with the error. We'll go from there! 
 
Patrick.

---

### Post by MacHackers on 2011-06-17
> **Fasopus said:**
> I don't know if anybody can help me but I have a question about rEFIt and its behaviour, you'll have to forgive me, I'm sorta new to this whole multiple OS thing. So right now I have rEFIt on my mac pro and when I load it all 4 drives I have installed appear, one drive for OSx and then the windows formated drives I have (Windows 7, Windows Vista, and a storage drive). Right now everything is working fine but I'm looking to reformat my Vista drive and install Ubuntu on it. I didn't setup the computer originally (All I've personally done is bootcamp the windows 7 drive) but I know bootcamp doesn't support linux distros as an option. So I'm wondering, since rEFIt sees the Vista drive already, if I completely wipe the drive and install Ubuntu on it, what happens? I know rEFIt can boot linux paritions, so will it just bring up the options as it does now, except with the linux partition? All the solutions I've found online have been for macbooks and relate to using 1 hard drive with 3 partitions as opposed to 3 drives.
Hey, by the way, does rEFIT see the other drives? And are they external? Read my other post for help.....

---

### Post by Fasopus on 2011-06-17
> **MacHackers said:**
> Hey, by the way, does rEFIT see the other drives? And are they external? Read my other post for help.....
 
Yeah, rEFIt sees all 4 of my drives and gives me the options to boot to all of them, they are all internal. Ill post back tonight after I give the Ubuntu install a try. From reading your above steps I'm assuming that I can't just use Ubuntu's automated installer on the correct drive and have rEFIt work properly with it? Or is that what your steps are telling me to do? I'm not familar with installing Linux distros.

---

### Post by dubmartian on 2011-06-17
the confusion or apprehension may be from the misconception that a bootcamp partition must be made with bootcamp assistant which is incompatable with linux. bootcamp assistant is just a helper. using windows, linux, or macs disk utility to format a partition to any common filesystem (ntfs, ext3, fat..) is considered a bootcamp partition by osx. the helper will be useless if your adding linux to your multiboot scheme.  also, it would be obvious immediately but i think gparted is already installed when running a live cd, but not installed after installation.  lastly, if moving to a single drive, i recommend doing a dry run with a virtual machine. if keeping systems separated, maybe unplug all drives except one you want to install to.  good luck

---

### Post by Fasopus on 2011-06-18
Ok so I installed Ubuntu and had no errors or problems. rEFIt shows everything I want it to on boot, and allows me to boot to OSx and Windows 7, but when I select the boot Linux option, it boots windows, I've tried reinstalling rEFIt and nothing changed. From my reading I'm guessing the problem is where I placed my GRUB bootloader? Ill probably just format the linux drive and try to install it again when I know where to place the bootloader, so does anybody know where I was supposed to put it? The linux drive is currently in bay 4 of my computer.

---

### Post by dubmartian on 2011-06-18
in your case, if ubuntu is the only system on sdd, you install directly to sdd. 

example:  

sudo apt-get -y install --no-install-recommends grub-pc 

sudo grub-install /dev/sdd 

sudo update-grub2 

in my case, since i have ubuntu outside mbr on sda5 (mbr is sda1 through sda4) and grub needs to be installed within mbr. i install grub on sda3. 

i would use the command:  

sudo grub-install --force /dev/sda3

---

### Post by Fasopus on 2011-06-18
that's very strange, when I installed Ubuntu through the wizard I selected dev/sdd as the location for the bootloader, guess ill boot the live CD and execute those terminal commands and see what happens.

---

### Post by Fasopus on 2011-06-18
When I try to run the above commands I get the errors

/usr/sbin/grub-probe: error cannot stat `aufs'.

Does anyone know what this means or what I should do?

---

### Post by dubmartian on 2011-06-19
If you installed grub to sdd during install, that should have done it. Sorry, the commands I mentioned I use after booting from a "super grub2 disk" (very handy.) To install grub from a live cd you have to "bind" the live cd system to the installed system. My method for binding seems to be outdated so look around for bind, livecd and grub ..or check the manual page for the "mount" command (it's one of the few man pages I actually understand.)

---

### Post by Fasopus on 2011-06-19
I'm at a total loss for what to do here, I can see on the disk that grub is installed and is up to date, yet every time I select linux from the rEFIt menu it boots windows instead. The Ubuntu partition is /dev/sdd2, there is a /dev/sdd1 of EFI format that I can see, should I try putting grub there? The installer defaults to putting grub on the OSx drive, but if I put it there wont that cause later problems with booting to windows?

EDIT: Just tried installing GRUB in the EFI section, rEFIt says "Boot linux from EFI", yet it still boots into windows when I select it.

---

### Post by srs5694 on 2011-06-19
It's starting to sound as if Linux might not be in your GRUB configuration file. Try booting from an emergency disk and posting the contents of /boot/grub/grub.cfg, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags to keep it legible. Alternatively, you could run the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) and post its RESULTS.txt file, which will have that and more information.

---

### Post by Fasopus on 2011-06-20
The contents of my grub.cfg file are as follows

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sdd,gpt1)'
search --no-floppy --fs-uuid --set=root a793e32c-f342-4a3c-b805-e59192d72741
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sdd,gpt1)'
search --no-floppy --fs-uuid --set=root a793e32c-f342-4a3c-b805-e59192d72741
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdd,gpt1)'
    search --no-floppy --fs-uuid --set=root a793e32c-f342-4a3c-b805-e59192d72741
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a793e32c-f342-4a3c-b805-e59192d72741 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdd,gpt1)'
    search --no-floppy --fs-uuid --set=root a793e32c-f342-4a3c-b805-e59192d72741
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a793e32c-f342-4a3c-b805-e59192d72741 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdd,gpt1)'
    search --no-floppy --fs-uuid --set=root a793e32c-f342-4a3c-b805-e59192d72741
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdd,gpt1)'
    search --no-floppy --fs-uuid --set=root a793e32c-f342-4a3c-b805-e59192d72741
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" --class osx --class darwin --class os {
    insmod part_gpt
    insmod hfsplus
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root b65a461da7e3835a
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid b65a461da7e3835a uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" --class osx --class darwin --class os {
    insmod part_gpt
    insmod hfsplus
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root b65a461da7e3835a
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid b65a461da7e3835a uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows 7 (loader) (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 4CA22BA6A22B940C
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

---

### Post by srs5694 on 2011-06-20
Your GRUB configuration looks OK. You could try installing [ELILO.](http://elilo.sourceforge.net/cgi-bin/blosxom) You'll need to do this:


[list=1]
[*]Download the ELILO binary files [from here.](http://sourceforge.net/projects/elilo/files/elilo/elilo-3.14/)
[*]Mount your EFI System Partition (ESP) so you can access it. In OS X, you'd do "sudo mkdir /Volumes/ESP; sudo mount_msdos /dev/disk0s1 /Volumes/ESP", although you might need to change the device node name.
[*]Create an EFI/elilo directory on the ESP (it'll be /Volumes/ESP/EFI/elilo if you mount as I suggested).
[*]Copy the .efi file for your architecture (elilo-3.14-ia32.efi or elilo-x86_64.efi) to the EFI/elilo directory you just created.
[*]Copy the Ubuntu kernel (vmlinuz-*) and initial RAM disk (initrd.img-*) files to the EFI/elilo directory. This is the tricky part, since you'll need access to your Ubuntu partition to do it. You should be able to do it from an Ubuntu live CD boot, though.
[*]Create an elilo.conf file in the EFI/elilo directory. This will direct the boot process. See the example below.
[/list]


Here's my elilo.conf file on a UEFI-based PC:

```
prompt
timeout=50
default=linux
#chooser=textmenu

image=vmlinuz-2.6.38-8-generic
        label=linux
        initrd=initrd.img-2.6.38-8-generic
        read-only
        root=/dev/sda5
        append=""

```

You'll need to modify the filenames for the Linux kernel (on the image= line), for the initial RAM disk (on the initrd= line), and for the root filesystem (on the root= line).

With any luck, when you're done, you should see a new entry in rEFIt to boot via ELILO and it should work. If it does, you'll have to maintain your ELILO configuration yourself whenever you upgrade your kernel. Note that ELILO can't read kernels and initial RAM disks from the Linux root (/) or /boot partition, so you'll have to copy them to the ESP, from which ELILO can read them.

---

### Post by Fasopus on 2011-06-20
> **srs5694 said:**
> Your GRUB configuration looks OK. You could try installing [ELILO.](http://elilo.sourceforge.net/cgi-bin/blosxom) You'll need to do this:


[list=1]
[*]Download the ELILO binary files [from here.](http://sourceforge.net/projects/elilo/files/elilo/elilo-3.14/)
[*]Mount your EFI System Partition (ESP) so you can access it. In OS X, you'd do "sudo mkdir /Volumes/ESP; sudo mount_msdos /dev/disk0s1 /Volumes/ESP", although you might need to change the device node name.
[*]Create an EFI/elilo directory on the ESP (it'll be /Volumes/ESP/EFI/elilo if you mount as I suggested).
[*]Copy the .efi file for your architecture (elilo-3.14-ia32.efi or elilo-x86_64.efi) to the EFI/elilo directory you just created.
[*]Copy the Ubuntu kernel (vmlinuz-*) and initial RAM disk (initrd.img-*) files to the EFI/elilo directory. This is the tricky part, since you'll need access to your Ubuntu partition to do it. You should be able to do it from an Ubuntu live CD boot, though.
[*]Create an elilo.conf file in the EFI/elilo directory. This will direct the boot process. See the example below.
[/list]


Here's my elilo.conf file on a UEFI-based PC:

```
prompt
timeout=50
default=linux
#chooser=textmenu

image=vmlinuz-2.6.38-8-generic
        label=linux
        initrd=initrd.img-2.6.38-8-generic
        read-only
        root=/dev/sda5
        append=""

```

You'll need to modify the filenames for the Linux kernel (on the image= line), for the initial RAM disk (on the initrd= line), and for the root filesystem (on the root= line).

With any luck, when you're done, you should see a new entry in rEFIt to boot via ELILO and it should work. If it does, you'll have to maintain your ELILO configuration yourself whenever you upgrade your kernel. Note that ELILO can't read kernels and initial RAM disks from the Linux root (/) or /boot partition, so you'll have to copy them to the ESP, from which ELILO can read them.

So I'm reading your directions and I think I should be able to complete the steps but I'm wondering if doing this will have any effect on rEFIt or my functioning OSx/Windows 7 partitions, I mostly just don't understand what this is doing/changing. (something gives me the feeling that it would create extra options on the rEFIt menu)

---

### Post by srs5694 on 2011-06-20
My procedure will create one new entry in the rEFIt menu. (If it works, you should be able to find a way to remove the non-functional entries, but that's something that's best dealt with later. Likewise, if it doesn't work, you can delete the ELILO files to delete the new entry.) My procedure will not delete any existing configurations (unless you happen to already have the EFI/elilo directory I suggested creating), so it shouldn't break anything.

Basically, you can thank Apple and Microsoft for an overly complicated booting system. Your Mac can boot in either of two ways, and rEFIt is providing you with a mish-mash of options for both methods of booting:


[list]
[*]Natively, Macs use the Extensible Firmware Interface (EFI) to boot. Normally, this works by the firmware detecting boot loader files on the EFI System Partition (ESP) and booting one of them. Apple extended this a bit so that a Mac's EFI loads the Mac's boot files from the OS X installation partition, but the principle is the same. EFI boot files (and some other types of EFI files) have .efi extensions, and rEFIt searches for such files and presents them as boot options.
[*]The Mac's firmware also supports a BIOS compatibility mode that it uses for booting Windows. In this mode, boot code in a disk's Master Boot Record (MBR; that is, the first sector of the disk) or in a partition's Partition Boot Record (PBR; the first sector of a partition) begins the boot process, which then continues through a convoluted path. rEFIt scans disks and partitions for likely MBR/BIOS boot code and, if it finds it, rEFIt presents these as options.
[/list]


In both cases, rEFIt basically guesses at the name to present to you, so it may get the name wrong. This just adds to the confusion. IIRC, though, rEFIt does at least show you the path to the EFI boot loaders under the icons, which can help you identify what you're about to boot.

What's worse, it's easy to get mixed up about what's installed to the MBR (and to *which* MBR, if you've got multiple disks) and what's installed to what PBR. My suspicion at this point is that you've somehow gotten Windows boot code into locations where there should be GRUB boot code, and that rEFIt is therefore presenting Windows boot options as Linux boot options.

The method I've suggested adds ELILO, which in my experiments on *non-Mac* UEFI-based computers has been much more reliable than GRUB. I emphasize "non-Mac" because the Mac's EFI and typical PC UEFI implementations are a bit different, so I can't promise ELILO will work correctly on a Mac. I've also tested the handoff from rEFIt to ELILO (again, on non-Mac UEFI systems), and it seems to work fine.

The EFI boot process is less kludgey than the BIOS boot process, so it should be easier to debug once you start using it. Since there's *something* amiss in your current configuration, and since it seems to have something to do with the MBR/BIOS style booting, I figure it's best to switch to a purely EFI method of booting Linux, which means ELILO, a GRUB 2 configuration for EFI (flaky, in my experience), or a hacked GRUB Legacy with EFI support (rare, but used by Fedora).

---

### Post by Fasopus on 2011-06-21
I tried to get ELILO up and running yesterday but I couldn't get it to work, the rEFIt entry showed up but when selected didn't do anything, I removed all the ELILO files I added and I plan on giving it another chance tonight. I've also read that rEFIt reccommends using the LILO bootloader installed on the partition boot sector, but I havent found a good guide on how to install LILO from a live cd.
 
 
EDIT: I'm wondering if all of the problems are caused by the windows 7 bootloader install location. I don't remember being given an option as to where to place this bootloader, could it be possible that it got placed on the MBR instead of the PBR? Does anyone know how to check this and move it to the PBR of the windows drive? Or does the MBR issue only affect having multiple OS's and partitions on a given drive?

---

### Post by srs5694 on 2011-06-21
At this point I think more and better data are in order. I suggest you post two things:


[list]
[*]The RESULTS.txt file created by the [Boot Info Script.](http://sourceforge.net/projects/bootinfoscript/) This will tell us what BIOS-style boot loaders are installed to what MBRs and PBRs.
[*]A list of all the .efi files in your ESP. You'll need to mount your ESP, as described in my earlier post, and then type 'find /Volumes/ESP -iname "*efi"' (changing the mount point as necessary).
[/list]


Post both results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags to keep it legible.

---

### Post by Fasopus on 2011-06-21
When I run the script the contents of the RESULTS.TXT are 
[sda should be OSX, sdb a FAT storage drive, sdc Windows 7, sdd Ubuntu]

```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 40.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 411648.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdd1 
                       and looks at sector 151317770 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt1)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2    *        409,640   624,880,263   624,470,624  af HFS / HFS+


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40       409,639       409,600 EFI System partition
/dev/sda2         409,640   624,880,263   624,470,624 Hierarchical File System Plus (HFS+) partition (Mac OS X)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1       409,639       409,639  ee GPT
/dev/sdb2             411,648   488,396,799   487,985,152   b W95 FAT32


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              40       409,639       409,600 EFI System partition
/dev/sdb2         411,648   488,396,799   487,985,152 Data partition (Windows/Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048 1,465,145,343 1,465,143,296   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1            33            33  ee GPT
/dev/sdd2    *             34   156,300,815   156,300,782  83 Linux


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1              34   156,300,815   156,300,782 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2860-11F4                              vfat       EFI
/dev/sda2        ed19e5b6-4197-3a51-b5d5-4291e667efef   hfsplus    Macintosh HD
/dev/sdb1        70D6-1701                              vfat       EFI
/dev/sdb2        BCD6-130D                              vfat       DATA
/dev/sdc1        4CA22BA6A22B940C                       ntfs       Windows 7
/dev/sdd1        a793e32c-f342-4a3c-b805-e59192d72741   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdd1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sdd,gpt1)'
search --no-floppy --fs-uuid --set=root a793e32c-f342-4a3c-b805-e59192d72741
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sdd,gpt1)'
search --no-floppy --fs-uuid --set=root a793e32c-f342-4a3c-b805-e59192d72741
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_gpt
	insmod ext2
	set root='(/dev/sdd,gpt1)'
	search --no-floppy --fs-uuid --set=root a793e32c-f342-4a3c-b805-e59192d72741
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a793e32c-f342-4a3c-b805-e59192d72741 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_gpt
	insmod ext2
	set root='(/dev/sdd,gpt1)'
	search --no-floppy --fs-uuid --set=root a793e32c-f342-4a3c-b805-e59192d72741
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a793e32c-f342-4a3c-b805-e59192d72741 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(/dev/sdd,gpt1)'
	search --no-floppy --fs-uuid --set=root a793e32c-f342-4a3c-b805-e59192d72741
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(/dev/sdd,gpt1)'
	search --no-floppy --fs-uuid --set=root a793e32c-f342-4a3c-b805-e59192d72741
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" --class osx --class darwin --class os {
	insmod part_gpt
	insmod hfsplus
	set root='(/dev/sda,gpt2)'
	search --no-floppy --fs-uuid --set=root b65a461da7e3835a
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid b65a461da7e3835a uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" --class osx --class darwin --class os {
	insmod part_gpt
	insmod hfsplus
	set root='(/dev/sda,gpt2)'
	search --no-floppy --fs-uuid --set=root b65a461da7e3835a
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid b65a461da7e3835a uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows 7 (loader) (on /dev/sdc1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root 4CA22BA6A22B940C
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdd1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdd1       /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  72.153962135 = 77.474726912   boot/grub/core.img                             1
  12.144886971 = 13.040473088   boot/grub/grub.cfg                             1
   0.660386086 = 0.709084160    boot/initrd.img-2.6.38-8-generic               1
  72.191727638 = 77.515277312   boot/vmlinuz-2.6.38-8-generic                  1
   0.660386086 = 0.709084160    initrd.img                                     1
  72.191727638 = 77.515277312   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  3f 00 10 00 28 00 00 00  |........?...(...|
00000020  00 40 06 00 67 0c 00 00  00 00 00 00 02 00 00 00  |.@..g...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 f4 11 60 28 45  46 49 20 20 20 20 20 20  |..)..`(EFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 01 17 d6 70 45  46 49 20 20 20 20 20 20  |..)...pEFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb2

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 40 20 00  |.X.BSD  4.4..@ .|
00000010  02 00 00 00 00 f0 00 00  20 00 ff 00 00 00 00 00  |........ .......|
00000020  00 10 16 1d a2 e8 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 0d 13 d6 bc 44  41 54 41 20 20 20 20 20  |..)....DATA     |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

Then when I do the find on /Volumes/ESP I get nothing returned, however if I do run the find on the /Volumes directory I recieve the following output

```
/Volumes/Windows 7/Windows/Boot/DVD/EFI
/Volumes/Windows 7/Windows/Boot/EFI
/Volumes/Windows 7/Windows/Boot/EFI/bootmgfw.efi
/Volumes/Windows 7/Windows/Boot/EFI/bootmgr.efi
/Volumes/Windows 7/Windows/Boot/EFI/memtest.efi
/Volumes/Windows 7/Windows/System32/Boot/winload.efi
/Volumes/Windows 7/Windows/System32/Boot/winresume.efi
/Volumes/Windows 7/Windows/System32/winload.efi
/Volumes/Windows 7/Windows/System32/winresume.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7600.16385_none_c52d88d1a67ba4c0/winload.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7600.16385_none_c52d88d1a67ba4c0/winresume.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7600.16757_none_c55000c1a6617837/winload.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7600.16757_none_c55000c1a6617837/winresume.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7600.20897_none_c5ae5ddcbf9f87c5/winload.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7600.20897_none_c5ae5ddcbf9f87c5/winresume.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7601.17556_none_c7355d7da388cacc/winload.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7601.17556_none_c7355d7da388cacc/winresume.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7601.21655_none_c7bdf9febca7513f/winload.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7601.21655_none_c7bdf9febca7513f/winresume.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..ore-bootmanager-efi_31bf3856ad364e35_6.1.7600.16385_none_e375da7eb610e1bf/bootmgfw.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..ore-bootmanager-efi_31bf3856ad364e35_6.1.7600.16385_none_e375da7eb610e1bf/bootmgr.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..re-memorydiagnostic_31bf3856ad364e35_6.1.7600.16385_none_342a40111e4e6165/memtest.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7600.16385_none_b71babd98657e6ef/winload.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7600.16385_none_b71babd98657e6ef/winresume.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7600.16757_none_b73e23c9863dba66/winload.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7600.16757_none_b73e23c9863dba66/winresume.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7600.20897_none_b79c80e49f7bc9f4/winload.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7600.20897_none_b79c80e49f7bc9f4/winresume.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7601.17556_none_b923808583650cfb/winload.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7601.17556_none_b923808583650cfb/winresume.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7601.21655_none_b9ac1d069c83936e/winload.efi
/Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7601.21655_none_b9ac1d069c83936e/winresume.efi
/Volumes/Windows 7/Windows/Boot/DVD/EFI /Volumes/Windows 7/Windows/Boot/EFI /Volumes/Windows 7/Windows/Boot/EFI/bootmgfw.efi /Volumes/Windows 7/Windows/Boot/EFI/bootmgr.efi /Volumes/Windows 7/Windows/Boot/EFI/memtest.efi /Volumes/Windows 7/Windows/System32/Boot/winload.efi /Volumes/Windows 7/Windows/System32/Boot/winresume.efi /Volumes/Windows 7/Windows/System32/winload.efi /Volumes/Windows 7/Windows/System32/winresume.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7600.16385_none_c52d88d1a67ba4c0/winload.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7600.16385_none_c52d88d1a67ba4c0/winresume.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7600.16757_none_c55000c1a6617837/winload.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7600.16757_none_c55000c1a6617837/winresume.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7600.20897_none_c5ae5ddcbf9f87c5/winload.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7600.20897_none_c5ae5ddcbf9f87c5/winresume.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7601.17556_none_c7355d7da388cacc/winload.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7601.17556_none_c7355d7da388cacc/winresume.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7601.21655_none_c7bdf9febca7513f/winload.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..environment-windows_31bf3856ad364e35_6.1.7601.21655_none_c7bdf9febca7513f/winresume.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..ore-bootmanager-efi_31bf3856ad364e35_6.1.7600.16385_none_e375da7eb610e1bf/bootmgfw.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..ore-bootmanager-efi_31bf3856ad364e35_6.1.7600.16385_none_e375da7eb610e1bf/bootmgr.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..re-memorydiagnostic_31bf3856ad364e35_6.1.7600.16385_none_342a40111e4e6165/memtest.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7600.16385_none_b71babd98657e6ef/winload.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7600.16385_none_b71babd98657e6ef/winresume.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7600.16757_none_b73e23c9863dba66/winload.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7600.16757_none_b73e23c9863dba66/winresume.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7600.20897_none_b79c80e49f7bc9f4/winload.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7600.20897_none_b79c80e49f7bc9f4/winresume.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7601.17556_none_b923808583650cfb/winload.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7601.17556_none_b923808583650cfb/winresume.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7601.21655_none_b9ac1d069c83936e/winload.efi /Volumes/Windows 7/Windows/winsxs/amd64_microsoft-windows-b..vironment-os-loader_31bf3856ad364e35_6.1.7601.21655_none_b9ac1d069c83936e/winresume.efi

```

---

### Post by srs5694 on 2011-06-21
My instruction to look in /Volumes/ESP was based on the instruction that you mount it, as described in [post #14 in this thread.](http://ubuntuforums.org/showpost.php?p=10961804&postcount=14) That information may still be useful, but I have some observations and suggestions from the data you have provided:


[list]
[*]/dev/sda, /dev/sdb, and /dev/sdd all have unnecessary [hybrid MBRs,](http://www.rodsbooks.com/gdisk/hybrid.html) which are accidents waiting to happen. What's more, the presence of a hybrid MBR on /dev/sdd *might* be related to your problem. You might want to eliminate at least that hybrid MBR, and perhaps the ones on /dev/sda and /dev/sdb, in favor of a legal protective MBR. You can do that with my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program, as follows:

[list=1]
[*]Launch gdisk on the disk by typing "sudo gdisk /dev/disk3". (I'm assuming you'll run the OS X version from OS X, hence the OS X-style disk identifier.)
[*]Type "p" to view the partition table and verify you're working on the correct disk. If not, type "q" to quit without saving your changes and try again with another disk identifier until you find the correct disk.
[*]Type "x" to enter the experts' menu.
[*]Type "n" to create a new protective MBR. You'll see no confirmation, just a new prompt.
[*]Type "w" to save your changes.
[/list]

[*]Your /dev/sdc is an MBR disk with traces of old GPT data on it. This will confuse partitioning tools such as GParted into thinking the disk is empty. It's conceivable this situation is contributing to your boot problems. I recommend you fix it. The easiest way is to run my [FixParts](http://www.rodsbooks.com/fixparts/) program on the disk. You can do this using the OS X version. See the FixParts Web page for a full description.
[*]You've got the MBR version of SYSLINUX installed in the MBR of /dev/sdd. This is probably what's redirecting the boot process to Windows. What I'm about to suggest should wipe it out....
[*]I recommend using GParted from a Linux emergency boot disk to shrink your Linux partition by ~1 MiB and create a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) in the free space. You might not need it, depending on how you ultimately resolve the problem, but it will be necessary for some types of booting, such as the one I'm about to have you set up.
[*]*After* you've set up a BIOS Boot Partition, use [Super GRUB 2 Disk](http://www.supergrubdisk.org/) to boot Linux. When you boot with this disc, it should be able to discover your Linux installation and boot it. You should then be able to install GRUB 2 to the MBR of /dev/sdd by typing "sudo grub-install /dev/sdd". Note that's "/dev/sdd", not "/dev/sdd1" or any other partition number. This will wipe out the SYSLINUX on the MBR and use the BIOS Boot Partition. With any luck, when you reboot rEFIt will then give you a new Linux boot option (replacing one that didn't work) that will boot GRUB 2. (It's conceivable that rEFIt will misidentify or be unable to identify GRUB as a Linux option, but that's a minor cosmetic issue.) If it doesn't (if the Linux option goes away entirely and isn't replaced by anything), you'll have to go for a straight-EFI boot option, which I'll describe if that becomes necessary.
[/list]

---

### Post by Fasopus on 2011-06-22
Ok Ill try that when I get home tonight, am I supposed to run gdisk on all of the drives or just disk3 (disk3 =sdd?)? Also I don't have much experience with gparted, I'm assuming BIOS boot partition will be an available partition format after the linux partition is shrunk?

---

### Post by srs5694 on 2011-06-22
> **Fasopus said:**
> Ok Ill try that when I get home tonight, am I supposed to run gdisk on all of the drives or just disk3 (disk3 =sdd?)?

I recommend doing it on /dev/sda, /dev/sdb, and /dev/sdd; but at the very least, do it on /dev/sdd.

> Also I don't have much experience with gparted, I'm assuming BIOS boot partition will be an available partition format after the linux partition is shrunk?

In GParted, you create a BIOS Boot Partition by creating a partition without a filesystem and then setting the "bios_grub" flag on it. In gdisk, you create one by creating a partition and giving it a type code of EF02.

---

### Post by Fasopus on 2011-06-22
So I've completed all the above steps, but after I discover my install in the GRUB2 disk and attempt to launch it I get an error saying /dev/disk/by-uuid/xxxx.... does not exist, dropping to a shell.

---

### Post by srs5694 on 2011-06-22
It's possible to re-install GRUB in other ways. One is to use the Ubuntu installer in its "live CD" mode, as described [here,](http://alexsleat.co.uk/2010/03/11/howto-reinstall-grub-using-ubuntu-live-cd/) among other places. (In your case, though, fdisk will be useless. You already know your installation is on /dev/sdd1, so you don't need to use fdisk to learn that.)

---

### Post by Fasopus on 2011-06-22
I booted into the live CD but when I attempt to mount my partition with

```
sudo mount /dev/sdd1 /mnt
```

I get an error along the lines of special device does not exist or cannot be found

---

### Post by srs5694 on 2011-06-22
Please boot the live CD and run the Boot Info Script again. Something may have gone wrong to cause you to lose partitioning data. (If so, don't worry; your original Boot Info Script output is detailed enough that you can recover your original partitions.)

---

