---
title: "Win7 won't boot (even after reformat), but Ubuntu works fine (after repairing Grub2)"
date: 2012-04-27
forum: Any Other OS
---

### Post by lf610 on 2012-04-27
I'm completely stumped over this since I don't really know how GNU GRUB or  MBR work and have relatively limited knowledge of partitions. I need some help on getting Windows 7 to simply boot.

Anyway, I have one 120GB hard drive. I kept a 110GB partition for  Windows 7, and the remaining 10GB I've used as a separate partition (or  two if you include the swap) for trying all sorts of derivatives of  Ubuntu and Debian.

At some point today, Windows 7 just all of a sudden would refuse to boot if I select it from the GRUB menu.


Here's a clearer description of the boot process:

[IMG]http://oi50.tinypic.com/35243yu.jpg[/IMG]
After POST, it goes to the Grub 1.99-21 menu as it normally does, with this selection list:
[I]
Ubuntu, with Linux 3.2.0-23-generic
Ubuntu, with Linux 3.2.0-23-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)[/I]

All these items work fine except for Windows 7 (loader). When I select  Windows 7, it stays in a blank screen with a blinking text cursor at the  top left, with no HDD activity:

[IMG]http://oi50.tinypic.com/wk5rwm.jpg[/IMG]


I initially thought it was just some simple problem with the Master Boot  Record. I could still access the files on my Windows partition with  Xubuntu or any Live CD/USB.

What I've tried:
1) popped in Win7 install disc, setup recognized the Win7 installation  as if there was no problem, so I went straight to command prompt, typed  in [COLOR=Red]*bootrec /fixmbr*[/COLOR] and [COLOR=Red]*bootrec /fixboot*[/COLOR].  I rebooted the system, but it didn't fix anything. Instead, GRUB2 menu  was removed (as expected), but it went to the same blank screen with  blinking text cursor.

2) Startup Repair on the Win7 installation disc. Didn't fix anything, still blank screen+text cursor.

3) System restore. Actually I didn't try it. Unfortunately I had no saved restore point. Not that it really mattered at that point.

4) A reformat of Win7 x86. Even that didn't fix it. Still blank screen+text cursor.

Retrieving the GRUB2 menu was no problem at all, all I had to do was put  in my Xubuntu Live CD, open up terminal, input the commands [COLOR=Red]*sudo -i*[/COLOR], *[COLOR=Red]mount /dev/sda7 /mnt[/COLOR]*, then [COLOR=Red]*grub-install --root-directory=/mnt/ /dev/sda*[/COLOR].  This only takes me back to square one. Everything on the GRUB2 menu  including Xubuntu works fine, Windows 7 (loader) on the other hand still  has that blank screen. But again, I am still able to access the files  in the Windows partition on Xubuntu or any Live CD.

Here is my 120GB hard drive configuration:
```
/dev/sda
    /dev/sda1    ntfs    110071 MB
    /dev/sda6    ext4    9449 MB
    /dev/sda5    swap    511 MB
```

---

### Post by garvinrick4 on 2012-04-27
In ubuntu open a terminal and copy and paste this:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'


