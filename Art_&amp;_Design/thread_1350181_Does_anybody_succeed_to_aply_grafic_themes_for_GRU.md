---
title: "Does anybody succeed to aply grafic themes for GRUB?"
date: 2009-12-09
forum: Art &amp; Design
---

### Post by RomanIvanov on 2009-12-09
My system is Ubuntu 9.10, I updated Grub from
[https://launchpad.net/~fzielcke/+archive/grub-ppa](https://launchpad.net/~fzielcke/+archive/grub-ppa).
I installed themes to "/boot/grub/themes". 
I changed grub.cfg file (according to [http://grub.gibibit.com/Journal](http://grub.gibibit.com/Journal) post from "26 July 2008")
to set the theme persistently 
```
set theme=/boot/grub/themes/ubuntu1/theme.txt
```
But I am not sure about
location of "set theme=......" in grub.cfg. 
Even tried, following to be precise:
```
set theme=(hd1,1)/boot/grub/themes/ubuntu1/theme.txt
```

Please help.

---

