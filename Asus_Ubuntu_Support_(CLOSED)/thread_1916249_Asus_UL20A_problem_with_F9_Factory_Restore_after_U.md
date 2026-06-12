---
title: "Asus UL20A problem with F9 Factory Restore after Ubuntu  installation"
date: 2012-01-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dsurfer21 on 2012-01-27
Hi Everyone,

I am having an issue with an Asus UL20A notebook.  I got this notebook 2 years ago and it came with Windows 7 Home premium installed and a hidden partition for recovery.  It did not come with any factory restore DVD or a DVD drive.

After installing Ubuntu in Windows 7 using Wubi, I can no longer access the factory restore option when I boot my laptop up and when I press F9 continuously.  The F9 key should allow for accessing a menu to restore to factory settings.  I need to reformat my machine due to a bad virus I had gotten in my Windows 7 setup.

Is there anything I can do at this point?  It seems like my ubuntu installation removed that F9 capability.

One option is to use AI recovery to create a bunch of DVD disks but I prefer not to.  I would like to restore with the F9 option.  If I can't do that, I will download a copy of the Windows 7 Home Premium ISO and use my activation key that came with my machine and a USB boot program like BartPE.  Also, if I can't use the F9 option to restore in the future, I might as well format the recovery partition and use that space for my c:

Any suggestions would be greatly appreciated.  Thanks.

---

### Post by cbanakis on 2012-01-27
Might not be anything you can do at this point.

But don't take my word for it.

I'm no expert.

Is the recovery partition still there?
Or did you delete it when you installed ubuntu?

If its still there, then there may be a way to fix it.

Otherwise, for all practical intents and purposes, its gone.

You can reformat using your product ID, but you need to make sure the windows disk you obtain matches up with the key.

Getting Windows 7 Home Premium is not enough to ensure your key will work.

There are at least 4 different versions of Windows 7 Home Premium.

Retail 32bit
Retail 64bit
OEM 64bit
OEM 32bit

Your key is probably for (Windows7 Home Premium 32bit OEM)

So your key will only work if you get that disk.

---

### Post by bcbc on 2012-01-27
Wubi can't do that. You need to go into the BIOS and change it to bypass quick/express boot (I forget the exact details), but it bypasses the bit where you hit F9 or whatever the restore key is.

---

### Post by dsurfer21 on 2012-01-27
Thanks,  in Bios I made sure that Quick Boot was disabled.  That seems to be the only setting in the BIOS section that would be relevant.

I press F9 and nothing really happens, it goes to the Windows Boot Manager menu and I see the two options,  the first being Windows Home Premium and the second one being Ubuntu.

I have not formatted the recovery partition or modified it.  It is still intact and hidden.  
I'm hoping there is a manual fix for having the F9 factory restore enabled but it doesn't seem likely.

---

### Post by bcbc on 2012-01-28
Is there any chance you replaced the boot loader? i.e. ran a boot-repair, or installed the normal windows bootloader? Some OEM computers have a custom bootloader that traps the F9 key and does something special.

Make sure you're hitting F9 when the bios splash is shown. Also you could try to see if grub picked up the recovery partition and boot it that way.

If all that fails you may have to get a restore disk from the manufacturer, but that'll likely cost something. 
If you decide to reinstall Windows from scratch make sure you have a separate drivers CD from Asus or you'll likely have problems getting all your hardware working.

Edit: searching the web shows many people have problems with Asus and F9 recovery. Here's a post that seems to have a lot of information and the user finally got it working. Might have some hints for things you haven't tried: [http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+1000HE&id=20090916031334484&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+1000HE&id=20090916031334484&page=1&SLanguage=en-us)

e.g. it mentions quiet boot as well as boot booster should be disabled.

---

### Post by dsurfer21 on 2012-01-28
Hey bcbc.  Thanks so much for the advice.  I have tried hitting F9 in many different times, starting from the second I turn power on.  I'm pretty sure the OEM bootloader is no longer in existence, either from when I installed Ubuntu or perhaps when I used BCDedit long ago to fix a Wubldr issue when I tried to select Ubuntu from the boot menu.   I'm not sure how to check if grub picked up the recovery partition?  From the Ubuntu menu I see a couple options, three of them are ubuntu and one of them says ubuntu recovery mode.  The factore restore dvd costs $50.  I think its lame to have to buy something they should have provided.  They did however provide the drivers CD.  I will check the link you pasted.  Thanks so much for your help!

