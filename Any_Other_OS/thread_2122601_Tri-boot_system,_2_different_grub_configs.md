---
title: "Tri-boot system, 2 different grub configs"
date: 2013-03-05
forum: Any Other OS
---

### Post by Hodevah on 2013-03-05
Hello. Recently I installed a 3rd Distro beside Windows 7, and Linux Mint Nadia 14. 


Mint was running Grub with Windows just fine. Yesterday, I installed Peppermint OS 3. Post install of Peppermint 3, a new Grub came into existance. Normally, one expects a new install of Grub to recognize the existance of other distros and OS such as Windows. Peppermint did that with the exception that the Grub is kind of messed up. I will present pics of what I see when Grub loads up below.  Immediatly post install, I booted into Mint to 

```
sudo os-prober
```

```
sudo update-grub
```

I then booted into Peppermint to do the same Terminal commands as expresed above while in Mint. However, the Grub displays are not synonymous between the two distros. 

Grub Customizer display while in Mint:

[IMG]http://i.imgur.com/UfVxqZB.png[/IMG]
[IMG]http://i.imgur.com/NHP9i32.png[/IMG]

While in Peppermint, Grub Customizer presents this output. Please note that this is the output that I see when Grub loads up. The other Grub Customizer pictures from Mint do not present while Grub loads up. Below you will see ":Linux Mint --xxxxxxxx" and the 2 subsequent grub entries as compared to the above menu items displayed in Mint. The Grub menu entries displayed below are what I see when Grub boots up. In other words, the Grubs between the two distros are not synonymous where I believe they should be. 

Additionally, I have tried to start the script 'bootinfrscrip' after downloading that script but when I run it in Terminal, I get 
```
user@user-Aspire-5749 ~ $ ./bootinfoscript --help
bash: ./bootinfoscript: No such file or directory

```

I feel that the use of this scrip would help to navigate the problem a bit further; however, I am wondering that the script is not compatible for neither Mint nor Peppermint. 
Regardless, please view the Grub Customizer output below of what is presented while in Peppermint. Again, it is this Grub menu that is displayed. Not the one that is a 'bit cleaner looking" than the output while in Mint. 

**EDIT; **by the way, I have tried to 'right-click' to 'Rename' but that does not work. 

[IMG]http://i.imgur.com/fmRrqCK.png[/IMG]
[IMG]http://i.imgur.com/IoQFPzF.png[/IMG]

---

### Post by oldfred on 2013-03-05
This also runs bootinfoscript and adds extra info. Were you in the same folder that you downloaded boot script? It now downloads to Downloads, so cd Downloads. I think it needs sudo also.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Hodevah on 2013-03-05
Hi Oldfred. Thanks for getting back to me. I downloaded the bootinfoscript via Software Manager. 

Here is the link to Bootrepair pastebin report Mint:

