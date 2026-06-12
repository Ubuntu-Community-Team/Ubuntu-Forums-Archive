---
title: "installing without it affecting grub?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by wwjoeyd on 2007-04-19
hello everyone


im ok at computers
i havent got all the names down

how can i install ubuntu on a external hardrive without it affecting my bootscreen ?

[so i can manuelly push F12 and push load from "forgot what it says"]

i have installed ubuntu on a external before
but this time i would like it not to affect the boot screen


cheers
:)

---

### Post by wwjoeyd on 2007-04-20
sorry if all this doesnt make sense

i wish to install ubuntu on a 80 gig external without having "ubuntu" below
so can manually push F12 and load from the external 

[IMG]http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/IMG_0345.JPG[/IMG]

---

### Post by louieb on 2007-04-20
The installer wants to put grub somewhere. You can tell it where. So put in the mbr of the external drive **example (hd#)**  or install in the boot sector of the Ubuntu / (root) partition. **example (  hd#,#) ** Can't tell what # or #,#. If your using the live CD  just watch very carefully  and you will see where the install location can be changed. You might also want to check the Dual Boot link in my signature.

---