---

### Post by bcbc on 2012-01-28
Neither installing wubi or running bcdedit can affect your bootloader. The only way to do that would be to install a bootloader such as grub, windows, lilo. i.e. running "grub-install", "fixboot /mbr", or "lilo".

The current version of wubi-installed Ubuntu suppresses windows entries in grub. So that's why you don't see anything there. You could edit */etc/grub.d/30_os-prober* to remove this - comment the line shown in bold:

```
      case ${LONGNAME} in
	Windows*)
	  if [ -z "$wubi" ]; then
	    if [ -x /usr/share/lupin-support/grub-mkimage ] && \
	       /usr/share/lupin-support/grub-mkimage --test; then
	      wubi=yes
	    else
	      wubi=no
	    fi
	  fi
	  if [ "$wubi" = yes ]; then
	    echo "Skipping ${LONGNAME} on Wubi system" >&2
**#	    continue**
	  fi

```

To edit use this command:
```
cd /etc/grub.d
sudo cp 30_os-prober 30_os-proberBACKUP
gksu gedit 30_os-prober
sudo update-grub
```

Make sure there are no errors - otherwise restore the backup:
```
sudo cp 30_os-proberBACKUP 30_os-prober
sudo update-grub
```

To check look for the entry in grub.cfg:
```
less /boot/grub/grub.cfg
```

