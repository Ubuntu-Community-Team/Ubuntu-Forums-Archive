---
title: "installing ubuntu twice same hdd"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by klein de usa on 2007-02-25
hi 
i'm curious can i use the same swap file if i install ubuntu twice on the same hdd and only run one at a time ? or do i need a seperate swap for each i would like to use one install as a test install so if i crash it , i still have the other and copy that insted of reinstall.

---

### Post by ashmew2 on 2007-02-25
I need to know the answer to this one too , was just gonna start a thread....Good that i looked!!

---

### Post by oilchangeguy on 2007-02-25
when you install and get to the part about setting up a partition, just select the option to keep your present os, and add the new one. and let it auto set it's partition. no need to manually create a swap partition, it gets created anyway when the os is being installed. i do suggest using another hard drive for the second install, and use it for testing. that way your main install is protected, if you damage the other install.

---

### Post by solar george on 2007-02-25
If you mean a swap partition not a swap file, yes you can (you could probably share a swap file but that would be a lot of work)

You can share the swap between many different linuxes.

Just select the same swap partition each time you are installing ubuntu.

If you are using edgy you may need to alter the fstab files for it to work properly, if you are just post back and I'll try to help.

---

### Post by klein de usa on 2007-02-25
hi 
thanks for all the info! 
i'm using bootit ng and it lets me clone or copy one partion to another.
and yes i did mean swap partition thank you i didn't notice i did that.
one other thing can i install the native and swap partition in an logical partition ?

---

### Post by solar george on 2007-02-25
The installer handles primary and extended partitions transparently.

Or did you mean using logical volume manager?

---