```
```
chmod +x bootinfoscript
```
```
sudo bash bootinfoscript
```

Now go to Home and will be a RESULTS file open it and copy and paste whole thing into message box.
Highlight whole thing again and click on # in upper right of message box and will put in nice little box to read from.
Now submit reply.

##This will show whole boot info so as to see what problem is.

---

### Post by lf610 on 2012-04-28
RESULTS.txt file
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......k..8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 7367928 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   214,982,895   214,982,833   7 NTFS / exFAT / HPFS
/dev/sda2         214,984,702   234,440,703    19,456,002   5 Extended
/dev/sda5         233,441,280   234,440,703       999,424  82 Linux swap / Solaris
/dev/sda6         214,984,704   233,441,279    18,456,576  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3999 MB, 3999268864 bytes
82 heads, 17 sectors/track, 5603 cylinders, total 7811072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192     7,811,071     7,802,880   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4600C31D00C312BB                       ntfs       
/dev/sda5        4adf6714-0e34-4034-8351-0ab731b958a3   swap       
/dev/sda6        2123fbdb-972b-438f-86d7-603ad2217eae   ext4       
/dev/sdb1        26B1-E00C                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 2123fbdb-972b-438f-86d7-603ad2217eae
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 2123fbdb-972b-438f-86d7-603ad2217eae
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 2123fbdb-972b-438f-86d7-603ad2217eae
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=2123fbdb-972b-438f-86d7-603ad2217eae ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 2123fbdb-972b-438f-86d7-603ad2217eae
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=2123fbdb-972b-438f-86d7-603ad2217eae ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 2123fbdb-972b-438f-86d7-603ad2217eae
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 2123fbdb-972b-438f-86d7-603ad2217eae
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4600C31D00C312BB
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=2123fbdb-972b-438f-86d7-603ad2217eae /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4adf6714-0e34-4034-8351-0ab731b958a3 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Xubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Xubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  f1 f1 91 e8 fd 68 d6 ba  a0 b6 37 18 d6 12 5f 67  |.....h....7..._g|
00000010  40 03 cf 5d 57 88 01 b5  71 40 d3 65 92 5c 67 60  |@..]W...q@.e.\g`|
00000020  ab 97 e2 d3 20 a2 c8 93  60 f6 80 25 35 8e b8 a6  |.... ...`..%5...|
00000030  5c f8 f0 46 c4 18 72 0e  72 8c d0 a2 c4 81 25 ce  |\..F..r.r.....%.|
00000040  42 c9 62 7b f8 af 97 b6  24 23 b8 e0 17 4c ed 72  |B.b{....$#...L.r|
00000050  ff b9 a9 09 e0 01 7f 70  b5 78 d4 95 69 23 e9 ff  |.......p.x..i#..|
00000060  b8 3e 2d 6d fe 58 d9 26  d7 2f 3a 93 03 dd 2f c5  |.>-m.X.&./:.../.|
00000070  56 21 65 cc 9f de 6a 8d  df 74 d4 55 03 e9 77 74  |V!e...j..t.U..wt|
00000080  49 b1 18 a1 8e e7 bc 0e  72 39 34 8c de 00 2b f4  |I.......r94...+.|
00000090  91 c9 f1 9c 5c 44 12 2c  d3 d9 68 bb 3b d8 1d a6  |....\D.,..h.;...|
000000a0  1c 7d 4e 41 65 1c c7 0f  c5 30 35 c2 9e 1c d2 56  |.}NAe....05....V|
000000b0  8a ae 46 9a 5c 8a 34 d9  74 a6 01 c3 62 32 99 4d  |..F.\.4.t...b2.M|
000000c0  65 3b cb 0c 75 f7 18 4a  89 b8 93 56 5c f3 a2 f6  |e;..u..J...V\...|
000000d0  67 db d9 01 db d3 52 5a  41 53 42 30 1a 00 de d4  |g.....RZASB0....|
000000e0  86 ce 3b 17 cf 28 91 94  40 62 44 61 11 4f 54 5d  |..;..(..@bDa.OT]|
000000f0  35 5b fc f8 7b 13 92 5a  04 5e ad 2e 8e ab 2d 37  |5[..{..Z.^....-7|
00000100  b2 8d 6d 43 fc e9 41 6b  21 33 ba a5 cd a2 2a 20  |..mC..Ak!3....* |
00000110  38 29 0b f4 42 52 79 e0  da d3 74 a9 e8 19 c9 22  |8)..BRy...t...."|
00000120  e0 9d 49 90 07 ad 15 d4  96 28 d7 44 b5 f9 17 74  |..I......(.D...t|
00000130  f3 f1 8d 2a 1e 5b c7 13  e3 c5 02 bb a4 d7 21 3a  |...*.[........!:|
00000140  07 54 5a 2e 2a c2 08 6b  a8 82 6d a4 2e 6d 19 b9  |.TZ.*..k..m..m..|
00000150  05 d4 ac eb 10 88 cb 74  36 9a 12 8b 52 82 a0 7a  |.......t6...R..z|
00000160  e7 f5 0b 58 f5 cf 50 57  da 73 db be dd 83 78 bd  |...X..PW.s....x.|
00000170  fa 73 89 57 93 87 f7 06  70 b5 3b f4 50 23 8f f8  |.s.W....p.;.P#..|
00000180  cb 29 f1 97 b7 a5 68 7b  96 de c3 24 16 35 00 fa  |.)....h{...$.5..|
00000190  de 4b 2b 75 42 c4 e5 3e  93 9f fa 54 f5 89 eb 19  |.K+uB..>...T....|
000001a0  ab 8d d5 5b db 87 75 9d  0c 2d 20 fe 1d 76 ec d8  |...[..u..- ..v..|
000001b0  51 57 69 88 86 9b 74 46  a8 78 57 f4 0e 08 00 fe  |QWi...tF.xW.....|
000001c0  ff ff 82 fe ff ff 02 a0  19 01 00 40 0f 00 00 fe  |...........@....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 a0 19 01 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected



```

---

### Post by OpenSourceRules on 2012-04-29
I just don't know if dual booting ends up with more issues?

---

### Post by lf610 on 2012-04-30
I couldn't figure out the problem so I ended up wiping the whole hard drive and reinstalled both operating systems. The sda#'s for the partitions still have a strange order (sda1, sda6, sda5) but I guess it's no big deal. Hopefully Win7 doesn't mess up again in the future.

---

### Post by garvinrick4 on 2012-04-30
> The sda#'s for the partitions still have a strange order (sda1, sda6,  sda5) but I guess it's no big deal. Hopefully Win7 doesn't mess up again  in the future.
Sorry did not get back to you quickly you did not get proper help and I apologize for that. 

sda5 is where the logical partitions start where linux can survive.
sda1 thru sda4 are primary partitions and you only get four on a basic drive. So there will be a Extended
partition which is a primary and then as many logical as you want inside that Extended partition. (there is a limit but a large number) So you are cool with sda1 Windows, sda2 Extended and sda5 linux and sda6 swap(scratch drive for extra RAM slower than RAM but helps when short on RAM.

In time you will be able to make your own partitions in "gparted" before you install so as to make exactly what you want. Like a logical partition for /home so you have a seperate partition for your file system.
Like 10 gig for file system and 100 gig for /home and when you want to fresh install you just install in / (file system) and not bother your personals in /home. 

Run that boot script again and look in sda1 at beginning of Results file and look at the boot files for Windows and see what is different from your first boot script so you can see the difference.

---

### Post by Stealth1402 on 2012-07-20
when you reformatted the windows it changed the id of the operating system you just need to update the grub so it recognizes it. When in ubuntu open a terminal and type sudo update-grub

that should fix it if you do it again

---