[http://paste2.org/p/3053073](http://paste2.org/p/3053073)

Here is the link to Bootrepair report for Peppermint:

[http://paste2.org/p/3053259](http://paste2.org/p/3053259)



Just to be clear, the grub menu from Mint does not show upon boot up. Only the grub from Peppermint does. 
Also, when going into Boot repair while in Mint, it shows that the OS to boot by default is Mint. Not so according to Grub. It is Peppermint. Peppermint is at the top when grub loads. Normally, and according to Boot-repair, it would/should be Mint.

Also, terribly sorry for the big pictures above. I had no idea that screen capture would output such large pics. I thought that I enabled 'rectangular' sceenshots from the program while on one then the other OS to get such pics.

---

### Post by oldfred on 2013-03-05
Always best to attach screen shots with paper clip icon in advanced editor message.

You only have one MBR and it has the grub from sda11. It does not chain load to sda10's install but directly boots. But grub2's os-prober uses the grub menu in sda10 to update the entires in sda11, so if sda10 is updated, you then have to boot into sda11 and run the sudo grub-update for it to see new kernels.

Both installs refer to swap by device in sdb. You are not showing an sdb drive, so you may  be getting an error on booting about swap?

Do both boot ok?

Boot script only needs to be run once from one system to see details.

---

### Post by Hodevah on 2013-03-05
[ATTACH=CONFIG]239823[/ATTACH]



I reallize that you might have an idea of what the Grub menu looks like from the past2 weblinks but I decided to post here a screenshot of what it looks like on the laptop anyways. 

Both distro's boot fine. I did update grub earlier post install on both distros. 
There was no change in how Grub was/is after the Terminal command was entered. Having the necessity to update grub for the right distro was the first thing that came to mind.
Regardless, I decided to venture to update Grub again and unfortunately Grub remains the same. 

I uninstalled the bootinfoscript from Software Mgr and went instead to Sourceforge to download the script.
I dont know how to run this bootinfoscript so as to get some info from it. I have read the README file and there does not seem to be any info on what commands to run to get info.

```
user@user-Aspire-5749 ~ $ cd Downloads ./bootinfoscript /home/user/Downloads/bootinfoscript-061
user@user-Aspire-5749 ~/Downloads $ 

```
```
user@user-Aspire-5749 ~/Downloads $ ./bootinfoscript -h
bash: ./bootinfoscript: No such file or directory
user@user-Aspire-5749 ~/Downloads $ ./bootinfoscript -help
bash: ./bootinfoscript: No such file or directory
user@user-Aspire-5749 ~/Downloads $ ./bootinfoscript --help
bash: ./bootinfoscript: No such file or directory
user@user-Aspire-5749 ~/Downloads $
```

I'm kind of at a loss here.

.I am just wondering about something. Would purging Grub and then re-installing it via Boot-Repair help do you think? If so, from what distro might you think it best to do so?

Also, you mentioned about me not showing a /sdb device/drive. How do I enable that then if there is no report of one?

---

### Post by oldfred on 2013-03-06
I do not know about your sdb. Do you have another drive. Is it shown in BIOS because scripts do not show it. Or was that a removable drive that somehow had swap on it?

I always run bootinfoscript as part of my rsync backup so I have current data backed up.

I run this from the folder I have it in.
sudo bash bootinfoscript

---

### Post by Hodevah on 2013-03-06
Hi oldfred. :)

```
user@user-Aspire-5749 ~ $ cd Downloads /home/user/Downloads/bootinfoscript-061
user@user-Aspire-5749 ~/Downloads $ sudo bash bootinfoscript
[sudo] password for user: 
bash: bootinfoscript: No such file or directory
user@user-Aspire-5749 ~/Downloads $ 
```

no go. 
Not sure where to go now. 

By the way, I think the /sdb might have been the Live USB I used. 

Regardless, I managed to solve my problem. I decided to boot into a Live version of Ubuntu, install the ppa for boot-repair, and manipulate/re-install Grub on the original partition I had itl. Which in this case was with Mint. Grub menu is much better now and not as 'wacked' as it showed in the last picture/attachment I showed. I'm a happy man now. :)


**EDIT: **Cant seem to SOLVE my own thread via Thread Tools.

---

### Post by oldfred on 2013-03-06
They are downloading as a tar file now. I had to go into Downloads click on the file & extract.

Then I ran this>
```
fred@A105-Precise:~$ cd Downloads
fred@A105-Precise:~/Downloads$ ls boo*
bootinfoscript           boot_info_script060.zip    boot_info_script.sh
boot_info_script055a.sh  bootinfoscript-061.tar.gz
fred@A105-Precise:~/Downloads$ sudo bash bootinfoscript
[sudo] password for fred: 

Boot Info Script 0.61      [1 April 2012]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/mnt/data/Downloads/".

```

See my signature for temporary workaround on Solved threads.

---

### Post by Hodevah on 2013-03-07
```
user@user-Aspire-5749 ~/Downloads/bootinfoscript-061 $ sudo bash bootinfoscript

Boot Info Script 0.61      [1 April 2012]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sda11 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/user/Downloads/bootinfoscript-061/".

user@user-Aspire-5749 ~/Downloads/bootinfoscript-061 $ 

ok. I got it. Here are the results.

I cannot seem to get the Results.txt file uploaded as an attachment to this post. There is always a 'red' icon suggesting it is not able to upload.  It is only 23 Kb in size. Very small. Nevertheless, sorry but I am going to have to submit a copy/paste of it. 

                Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /BOOT/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 14 Nadia
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Peppermint Three
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden NTFS (Recovery Environment)
/dev/sda2          31,459,328    31,678,463       219,136  17 Hidden NTFS / HPFS
/dev/sda3    *     31,680,180   347,100,389   315,420,210   7 NTFS / exFAT / HPFS
/dev/sda4         347,100,451 1,250,258,624   903,158,174   f W95 Extended (LBA)
/dev/sda5         347,100,453   491,283,764   144,183,312   b W95 FAT32
/dev/sda6         491,283,828   655,066,439   163,782,612   7 NTFS / exFAT / HPFS
/dev/sda7         655,066,503   878,853,003   223,786,501   7 NTFS / exFAT / HPFS
/dev/sda8       1,232,876,358 1,250,258,624    17,382,267  82 Linux swap / Solaris
/dev/sda9         878,854,144 1,023,333,351   144,479,208  83 Linux
/dev/sda10      1,023,334,400 1,143,601,151   120,266,752  83 Linux
/dev/sda11      1,143,603,200 1,232,875,519    89,272,320  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D6A0AB35A0AB1B4F                       ntfs       PQSERVICE
/dev/sda10       aa3df309-dbbb-48db-9d75-a90905d9c6fc   ext4       
/dev/sda11       795b204b-4acc-471d-8cc8-26791a9e9836   ext4       
/dev/sda2        5A68AC2568AC023D                       ntfs       SYSTEM RESERVED
/dev/sda3        AAFECB00FECAC3B3                       ntfs       C.Drive.Win.7
/dev/sda5        01CBE1926F41FE8B                       ntfs       Drive D_DATA
/dev/sda6        01CD0E0523824E20                       ntfs       Back Up HDD
/dev/sda7        01CDE83A17DFC2E0                       ntfs       Media Drive(F:)
/dev/sda8                                               swap       
/dev/sda9        79276E34487ACD31                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /                        ext4       (rw,errors=remount-ro)


========================== sda10/boot/grub/grub.cfg: ===========================

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

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos10'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  aa3df309-dbbb-48db-9d75-a90905d9c6fc
else
  search --no-floppy --fs-uuid --set=root aa3df309-dbbb-48db-9d75-a90905d9c6fc
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
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
if background_color 0,0,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'LinuxMint' --class linuxmint --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-aa3df309-dbbb-48db-9d75-a90905d9c6fc' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos10'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  aa3df309-dbbb-48db-9d75-a90905d9c6fc
    else
      search --no-floppy --fs-uuid --set=root aa3df309-dbbb-48db-9d75-a90905d9c6fc
    fi
    linux    /boot/vmlinuz-3.5.0-25-generic root=UUID=aa3df309-dbbb-48db-9d75-a90905d9c6fc ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-25-generic
}
submenu 'Advanced options for LinuxMint' $menuentry_id_option 'gnulinux-advanced-aa3df309-dbbb-48db-9d75-a90905d9c6fc' {
    menuentry 'LinuxMint, with Linux 3.5.0-25-generic' --class linuxmint --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-25-generic-advanced-aa3df309-dbbb-48db-9d75-a90905d9c6fc' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos10'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  aa3df309-dbbb-48db-9d75-a90905d9c6fc
        else
          search --no-floppy --fs-uuid --set=root aa3df309-dbbb-48db-9d75-a90905d9c6fc
        fi
        echo    'Loading Linux 3.5.0-25-generic ...'
        linux    /boot/vmlinuz-3.5.0-25-generic root=UUID=aa3df309-dbbb-48db-9d75-a90905d9c6fc ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-25-generic
    }
    menuentry 'LinuxMint, with Linux 3.5.0-25-generic (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-25-generic-recovery-aa3df309-dbbb-48db-9d75-a90905d9c6fc' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos10'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  aa3df309-dbbb-48db-9d75-a90905d9c6fc
        else
          search --no-floppy --fs-uuid --set=root aa3df309-dbbb-48db-9d75-a90905d9c6fc
        fi
        echo    'Loading Linux 3.5.0-25-generic ...'
        linux    /boot/vmlinuz-3.5.0-25-generic root=UUID=aa3df309-dbbb-48db-9d75-a90905d9c6fc ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-25-generic
    }
    menuentry 'LinuxMint, with Linux 3.5.0-17-generic' --class linuxmint --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-aa3df309-dbbb-48db-9d75-a90905d9c6fc' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos10'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  aa3df309-dbbb-48db-9d75-a90905d9c6fc
        else
          search --no-floppy --fs-uuid --set=root aa3df309-dbbb-48db-9d75-a90905d9c6fc
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=aa3df309-dbbb-48db-9d75-a90905d9c6fc ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'LinuxMint, with Linux 3.5.0-17-generic (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-aa3df309-dbbb-48db-9d75-a90905d9c6fc' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos10'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  aa3df309-dbbb-48db-9d75-a90905d9c6fc
        else
          search --no-floppy --fs-uuid --set=root aa3df309-dbbb-48db-9d75-a90905d9c6fc
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=aa3df309-dbbb-48db-9d75-a90905d9c6fc ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-D6A0AB35A0AB1B4F' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  D6A0AB35A0AB1B4F
    else
      search --no-floppy --fs-uuid --set=root D6A0AB35A0AB1B4F
    fi
    chainloader +1
}
menuentry 'Peppermint Three (3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-795b204b-4acc-471d-8cc8-26791a9e9836' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos11'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  795b204b-4acc-471d-8cc8-26791a9e9836
    else
      search --no-floppy --fs-uuid --set=root 795b204b-4acc-471d-8cc8-26791a9e9836
    fi
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=795b204b-4acc-471d-8cc8-26791a9e9836 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-23-generic
}
submenu 'Advanced options for Peppermint Three (3)' $menuentry_id_option 'osprober-gnulinux-advanced-795b204b-4acc-471d-8cc8-26791a9e9836' {
    menuentry 'Peppermint, with Linux 3.2.0-23-generic (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-generic--795b204b-4acc-471d-8cc8-26791a9e9836' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos11'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  795b204b-4acc-471d-8cc8-26791a9e9836
        else
          search --no-floppy --fs-uuid --set=root 795b204b-4acc-471d-8cc8-26791a9e9836
        fi
        linux /boot/vmlinuz-3.2.0-23-generic root=UUID=795b204b-4acc-471d-8cc8-26791a9e9836 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-23-generic
    }
    menuentry 'Peppermint, with Linux 3.2.0-23-generic (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-generic-root=UUID=795b204b-4acc-471d-8cc8-26791a9e9836 ro recovery nomodeset-795b204b-4acc-471d-8cc8-26791a9e9836' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos11'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  795b204b-4acc-471d-8cc8-26791a9e9836
        else
          search --no-floppy --fs-uuid --set=root 795b204b-4acc-471d-8cc8-26791a9e9836
        fi
        linux /boot/vmlinuz-3.2.0-23-generic root=UUID=795b204b-4acc-471d-8cc8-26791a9e9836 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-23-generic
    }
}

menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-5A68AC2568AC023D' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  5A68AC2568AC023D
    else
      search --no-floppy --fs-uuid --set=root 5A68AC2568AC023D
    fi
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-AAFECB00FECAC3B3' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  AAFECB00FECAC3B3
    else
      search --no-floppy --fs-uuid --set=root AAFECB00FECAC3B3
    fi
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb11 during installation
UUID=aa3df309-dbbb-48db-9d75-a90905d9c6fc /               ext4    errors=remount-ro 0       1
/dev/sdb9       none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sda10/boot/extlinux/extlinux.conf: ======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 536.704544067 = 576.282116096  boot/grub/grub.cfg                             1
 488.265617371 = 524.271214592  boot/initrd.img-3.5.0-17-generic               3
 488.796890259 = 524.841664512  boot/initrd.img-3.5.0-25-generic               2
 528.097618103 = 567.040499712  boot/vmlinuz-3.5.0-17-generic                  1
 488.316310883 = 524.325646336  boot/vmlinuz-3.5.0-25-generic                  1
 488.796890259 = 524.841664512  initrd.img                                     2
 488.796890259 = 524.841664512  initrd.img.old                                 2
 488.316310883 = 524.325646336  vmlinuz                                        1
 488.316310883 = 524.325646336  vmlinuz.old                                    1

================= sda10: Location of files loaded by Syslinux: =================

           GiB - GB             File                                 Fragment(s)

 544.090969086 = 584.213229568  boot/extlinux/chain.c32                        1
 528.100025177 = 567.043084288  boot/extlinux/extlinux.conf                    1

============== sda10: Version of COM32(R) files used by Syslinux: ==============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

========================== sda11/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set=root 795b204b-4acc-471d-8cc8-26791a9e9836
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos11)'
  search --no-floppy --fs-uuid --set=root 795b204b-4acc-471d-8cc8-26791a9e9836
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
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Peppermint, with Linux 3.2.0-23-generic' --class peppermint --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 795b204b-4acc-471d-8cc8-26791a9e9836
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=795b204b-4acc-471d-8cc8-26791a9e9836 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Peppermint, with Linux 3.2.0-23-generic (recovery mode)' --class peppermint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 795b204b-4acc-471d-8cc8-26791a9e9836
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=795b204b-4acc-471d-8cc8-26791a9e9836 ro recovery nomodeset 
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
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 795b204b-4acc-471d-8cc8-26791a9e9836
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 795b204b-4acc-471d-8cc8-26791a9e9836
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root D6A0AB35A0AB1B4F
    chainloader +1
}
menuentry "LinuxMint' --class linuxmint --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-aa3df309-dbbb-48db-9d75-a90905d9c6fc (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root aa3df309-dbbb-48db-9d75-a90905d9c6fc
    linux /boot/vmlinuz-3.5.0-25-generic root=UUID=aa3df309-dbbb-48db-9d75-a90905d9c6fc ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-25-generic
}
menuentry "LinuxMint, with Linux 3.5.0-25-generic' --class linuxmint --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-25-generic-advanced-aa3df309-dbbb-48db-9d75-a90905d9c6fc (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root aa3df309-dbbb-48db-9d75-a90905d9c6fc
    linux /boot/vmlinuz-3.5.0-25-generic root=UUID=aa3df309-dbbb-48db-9d75-a90905d9c6fc ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-25-generic
}
menuentry "LinuxMint, with Linux 3.5.0-25-generic (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-25-generic-recovery-aa3df309-dbbb-48db-9d75-a90905d9c6fc (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root aa3df309-dbbb-48db-9d75-a90905d9c6fc
    linux /boot/vmlinuz-3.5.0-25-generic root=UUID=aa3df309-dbbb-48db-9d75-a90905d9c6fc ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-25-generic
}
menuentry "LinuxMint, with Linux 3.5.0-17-generic' --class linuxmint --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-aa3df309-dbbb-48db-9d75-a90905d9c6fc (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root aa3df309-dbbb-48db-9d75-a90905d9c6fc
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=aa3df309-dbbb-48db-9d75-a90905d9c6fc ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "LinuxMint, with Linux 3.5.0-17-generic (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-aa3df309-dbbb-48db-9d75-a90905d9c6fc (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root aa3df309-dbbb-48db-9d75-a90905d9c6fc
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=aa3df309-dbbb-48db-9d75-a90905d9c6fc ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 5A68AC2568AC023D
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root AAFECB00FECAC3B3
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

=============================== sda11/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=795b204b-4acc-471d-8cc8-26791a9e9836 /               ext4    errors=remount-ro 0       1
/dev/sda8       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 549.445465088 = 589.962575872  boot/grub/core.img                             1
 555.516605377 = 596.481413120  boot/grub/grub.cfg                             1
 545.981956482 = 586.243661824  boot/initrd.img-3.2.0-23-generic               1
 547.446033478 = 587.815702528  boot/vmlinuz-3.2.0-23-generic                  1
 545.981956482 = 586.243661824  initrd.img                                     1
 547.446033478 = 587.815702528  vmlinuz                                        1
```

---

### Post by oldfred on 2013-03-07
How did you copy it? Without line endings it is not readable? Copy & repaste again.
I sometimes have to copy to gedit or another edit and then copy here as line endings are not correct.

---

### Post by Hodevah on 2013-03-07
Is the above copy/paste better? Please have a look. I copy/pasted originally in Libre Office. Hence the obscure results. Changed it to be opened by Kate. It is a bit more readable now, I think.
The results are after having re-set the Grub through the live USB, of course.

---

### Post by oldfred on 2013-03-07
Changed a /QUOTE to /CODE to get it all in code tags.

If it boots it must be an issue with script as the MBR says partition 72. I have seen that before and some versions of grub must not parse correctly?

Very minor point - some of your labels have spaces. I stopped using spaces when I converted to Linux as if you later want to use the labels to mount partitions or other uses you have to add quotes or escape the space to get it seen correctly. I now use CamelCase or under_score or justonelongname, up to length allowed.

---

### Post by Hodevah on 2013-03-07
Hi oldfred. Ok. So you mention, and I noticed this too on the output results text, what is necessary to having the MBR on partition 72 fixed or altered ( if possible, that is and also if it is necesary) to have this issue fixed?
 I guess I should be asking this question because I am thinking of installing Fedora or OpenSuse at some point in the future and would like to ensure that this problem is resolved. Right now, it is resolved albiet by having used the Boot repair through the Ubuntu Live CD. This fixed the problem. However, as I had Grub-customizer installed in Peppermint as well (uninstalled it as I didnt deem it necessary to have 2 insalls of same program). In having said that last bit, I still saw that  grub-customizer (before uninstall) still showed the 'wacked-up" display of Grub within Peppermint. 

So to prevent any future occurances of this occuring again, how to resolve, please?

Secondly, you mentioned that having labels for some of the NTFS drives. 
Are you saying that with some of the labels on the drives:

> 
C.Drive.Win.7
 Media Drive 

I should/might/ re-label them as such for example:
> C_Drive_Win.7
 Drive_D_DATA
 Back_Up_HDD
 Media_Drive

or even place quotes on the labels?

I just want to ensure that I understand you correctly so that I can go and make necessary corrections based on your experience and/or knowledge. 
Thanks again for your response. :)

