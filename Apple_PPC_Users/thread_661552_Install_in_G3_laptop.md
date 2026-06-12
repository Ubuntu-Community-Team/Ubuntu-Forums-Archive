---
title: "Install in G3 laptop"
date: 2008-01-08
forum: Apple PPC Users
---

### Post by bengki on 2008-01-08
Hi...I need some extra help here
I install from minimal cd..and then download a base system file from internet 
but when it download available kernel, it give me a error message such as 

" an error was returned while trying to install the kernel into target system"

I tried, every available kernel in option but gave me a same result.  

Thanks before..

---

### Post by bengki on 2008-01-08
FYI

Finally :confused: I choose option "none" so the installing continue but then I can't install yaboot on my HD, it said I have to configure manually so I can boot from my HD..

Please help me .

---

### Post by Gen2ly on 2008-01-09
Hi bengki, this will take a bit of reading to learn how yaboot works.  I've done this before and it isn't too difficult.  You'll need to use the Ubuntu LiveCD and chroot (change root)to the partition Ubuntu has been installed on.  With a properly configured /etc/yaboot.conf yaboot should install correctly.  I've done this before and put it on the wiki:

[Gentoo Linux on an iBook]("http://gentoo-wiki.com/HOWTO_Install_Gentoo_-_From_Stage1_on_an_iBook_G3#BootLoader_Setup")

It would probably be helpful to look at the original documentation too

[http://penguinppc.org/projects/yaboot/](http://penguinppc.org/projects/yaboot/)

---

