---
title: "Dual booting with Mandriva 2011 and Ubuntu 10.11"
date: 2012-01-29
forum: Any Other OS
---

### Post by cyril.godart on 2012-01-29
Hi,

I have installed Mandriva 2011 on a 140GiB hard drive. Gparted tells me that this is the 3rd hard drive and that there is a boot on 
/dev/sdc1 
and
/dev/sdc5 is a linux partition where Mandriva lives. 
Under /etc/grub.d/ I have created a 11_mandriva_2011 file which is executable, whose content:
#!/bin/sh -e
echo "Adding Mandriva 2011 to GRUB 2"
cat << EOF
menuentry "Mandriva 2011" {
set root=(hd2,5)
linux (hd2,5)/boot/vmlinuz
initrd (hd2,5)/boot/initrd.img
}
EOF 
I have: sudo update-grub. 

Now I see the entry but when I try to boot I get the error that the partition does not exist. Can someone help ?

Thanks in advance,

---

### Post by oldfred on 2012-01-29
What drive do you boot from. In grub the boot drive is always hd0 and the other drives may change numbers. I often boot sdc and that is hd0 then.

To see your entire configuration. New beta version has some fixes.

Get last development version of Boot Info Script:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```
old version:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by cyril.godart on 2012-01-30
This looks like an interesting tool. I am new to this but something jumps to my eyes immediately: I have never installed intentionally anything on sdb. This is supposed to be a back-up drive. I might have got mixed up with my drives in one of the multiple re-installations of Mandriva (or Ubuntu). Anyway, thanks a bunch for getting involved. 

Best.

Cyril Godart



```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on boot 
    drive #2 in partition #5 for /grub/stage2 and /grub/menu.lst.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 2386600240 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive.
    Boot file info:      Grub Legacy (v0.97) in the file /boot.backup.sda 
                       looks at sector 32520964 on boot drive #3 for the 
                       stage2 file.  A stage2 file is at this location on 
                       /dev/sdc.  Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.10
    Boot files:        /grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /ntdetect.com

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Mandriva Linux release 2011.0 
                       (Official) for x86_64 Kernel 2.6.39.4-4.2-desktop on a 
                       12-processor x86_64 /
    Boot files:        /etc/fstab

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1798.8 GB, 1798752436224 bytes
255 heads, 63 sectors/track, 218685 cylinders, total 3513188352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,026,048    13,314,047    12,288,000  27 Hidden NTFS (Recovery Environment)
/dev/sda3          13,314,048   599,642,172   586,328,125   7 NTFS / exFAT / HPFS
/dev/sda4         599,646,206 3,513,186,303 2,913,540,098   5 Extended
/dev/sda5       1,639,636,992 2,523,072,511   883,435,520  83 Linux
/dev/sda6       3,395,328,000 3,513,186,303   117,858,304  82 Linux swap / Solaris
/dev/sda7         599,646,208 1,639,634,943 1,039,988,736   7 NTFS / exFAT / HPFS
/dev/sda8       2,523,074,560 3,395,325,951   872,251,392   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    29,511,404    29,511,342   7 NTFS / exFAT / HPFS
/dev/sdc2          29,511,466   312,576,704   283,065,239   f W95 Extended (LBA)
/dev/sdc5          29,511,468   303,259,004   273,747,537  83 Linux
/dev/sdc6         303,259,068   312,576,704     9,317,637  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        44E0D986E0D97F1C                       ntfs       System
/dev/sda2        F2CADAB9CADA78F5                       ntfs       Recovery
/dev/sda3        9002DC9802DC849E                       ntfs       OS
/dev/sda5        3a934db0-24d0-42cd-aeed-5b52f30061e0   ext4       
/dev/sda6        28fa5963-54cc-4876-847a-d176d38c4e2d   swap       
/dev/sda7        0FA1F85036203798                       ntfs       LaBausse
/dev/sda8        18E23574145A12C1                       ntfs       Voivodina
/dev/sdc1        0C2CCCFD2CCCE2B6                       ntfs       
/dev/sdc5        e15d26da-9018-4cec-b5a8-375ad4d65cda   ext3       
/dev/sdc6        f0ef886a-ae6c-439d-abf4-55c868da8e7a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


============================= sda5/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1,4)/gfxmenu
default 0

title linux
kernel (hd1,4)/vmlinuz BOOT_IMAGE=linux root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d splash=silent vga=788
initrd (hd1,4)/initrd.img

title linux-nonfb
kernel (hd1,4)/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d
initrd (hd1,4)/initrd.img

title failsafe
kernel (hd1,4)/vmlinuz BOOT_IMAGE=failsafe root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda  nokmsboot failsafe
initrd (hd1,4)/initrd.img

title windows
root (hd2,0)
map (0x80) (0x82)
map (0x82) (0x80)
makeactive
chainloader +1

title windows1
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.39.4-4.2-desktop' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /vmlinuz-2.6.39.4-4.2-desktop root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /initrd-2.6.39.4-4.2-desktop.img
}
menuentry 'Ubuntu, with Linux 2.6.39.4-4.2-desktop (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 2.6.39.4-4.2-desktop ...'
    linux    /vmlinuz-2.6.39.4-4.2-desktop root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd-2.6.39.4-4.2-desktop.img
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_mandriva_2011 ###
Adding Mandriva 2011 to GRUB 2
menuentry "Mandriva 2011" {
set root=(hd2,5)
linux (hd2,5)/boot/vmlinuz
initrd (hd2,5)/boot/initrd.img
}
EOF ### END /etc/grub.d/11_mandriva_2011 ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 44E0D986E0D97F1C
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9002DC9802DC849E
    chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 0C2CCCFD2CCCE2B6
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "linux (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux /vmlinuz BOOT_IMAGE=linux root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d splash=silent vga=788
    initrd (hd1,4)/initrd.img
}
menuentry "linux-nonfb (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux /vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d
    initrd (hd1,4)/initrd.img
}
menuentry "failsafe (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux /vmlinuz BOOT_IMAGE=failsafe root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda nokmsboot failsafe
    initrd (hd1,4)/initrd.img
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=28fa5963-54cc-4876-847a-d176d38c4e2d none            swap    sw              0       0
/dev/sdc6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-13-generic               2
               =                boot/initrd.img-3.0.0-14-generic               2
               =                boot/initrd.img-3.0.0-15-generic               2
               =                boot/initrd.img-3.0.0-16-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  2
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                boot/vmlinuz-3.0.0-15-generic                  2
               =                boot/vmlinuz-3.0.0-16-generic                  2
               =                grub/menu.lst                                  1
               =                grub/stage2                                    1
               =                initrd-2.6.39.4-4.2-desktop.img                3
               =                initrd.img                                     2
               =                initrd.img.old                                 3
               =                vmlinuz                                        2
               =                vmlinuz-2.6.39.4-4.2-desktop                   1
               =                vmlinuz.old                                    1

