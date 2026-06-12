---
title: "How to do a fresh install (in regards to GRUB)?"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by mrdeeno on 2006-12-26
I am having wireless networking problems (Broadcom card).  I am not using ndiswrapper, but got it working otherwise but it works on and off intermittently and the network manager doesn't help at all (it only sees the wired network, whether my wireless internet access is working or not).  Since it was "inexperience" trying to get the wireless to work, i jsut tried doing a bunch of things i saw on these forums and most didn't work and i'm not even sure what i did to get it to work, although it still only works intermittently.

I'm thinking of doing a fresh install but am concerned mostly about the GRUB loader.  How do I ensure that this is removed and reinstalled rather than installing more options to it (the options i currently have are 2 different kernals along wtih the recover modes for each and then xp)?

---

### Post by Rippey on 2006-12-26
it shoud be no problem to format your ubuntu drive and reinstall it, grub wil auto detect windows and make a new config.

---

### Post by halitech on 2006-12-26
even if it's not removed, you can always edit the grub file to get rid of the extra entries that aren't needed.

if it is on the same drive as windows, y ou can always get a windows boot disk and run 

```

fdisk /mbr

```

and that will restore the mbr back to the windows defaults

---

### Post by kinematic on 2006-12-26
when you do a fresh install you can overwrite your current grub with the grub from the install cd.
it will detect windows again just like the first time you installed ubuntu ;)

---

### Post by mrdeeno on 2006-12-26
> **halitech said:**
> even if it's not removed, you can always edit the grub file to get rid of the extra entries that aren't needed.

if it is on the same drive as windows, y ou can always get a windows boot disk and run 

```

fdisk /mbr

```

and that will restore the mbr back to the windows defaults

so if i'm reading this right, the grub program itself is loaded in the mbr, but the configurations (choices) are on the grub boot list, correct?  

So even if I do a fresh ubuntu install (format the ubuntu partition), i can just leave the current grub on the mbr and the next ubuntu installation will just install over it or not do anything since the program is already there, right?

---