---

### Post by oldfred on 2013-03-07
Do not use quotes, that may confuse it more. But underscores or just leaving out spaces is fine. I find I can use Disk Utility about the easiest to edit labels.

I think it is a boot script (and grub?) issue on displaying the correct info. If you can boot then it is not an install issue.

---

### Post by Hodevah on 2013-03-07
Ok. Great. :D  At least one of 2 questions answered. So with it being a boot *(and possibly a Grub)* script, what can I do to enable a correction, then?

 I can boot into either of the 3 operating systems just fine. So therefore, per your knowledge *(and I think I do agree with you)* that it is not an install issue of Peppermint. Or of either OS for that matter.

---

### Post by oldfred on 2013-03-07
If you can boot then it has to be ok, grub would not be booting if it really was looking at partition 72. Not sure why script sees that. Grub keeps changing and script has to keep up, but then newest version may not parse the same as the old version.

---

### Post by Hodevah on 2013-03-07
It seems to me that every time Peppermint has an update ( like just recently) that the Grub is reconfigured to its 'wacked-out' state. Having to go and do a Boot-repair each time is a bit of a hassle. So I was thinking, would a simple copy/paste of Grub from Mint to Peppermint (* after backing up Grub from Peppermint*) have some kind of a permanent effect so that I dont have to go and renew Grub each and every time there is a Peppermint update? They both use Grub2.

---

### Post by oldfred on 2013-03-08
I have so many Ubuntu installs from testing and then adding another 25GB partition for another test and never housecleaning that I do it almost all manually. And I have flash drives that I totally maintain manual grub configurations that boot the installs I most use.

I turn-off os-prober and add only the entries I want in 40_custom. Debian based distributions put a link to the most current kernel into / (root).

 #Add menu entry to 40_custom, change example from sda13 to your partition.
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu
sudo update-grub
sudo dpkg-reconfigure grub-pc

   I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

You may want to turn off the writing of grub in your other install also. If you uncheck all drives & partitions it does not reinstall anywhere.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

