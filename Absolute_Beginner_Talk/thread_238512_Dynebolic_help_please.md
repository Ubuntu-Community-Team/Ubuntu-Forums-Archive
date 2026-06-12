---
title: "Dyne:bolic help please"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Max1130 on 2006-08-17
I'm trying to dock dyne 2.1 I believe to a external hardrive but know matter what I do the drive doesn't show up. but it does show up during the boot process anyone have any ideas right now I'm getting kinda desperate I really need to fix my home computer because windows died and I need a os of some sort so I can replace an important file.

---

### Post by kaffelars on 2006-08-18
How is this related to Ubuntu?

---

### Post by bodhi.zazen on 2006-08-18
Not sure if it helps, but you likely have to mount the drive.

In a terminal:

su (I think the dyne passowrd is Luther)
mkdir /mnt/hd

Now, assuming you have a USB connection:

mount /dev/sda /mnt/hd

Or mount /dev/sda1 /mnt/hd

If this works, you can change the permissions on your mount.

umount /mnt/hd
chown root:user or root:users /mnt/hd
chmod 770 /mnt/hd

exit the root shell

As a regular user mount the hard drive:

mount /mnt/hd

Should be good to go.

---

