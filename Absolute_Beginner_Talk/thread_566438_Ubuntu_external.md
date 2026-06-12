---
title: "Ubuntu external"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-10-03
ive jsut  installed ubuntu on my external aswell as on my internal.

the external so i can take round my mums.

i want to know, will i be able to boot into it?
will it have grub following it?

from pc to pc?

---

### Post by Nehvrook on 2007-10-03
I think you might be able to boot into it if GRUB is on the external and your mothers PC supports booting from USB. Give it a go to see if you can or not :P

---

### Post by skymera on 2007-10-03
cool.
i dont want it interfeering with my grub i have at the moment.
does it need a grub if my mum supports USB boot?
can i stop it being mounted at boot?

i still use it partly as NTFS for backups etc. and media.

my mum has a Dell inspiron 1501, Vista. :(

---

### Post by skymera on 2007-10-03
when i choose boot from USB it says NTLDR is missing.

im going to unplug my HDD and see if my external has a boot menu

---

### Post by Nehvrook on 2007-10-03
It depends. When you installed it on your external you may have just added the external to GRUB, which is already on your internal hard drives master boot record.

I've never done an install to an external before so I'm not 100% on all this.

A quick google suggests to me the "NTLDR is missing" is the windows boot manager complaining, so yeah I think it's due to lack of GRUB.

---

### Post by skymera on 2007-10-03
ok it seems the external install has overwritten my internal ones grub...

i cant boot unless my external is on..

how do i remove grub from my external

then how do i add to my internal?

---

### Post by skymera on 2007-10-03
ok got rid of external.

believe i have reinstalled grub on hd0,1

which is my internal.

time to reboot and if it fails, i'll be bakc! :lol:

---

