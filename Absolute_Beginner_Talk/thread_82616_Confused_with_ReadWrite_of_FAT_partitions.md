---
title: "Confused with Read/Write of FAT partitions"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by jvslice on 2005-10-26
At the persent time my fstab file reads, for two FAT partitions:

/dev/hda2       /media/hda2     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0

I have read access but unable to write from linux.

I did a search and found entires on mounting as read-write with two different formats, one just as above, execpt that the mount point was not in /media, 

And the second entry added iocharset, and umask entries as below:

/dev/hda<what ever> /mnt/<what ever> vfat defaults,iocharset=utf8,umask=000 0 0

I guess my question is do I need to uses a different mount point than /media
and which format in the mount do I use?

Oh by the way I am using breezy 5.10

thanks

---

### Post by Breezy Badger on 2005-10-26
Hello there,

There is a rather easy solution for this, or so I thought.  Try this, use gedit to make a text (sh) file of the code I am going to give you below and follow the instructions that are inside it.

Hope this helps you

Badger

```
#!/bin/bash
####################
# This utility searches for available HFS+, NTFS and FAT32 partitions, creates
# mount points for them and adds them to /etc/fstab
# (c)2005 Dennis Kaarsemaker <dennis@ubuntu-nl.org>
# Thanks to Nalioth for suggesting, assisting with and testing the HFS+ bits
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
# 
# Instructions for use:
#  - Save this file on your local hard drive
#  - Open a terminal and type sudo bash winmac_fstab
#  - If sudo asks for a password, use your own password
#  - Your windows and mac partitions will now be mounted everytime
#    you boot. You can delete this script now
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
###################

# Root check
if [[ $UID != 0 ]]; then
    echo 'You should run this program as root or using sudo'
    exit 1
fi

# Get label for disk, consisting of size and name (fs labels proves too hard)
getlabel() {
    MAJ=`file /dev/$drive | sed -e 's/.*(\(.\).*/\1/'`
    MIN=`file /dev/$drive | sed -e 's/.*(..\(.\).*/\1/'`
    UDI="/org/freedesktop/Hal/devices/block_${MAJ}_${MIN}"
    SIZE=`hal-get-property --udi $UDI --key volume.size`
    GB=`python -c "print int(round($SIZE.0 / (1024**3)))"`
    label="$GB\\040GB\\040Disk\\040($drive)"
    label2="$GB GB Disk ($drive)"
}

# Simple command line argument for installers
# -w: mount them with user,umask=0111
# -r: mount them with user,umask=0133,uid=1000,gid=1000
RWALL=-1;
if [[ $1 == '-w' ]]; then RWALL=1; fi
if [[ $1 == '-r' ]]; then RWALL=0; fi

if [[ $RWALL == -1 ]]; then
    echo 'By default the disks will be writable only by root and'
    cat /etc/passwd | awk -F ':|,' '/:1000:/ {print $5 " (" $1 ")"}'
    echo 'Do you want to make the disk writable by all users instead? (y/n)'
    read RESP
    if [[ $RESP == 'y' || $RESP == 'Y' ]]; then
        RWALL=1
    else
        RWALL=0
    fi
fi

if [[ $RWALL == 1 ]]; then
    OPTIONS='user,fmask=0111,dmask=0000'
    MACOPTIONS='user,file_umask=0111,dir_umask=0000'
else
    OPTIONS='user,fmask=0133,dmask=0022,uid=1000,gid=1000'
    MACOPTIONS='user,file_umask=0133,dir_umask=0022,uid=1000,gid=1000'
fi

# Now for the real work
drivesntfs=`fdisk -l | grep -i 'ntfs' | awk -F '/| ' '{print $3}'`
drivesfat=`fdisk -l | grep -i 'fat32' | awk -F '/| ' '{print $3}'`
driveshfs=`fdisk -l | grep -i 'Apple_HFS' | awk -F '/| ' '{print $3}'`

donesomething='n'
for drive in $drivesntfs
do
    getlabel $drive
    if [[ ! `grep $drive /etc/fstab` ]]
    then
        mkdir "/media/$label2"
        echo "#Added by winmac_fstab utility" >> /etc/fstab
        echo "/dev/$drive /media/$label ntfs ro,$OPTIONS 0 0" >> /etc/fstab
        echo "Added /dev/$drive as '/media/$label2'"
        donesomething='y'
    else
        echo "Ignoring /dev/$drive - already in /etc/fstab"
    fi
done
if [[ $donesomething == 'y' ]]
then
    echo "NTFS drives will be mounted read-only!"
fi
for drive in $drivesfat
do
    getlabel $drive
    if [[ ! `grep $drive /etc/fstab` ]]
    then
        mkdir "/media/$label2"
        ln -s "/media/$label2" /media/$drive # yay, spaceless link for b0rken programs
        echo "#Added by winmac_fstab utility" >> /etc/fstab
        echo "/dev/$drive /media/$label vfat rw,$OPTIONS 0 0" >> /etc/fstab
        echo "Added /dev/$drive as '/media/$label2'"
        donesomething='y'
    else
        echo "Ignoring /dev/$drive - already in /etc/fstab"
    fi
done
for drive in $driveshfs
do
    getlabel $drive
    if [[ ! `grep $drive /etc/fstab` ]]
    then
        mkdir "/media/$label2"
        echo "#Added by winmac_fstab utility" >> /etc/fstab
        echo "/dev/$drive /media/$label hfsplus rw,$MACOPTIONS 0 0" >> /etc/fstab
        echo "Added /dev/$drive as '/media/$label2'"
        donesomething='y'
    else
        echo "Ignoring /dev/$drive - already in /etc/fstab"
    fi
done

if [[ $donesomething == 'y' ]]
then
    # And mount them
    mount -a
    echo "All windows and mac partitions will now be mounted every time you boot"
    echo "You do not need to reboot, the partitions are mounted now too"
else
    echo "No usable windows/mac partitions found"
fi

```

---

### Post by xmastree on 2005-10-26
[QUOTE=jvslice]/dev/hda2       /media/hda2     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0[/quote]
```
/dev/hda2       /media/hda2	vfat	umask=0000	0	0
/dev/hda6       /media/hda6	vfat	umask=0000	0	0
```Should do it.


> I guess my question is do I need to uses a different mount point than /mediaYou can mount them anywhere. /media/hda<2&6> are fine.

---

### Post by jvslice on 2005-10-26
Thanks all, just wanted to give a follow-up.

Tried the script, and it added my NTFS partition to the fstab file as read only as it should, but didnot change the read only for non-root users to read-write for the existing FAT partitions.

I than edited fstab and changed 

/dev/hda2 /media/hda2 vfat defaults 0 0 **to** 
/dev/hda2 /media/hda2 vfat umask=0000 0 0
/dev/hda6 /media/hda6 vfat defaults 0 0 **to**
/dev/hda6 /media/hda6 vfat umask=0000 0 0

changing defaults to umask=0000 in each entry works after re-booting

thanks to all

---

### Post by aysiu on 2005-10-26
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by LinuxWiz83 on 2005-10-26
So there is no way to write to a NTFS drive?

---

### Post by Breezy Badger on 2005-10-27
> So there is no way to write to a NTFS drive?

No, I suggest fat32..that way if you have both windows and linux installed they can both read it.

ntfs is not universal, linux can read it but you cannot write to it

Badger

---

