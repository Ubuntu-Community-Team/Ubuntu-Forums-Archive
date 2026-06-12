---
title: "How I finally get  Live CD on macbook pro hd to boot."
date: 2008-05-16
forum: Apple Hardware Users
---

### Post by a1234 on 2008-05-16
The reasons for this articles are:

1) To facilitate multiple re installation.
2) Hoping some one will build on this concept and   make Linux on mac fly ie come up with script for "persistentce" mode etc etc.!!

The theories behind this article are from multiple sources. I thank those even though I did not directly credit them. It will be self evident to those contributors when they read this. Thank you all of you that make Linux great and keep a [COLOR="Black"]noob[/COLOR] like me hanging on.

Let's get started with what you will need and the steps involved. 

A) Usb flash drive formatted MBR/ Fat 16 with Disk utility in OSX (usb1)

B) Get isotostick.sh from this site

[HTML]http://www.startx.ro/sugar/
[/HTML]
C) copy the 'heron' and the .sh to the usb flash (usb1)

D) we will need to install Linux on to mac first. JUST  A BOOT SECTOR.
    This is what I did:

  1) Plug in to mac another HD or usb.  NOT usb1
  2)  Fire up the CD as you will for Live use session.
  3) Use regular partition editor to create two partitions on your mac HD! 1G each.
  4) Proceed with the installation 1-3
  5) Choose "manual" for partitioning.

E) This following are very important points:
 
         [B]PLEASE READ AND FOLLOW CAREFULLY.
[/B]
Formatting to install ubuntu heron

1) On mac the end partition must be formatted to ext 2 and "/boot" as mount point
2) The rest of the essential partitions must be on the attached usb or HD,ie swamp & / partitions.
3) At the last step before install,choose 'Advance' and select the partition on you mac ie the ext 2 formatted /boot partition, where you will want your boot loader.

( If you intend to use the external drive as Linux then the boot loader must be on that drive. You can then install GRUB to the mac partition after the full installation. )

Proceed with full installation. Blah Blah Blah. Grab a bite if you are using a slow write speed usb flash.

F) When installation is done choose Live CD option instead of "restart".

G) Use partition editor to format the other mac partition as Fat 32 and flag it as 'boot'

H) Now plug in the Fat formatted usb1 and copy the iso image of heron and .sh to the desktop.

Since mac partition is GPT we need to alter the .sh script as followed.

The colored parts are what I have altered [COLOR="MediumTurquoise"]BLUE[/COLOR] for addition [COLOR="Red"]RED [/COLOR]for deletion.


----------------------------------------------------------------------------------------------------------------

Before the changes

----------------------------------------------------------------------------------------------------------------
#!/bin/bash
# Convert an Ubuntu live CD iso so that it's bootable off of a USB stick
# Copyright 2007  Red Hat, Inc.
# Jeremy Katz <katzj@redhat.com>
# Jani Monoses <jani@ubuntu.com> (slightly adapted to Ubuntu LiveCD)
# 
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; version 2 of the License.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU Library General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.


export PATH=/sbin:/usr/sbin:$PATH

usage() {
    echo "$0 [--reset-mbr] [--noverify] <isopath> <usbstick device>"
    exit 1
}

cleanup() {
    [ -d "$CDMNT" ] && umount $CDMNT && rmdir $CDMNT
    [ -d "$USBMNT" ] && umount $USBMNT && rmdir $USBMNT
}

exitclean() {
    echo "Cleaning up to exit..."
    cleanup
    exit 1
}

getdisk() {
    DEV=$1

    p=$(udevinfo -q path -n $DEV)
    if [ -e /sys/$p/device ]; then
	device=$(basename /sys/$p)
    else
	device=$(basename $(readlink -f /sys/$p/../))
    fi
    if [ ! -e /sys/block/$device -o ! -e /dev/$device ]; then
	echo "Error finding block device of $DEV.  Aborting!"
	exitclean
    fi

    device="/dev/$device"
}

resetMBR() {
    getdisk $1
    cat /usr/lib/syslinux/mbr.bin > $device
}

checkMBR() {
    getdisk $1

    bs=$(mktemp /tmp/bs.XXXXXX)
    dd if=$device of=$bs bs=512 count=1 2>/dev/null || exit 2
    
    mbrword=$(hexdump -n 2 $bs |head -n 1|awk {'print $2;'})
    rm -f $bs
    if [ "$mbrword" = "0000" ]; then
	echo "MBR appears to be blank."
	echo "Do you want to replace the MBR on this device?"
	echo "Press Enter to continue or ctrl-c to abort"
	read
	resetMBR $1
    fi

    return 0
}