You'll see something like:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos2)'
        search --no-floppy --fs-uuid --set=root CAB28E67B28E5839
        chainloader +1
}
```

Hopefully you'll see two entries (one for recovery). However, it depends whether grub recognizes your recovery partition as bootable.

---

### Post by dsurfer21 on 2012-01-28
Hi bcbc,
Thanks again!  
When I ran the gksu gedit 30_os-prober command I see the following in the gedit window.. I'm not sure what I need to edit?




#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib

. ${libdir}/grub/grub-mkconfig_lib

found_other_os=

make_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${1}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
    verbose=
      else
    verbose=" --verbose"
      fi

      if [ "x${1}" = "x0" ] ; then
    cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
    cat << EOF
if [ "x\${timeout}" != "x-1" ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

adjust_timeout () {
  if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
    make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
    echo else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
    echo fi
  else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  adjust_timeout
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi

osx_entry() {
        cat << EOF
menuentry "${LONGNAME} (${2}-bit) (on ${DEVICE})" {
EOF
    save_default_entry | sed -e "s/^/\t/"
    prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
    cat << EOF
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ \$do_resume = 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
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
EOF
}

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  echo "Found ${LONGNAME} on ${DEVICE}" >&2
  found_other_os=1

  case ${BOOT} in
    chain)

      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
    Windows\ Vista*|Windows\ 7*)
    ;;
    *)
      cat << EOF
    drivemap -s (hd0) \${root}
EOF
    ;;
      esac

      cat <<EOF
    chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
      prepare_boot_cache=

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

    if [ "${LROOT}" != "${LBOOT}" ]; then
      LKERNEL="${LKERNEL#/boot}"
      LINITRD="${LINITRD#/boot}"
    fi

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" {
EOF
    save_default_entry | sed -e "s/^/\t/"
    if [ -z "${prepare_boot_cache}" ]; then
      prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
    fi
    printf '%s\n' "${prepare_boot_cache}"
    cat <<  EOF
    linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
    initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
      grub_device="`${grub_probe} --device ${DEVICE} --target=drive`"
      mach_device="`echo "${grub_device}" | tr -d '()' | tr , s`"
      grub_fs="`${grub_probe} --device ${DEVICE} --target=fs`"
      case "${grub_fs}" in
    *fs)    hurd_fs="${grub_fs}" ;;
    *)    hurd_fs="${grub_fs}fs" ;;
      esac
      cat << EOF
    multiboot /boot/gnumach.gz root=device:${mach_device}
    module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
            --multiboot-command-line='\${kernel-command-line}' \\
            --host-priv-port='\${host-port}' \\
            --device-master-port='\${device-port}' \\
            --exec-server-task='\${exec-task}' -T typed '\${root}' \\
            '\$(task-create)' '\$(task-resume)'
    module /lib/ld.so.1 exec /hurd/exec '\$(exec-task=task-create)'
}
EOF
    ;;
    *)
      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
    ;;
  esac
done

adjust_timeout

---

### Post by dsurfer21 on 2012-01-28
When I run Disk Management in Windows 7 I see the following:

RECOVERY
14.65 GB NTFS
Healthy (System, Active, Primary Partition)

OS (C: )
58.22 GB NTFS
Healthy (Boot, Page File, Crash Dump, Pimary Partition)

DATA (D: )
160.02 GB NTFS
Healthy (Logical Drive)


Are the above settings correct for each drive?

Thanks.

---

### Post by bcbc on 2012-01-28
> **dsurfer21 said:**
> Hi bcbc,
Thanks again!  
When I ran the gksu gedit 30_os-prober command I see the following in the gedit window.. I'm not sure what I need to edit?



Sorry I should have checked before - you're not running 11.10 I guess.

So whatever you see in the grub menu is it. Do you see the recovery partition? What happens if you boot it? (PS backup before doing that)

---

### Post by dsurfer21 on 2012-01-29
Hi bcbc,
Thanks!

When I start up I see the windows boot manager menu and it shows Windows Home Premium or Ubuntu.  If I select Ubuntu, it shows two versions of Linux, then recovery mode for linux, then another two versions of Linux, and then recovery mode for linux.

I had tried each option and none of them start the factory restore option.  I am not sure how to boot the recovery partition.

---

### Post by bcbc on 2012-01-29
Can you post your grub.cfg please? Also your /etc/default/grub file. Thanks

---

### Post by dsurfer21 on 2012-01-29
Hi bcbc,

here is the /etc/default/grub file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

GRUB_CMDLINE_LINUX_DEFAULT="rootflags=umask=002,uid=1000,gid=1000 quiet splash"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



Here is the /boot/grub/grub.cfg file:






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
}

insmod part_msdos
insmod ntfs
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-32-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-32-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  rootflags=umask=002,uid=1000,gid=1000 quiet splash
    initrd /boot/initrd.img-2.6.35-32-generic
}
menuentry "Ubuntu, Linux 2.6.35-32-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-32-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.35-32-generic
}
menuentry "Ubuntu, Linux 2.6.35-31-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-31-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  rootflags=umask=002,uid=1000,gid=1000 quiet splash
    initrd /boot/initrd.img-2.6.35-31-generic
}
menuentry "Ubuntu, Linux 2.6.35-31-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-31-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.35-31-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  rootflags=umask=002,uid=1000,gid=1000 quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-27-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  rootflags=umask=002,uid=1000,gid=1000 quiet splash
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, Linux 2.6.35-27-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  rootflags=umask=002,uid=1000,gid=1000 quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set EC60A75C60A72BF0
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 3C76B1C676B18166
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

---

### Post by bcbc on 2012-01-29
So you should see an entry for "Windows 7 (loader) (on /dev/sda1)" in your grub menu. It's there and it's pointing at your recovery partition. If you're not seeing it... maybe something is corrupted. But it should be at the bottom of the grub menu.

You could try to boot it manually if you can't see it:
1. Boot
2. Select Ubuntu
3. Hit 'C' when you see the grub menu.
4. Enter the following at the command prompt:
```
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
chainloader +1
boot
```

That should boot your recovery partition. What happens after that? If your recovery is successful you won't have Wubi anymore. So backup the contents of /host/ubuntu/disks (i.e. root.disk and other virtual disks if you have any).

Good luck.

---

### Post by dsurfer21 on 2012-01-29
Hi bcbc,

When I follow your instructions and get to the command line and run the following:

insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'

and then try chainloader +1 it says no such partition.


if I try this:

insmod part_msdos
insmod ntfs
set root=`(hd0,msdos1)'
chainloader +1

I get a > and blinking cursor (before the chainloader +1 command the I would see grub> and a blinking cursor).

Then when I type boot and hit enter, I just get another > and blinking cursor and nothing happens.

