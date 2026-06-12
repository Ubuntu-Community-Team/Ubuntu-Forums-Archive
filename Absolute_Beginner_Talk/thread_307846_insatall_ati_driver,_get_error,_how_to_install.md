---
title: "insatall ati driver, get error, how to install?"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Half-man on 2006-11-27
hi,  Im tryng to install Ati driver to my laptop. but, i cant get it to install..  got a error in my terminal: ./ati-installer.sh: 176: Syntax error: Bad substitution

hov do i fix this?
i im runing Ubuntu 6.06 
on a HP Pavilion zd8000


thx for al help i get =)


Fix:
This is a dash/bash conflict ATI wants bash, Edgy uses dash.
Try running this before running ATI driver:
Code:

sudo mv /bin/sh /bin/SH sudo ln -s /bin/bash /bin/sh

Afterwards, once you've finished with ATI's driver run

Code:

sudo mv /bin/SH /bin/sh

---