[COLOR="Red"][I]checkPartActive() {
    dev=$1
    getdisk $dev
    
    # if we're installing to whole-disk and not a partition, then we 
    # don't need to worry about being active
    if [ "$dev" = "$device" ]; then
	return
    fi

    if [ "$(/sbin/fdisk -l $device 2>/dev/null |grep $dev |awk {'print $2;'})" != "*" ]; then
	echo "Partition isn't marked bootable!"
	echo "You can mark the partition as bootable with "
        echo "    # /sbin/parted $device"
	echo "    (parted) toggle N boot"
	echo "    (parted) quit"
	exitclean
    fi
}[/I]
[/COLOR]
checkFilesystem() {
    dev=$1

    USBFS=$(/lib/udev/vol_id -t $dev)
    if [ "$USBFS" != "vfat" -a "$USBFS" != "msdos" -a "$USBFS" != "ext2" -a "$USBFS" != "ext3" ]; then
	echo "USB filesystem must be vfat or ext[23]"
	exitclean
    fi

    USBLABEL=$(/lib/udev/vol_id -u $dev)
    if [ -n "$USBLABEL" ]; then 
	USBLABEL="UUID=$USBLABEL" ; 
    else
	USBLABEL=$(/lib/udev/vol_id -l $dev)
	if [ -n "$USBLABEL" ]; then 
	    USBLABEL="LABEL=$USBLABEL" 
	else
	    echo "Need to have a filesystem label or UUID for your USB device"
	    if [ "$USBFS" = "vfat" -o "$USBFS" = "msdos" ]; then
		echo "Label can be set with /sbin/dosfslabel"
	    elif [ "$USBFS" = "ext2" -o "$USBFS" = "ext3" ]; then
		echo "Label can be set with /sbin/e2label"
	    fi
	    exitclean
	fi
    fi
}

checkSyslinuxVersion() {
    if [ ! -x /usr/bin/syslinux ]; then
	echo "You need to have syslinux installed to run this script"
	exit 1
    fi
    if ! syslinux 2>&1 | grep -qe -d; then
	SYSLINUXPATH=""
    else
	SYSLINUXPATH="syslinux"
	#menu texts are trimmed when syslinux is not in / no idea why
	SYSLINUXPATH=""
    fi
}

if [ $(id -u) != 0 ]; then 
    echo "You need to be root to run this script"
    exit 1
fi

while [ $# -gt 2 ]; do
    case $1 in
	--noverify)
	    noverify=1
	    ;;
	--reset-mbr|--resetmbr)
	    resetmbr=1
	    ;;
	*)
	    usage
	    ;;
    esac
    shift
done

ISO=$1
USBDEV=$2

if [ -z "$ISO" -o ! -e "$ISO" ]; then
    usage
fi

if [ -z "$USBDEV" -o ! -b "$USBDEV" ]; then
    usage
fi

if [ -z "$noverify" ]; then
    # verify the image
    echo "Not verifying image...(no checkisomd5 in Ubuntu so skipping)!"
    #checkisomd5 --verbose $ISO
    if [ $? -ne 0 ]; then
	echo "Are you SURE you want to continue?"
	echo "Press Enter to continue or ctrl-c to abort"
	read
    fi
fi

# do some basic sanity checks.  
checkSyslinuxVersion 
checkFilesystem $USBDEV
checkPartActive $USBDEV
checkMBR $USBDEV
[ -n $resetmbr ] && resetMBR $USBDEV

# FIXME: would be better if we had better mountpoints
CDMNT=$(mktemp -d /media/cdtmp.XXXXXX)
mount -o loop $ISO $CDMNT || exitclean
USBMNT=$(mktemp -d /media/usbdev.XXXXXX)
mount $USBDEV $USBMNT || exitclean

trap exitclean SIGINT SIGTERM

if [ -d $USBMNT/casper ]; then
    echo "Already set up as live image.  Deleting old in fifteen seconds..."
    sleep 15

    rm -rf $USBMNT/casper
fi

echo "Copying live image to USB stick"
if [ ! -d $USBMNT/$SYSLINUXPATH ]; then mkdir $USBMNT/$SYSLINUXPATH ; fi

for file in \
	 README.diskdefines md5sum.txt \
	.disk casper pool dists preseed install;do
	cp -a $CDMNT/$file $USBMNT/
done