The difference between the first and second try is that I used ` and '  before/after the (hd0,msdos1) in my second try.  I'm not sure which is the right way.

Thanks!!

---

### Post by bcbc on 2012-01-29
Try:
set root=(hd0,1)

No quotes and that's a zero and a one

---

### Post by dsurfer21 on 2012-01-29
hi bcbc thanks!

I tried that and it takes me back to the Windows Boot Menu where I can select Windows 7 Home Premium or Ubuntu.  There is no option for factory recovery.

I logged back in to the grub command prompt and did ls and saw the following:

loop(0)  (hd0)  (hd0,2)  (hd0,5)  (hd0,1)

not sure if they were in that exact order.

I tried the commands you suggested and tried each of those except for loop(0).  The hd0,5 does nothing and the rest take me back to the Windows Boot Menu.

Do you think there is any issue with the configuration of my disks?  These are the settings in Windows 7 when I run disk management.   




RECOVERY
14.65 GB NTFS
Healthy (System, Active, Primary Partition)

OS (C: )
58.22 GB NTFS
Healthy (Boot, Page File, Crash Dump, Pimary Partition)

DATA (D: )
160.02 GB NTFS
Healthy (Logical Drive)

---

### Post by bcbc on 2012-01-29
I suppose you've true hitting the F8 key as windows boots to get the extended boot menu?

I'm running out of ideas.

---

### Post by dsurfer21 on 2012-01-29
hi bcbc thanks,

Yes I have hit F8 to get the extended windows boot menu to see all the different options (like Safe Mode... etc) but no where in there does it show factory restore.

I don't have any other ideas other than to just format that recovery partition and add 15GB more to my C: so I have more space on it.

---

### Post by dsurfer21 on 2012-01-30
Hi bcbc,

any other hints or things i should try before I give up?

thanks..

---

### Post by bcbc on 2012-01-30
Why don't you post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). This will give some more info on your partitions and maybe show what bootloader you have (it will most likely be unknown if it's the custom Asus one).

I wouldn't give up just yet. If you can still boot Windows, is there an Asus program that will allow you to kick of the recovery from within Windows and then reboot to complete?

---

### Post by dsurfer21 on 2012-01-30
Hi bcbc thanks,

There are no asus tools for restoring other than perhaps using something like AI recovery and making a whole bunch of DVDs.  I was hoping to get around that as I don't have a DVD drive in my UL20a 12 inch notebook


Here are the results of the bootinfoscript:


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    30,716,279    30,714,232   7 NTFS / exFAT / HPFS
/dev/sda2          30,716,280   152,810,279   122,094,000   7 NTFS / exFAT / HPFS
/dev/sda3         152,810,280   488,392,064   335,581,785   f W95 Extended (LBA)
/dev/sda5         152,810,343   488,392,064   335,581,722   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       c4e73368-ce25-498f-9887-aa63ea4b8dc6   ext4       
/dev/sda1        EC60A75C60A72BF0                       ntfs       RECOVERY
/dev/sda2        3C76B1C676B18166                       ntfs       OS
/dev/sda5        27C001CAA8B90A8D                       ntfs       DATA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096)


======================== sda5/Wubi/boot/grub/grub.cfg: =========================

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
}

insmod part_msdos
insmod ntfs
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-32-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-32-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  rootflags=umask=002,uid=1000,gid=1000 quiet splash
    initrd /boot/initrd.img-2.6.35-32-generic
}
menuentry "Ubuntu, Linux 2.6.35-32-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-32-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.35-32-generic
}
menuentry "Ubuntu, Linux 2.6.35-31-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-31-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  rootflags=umask=002,uid=1000,gid=1000 quiet splash
    initrd /boot/initrd.img-2.6.35-31-generic
}
menuentry "Ubuntu, Linux 2.6.35-31-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-31-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.35-31-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  rootflags=umask=002,uid=1000,gid=1000 quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-27-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  rootflags=umask=002,uid=1000,gid=1000 quiet splash
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, Linux 2.6.35-27-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-27-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  rootflags=umask=002,uid=1000,gid=1000 quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 27C001CAA8B90A8D
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=27C001CAA8B90A8D loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set EC60A75C60A72BF0
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 3C76B1C676B18166
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

============================= sda5/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda5/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   3.226070404 = 3.463966720    boot/grub/grub.cfg                             1
   2.101917267 = 2.256916480    boot/initrd.img-2.6.32-26-generic              2
   3.945312500 = 4.236247040    boot/initrd.img-2.6.35-27-generic              2
   5.203125000 = 5.586812928    boot/initrd.img-2.6.35-28-generic              2
   3.909111023 = 4.197376000    boot/initrd.img-2.6.35-31-generic              2
   5.264095306 = 5.652279296    boot/initrd.img-2.6.35-32-generic              2
   3.038982391 = 3.263082496    boot/vmlinuz-2.6.32-26-generic                 1
   3.585330963 = 3.849719808    boot/vmlinuz-2.6.35-27-generic                 1
   3.897972107 = 4.185415680    boot/vmlinuz-2.6.35-28-generic                 1
   4.937358856 = 5.301448704    boot/vmlinuz-2.6.35-31-generic                 1
   4.080932617 = 4.381868032    boot/vmlinuz-2.6.35-32-generic                 1
   5.264095306 = 5.652279296    initrd.img                                     2
   3.909111023 = 4.197376000    initrd.img.old                                 2
   4.080932617 = 4.381868032    vmlinuz                                        1
   4.937358856 = 5.301448704    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 10 20 00  |.X.FRDOS4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 28 b3 1b 09  |........?...(...|
00000020  3b 8b 38 01 08 27 00 00  00 00 00 00 12 05 00 00  |;.8..'..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f2 2c 9e 58 4e  4f 20 4e 41 4d 45 20 20  |..).,.XNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 00 fe  |@.^.s........_..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 1a 92 00 14 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by bcbc on 2012-01-30
So you have a normal Windows bootloader. So it doesn't look like it's a custom bootloader issue (since you don't recall replacing it). 

And the boot flag is on the recovery partition (/dev/sda1) so booting it from Ubuntu makes no difference.

But you did mention that you can boot Windows, and there is an option to burn recovery DVD's from within Windows. Have you tried this option?
> Creating the Recovery DVD:
1. Double-click the AI Recovery Burner icon on the Window desktop.

---

### Post by dsurfer21 on 2012-01-30
Hi bcbc thanks,

It seems like that is the last resort option using the AI recovery,

I would need to get a DVD drive and DVDs so I have not tried this yet.  I do have AI recovery though.
Given what showed up on the bootinfoscript,  you think this is probably the last option I have?

If there was some way to restore the OEM bootloader, I could see a solution but that doesn't seem at all possible without using AI recovery and making the DVDs.

---

### Post by bcbc on 2012-01-30
> **dsurfer21 said:**
> Hi bcbc thanks,

It seems like that is the last resort option using the AI recovery,

I would need to get a DVD drive and DVDs so I have not tried this yet.  I do have AI recovery though.
Given what showed up on the bootinfoscript,  you think this is probably the last option I have?

If there was some way to restore the OEM bootloader, I could see a solution but that doesn't seem at all possible without using AI recovery and making the DVDs.

Well the problem is that it's not clear whether there is in fact an OEM bootloader - you stated that you hadn't replaced the bootloader and since this cannot happen by installing Wubi or running bcdedit (or by accident) etc. I would have to assume that there is no OEM bootloader.
In order to install a Window bootloader you need to actually boot a windows repair CD (or copy from a backed up Windows bootloader). Neither of which you could forget.

So I would say this is more likely some deficiency in the Asus factory restore procedure - but where I cannot say. Perhaps it's the interruption of the windows boot manager... this is all speculation because unless Asus publishes the mechanism it is using all we can do is guess.

If you want to experiment you could go to "Startup & Recovery" settings, change the 'time to display operating systems' to zero. (Double check to make sure that Windows is set as the default OS to boot in this case, or you won't boot Windows again without a repair CD). 
Also make sure the 'time to display recovery options when needed' is checked
Then retry the whole F9 thing.

If that doesn't work, then yes the AI recovery tool seems the most convenient. But the F9 recovery is obviously better than having to pay for an external DVD drive.

The other thing you could do is phone Asus and see if they have some tips. The recovery partition is there, it's just a question of how to get it to run.

---

### Post by dsurfer21 on 2012-01-30
Hi bcbc thanks!
I tried your startup and recovery suggestions and f9 and did not get to any factory restore menu.

I had sent Asus an email and never heard back.  I doubt I will get any support since my machine is a year and a 3/4 old.  

Any last suggestions?  A while ago I had created a system image onto an external flash drive and also a system restore CD.  I'm not sure if that is enough to format a hard drive and reinstall everything without the F9 option or buying a DVD drive.

I'm wondering if I should just format the recovery partition and use the space for something else given the backup I made?  Any advice?

---

### Post by bcbc on 2012-01-31
> **dsurfer21 said:**
> Hi bcbc thanks!
I tried your startup and recovery suggestions and f9 and did not get to any factory restore menu.

I had sent Asus an email and never heard back.  I doubt I will get any support since my machine is a year and a 3/4 old.  

Any last suggestions?  A while ago I had created a system image onto an external flash drive and also a system restore CD.  I'm not sure if that is enough to format a hard drive and reinstall everything without the F9 option or buying a DVD drive.

I'm wondering if I should just format the recovery partition and use the space for something else given the backup I made?  Any advice?
My advice is to leave it. You had a problem with Windows so you wanted to restore. Removing the partition isn't going to help that, plus it's your active boot partition - so odds are it will break your boot (which while probably fixable isn't so easy without a suitable rescue disk). 

Also, you can still create the restore DVD's which likely require that partition (just a guess, but I'd say they transfer the boot partition contents to 3 DVDs and add the code to boot from it and restore.

So, my advice is definitely - don't mess with the recovery partition. Create the recover DVDs when you get the chance, and also create a bootable USB that contains the Windows 7 repair CD.

---

### Post by cbanakis on 2012-02-08
This is a strange situation, because I too have an Asus.

And somehow, the F9 to restore option is still listed when by BIOS posts.

Except not only do I not have the recovery partition, but I don't even have the original hard drive.

I assume pressing F9 to recover on my system will undoubtedly fail if I were to try it.

But its strange that I still have the option, when I don't even have the original hard drive, and you still have the partition intact, but your missing the F9 option.

---

### Post by malekims on 2012-12-18
I have the same problem with Asus Eeepc 1005HA.

After a few trial and error to make the Recovery partition work (as before), I realized that pressing F9 key makes the Recovery partition Active, to boot from that partition.

If boot sector of that partition is changed somehow, it makes the Windows partition active again and boots from there, so it seems that nothing has happened. The same happens when recovery process from partition is intact and you exit the process normally. 

When you format that Windows partition, pressing F9 makes the Recovery patition Active and does not return back if it can not boot from Recovery partition.

This was my experience!

---

### Post by malekims on 2012-12-18
... So far I did a manual recovery using the the recovery image of the OS that is contained as a Norton Ghost file on the Recovery partition.

I am working to find out how I can revive the recovery process by F9 key.

---

### Post by germn2 on 2013-10-24
Hi, I'm new in the formun, I only had the the same problem, maybe a bit different. I have read all the post and reply locking for my solution.
 

Y installed Ubuntu 12.04 LTS in the mi asus k52f which comes with windows home premium OA.

Then my windows started to get bad and I decided to use de recovery partition with F9 but doesnt work, GRUB always started first.

But in my options of grub there was one to boot with the recovery partition. But when was starting my computer always failed and restart automatically, so I always couldn't restore it.

Then I stupidly decide to make de four DVDs with AI Burner (obviously y did the back of al my important data), y boot with those DVD, but after that my windows still the same. Then I realized that the back up was of my actual state of windows.

I was locking for solutions to this and I founded this [http://www.youtube.com/watch?v=u0iEDk6n23k](http://www.youtube.com/watch?v=u0iEDk6n23k)

But Then I decided to give one more oportunity to boot from GRUB in the restore partition, I thought that maybe the last stupid change fixed what was happennig (the failure and restart)
And Finaly Yes! It worked.

I used this option **Recover Windows to first partition only. **, and didnt make changes of ubuntu, only on windows partition, that was what i wanted.


**Conclusion:** Using the AI Recovery burner was not so stupid and finally coud start the recovery partition. Maybe isn't the solution to the problem of last year of [COLOR=#000000][FONT=verdana]**dsurfer21. **[/FONT][/COLOR]Because in his situation the partition didn't appear in the options. In my case the differnce was that it appeared but didnt work.

**One unique problem:**When I start the windows from Grub it throws one Error "No such device ............." I dont know why but then works fine, tipping any key. Maybe in the future will fix it some way. The owner of the notebook is my uncle, he was who wanted the recovery, if it was my decision i would have decide to format the partition and install windows and the drivers manually.

Spect to help someone.
Apologises about my english.
Good Lock!

---

