---
title: "Virtual dvd drive"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2008-01-09
Is there a virtual dvd drive in the repos? Like daemon tools lite for windows. That emulates a dvd drive. I searched in Synaptics, but saw nothing I was looking for.

---

### Post by AusIV4 on 2008-01-10
I believe you're trying to loopmount an ISO.

To mount an ISO in your filesystem, run:
```
sudo mount -o loop -t iso9660 dvd.iso /media/ISO
```
Where 'dvd.iso' is the ISO you're trying to mount, and /media/ISO is the location you're trying to mount to.

I have the following scripts in my ~/.gnome2/nautilus-scripts folder:

Mount ISO:
> #!/bin/bash
#
for I in `echo $*`
do
  foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`
sudo mount -o loop -t iso9660 $I /media/ISO
  done
done
exit 0

Unmount ISO:
> #!/bin/bash
#
for I in `echo $*`
do
  foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`
sudo umount $I
 done
done
exit 0

If you save these files in ~/.gnome2/nautilus-scripts, they will show up when you right click within Nautilus (or on your desktop). Then you can just mount or unmount an ISO easily.

---

### Post by feistybird on 2008-01-10
search for : gmountiso

Run gmountiso, and mount ISO to your preferred folder in /media/xxx or your home directory

If you are trying to play Windows games that requires CD/DVD detections via WINE, you can mount it to /media/cdrom0 (your physical cdrom drive), but must make sure there is no real CD inserted in your physical cdrom drive

---

### Post by swoll1980 on 2008-01-10
Thanks guys

---

