---
title: "Noatime question?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by eaglealadin on 2008-03-25
Hello
Please tell me is it OK to set noatime as this? And is there any mistake?

 UUID=f3414867-f197-43af-84d6-d79397a09cff /               ext3    noatime,defaults,errors=remount-ro 0       1

    * Add these lines to the end of the file: 

tmpfs     /var/log       tmpfs     defaults,noatime        0 0
tmpfs     /tmp              tmpfs     defaults,noatime        0 0
tmpfs     /var/tmp       tmpfs     defaults,noatime        0 0

Thanks

---

### Post by RealPSL on 2008-03-25
You mean like this?

UUID=bf70cc3e-7b95-46d2-b5b6-be1b618f35e9 /var/lib/vm     ext3    defaults,noatime 0      0

The above is directly from my /etc/fstab file. The noatime option is supposed to speed things up a bit because it skips updating the file system every time a file is accessed. I think Hardy comes with a similar flag but I am not 100% sure as I have not looked yet. The above obviously works fine for me.

As for the rest of your proposed entries like /var/log I don't get those. tmpfs as far as I remember is a Solaris thing.

---