================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="VGA MODE" /basevideo 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect--------------------------------------------------------------------------------

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# Entry for /dev/sdb5 :
UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda / ext3 acl,relatime 1 1
# Entry for /dev/sdc5 :
UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 /boot ext4 acl,relatime 1 2
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
# Entry for /dev/sdc2 :
UUID=F2CADAB9CADA78F5 /media/win_ ntfs-3g defaults 0 0
# Entry for /dev/sdc1 :
UUID=44E0D986E0D97F1C /media/win_c2 ntfs-3g defaults 0 0
# Entry for /dev/sdc7 :
UUID=0FA1F85036203798 /media/win_d ntfs-3g defaults 0 0
# Entry for /dev/sdc8 :
UUID=18E23574145A12C1 /media/win_e ntfs-3g defaults 0 0
# Entry for /dev/sdc3 :
UUID=9002DC9802DC849E /media/win_f ntfs-3g defaults 0 0
# Entry for /dev/sdb1 :
UUID=0C2CCCFD2CCCE2B6 /mnt/win_c2 ntfs-3g defaults 0 0
none /proc proc defaults 0 0
# Entry for /dev/sdb6 :
UUID=f0ef886a-ae6c-439d-abf4-55c868da8e7a swap swap defaults 0 0
# Entry for /dev/sdc6 :
UUID=28fa5963-54cc-4876-847a-d176d38c4e2d swap swap defaults 0 0
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by cyril.godart on 2012-01-30
Hum... Being lazy after a day at work. I had not read your post properly until the end. 
Installed gawk. 

```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on boot 
    drive #2 in partition #5 for /grub/stage2 and /grub/menu.lst.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 2386600240 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive.
    Boot file info:      Grub Legacy (v0.97) in the file /boot.backup.sda 
                       looks at sector 32520964 on boot drive #3 for the 
                       stage2 file.  A stage2 file is at this location on 
                       /dev/sdc.  Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.10
    Boot files:        /grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /ntdetect.com

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Mandriva Linux release 2011.0 
                       (Official) for x86_64 Kernel 2.6.39.4-4.2-desktop on a 
                       12-processor x86_64 /
    Boot files:        /etc/fstab

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1798.8 GB, 1798752436224 bytes
255 heads, 63 sectors/track, 218685 cylinders, total 3513188352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,026,048    13,314,047    12,288,000  27 Hidden NTFS (Recovery Environment)
/dev/sda3          13,314,048   599,642,172   586,328,125   7 NTFS / exFAT / HPFS
/dev/sda4         599,646,206 3,513,186,303 2,913,540,098   5 Extended
/dev/sda5       1,639,636,992 2,523,072,511   883,435,520  83 Linux
/dev/sda6       3,395,328,000 3,513,186,303   117,858,304  82 Linux swap / Solaris
/dev/sda7         599,646,208 1,639,634,943 1,039,988,736   7 NTFS / exFAT / HPFS
/dev/sda8       2,523,074,560 3,395,325,951   872,251,392   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    29,511,404    29,511,342   7 NTFS / exFAT / HPFS
/dev/sdc2          29,511,466   312,576,704   283,065,239   f W95 Extended (LBA)
/dev/sdc5          29,511,468   303,259,004   273,747,537  83 Linux
/dev/sdc6         303,259,068   312,576,704     9,317,637  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        44E0D986E0D97F1C                       ntfs       System
/dev/sda2        F2CADAB9CADA78F5                       ntfs       Recovery
/dev/sda3        9002DC9802DC849E                       ntfs       OS
/dev/sda5        3a934db0-24d0-42cd-aeed-5b52f30061e0   ext4       
/dev/sda6        28fa5963-54cc-4876-847a-d176d38c4e2d   swap       
/dev/sda7        0FA1F85036203798                       ntfs       LaBausse
/dev/sda8        18E23574145A12C1                       ntfs       Voivodina
/dev/sdc1        0C2CCCFD2CCCE2B6                       ntfs       
/dev/sdc5        e15d26da-9018-4cec-b5a8-375ad4d65cda   ext3       
/dev/sdc6        f0ef886a-ae6c-439d-abf4-55c868da8e7a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


============================= sda5/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1,4)/gfxmenu
default 0

title linux
kernel (hd1,4)/vmlinuz BOOT_IMAGE=linux root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d splash=silent vga=788
initrd (hd1,4)/initrd.img

title linux-nonfb
kernel (hd1,4)/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d
initrd (hd1,4)/initrd.img

title failsafe
kernel (hd1,4)/vmlinuz BOOT_IMAGE=failsafe root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda  nokmsboot failsafe
initrd (hd1,4)/initrd.img

title windows
root (hd2,0)
map (0x80) (0x82)
map (0x82) (0x80)
makeactive
chainloader +1

title windows1
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.39.4-4.2-desktop' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /vmlinuz-2.6.39.4-4.2-desktop root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /initrd-2.6.39.4-4.2-desktop.img
}
menuentry 'Ubuntu, with Linux 2.6.39.4-4.2-desktop (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 2.6.39.4-4.2-desktop ...'
    linux    /vmlinuz-2.6.39.4-4.2-desktop root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd-2.6.39.4-4.2-desktop.img
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_mandriva_2011 ###
Adding Mandriva 2011 to GRUB 2
menuentry "Mandriva 2011" {
set root=(hd2,5)
linux (hd2,5)/boot/vmlinuz
initrd (hd2,5)/boot/initrd.img
}
EOF ### END /etc/grub.d/11_mandriva_2011 ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 44E0D986E0D97F1C
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9002DC9802DC849E
    chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 0C2CCCFD2CCCE2B6
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "linux (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux /vmlinuz BOOT_IMAGE=linux root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d splash=silent vga=788
    initrd (hd1,4)/initrd.img
}
menuentry "linux-nonfb (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux /vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d
    initrd (hd1,4)/initrd.img
}
menuentry "failsafe (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux /vmlinuz BOOT_IMAGE=failsafe root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda nokmsboot failsafe
    initrd (hd1,4)/initrd.img
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=28fa5963-54cc-4876-847a-d176d38c4e2d none            swap    sw              0       0
/dev/sdc6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1138.019702911 = 1221.939351552 boot/grub/core.img                             1
1024.707237244 = 1100.271017984 boot/grub/grub.cfg                             1
 783.292968750 = 841.054420992  boot/initrd.img-3.0.0-12-generic               2
1138.969837189 = 1222.959550464 boot/initrd.img-3.0.0-13-generic               2
1140.914428711 = 1225.047539712 boot/initrd.img-3.0.0-14-generic               2
 798.282321930 = 857.149116416  boot/initrd.img-3.0.0-15-generic               2
 795.879268646 = 854.568857600  boot/initrd.img-3.0.0-16-generic               2
1103.972846985 = 1185.381818368 boot/vmlinuz-3.0.0-12-generic                  1
1129.777778625 = 1213.089652736 boot/vmlinuz-3.0.0-13-generic                  2
1137.730903625 = 1221.629255680 boot/vmlinuz-3.0.0-14-generic                  1
 797.629364014 = 856.448008192  boot/vmlinuz-3.0.0-15-generic                  2
 783.152805328 = 840.903921664  boot/vmlinuz-3.0.0-16-generic                  2
 817.964855194 = 878.283075584  grub/menu.lst                                  1
 817.965084076 = 878.283321344  grub/stage2                                    1
 782.070312500 = 839.741603840  initrd-2.6.39.4-4.2-desktop.img                3
 795.879268646 = 854.568857600  initrd.img                                     2
 782.070312500 = 839.741603840  initrd.img.old                                 3
 783.152805328 = 840.903921664  vmlinuz                                        2
 782.007534027 = 839.674195968  vmlinuz-2.6.39.4-4.2-desktop                   1
 782.007534027 = 839.674195968  vmlinuz.old                                    1

================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="VGA MODE" /basevideo 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect--------------------------------------------------------------------------------

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# Entry for /dev/sdb5 :
UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda / ext3 acl,relatime 1 1
# Entry for /dev/sdc5 :
UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 /boot ext4 acl,relatime 1 2
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
# Entry for /dev/sdc2 :
UUID=F2CADAB9CADA78F5 /media/win_ ntfs-3g defaults 0 0
# Entry for /dev/sdc1 :
UUID=44E0D986E0D97F1C /media/win_c2 ntfs-3g defaults 0 0
# Entry for /dev/sdc7 :
UUID=0FA1F85036203798 /media/win_d ntfs-3g defaults 0 0
# Entry for /dev/sdc8 :
UUID=18E23574145A12C1 /media/win_e ntfs-3g defaults 0 0
# Entry for /dev/sdc3 :
UUID=9002DC9802DC849E /media/win_f ntfs-3g defaults 0 0
# Entry for /dev/sdb1 :
UUID=0C2CCCFD2CCCE2B6 /mnt/win_c2 ntfs-3g defaults 0 0
none /proc proc defaults 0 0
# Entry for /dev/sdb6 :
UUID=f0ef886a-ae6c-439d-abf4-55c868da8e7a swap swap defaults 0 0
# Entry for /dev/sdc6 :
UUID=28fa5963-54cc-4876-847a-d176d38c4e2d swap swap defaults 0 0
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt


```

