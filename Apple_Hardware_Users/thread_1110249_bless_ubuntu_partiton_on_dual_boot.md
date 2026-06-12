---
title: "bless ubuntu partiton on dual boot?"
date: 2009-03-29
forum: Apple Hardware Users
---

### Post by inphektion on 2009-03-29
I dual boot mac osx and jaunty on a macbook pro.  One thing that bothers me is after I select to boot linux in refit it takes about 20 seconds to even get to grub.  Once there the boot is very fast.  I read that I could speed this up with blessing my ubuntu boot partition but then in that same doc it mentioned this was only needed if ubuntu was installed by itself on the mac.  So, 1. will blessing help this out for me and 2. i tried blessing from the refit program on the mac but got errors, any good tut on how to bless that will step me through it?

---

### Post by cyberdork33 on 2009-03-29
> **inphektion said:**
> I dual boot mac osx and jaunty on a macbook pro.  One thing that bothers me is after I select to boot linux in refit it takes about 20 seconds to even get to grub.  Once there the boot is very fast.  I read that I could speed this up with blessing my ubuntu boot partition but then in that same doc it mentioned this was only needed if ubuntu was installed by itself on the mac.  So, 1. will blessing help this out for me and 2. i tried blessing from the refit program on the mac but got errors, any good tut on how to bless that will step me through it?
I think that blessing the Ubuntu partition will leave rEFIt/OSX inaccessible (until you hold alt on startup and select a new device to boot from).

You want rEFIt to be the "blessed" executable... I do not know why you have such a delay... that seems odd. Is the rEFIt tux screen showing during this time or something else?

---

### Post by inphektion on 2009-03-29
ok. so I don't want to bless anything.  and yes I select the tux penguin and it sits there with just the penguin in the center for another 15 seconds or so and then I see grub.  Once I get to grub its a 10 second boot.

---

### Post by cyberdork33 on 2009-03-30
> **inphektion said:**
> ok. so I don't want to bless anything.  and yes I select the tux penguin and it sits there with just the penguin in the center for another 15 seconds or so and then I see grub.  Once I get to grub its a 10 second boot.
blessing may help... the symptoms sound similar... I just don't know the reason for it (on a single-boot, it is because there are no efi executables...). You would be trying something new though.

---

