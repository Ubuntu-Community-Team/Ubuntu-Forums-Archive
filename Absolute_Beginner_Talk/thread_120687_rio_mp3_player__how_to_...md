---
title: "rio mp3 player ? how to .."
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by djlilyazi on 2006-01-23
Hi,

i have a rio nitrus mp3 player how do i make it work tho ? with linux...i want to upload my music on it.... 

Thank

Yaz

---

### Post by davmac on 2006-01-27
Hi,

I have a Rio Carbon and the way I've got it working is to just plug it in and it auto-mounts as a disk.

You can then just drag your mp3s to it.

I've set up a script that uses rsync to keep the music on the Rio synchronised with my music directory. Just reply if you want a copy of this.

Regards,

Dave Mac

---

### Post by kinseikun on 2006-01-29
I'm having the same problem. When I plug in my Rio Nitrus it does nothing tho, how would I go about manually mounting it? If I manually mount it, will that work? Thanks.

---

### Post by tousman on 2007-05-27
I have to mount mine manually, I use: 

sudo mount -t vfat /dev/sda1 /media/RIO

it works but when copying files from the RIO to my home dir. the files are under the ownership of root, so I cannot rename, delete form the GUI and need to do it from the command line as Super User. 

Any idea on how to fix that ? 
Cheers

---

### Post by tousman on 2007-05-27
to change the ownership I just added the device to my /etc/fstab. Now copied files from mp3 player to my home are under the normal user's ownership... 
If you have anytips for automounting the device.... Cheers.

---

### Post by tousman on 2007-05-27
Hi, I made the below script to mount the RIO it is not automatical but much easier anyway... 

Paste this in your text editor and save it under  /usr/local/bin/ and give it the name you like
(i.e:
 vi  /usr/local/bin/rio  
Then paste the script and save it)
So I saved mine as rio then from anywhere I type rio and I get asked if I wanna mount it or umount... 
Cheers, 
------------------------------------------------------------------------------------------------------------------

osch=0

echo "1. Mount"
echo "2. Umount"
echo -n "Make your choice [1 or 2]? "
read osch

if [ $osch -eq 1 ] ; then

     echo "Mounting device"
     sudo mount -t vfat /dev/sda1 /media/RIO

else
     echo "Unmounting device"
     sudo umount /media/RIO
fi

---

