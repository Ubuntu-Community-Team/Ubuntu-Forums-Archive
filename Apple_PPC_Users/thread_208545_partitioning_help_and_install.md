---
title: "partitioning help and install"
date: 2006-07-03
forum: Apple PPC Users
---

### Post by Digitallysick on 2006-07-03
ok i was able to use parted to free up 10 gigs of space, but i cant seem to install correctly, i create my swap space, and then my ext3 space, then when i go to the next screen , it says " mount point has to be more than 128mb


for some reason its seeing my partitions as 5k and 128 mb, when its actually 1500 mb for swap, and the rest is for the install, what am i doing wrong?

---

### Post by BitTorrentBuddha on 2006-07-03
Did you make sure to apply the changes in gparted after planning them? The app isn't very clear about making sure that happens.

---

### Post by Digitallysick on 2006-07-03
yes i applied the changes, but when i went to the next screen, it wasnt showing the correct partition sizes, i have since rebooted into osx, which shows a 9gb of free space ( i cant seem to partition it with disk utility)

So once i have 9 or 10 gb of "unformatted" , what do i need to do?

---

### Post by zachws on 2006-07-03
i assume you RESIZED your partitions using parted (gparted in the installer won't do this)

heres what you do:
DONT make your own swap and all, just clear up the space and let the installer install on the "largest continuous free space" (it's one of the options)

does this help?

---

### Post by zachws on 2006-07-03
addendum:
if you have 9GB "unformatted" just use the method above, it gets rid of any issues with bootstrap partitions and swap files that are not too uncommon on PPC installations.

---

### Post by Digitallysick on 2006-07-03
thanks! that did the trick!  (they should make that a side note for the install) worked out just right!

---

### Post by zachws on 2006-07-03
[QUOTE=Digitallysick]thanks! that did the trick!  (they should make that a side note for the install) worked out just right![/QUOTE]

yup, i had the same problem (without knowing it). just relaying what someone told me. glad to be of help. :cool:

---

