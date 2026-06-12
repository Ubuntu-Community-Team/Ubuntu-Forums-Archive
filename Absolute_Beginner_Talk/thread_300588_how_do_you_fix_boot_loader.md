---
title: "how do you fix boot loader ?"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by at0mic on 2006-11-15
hi guys,

i installed windows [shame i know] on a seperate partition of the same drive with linux on it ... well i think you know what happened to the boot loader. is there any documentation on how to get grub to fix the mess that windows created using the live cd? Whats the first steps?

---

### Post by aidanr on 2006-11-15
[super grub disk]("http://adrian15.raulete.net/grub/")

---

### Post by hearnden on 2006-11-15
Basically you want to run [grub-install]("http://http://www.gnu.org/software/grub/manual/html_node/Invoking-grub-install.html") again to overwrite Windows' bootloader (NTLDR I think) on the master boot record.  Make sure you have an entry in grub's menu.lst for Windows though (there's a commented out example you can uncomment).  You just need to know what partition it's on.  Have a look around some Grub HOW-TOs

---

### Post by hearnden on 2006-11-15
if /dev/hda is your disk's device name, then just run

```

$ sudo grub-install /dev/hda

```

Do NOT do 'sudo grub-install /dev/hda1'; you want grub on the master boot record, not in the boot sector of a partition.

---

### Post by at0mic on 2006-11-15
WOW! thanks aidanr! that cd is extremely powerful and going into my special cd book :)

back up and running with both os's in a matter of 2 minutes

good to know that you can also do this from the kbuntu live cd though :)

---

