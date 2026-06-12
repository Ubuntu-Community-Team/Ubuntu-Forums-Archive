---
title: "Allow all users to eject CD drive"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by sparkguitar05 on 2008-03-28
In my current install of Gutsy, the only user who can eject a CD is the user who inserted the CD in the first place.  This is very annoying.  I want to allow all users to eject a CD at any time.  How can this be done?

---

### Post by DBrocks on 2008-03-28
Try
```
sudo eject /media/cdrom0
```

---

### Post by pieisgood4589 on 2008-03-28
You could also add it as an icon in the GNOME menu by clicking "Add Launcher" then putting in that line of code :popcorn:

~pieisgood4859

---

### Post by DBrocks on 2008-03-28
> **pieisgood4589 said:**
> You could also add it as an icon in the GNOME menu by clicking "Add Launcher" then putting in that line of code :popcorn:

~pieisgood4859

Lol. I was gonna say a shell script: (I'm a Command-Line kind of guy :) )
But, yes that works.

---

### Post by sparkguitar05 on 2008-03-29
Isn't there a way to set it up so that anyone can just push the **button** on the CD drive to open it?

---

### Post by banewman on 2008-03-29
Go to users and groups in the menu and click on each user and make sure the checkbox is selected that enables them to use cdrom drives.
:)

---

### Post by sparkguitar05 on 2008-03-29
> **banewman said:**
> Go to users and groups in the menu and click on each user and make sure the checkbox is selected that enables them to use cdrom drives.
:)
They all have the cdrom checkbox.  That's not the problem.

The problem is that the only user than can open the CD drive is the user that put it in in the first place.  I want to enable all users to open the CD drive at any time, no matter who put it in, just by pushing the button.  (Just like in Windows.)

---

### Post by SOULRiDER on 2008-03-29
Something should probably be changed in HALs config. Make sure all the users are in the storage and optical groups.

---

### Post by sparkguitar05 on 2008-04-26
> **SOULRiDER said:**
> Something should probably be changed in HALs config. Make sure all the users are in the storage and optical groups.

How do I do that?

---

