---
title: "[SOLVED] Typing Chinese characters"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-08-09
Hi all, I would like to know how do you type in chinese, i had it last time in fedora 6 where i can find languages to download in Package Manager, but now i dont know how to install so that i can type chinese in pinyin by just switching.

If any of you used windows before you would know on the start menu bar on the right theres a box which you can click to select the language you want to type in, how do i get that in ubuntu?

---

### Post by splintercellguy on 2007-08-09
This guide is a bit dated but might still be of interest: [http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)

EDIT: And this: [http://doc.vic.computerbank.org.au/software_docs/Chinese%20Input%20Editor/](http://doc.vic.computerbank.org.au/software_docs/Chinese%20Input%20Editor/), though I would suppose you would have to change breezy to feisty, if that's what you're using

EDIT 2: Third thought, and probably what you want to look at: [https://help.ubuntu.com/community/SCIM/Chinese?highlight=%28Chinese%29%7C%28input%29](https://help.ubuntu.com/community/SCIM/Chinese?highlight=%28Chinese%29%7C%28input%29)

---

### Post by Hospadar on 2007-08-09
Have a look at this as well
[http://robrohan.com/2007/05/27/chinese-on-ubuntu/](http://robrohan.com/2007/05/27/chinese-on-ubuntu/)

---

### Post by kinngg on 2007-08-09
sorry but it doesnt really help me

i followed the link instructions but i got this 

chilin@Ubuntu-Laptop:~$ sudo apt-get install scim-chinese scim-config-socket scim-frontend-socket scim-gtk2-immodule scim-server-socket scim-tables-zh xfonts-intl-chinese xfonts-intl-chinese-big ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp ttf-arphic-bsmi00lp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package scim-chinese is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  scim-pinyin

i dont get it

---

### Post by splintercellguy on 2007-08-09
Replace scim-chinese with scim-pinyin in your command. Preferably follow the Ubuntu Wiki guide here: [https://help.ubuntu.com/community/SCIM/Chinese?highlight=%28Chinese%29%7C%28input%29](https://help.ubuntu.com/community/SCIM/Chinese?highlight=%28Chinese%29%7C%28input%29)

---

### Post by kinngg on 2007-08-09
Thx that worked!

---

