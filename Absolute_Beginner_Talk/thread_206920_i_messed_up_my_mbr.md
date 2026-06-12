---
title: "i messed up my mbr"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by drtvasudevan on 2006-06-30
i messed up my mbr.
this is how i achieved it:
i have installed several versions of linux and win 98 win xp.
the last was an upgrade to i-686

i have installed all linux and their grub in thier own partitions.
(i used to boot witha third party boot loader xosl)
except the one in hdb2; that was from a live cd and it did not give any options but installed in mbr. i thought of installing xosl again and so did this

```
sudo grub-install /dev/hdb2
```
but i let things lie the same till yesterday
after upgrade to i 686 in hda6 i needed to edit grub to boot from 686

so i  got the menu.lst and added the lines.
and did a
```
sudo update-grub
```

now while booting i cant boot into windows xp

if i choose xp it just reverts back to grub loader

while booting linux it says there are differences in offset in the backup and the original and then prints a load of hex

this my menu.lst:

sorry could not post it as it was rejected:
there are 16 images and you are allowed only 8.
though i fail to see the images (includes  tags) i have attached the list in a zip format.

i know i can recover xp by booting with xp cd create a new mbr and then recover linux.
but is there a painless way just to wipe the mbr and write anew?

tv

---

### Post by Apple 101 on 2006-07-01
Edit one of the Grub configuration files, to have Windows and all of the operating systems on it.  Then run the Grub install command.  In a terminal: *grub-install /dev/hda* or whereever your MBR is located.

---

### Post by drtvasudevan on 2006-07-01
ok will try.
am on travel.
shall do it and post on monday.

tv

---

### Post by drtvasudevan on 2006-07-03
[QUOTE=drtvasudevan]ok will try.
am on travel.
shall do it and post on monday.

tv[/QUOTE]

ok done that.
but the problem remains.
now there are even a longer error msg (duplication of the same error msg)

xp wont boot.
tv

---