cp $CDMNT/isolinux/* $USBMNT/$SYSLINUXPATH


echo "Installing boot loader"
if [ "$USBFS" = "vfat" -o "$USBFS" = "msdos" ]; then
    # syslinux expects the config to be named syslinux.cfg 
    # and has to run with the file system unmounted
    mv $USBMNT/$SYSLINUXPATH/isolinux.cfg $USBMNT/$SYSLINUXPATH/syslinux.cfg
    cleanup
    if [ -n "$SYSLINUXPATH" ]; then
	syslinux -d $SYSLINUXPATH $USBDEV
    else
	syslinux $USBDEV
    fi
elif [ "$USBFS" = "ext2" -o "$USBFS" = "ext3" ]; then
    # extlinux expects the config to be named extlinux.conf
    # and has to be run with the file system mounted
    mv $USBMNT/$SYSLINUXPATH/isolinux.cfg $USBMNT/$SYSLINUXPATH/extlinux.conf
    extlinux -i $USBMNT/syslinux
    cleanup
fi

echo "USB stick set up as live image!"

----------------------------------------------------------------------------------------------------------------

After Deletion and ADDITION

------------------------------------------------------------------------------------------------------------------
#!/bin/bash
# Convert an Ubuntu live CD iso so that it's bootable off of a USB stick
# Copyright 2007  Red Hat, Inc.
# Jeremy Katz <katzj@redhat.com>
# Jani Monoses <jani@ubuntu.com> (slightly adapted to Ubuntu LiveCD)
# 
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; version 2 of the License.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU Library General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.


export PATH=/sbin:/usr/sbin:$PATH

usage() {
    echo "$0 [--reset-mbr] [--noverify] <isopath> <usbstick device>"
    exit 1
}

cleanup() {
    [ -d "$CDMNT" ] && umount $CDMNT && rmdir $CDMNT
    [ -d "$USBMNT" ] && umount $USBMNT && rmdir $USBMNT
}

exitclean() {
    echo "Cleaning up to exit..."
    cleanup
    exit 1
}

getdisk() {
    DEV=$1

    p=$(udevinfo -q path -n $DEV)
    if [ -e /sys/$p/device ]; then
	device=$(basename /sys/$p)
    else
	device=$(basename $(readlink -f /sys/$p/../))
    fi
    if [ ! -e /sys/block/$device -o ! -e /dev/$device ]; then
	echo "Error finding block device of $DEV.  Aborting!"
	exitclean
    fi

    device="/dev/$device"
}

resetMBR() {
    getdisk $1
    cat /usr/lib/syslinux/mbr.bin > $device
}

checkMBR() {
    getdisk $1

    bs=$(mktemp /tmp/bs.XXXXXX)
    dd if=$device of=$bs bs=512 count=1 2>/dev/null || exit 2
    
    mbrword=$(hexdump -n 2 $bs |head -n 1|awk {'print $2;'})
    rm -f $bs
    if [ "$mbrword" = "0000" ]; then
	echo "MBR appears to be blank."
	echo "Do you want to replace the MBR on this device?"
	echo "Press Enter to continue or ctrl-c to abort"
	read
	resetMBR $1
    fi

    return 0
}


checkFilesystem() {
    dev=$1

    USBFS=$(/lib/udev/vol_id -t $dev)
    if [ "$USBFS" != "vfat" -a "$USBFS" != "msdos" -a "$USBFS" != "ext2" -a "$USBFS" != "ext3" ]; then
	echo "USB filesystem must be vfat or ext[23]"
	exitclean
    fi

    USBLABEL=$(/lib/udev/vol_id -u $dev)
    if [ -n "$USBLABEL" ]; then 
	USBLABEL="UUID=$USBLABEL" ; 
    else
	USBLABEL=$(/lib/udev/vol_id -l $dev)
	if [ -n "$USBLABEL" ]; then 
	    USBLABEL="LABEL=$USBLABEL" 
	else
	    echo "Need to have a filesystem label or UUID for your USB device"
	    if [ "$USBFS" = "vfat" -o "$USBFS" = "msdos" ]; then
		echo "Label can be set with /sbin/dosfslabel"
	    elif [ "$USBFS" = "ext2" -o "$USBFS" = "ext3" ]; then
		echo "Label can be set with /sbin/e2label"
	    fi
	    exitclean
	fi
    fi
}

checkSyslinuxVersion() {
    if [ ! -x /usr/bin/syslinux ]; then
	echo "You need to have syslinux installed to run this script"
	exit 1
    fi
    if ! syslinux 2>&1 | grep -qe -d; then
	SYSLINUXPATH=""
    else
	SYSLINUXPATH="syslinux"
	#menu texts are trimmed when syslinux is not in / no idea why
	SYSLINUXPATH=""
    fi
}

if [ $(id -u) != 0 ]; then 
    echo "You need to be root to run this script"
    exit 1
fi

while [ $# -gt 2 ]; do
    case $1 in
	--noverify)
	    noverify=1
	    ;;
	--reset-mbr|--resetmbr)
	    resetmbr=1
	    ;;
	*)
	    usage
	    ;;
    esac
    shift
done

ISO=$1
USBDEV=$2


if [ -z "$ISO" -o ! -e "$ISO" ]; then
    usage
fi

if [ -z "$USBDEV" -o ! -b "$USBDEV" ]; then
    usage
fi

if [ -z "$noverify" ]; then
    # verify the image
    echo "Not verifying image...(no checkisomd5 in Ubuntu so skipping)!"
    #checkisomd5 --verbose $ISO
    if [ $? -ne 0 ]; then
	echo "Are you SURE you want to continue?"
	echo "Press Enter to continue or ctrl-c to abort"
	read
    fi
fi

# do some basic sanity checks.  
checkSyslinuxVersion 
checkFilesystem $USBDEV
checkPartActive $USBDEV
checkMBR $USBDEV
[ -n $resetmbr ] && resetMBR $USBDEV

# FIXME: would be better if we had better mountpoints
CDMNT=$(mktemp -d /media/cdtmp.XXXXXX)
mount -o loop $ISO $CDMNT || exitclean
USBMNT=$(mktemp -d /media/usbdev.XXXXXX)
mount $USBDEV $USBMNT || exitclean

trap exitclean SIGINT SIGTERM

if [ -d $USBMNT/casper ]; then
    echo "Already set up as live image.  Deleting old in fifteen seconds..."
    sleep 15

    rm -rf $USBMNT/casper
fi

echo "Copying live image to USB stick"
if [ ! -d $USBMNT/$SYSLINUXPATH ]; then mkdir $USBMNT/$SYSLINUXPATH ; fi

for file in \
	 README.diskdefines md5sum.txt \
	.disk casper pool dists preseed install;do
	cp -a $CDMNT/$file $USBMNT/
done

cp $CDMNT/isolinux/* $USBMNT/$SYSLINUXPATH
[COLOR="MediumTurquoise"]cp $CDMNT/ wubi.exe $USBMNT
cp $CDMNT/umenu.exe $USBMNT
[/COLOR]
echo "Installing boot loader"
if [ "$USBFS" = "vfat" -o "$USBFS" = "msdos" ]; then
    # syslinux expects the config to be named syslinux.cfg 
    # and has to run with the file system unmounted
    mv $USBMNT/$SYSLINUXPATH/isolinux.cfg $USBMNT/$SYSLINUXPATH/syslinux.cfg
    cleanup
    if [ -n "$SYSLINUXPATH" ]; then
	syslinux -d $SYSLINUXPATH $USBDEV
    else
	syslinux $USBDEV
    fi
elif [ "$USBFS" = "ext2" -o "$USBFS" = "ext3" ]; then
    # extlinux expects the config to be named extlinux.conf
    # and has to be run with the file system mounted
    mv $USBMNT/$SYSLINUXPATH/isolinux.cfg $USBMNT/$SYSLINUXPATH/extlinux.conf
    extlinux -i $USBMNT/syslinux
    cleanup
fi

echo "USB stick set up as live image!"

-----------------------------------------------------------------------------------------------------------------
I)To recap, you must now have the following readied.

1) An end partition on your mac HD with '/boot'  and boot loader installed.'
2) The adjacent partition formatted to Fat 32 and flagged to boot.
3)An iso image of Heron and the altered .sh on the desktop of your Live user session.

IF YOU DO NOT HAVE ALL OF THE ABOVE PRECISELY YOU NEED TO GO THROUGH THE ABOVE AGAIN>

In the terminal do such:

```
cd /home/<user>/Desktop

```
```
chmod +x isotostick.sh

```
You can do this in terminal to make sure which partition the installation of heron is going to by doing this.

'```
blkid
```'

xy is the partition on your mac HD formatted to Fat 32

then do this and ignore the mesages.

 ```
./isothstick.sh /home/<user>/Desktop/<heron> /dev/sdxy
 
```
Should take a few minutes.

When done check the partition  to see everything is there or not. If so reboot choose the partition and enjoy the live CD on your the HD.

I hope someone will come up with "persistence'". Then we are way ahead.

So what do you do with the other external Linux installation?
That will be up to you. :):):)

---

### Post by a1234 on 2008-08-03
Ryan Cloke has come up with the initrd.gz edit for persisitence ! 

[http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/](http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/)

Thank you ryan.

---

