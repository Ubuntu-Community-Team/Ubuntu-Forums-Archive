---
title: "Installing rEFIt without OSX"
date: 2008-07-10
forum: Apple Hardware Users
---

### Post by capawi on 2008-07-10
How would I go about installing rEFIt on its own small partition without using OSX? I'm single booting Ubuntu 8.04 on my Macbook.

I am fine with creating partitions but for some reason gparted will not let me format in HFS+, is this a common problem? Am I missing a file?

Once I figure that out I'm unsure how to proceed, is there a guide for this?

Thanks

Carl

---

### Post by cyberdork33 on 2008-07-11
> **capawi said:**
> I am fine with creating partitions but for some reason gparted will not let me format in HFS+, is this a common problem? Am I missing a file?
parted magic can create HFS+ partitions.

I don't think that is required for rEFIt anyway. From the rEFIt website:
> Installing on the EFI System Partition  It is also possible to install rEFIt on the hidden “EFI System Partition” on your internal disk. This is recommended for advanced users only, and will not be detailed here. You will need to use bless with the --mount and --file options. Consult the man page for bless for more information.


The biggest issue is that you need the bless command which is only available in OS X. but you can use it from the OS X install dvd.


Before going further, is there any reason that you want to use rEFIt? are you planning to dual boot with another OS?


Basically, to install, all you have to do is copy the refit files to a partition in a folder named "efi" then bless the refit executable.

---

### Post by capawi on 2008-07-11
Yes my main reason is for dual booting and also so I can easily boot from external devices.

Thanks 

Carl

---

### Post by johnylovejoy on 2009-04-20
im looking for the same solution
only have ubuntu and i need to put xp on it

any ideas?

---