---

### Post by Double.J on 2012-01-30
Hi there, not sure it'll make a lot of difference, but try declaring the filesystem type? Afraid I don't know much about scripting, but this entry works for me in 40_custom (modified from my suse data to reflect your set up)
```

menuentry "Mandriva" {
insmod ext3
set root=(hd2,5)
linux (hd2,5)/boot/vmlinuz
initrd (hd2,5)/boot/initrd.img
}

```

Also I notice that my 40_custom file has
```
exec tail -n +3 $0
``` Line and !/bin/sh is commented out? It does say not to edit the exec tail line? Is there a reason not to add the entry to the 40_custom file?

Of course it could just be a wrong drive/partition number - could try the analogue trial and error changing them!
All the best :)

---

### Post by oldfred on 2012-01-30
I am not seeing the Mandriva boot files?? Or what it think is that the menu.lst and old grub legacy entries overlapping the Ubuntu partitioin are the Mandriva boot.

Not familiar with Madriva, does it normally have a separate /boot partition. Or sometimes script does not correctly parse a partition if it is not in the "normal" locations as it is just coded to look in certain places.

If installing grub legacy to something other than the MBR, you should install to the partition that it boot from. And you cannot share boot partitions, systems get very confused. 

So I think Madriva needs a separate /boot partition, not sure if it will install with that in / (root) like Ubuntu or not, but it cannot be the Ubuntu partition.

Separately - is sdb a new drive? It does not show any partitions. Also some of the entires for grub legacy in Ubuntu from Mandriva refer  to drive & partition, which now seem to have changed with the new sdb drive.

If you are adding a new drive you may want to make sure you use SATA ports in order. At least on my system drives appear in the same order as the ports used on the motherboard. I had used 1, 3, 5 and plugged a new drive in & it was sdb, when I wanted sdd. I had to go back and replug some of the existing (including DVD) to get order correct.

---

### Post by cyril.godart on 2012-01-31
[To gnu/mirow: ]("http://ubuntuforums.org/member.php?u=1523263")

It indeed crossed my mind to add the partition type but I forgot to do it. It could have been that and it is useful to know it is not. 
Not sure where the exec tail go but i have not seen it mentioned in the part of the manual I read. And that part did not include the 40_custom file I must confess. 
I might give it a try when I exhaust a few other alleys. I did try to change the partition numbers though, to no avail. 
[]("http://ubuntuforums.org/member.php?u=1523263")

---

### Post by cyril.godart on 2012-01-31
To oldfred:
Hum. I have come across the questions enough times while installing that I do recall Mandriva asking me where I wanted to install the boot(?) in: / or /boot if memory serves.
Since I was clueless, I chose randomly and not even systematically. 
I could go through the trouble of reinstalling it yet another time (it is not that long a process after all) but I would need to know what an educated answer to the question is. 

sdb is not a new drive (or not exactly, it has been hardly used) and you do make me notice it is not visible any more (I never use it as I planned to have it as a back-up but after several months I am yet to do it). I guess I must have made a bad manipulation while installing one of these systems. What I am certain of now is that it is clear I am totally out of my league on these subjects. 

Thanks for the time.

---

### Post by oldfred on 2012-01-31
Technically you could fix it, but it is probably easier just to reinstall. Just install grub to the same partition you install Mandriva to. If it asks about /boot leave it in / (root).

Ubuntu's -os-prober is good enough that it should find the Mandriva boot files and let you also boot it from the menu.

---

### Post by cyril.godart on 2012-02-05
Some re-installations of Mandriva 2011 later (the drive naming conventions changes between Ubutu and the Mandriva 2011 installer, which I was not paying enough attention to). 
I have made the entire Seagate (sdc) drive a Linux partition. There are 3 different places where the boot is mentioned during the installation (very good installation process by Mandriva or so it looks to me):
- in the Partitioning section
- in the boot loader section
- at the end in the summary of the installation, you can still customise a few things. 
That's where you can specify to put the boot in the partition as you suggested, OldFred. 
When I do that I get prompted by the Mandriva Installer that reminds me that, since I am putting the boot in with the Linux partition, I must have another Grub installed somewhere in the MBR and it asks me where. Given the right place, the installer displays the Grub 2 menu. At this point, I thought I was done and over and you could hear my sigh of relief from the street. I edited the entry for Mandriva 2011. And rebooted confidently. I chose the Mandriva 2011 entry. There I get an error but it proceeds, gets to a Mandriva console where it fails. That's where I am. 
I put the content of bootinfoscript if someone cares:

```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 2386600240 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive.
    Boot file info:      Grub Legacy (v0.97) in the file /boot.backup.sda 
                       looks at sector 32520964 on boot drive #3 for the 
                       stage2 file.  A stage2 file is at this location on 
                       /dev/sdc.  Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.10
    Boot files:        /grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sdc1 and looks at sector 19460639 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sdc.  Stage2 looks on partition #1 
                       for /boot/grub/menu.lst.
    Operating System:  
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1798.8 GB, 1798752436224 bytes
255 heads, 63 sectors/track, 218685 cylinders, total 3513188352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,026,048    13,314,047    12,288,000  27 Hidden NTFS (Recovery Environment)
/dev/sda3          13,314,048   599,642,172   586,328,125   7 NTFS / exFAT / HPFS
/dev/sda4         599,646,206 3,513,186,303 2,913,540,098   5 Extended
/dev/sda5       1,639,636,992 2,523,072,511   883,435,520  83 Linux
/dev/sda6       3,395,328,000 3,513,186,303   117,858,304  82 Linux swap / Solaris
/dev/sda7         599,646,208 1,639,634,943 1,039,988,736   7 NTFS / exFAT / HPFS
/dev/sda8       2,523,074,560 3,395,325,951   872,251,392   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    25,189,919    25,189,857  83 Linux
/dev/sdb2          25,189,920 3,907,024,064 3,881,834,145   5 Extended
/dev/sdb5          25,189,983    33,367,004     8,177,022  82 Linux swap / Solaris
/dev/sdb6          33,367,068 3,907,024,064 3,873,656,997  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63    25,189,919    25,189,857  83 Linux
/dev/sdc2          25,189,920   312,576,704   287,386,785   5 Extended
/dev/sdc5          25,189,983    33,367,004     8,177,022  82 Linux swap / Solaris
/dev/sdc6          33,367,068   312,576,704   279,209,637  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        44E0D986E0D97F1C                       ntfs       System
/dev/sda2        F2CADAB9CADA78F5                       ntfs       Recovery
/dev/sda3        9002DC9802DC849E                       ntfs       OS
/dev/sda5        3a934db0-24d0-42cd-aeed-5b52f30061e0   ext4       
/dev/sda6        28fa5963-54cc-4876-847a-d176d38c4e2d   swap       
/dev/sda7        0FA1F85036203798                       ntfs       LaBausse
/dev/sda8        18E23574145A12C1                       ntfs       Voivodina
/dev/sdb1        df28274c-046c-472f-acb5-8bbc7ef97cf3   ext4       
/dev/sdb5        09a38825-c92a-4a4f-b5e2-3838aa6126fd   swap       
/dev/sdb6        1aae39e5-d42f-4369-968d-939ebb8facfa   ext4       
/dev/sdc1        55a2047c-e9cf-434e-ac30-de3a344eda1b   ext4       
/dev/sdc5        73510b8c-e168-49e2-8b1f-b12fd63caab2   swap       
/dev/sdc6        ae636189-d0a1-45ad-8aa9-0d0bdce91a50   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


============================= sda5/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1,4)/gfxmenu
default 0

title linux
kernel (hd1,4)/vmlinuz BOOT_IMAGE=linux root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d splash=silent vga=788
initrd (hd1,4)/initrd.img

title linux-nonfb
kernel (hd1,4)/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d
initrd (hd1,4)/initrd.img

title failsafe
kernel (hd1,4)/vmlinuz BOOT_IMAGE=failsafe root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda  nokmsboot failsafe
initrd (hd1,4)/initrd.img

title windows
root (hd2,0)
map (0x80) (0x82)
map (0x82) (0x80)
makeactive
chainloader +1

title windows1
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.39.4-4.2-desktop' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /vmlinuz-2.6.39.4-4.2-desktop root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /initrd-2.6.39.4-4.2-desktop.img
}
menuentry 'Ubuntu, with Linux 2.6.39.4-4.2-desktop (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 2.6.39.4-4.2-desktop ...'
    linux    /vmlinuz-2.6.39.4-4.2-desktop root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd-2.6.39.4-4.2-desktop.img
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_mandriva_2011 ###
Adding Mandriva 2011 to GRUB 2
menuentry "Mandriva 2011" {
set root=(hd2,1)
linux (hd2,1)/boot/vmlinuz
initrd (hd2,1)/boot/initrd.img
}
EOF ### END /etc/grub.d/11_mandriva_2011 ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 44E0D986E0D97F1C
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9002DC9802DC849E
    chainloader +1
}
menuentry "linux (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root df28274c-046c-472f-acb5-8bbc7ef97cf3
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=df28274c-046c-472f-acb5-8bbc7ef97cf3 nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d splash=silent vga=788
    initrd (hd0,0)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root df28274c-046c-472f-acb5-8bbc7ef97cf3
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=df28274c-046c-472f-acb5-8bbc7ef97cf3 nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d
    initrd (hd0,0)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root df28274c-046c-472f-acb5-8bbc7ef97cf3
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=df28274c-046c-472f-acb5-8bbc7ef97cf3 nokmsboot failsafe
    initrd (hd0,0)/boot/initrd.img
}
menuentry "linux (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 55a2047c-e9cf-434e-ac30-de3a344eda1b
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=55a2047c-e9cf-434e-ac30-de3a344eda1b nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d splash=silent vga=788
    initrd (hd2,0)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 55a2047c-e9cf-434e-ac30-de3a344eda1b
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=55a2047c-e9cf-434e-ac30-de3a344eda1b nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d
    initrd (hd2,0)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 55a2047c-e9cf-434e-ac30-de3a344eda1b
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=55a2047c-e9cf-434e-ac30-de3a344eda1b nokmsboot failsafe
    initrd (hd2,0)/boot/initrd.img
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=28fa5963-54cc-4876-847a-d176d38c4e2d none            swap    sw              0       0
/dev/sdc6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1138.019702911 = 1221.939351552 boot/grub/core.img                             1
1024.212936401 = 1099.740266496 boot/grub/grub.cfg                             1
 783.292968750 = 841.054420992  boot/initrd.img-3.0.0-12-generic               2
1138.969837189 = 1222.959550464 boot/initrd.img-3.0.0-13-generic               2
1140.914428711 = 1225.047539712 boot/initrd.img-3.0.0-14-generic               2
 798.282321930 = 857.149116416  boot/initrd.img-3.0.0-15-generic               2
 797.882785797 = 856.720117760  boot/initrd.img-3.0.0-16-generic               2
1103.972846985 = 1185.381818368 boot/vmlinuz-3.0.0-12-generic                  1
1129.777778625 = 1213.089652736 boot/vmlinuz-3.0.0-13-generic                  2
1137.730903625 = 1221.629255680 boot/vmlinuz-3.0.0-14-generic                  1
 797.629364014 = 856.448008192  boot/vmlinuz-3.0.0-15-generic                  2
 797.184055328 = 855.969861632  boot/vmlinuz-3.0.0-16-generic                  1
 817.964855194 = 878.283075584  grub/menu.lst                                  1
 817.965084076 = 878.283321344  grub/stage2                                    1
 782.070312500 = 839.741603840  initrd-2.6.39.4-4.2-desktop.img                3
 797.882785797 = 856.720117760  initrd.img                                     2
 782.070312500 = 839.741603840  initrd.img.old                                 3
 797.184055328 = 855.969861632  vmlinuz                                        1
 782.007534027 = 839.674195968  vmlinuz-2.6.39.4-4.2-desktop                   1
 782.007534027 = 839.674195968  vmlinuz.old                                    1

=========================== sdb1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,0)/boot/gfxmenu
default 0

title linux
kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=df28274c-046c-472f-acb5-8bbc7ef97cf3  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d splash=silent vga=788
initrd (hd0,0)/boot/initrd.img

title linux-nonfb
kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=df28274c-046c-472f-acb5-8bbc7ef97cf3  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d
initrd (hd0,0)/boot/initrd.img

title failsafe
kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=df28274c-046c-472f-acb5-8bbc7ef97cf3  nokmsboot failsafe
initrd (hd0,0)/boot/initrd.img

title windows
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

title Linux sdc5
root (hd1,4)
configfile /grub/menu.lst
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# Entry for /dev/sda1 :
UUID=df28274c-046c-472f-acb5-8bbc7ef97cf3 / ext4 acl,relatime 1 1
# Entry for /dev/sda6 :
UUID=1aae39e5-d42f-4369-968d-939ebb8facfa /home ext4 acl,relatime 1 2
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
# Entry for /dev/sdc2 :
UUID=F2CADAB9CADA78F5 /media/win_ ntfs-3g defaults 0 0
# Entry for /dev/sdc1 :
UUID=44E0D986E0D97F1C /media/win_c2 ntfs-3g defaults 0 0
# Entry for /dev/sdc7 :
UUID=0FA1F85036203798 /media/win_d ntfs-3g defaults 0 0
# Entry for /dev/sdc8 :
UUID=18E23574145A12C1 /media/win_e ntfs-3g defaults 0 0
# Entry for /dev/sdc3 :
UUID=9002DC9802DC849E /media/win_f ntfs-3g defaults 0 0
none /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=09a38825-c92a-4a4f-b5e2-3838aa6126fd swap swap defaults 0 0
# Entry for /dev/sdc6 :
UUID=28fa5963-54cc-4876-847a-d176d38c4e2d swap swap defaults 0 0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   6.920318127 = 7.430635008    boot/grub/menu.lst                             1
   6.920547009 = 7.430880768    boot/grub/stage2                               1
   5.862895489 = 6.295236096    boot/initrd-2.6.39.4-4.2-desktop.img           1
   5.862895489 = 6.295236096    boot/initrd.img                                1
   6.315730572 = 6.781464064    boot/vmlinuz                                   1
   6.315730572 = 6.781464064    boot/vmlinuz-2.6.39.4-4.2-desktop              1

=========================== sdc1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
timeout 10
color black/cyan yellow/cyan
default 0

title linux
kernel (hd2,0)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=55a2047c-e9cf-434e-ac30-de3a344eda1b  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d splash=silent vga=788
initrd (hd2,0)/boot/initrd.img

title linux-nonfb
kernel (hd2,0)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=55a2047c-e9cf-434e-ac30-de3a344eda1b  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d
initrd (hd2,0)/boot/initrd.img

title failsafe
kernel (hd2,0)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=55a2047c-e9cf-434e-ac30-de3a344eda1b  nokmsboot failsafe
initrd (hd2,0)/boot/initrd.img

title windows
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

title Mandriva Linux (Official)
root (hd0,0)
configfile /boot/grub/menu.lst
--------------------------------------------------------------------------------

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# Entry for /dev/sdb1 :
UUID=55a2047c-e9cf-434e-ac30-de3a344eda1b / ext4 acl,relatime 1 1
# Entry for /dev/sdb6 :
UUID=ae636189-d0a1-45ad-8aa9-0d0bdce91a50 /home ext4 acl,relatime 1 2
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
# Entry for /dev/sdc2 :
UUID=F2CADAB9CADA78F5 /media/win_ ntfs-3g defaults 0 0
# Entry for /dev/sdc1 :
UUID=44E0D986E0D97F1C /media/win_c ntfs-3g defaults 0 0
# Entry for /dev/sdc7 :
UUID=0FA1F85036203798 /media/win_d ntfs-3g defaults 0 0
# Entry for /dev/sdc8 :
UUID=18E23574145A12C1 /media/win_e ntfs-3g defaults 0 0
# Entry for /dev/sdc3 :
UUID=9002DC9802DC849E /media/win_f ntfs-3g defaults 0 0
none /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=09a38825-c92a-4a4f-b5e2-3838aa6126fd swap swap defaults 0 0
# Entry for /dev/sdb5 :
UUID=73510b8c-e168-49e2-8b1f-b12fd63caab2 swap swap defaults 0 0
# Entry for /dev/sdc6 :
UUID=28fa5963-54cc-4876-847a-d176d38c4e2d swap swap defaults 0 0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   9.279464245 = 9.963748864    boot/grub/menu.lst                             1
   9.279689312 = 9.963990528    boot/grub/stage2                               1
   5.526896954 = 5.934460416    boot/initrd-2.6.39.4-4.2-desktop.img           2
   5.526896954 = 5.934460416    boot/initrd.img                                2
   8.141467571 = 8.741834240    boot/vmlinuz                                   1
   8.141467571 = 8.741834240    boot/vmlinuz-2.6.39.4-4.2-desktop              1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000  a4 c2 f0 40 ca 08 d5 0a  18 44 c3 3f 6b a0 ad b1  |...@.....D.?k...|
00000010  e2 55 cf 91 9b b5 76 dc  8d a2 c4 82 16 38 b3 14  |.U....v......8..|
00000020  41 e1 03 c7 11 a9 8e d0  a1 94 bc 6d 89 15 5b 85  |A..........m..[.|
00000030  cf b5 0d 48 57 d0 d0 00  34 32 1d cb 56 70 31 43  |...HW...42..Vp1C|
00000040  8c 94 ef c3 ae e7 33 45  89 09 95 b1 14 b5 8b c2  |......3E........|
00000050  5f 65 40 89 4c 9a 82 b8  38 5c 3a d8 f0 bd c8 0d  |_e@.L...8\:.....|
00000060  a2 7d 08 a9 6c b3 68 4b  13 0e b2 79 a7 cd 54 6a  |.}..l.hK...y..Tj|
00000070  46 d9 fc 34 ff fa a4 64  46 f7 d0 0e e4 51 5a 51  |F..4...dF....QZQ|
00000080  0b 29 1f 14 5a 24 ca 50  61 23 7c 0f 6c d7 46 0c  |.)..Z$.Pa#|.l.F.|
00000090  a5 13 01 cb 22 e8 c5 86  0a 38 ae fb 3f 04 59 33  |...."....8..?.Y3|
000000a0  1c f5 31 ed b5 fe 7b 58  a3 f0 7a f6 62 f4 92 f3  |..1...{X..z.b...|
000000b0  1c 3b 02 96 e8 f9 da f3  f5 94 8e cd 2a eb 55 6a  |.;..........*.Uj|
000000c0  9a 09 47 d6 e8 dd 5e f8  53 73 92 e2 aa 6b a6 3a  |..G...^.Ss...k.:|
000000d0  31 c7 30 30 64 63 76 80  01 00 00 00 01 b6 56 23  |1.00dcv.......V#|
000000e0  dc 0d 87 c1 6b 16 05 5a  e1 90 44 2f a5 60 99 8b  |....k..Z..D/.`..|
000000f0  9a d5 2b f5 fa 57 b1 69  42 d2 87 99 eb 71 bf ed  |..+..W.iB....q..|
00000100  b5 33 05 38 46 ef d9 32  5b 51 76 55 b6 b1 64 6b  |.3.8F..2[QvU..dk|
00000110  c4 69 5c 60 90 3f bf 1e  67 9b ff e6 04 d8 23 4f  |.i\`.?..g.....#O|
00000120  55 76 b2 bd da d9 d5 79  14 42 74 d8 c7 ab d5 9e  |Uv.....y.Bt.....|
00000130  76 53 89 d0 3f 06 3e 0c  a5 54 08 7e 1e 17 e5 8b  |vS..?.>..T.~....|
00000140  58 d2 73 eb e9 3f 49 d3  43 28 95 e5 65 d0 79 2c  |X.s..?I.C(..e.y,|
00000150  ff 98 3e 3f fa ff 1f 23  85 8d 1c f0 31 dc 12 ff  |..>?...#....1...|
00000160  30 95 36 d5 aa f2 a1 fd  cd be ab 2b 5d 2b 95 fc  |0.6........+]+..|
00000170  7c af dd d9 f9 25 df cf  c6 d6 92 6a bd 8e 2f 8a  ||....%.....j../.|
00000180  fd bb 90 fa b5 7e f2 bd  ee 69 30 6c 16 f6 cc 8a  |.....~...i0l....|
00000190  04 54 7b 51 fc ac 91 7e  5d 45 25 5f 9d b4 57 19  |.T{Q...~]E%_..W.|
000001a0  96 2e 22 ea e4 b2 12 12  d0 e5 02 04 4e 57 42 00  |..".........NWB.|
000001b0  96 9b 54 b5 fd d4 28 e3  70 61 a7 6f e5 e3 00 fe  |..T...(.pa.o....|
000001c0  ff ff 82 fe ff ff 3f 00  00 00 7e c5 7c 00 00 fe  |......?...~.|...|
000001d0  ff ff 05 fe ff ff bd c5  7c 00 e4 66 a4 10 00 00  |........|..f....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt


```

Best

---

### Post by oldfred on 2012-02-05
Since you installed totally to sdc, you could have the boot loader in the MBR of sdc. I prefer to have each system on a separate drive and install its boot loader in that same drive's MBR. When I used old grub legacy and had multiple installs on one drive I installed grub to the PBR - partition boot sector and chainloaded to the PBR.

Not sure your need the hd2,0 entry, I still do not know exactly when grub hands it over to the new system. Grub2 would need hd2,1 and grub legacy is the hd2,0.
initrd [COLOR=Red](hd2,0)[/COLOR]/boot/initrd.img

Since you have grub legacy in the PBR of sdc1 you can also add a chain load entry to 40_custom.

gksudo gedit /etc/grub.d/40_custom
sudo update-grub


# Chainload another bootloader
menuentry "Chainload partition sdc1" {
set root=(hd2,1)
chainloader +1
}

You do have some left over menu.lst from previous installs in sda5 and sdb1. It also looks like Mandriva sees the install drive that Ubuntu sees as sdc, as sdb but uses the UUIDs so it is not an issue.

---

### Post by cyril.godart on 2012-02-09
to oldfred: thought  what you suggested looked simpler as a solution. And I thought I had to reinstall Mandriva. So I did that. But I realise that the generated file is the same as the previous one I copied the content of. And that one had already Grub legacy in two other MBR (sdb and sdc). So I am not sure what I really achieved at this stage. 
Anyway, I copied your script into 40_custom and updated grub. 
When I select the chainloader entry, I do get to grub 0.97 but get the prompt. I am not sure that was what was intended. 

```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 2386600240 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive.
    Boot file info:      Grub Legacy (v0.97) in the file /boot.backup.sda 
                       looks at sector 32520964 on boot drive #3 for the 
                       stage2 file.  A stage2 file is at this location on 
                       /dev/sdc.  Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.10
    Boot files:        /grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sdc1 and looks at sector 19460639 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sdc.  Stage2 looks on partition #1 
                       for /boot/grub/menu.lst.

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Mandriva Linux release 2011.0 
                       (Official) for x86_64 Kernel 2.6.39.4-4.2-desktop on a 
                       12-processor x86_64 /
    Boot files:        /boot/grub/menu.lst /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1798.8 GB, 1798752436224 bytes
255 heads, 63 sectors/track, 218685 cylinders, total 3513188352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,026,048    13,314,047    12,288,000  27 Hidden NTFS (Recovery Environment)
/dev/sda3          13,314,048   599,642,172   586,328,125   7 NTFS / exFAT / HPFS
/dev/sda4         599,646,206 3,513,186,303 2,913,540,098   5 Extended
/dev/sda5       1,639,636,992 2,523,072,511   883,435,520  83 Linux
/dev/sda6       3,395,328,000 3,513,186,303   117,858,304  82 Linux swap / Solaris
/dev/sda7         599,646,208 1,639,634,943 1,039,988,736   7 NTFS / exFAT / HPFS
/dev/sda8       2,523,074,560 3,395,325,951   872,251,392   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    25,189,919    25,189,857  83 Linux
/dev/sdb2          25,189,920 3,907,024,064 3,881,834,145   5 Extended
/dev/sdb5          25,189,983    33,367,004     8,177,022  82 Linux swap / Solaris
/dev/sdb6          33,367,068 3,907,024,064 3,873,656,997  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     8,177,084     8,177,022  82 Linux swap / Solaris
/dev/sdc2           8,177,085   312,576,704   304,399,620   5 Extended
/dev/sdc5           8,177,148   312,576,704   304,399,557  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        44E0D986E0D97F1C                       ntfs       System
/dev/sda2        F2CADAB9CADA78F5                       ntfs       Recovery
/dev/sda3        9002DC9802DC849E                       ntfs       Windows 7
/dev/sda5        3a934db0-24d0-42cd-aeed-5b52f30061e0   ext4       
/dev/sda6        28fa5963-54cc-4876-847a-d176d38c4e2d   swap       
/dev/sda7        0FA1F85036203798                       ntfs       LaBausse
/dev/sda8        18E23574145A12C1                       ntfs       Voivodina
/dev/sdb1        df28274c-046c-472f-acb5-8bbc7ef97cf3   ext4       
/dev/sdb5        09a38825-c92a-4a4f-b5e2-3838aa6126fd   swap       
/dev/sdb6        1aae39e5-d42f-4369-968d-939ebb8facfa   ext4       
/dev/sdc1        1d603a36-a1bb-4b59-927a-bc3d1568a44d   swap       
/dev/sdc5        9437987c-f1fd-4e3f-b26a-ce56610e187e   ext4       Mandriva

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


============================= sda5/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1,4)/gfxmenu
default 0

title linux
kernel (hd1,4)/vmlinuz BOOT_IMAGE=linux root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d splash=silent vga=788
initrd (hd1,4)/initrd.img

title linux-nonfb
kernel (hd1,4)/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d
initrd (hd1,4)/initrd.img

title failsafe
kernel (hd1,4)/vmlinuz BOOT_IMAGE=failsafe root=UUID=e15d26da-9018-4cec-b5a8-375ad4d65cda  nokmsboot failsafe
initrd (hd1,4)/initrd.img

title windows
root (hd2,0)
map (0x80) (0x82)
map (0x82) (0x80)
makeactive
chainloader +1

title windows1
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.39.4-4.2-desktop' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux    /vmlinuz-2.6.39.4-4.2-desktop root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro   quiet splash vt.handoff=7
    initrd    /initrd-2.6.39.4-4.2-desktop.img
}
menuentry 'Ubuntu, with Linux 2.6.39.4-4.2-desktop (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    echo    'Loading Linux 2.6.39.4-4.2-desktop ...'
    linux    /vmlinuz-2.6.39.4-4.2-desktop root=UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd-2.6.39.4-4.2-desktop.img
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_mandriva_2011 ###
Adding Mandriva 2011 to GRUB 2
menuentry "Mandriva 2011" {
set root=(hd2,1)
linux (hd2,1)/boot/vmlinuz
initrd (hd2,1)/boot/initrd.img
}
EOF ### END /etc/grub.d/11_mandriva_2011 ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3a934db0-24d0-42cd-aeed-5b52f30061e0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 44E0D986E0D97F1C
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9002DC9802DC849E
    chainloader +1
}
menuentry "linux (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root df28274c-046c-472f-acb5-8bbc7ef97cf3
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=df28274c-046c-472f-acb5-8bbc7ef97cf3 nokmsboot splash=silent resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d vga=788
    initrd (hd2,0)/boot/initrd.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
# Chainload another bootloader
menuentry "Chainload partition sdc1" {
set root=(hd2,1)
chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3a934db0-24d0-42cd-aeed-5b52f30061e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=28fa5963-54cc-4876-847a-d176d38c4e2d none            swap    sw              0       0
/dev/sdc6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1138.019702911 = 1221.939351552 boot/grub/core.img                             1
1024.652339935 = 1100.212072448 boot/grub/grub.cfg                             1
 783.292968750 = 841.054420992  boot/initrd.img-3.0.0-12-generic               2
1138.969837189 = 1222.959550464 boot/initrd.img-3.0.0-13-generic               2
1140.914428711 = 1225.047539712 boot/initrd.img-3.0.0-14-generic               2
 798.282321930 = 857.149116416  boot/initrd.img-3.0.0-15-generic               2
 797.882785797 = 856.720117760  boot/initrd.img-3.0.0-16-generic               2
1103.972846985 = 1185.381818368 boot/vmlinuz-3.0.0-12-generic                  1
1129.777778625 = 1213.089652736 boot/vmlinuz-3.0.0-13-generic                  2
1137.730903625 = 1221.629255680 boot/vmlinuz-3.0.0-14-generic                  1
 797.629364014 = 856.448008192  boot/vmlinuz-3.0.0-15-generic                  2
 797.184055328 = 855.969861632  boot/vmlinuz-3.0.0-16-generic                  1
 817.964855194 = 878.283075584  grub/menu.lst                                  1
 817.965084076 = 878.283321344  grub/stage2                                    1
 782.070312500 = 839.741603840  initrd-2.6.39.4-4.2-desktop.img                3
 797.882785797 = 856.720117760  initrd.img                                     2
 782.070312500 = 839.741603840  initrd.img.old                                 3
 797.184055328 = 855.969861632  vmlinuz                                        1
 782.007534027 = 839.674195968  vmlinuz-2.6.39.4-4.2-desktop                   1
 782.007534027 = 839.674195968  vmlinuz.old                                    1

=========================== sdb1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd2,0)/boot/gfxmenu
default 0

title linux
kernel (hd2,0)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=df28274c-046c-472f-acb5-8bbc7ef97cf3 nokmsboot splash=silent resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d vga=788
initrd (hd2,0)/boot/initrd.img

title windows
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

title Linux sdc5
root (hd1,4)
configfile /grub/menu.lst

title alt_windows
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# Entry for /dev/sda1 :
UUID=df28274c-046c-472f-acb5-8bbc7ef97cf3 / ext4 acl,relatime 1 1
# Entry for /dev/sdb5 :
UUID=9437987c-f1fd-4e3f-b26a-ce56610e187e /home ext4 acl,relatime 1 2
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
# Entry for /dev/sdc2 :
UUID=F2CADAB9CADA78F5 /media/win_ ntfs-3g defaults 0 0
# Entry for /dev/sdc1 :
UUID=44E0D986E0D97F1C /media/win_c2 ntfs-3g defaults 0 0
# Entry for /dev/sdc7 :
UUID=0FA1F85036203798 /media/win_d ntfs-3g defaults 0 0
# Entry for /dev/sdc8 :
UUID=18E23574145A12C1 /media/win_e ntfs-3g defaults 0 0
# Entry for /dev/sdc3 :
UUID=9002DC9802DC849E /media/win_f ntfs-3g defaults 0 0
none /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=09a38825-c92a-4a4f-b5e2-3838aa6126fd swap swap defaults 0 0
# Entry for /dev/sdb1 :
UUID=1d603a36-a1bb-4b59-927a-bc3d1568a44d swap swap defaults 0 0
# Entry for /dev/sdc6 :
UUID=28fa5963-54cc-4876-847a-d176d38c4e2d swap swap defaults 0 0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   6.254863262 = 6.716108288    boot/grub/menu.lst                             1
   6.922854900 = 7.433358848    boot/grub/stage2                               1
   5.862895489 = 6.295236096    boot/initrd-2.6.39.4-4.2-desktop.img           1
   5.862895489 = 6.295236096    boot/initrd.img                                1
   6.315730572 = 6.781464064    boot/vmlinuz                                   1
   6.315730572 = 6.781464064    boot/vmlinuz-2.6.39.4-4.2-desktop              1

=========================== sdc5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/boot/gfxmenu
default 0

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=9437987c-f1fd-4e3f-b26a-ce56610e187e  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d splash=silent PROFILE=default vga=797
initrd (hd0,4)/boot/initrd.img

title linux-nonfb
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=9437987c-f1fd-4e3f-b26a-ce56610e187e  nokmsboot resume=UUID=28fa5963-54cc-4876-847a-d176d38c4e2d
initrd (hd0,4)/boot/initrd.img

title failsafe
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=9437987c-f1fd-4e3f-b26a-ce56610e187e  nokmsboot failsafe
initrd (hd0,4)/boot/initrd.img

title windows
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

title Linux sdc5
root (hd1,4)
configfile /grub/menu.lst

title Mandriva Linux (Official)
root (hd2,0)
configfile /boot/grub/menu.lst
--------------------------------------------------------------------------------

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# Entry for /dev/sdb5 :
UUID=9437987c-f1fd-4e3f-b26a-ce56610e187e / ext4 acl,relatime 1 1
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
# Entry for /dev/sdc2 :
UUID=F2CADAB9CADA78F5 /media/win_ ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sdc1 :
UUID=44E0D986E0D97F1C /media/win_c2 ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sdc7 :
UUID=0FA1F85036203798 /media/win_d ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sdc8 :
UUID=18E23574145A12C1 /media/win_e ntfs-3g defaults,umask=000 0 0
# Entry for /dev/sdc3 :
UUID=9002DC9802DC849E /media/win_f ntfs-3g defaults,umask=000 0 0
none /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=09a38825-c92a-4a4f-b5e2-3838aa6126fd swap swap defaults 0 0
# Entry for /dev/sdb1 :
UUID=1d603a36-a1bb-4b59-927a-bc3d1568a44d swap swap defaults 0 0
# Entry for /dev/sdc6 :
UUID=28fa5963-54cc-4876-847a-d176d38c4e2d swap swap defaults 0 0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 134.134080887 = 144.025372672  boot/grub/menu.lst                             1
 134.134317398 = 144.025626624  boot/grub/stage2                               1
   5.435392380 = 5.836208128    boot/initrd-2.6.39.4-4.2-desktop.img           1
   5.435392380 = 5.836208128    boot/initrd.img                                1
 134.029390335 = 143.912962048  boot/vmlinuz                                   1
 134.029390335 = 143.912962048  boot/vmlinuz-2.6.39.4-4.2-desktop              1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000  75 73 72 2f 73 68 61 72  65 2f 64 6f 63 2f 48 54  |usr/share/doc/HT|
00000010  4d 4c 2f 64 65 2f 6b 61  6c 67 65 62 72 61 2f 6b  |ML/de/kalgebra/k|
00000020  61 6c 67 65 62 72 61 2d  6d 61 69 6e 2d 77 69 6e  |algebra-main-win|
00000030  64 6f 77 2e 70 6e 67 00  04 00 01 00 00 08 6d 00  |dow.png.......m.|
00000040  2d 00 01 2f 75 73 72 2f  73 68 61 72 65 2f 64 6f  |-../usr/share/do|
00000050  63 2f 48 54 4d 4c 2f 64  65 2f 6b 61 6c 67 65 62  |c/HTML/de/kalgeb|
00000060  72 61 2f 69 6e 64 65 78  2e 64 6f 63 62 6f 6f 6b  |ra/index.docbook|
00000070  04 00 01 00 00 08 6d 00  2f 00 01 2f 75 73 72 2f  |......m./../usr/|
00000080  73 68 61 72 65 2f 64 6f  63 2f 48 54 4d 4c 2f 64  |share/doc/HTML/d|
00000090  65 2f 6b 61 6c 67 65 62  72 61 2f 69 6e 64 65 78  |e/kalgebra/index|
000000a0  2e 63 61 63 68 65 2e 62  7a 32 00 00 04 00 01 00  |.cache.bz2......|
000000b0  00 08 6d 00 26 00 01 2f  75 73 72 2f 73 68 61 72  |..m.&../usr/shar|
000000c0  65 2f 64 6f 63 2f 48 54  4d 4c 2f 64 65 2f 6b 61  |e/doc/HTML/de/ka|
000000d0  6c 67 65 62 72 61 2f 63  6f 6d 6d 6f 6e 00 00 00  |lgebra/common...|
000000e0  04 00 01 00 00 08 6d 00  30 00 01 2f 75 73 72 2f  |......m.0../usr/|
000000f0  73 68 61 72 65 2f 64 6f  63 2f 48 54 4d 4c 2f 64  |share/doc/HTML/d|
00000100  65 2f 6b 61 6c 67 65 62  72 61 2f 63 6f 6d 6d 61  |e/kalgebra/comma|
00000110  6e 64 73 2e 64 6f 63 62  6f 6f 6b 00 04 00 01 00  |nds.docbook.....|
00000120  00 08 6d 00 1f 00 01 2f  75 73 72 2f 73 68 61 72  |..m..../usr/shar|
00000130  65 2f 64 6f 63 2f 48 54  4d 4c 2f 64 65 2f 6b 61  |e/doc/HTML/de/ka|
00000140  6c 67 65 62 72 61 00 00  04 00 01 00 00 08 6d 00  |lgebra........m.|
00000150  2b 00 01 2f 75 73 72 2f  73 68 61 72 65 2f 64 6f  |+../usr/share/do|
00000160  63 2f 48 54 4d 4c 2f 64  65 2f 6b 61 6c 61 72 6d  |c/HTML/de/kalarm|
00000170  2f 69 6e 64 65 78 2e 64  6f 63 62 6f 6f 6b 00 00  |/index.docbook..|
00000180  04 00 01 00 00 08 6d 00  2d 00 01 2f 75 73 72 2f  |......m.-../usr/|
00000190  73 68 61 72 65 2f 64 6f  63 2f 48 54 4d 4c 2f 64  |share/doc/HTML/d|
000001a0  65 2f 6b 61 6c 61 72 6d  2f 69 6e 64 65 78 2e 63  |e/kalarm/index.c|
000001b0  61 63 68 65 2e 62 7a 32  04 00 01 00 00 08 00 01  |ache.bz2........|
000001c0  41 fd 83 fe ff ff 3f 00  00 00 c5 c4 24 12 00 00  |A.....?.....$...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt


```

---

### Post by oldfred on 2012-02-09
A chainload entry will just load the grub menu chained to. That way if you get a kernel entry in Mandriva, you do not have to boot Ubuntu and run a sudo update-grub to find the new kernel. Minor advantage on updates, but requires two levels of mneus every time. Grub2 finds the kernels & lets you directly boot, so you do not get two menus.

Does everything now work ok? The one entry hd2,0 still does not look correct, does it also work?

Updates will install new grub entries, but if everything is in the same place it may not be different.

---

### Post by cyril.godart on 2012-02-10
Hi, the current setup is failing. When I choose the entry "chainload", I get grub legacy but only the prompt not the menu. 
I tried then to change in your script:
# Chainload another bootloader
menuentry "Chainload partition sdc1" {
set root=(hd2,1)
chainloader +1
}
(hd2,1) into (hd2,0) but to no avail. 
Then I thought that since it was the MBR I could also try (hd2) simply. This gave me a menu (!) where I could choose to boot Mandriva. Doing that was a let down: 
an error saying that the cylinder cannot be handled by the BIOS. 
I guess the issue is with the fact that the grub legacy is in the MBR. Not sure what to do from here. Ready to reinstall Mandriva yet again but this time I would like to make sure where to put the boot. 
From the bios, I check that booting first the disk 2 gives me a valid OS.

---

### Post by oldfred on 2012-02-10
Is this an older computer that can only boot boot from the first 137GB? Both grub & grub2 cannot get past an old BIOS. Otherwise there may be a setting in BIOS that needs updating.

---

### Post by cyril.godart on 2012-02-17
A few steps forward. I suspected that the "cylinder not handled by BIOS" message was indicative of a disk too big. Whether this assumption was correct or not is to be clarified. Nonetheless, it pointed me to the fact that I was probably not ending on the right disk somehow. 
I have 3 disks and the two Linux see them mapped differently:
Ubuntu:
hd0 sda -> RAID
hd1 sdb -> Hitachi
hd2 sdc -> Seagate
whereas for Mandriva:
hd0 sda -> Hitachi
hd1 sdb -> Seagate
hd2 sdc -> RAID
And I read somewhere that the numbering of the hard drives was inherited from the BIOS. 
Ubuntu Grub 2 starts and get the first disk configuration. So for Mandriva Grub Legacy to look at the right disk I thought I had to remap the drives. 
The command for remapping the drives has changed in Grub2 to drivemap (it used to be "map" in Grub legacy). So here is my new 40_Custom:
```

menuentry "Chainload partition sdc1" {
set root=(hd2)
drivemap (hd2) (hd1)
drivemap (hd1) (hd0)
drivemap (hd0) (hd2) 
chainloader +1
}

```
I now get the proper Grub Legacy menulist from the Seagate drive where Mandriva is installed. But then it fails:
(hd0,4) /boot/gfxmenu file not found

Then it proceeds to another older menu (probably installed on the Hitachi) 
and this time the error message is:
kernel (hd0,4)/boot/vmlinux BOOT_image-linux root = UUID=9437987c-... cannot mount selected partition...

---

### Post by oldfred on 2012-02-18
I have not seen that much mapping. Interesting.

I have seen issues with grub2 picking up entires from other systems that include the drive & partition entry on the kernel or init lines. Often it does not match the set root line and then cannot find the correct drive, partition. 

I might try without the  hd0,4 in the kernel line.
kernel [COLOR=Red](hd0,4)[/COLOR]/boo....

---

### Post by cyril.godart on 2012-02-18
You have not seen so much mapping because it is wrong ;-). Reading your post, I went to change my script to a simpler:

menuentry "Chainload partition sdc1" { set root=(hd2) drivemap (hd2) (hd0) chainloader +1 }
and it works. 
And quite uncharacteristically, I have understood why. 
Looking in the Mandriva configuration after this chainload, I see that the disk order is the same for Ubuntu and Mandriva. The reason is that I boot now with RAID disk (the disk with Ubuntu Grub2 in the MBR) as primary disk. It is obvious now but it had not occured to me before. In order to launch Mandriva, I had to change the disk order in the BIOS to have the primary disk set to the Seagate(Mandriva Grub legacy in the MBR). Hence why I was seeing the two mappings mentioned in my previous post. But when I chain load I am not changing the disk order anymore. 
To state the obvious again, when I am installing Mandriva, I boot from a CD and install it on the MBR of a disk seen as sda (or hd0) in that BIOS configuration. When I am back to booting from another disk the infomation stored in Grub Legacy refers to a hd0 disk but that hd0 disk is the disk from the other system. Hence the use of the "drivemap" command. 
Thanks for your help and guidance, OldFred.

---

### Post by oldfred on 2012-02-18
Glad you have it figured out.:)

---

### Post by cyril.godart on 2012-02-19
Well, actually, not sure I have completly figured it out really. A few things did bother me after I wrote my post. So I went to check again. I run bootinfoscript again in the Mandriva OS boot from the BIOS. As you can see below the info is the same. So the drive mapping seen from Mandriva Linux booted directly from the BIOS has not changed, contrarily to what I was saying. 

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

```So I wen to check the device.map file (exists in Grub Legacy but not in Grub 2). 
/boot/grub/device.map
(hd0) /dev/sdb
(hd1) /dev/sdc
(hd2) /dev/sda

I read somewhere that some BIOS maps the drives differently when booting from a CD-ROM, which could explain partly why the Grub2 and Grub Legacy internal numbering are different when the Linux mapping are the same. 
I guess that the section: 3.3 (The map between BIOS drives and OS devices) at [http://www.gnu.org/software/grub/manual/grub.html#Device-map](http://www.gnu.org/software/grub/manual/grub.html#Device-map) shows clearly that this is still a work in progress.

Best.

---

