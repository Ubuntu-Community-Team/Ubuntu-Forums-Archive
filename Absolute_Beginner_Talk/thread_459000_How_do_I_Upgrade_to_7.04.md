---
title: "How do I Upgrade to 7.04"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by garthcrocker on 2007-05-30
Can I upgrade to 7.04 from 6.06 without a total reinstall? If so - how?

---

### Post by taurus on 2007-05-30
You need to go from 6.06 -> 6.10 -> 7.04.

---

### Post by Seisen on 2007-05-30
First you would need to upgrade to 6.10 then upgrade to 7.04. I have done it so I know it works. Here are some links to help you out.

[http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html]("http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html")

[http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html]("http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html")

[http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html]("http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html")

---

### Post by mlentink on 2007-05-30
"Users of Ubuntu 6.10 can upgrade to Ubuntu 7.04 by a convenient automated process. Complete instructions may be found at www.ubuntu.com/getubuntu/upgrading."

---

### Post by garthcrocker on 2007-05-30
Many thanks guys:p! If I'm not back within a week send out a search party!

---

### Post by finer recliner on 2007-05-30
i went from 6.06 >7.04 

i was recommended to reformat and install 7.04 from scratch instead of hoping that 2 upgrades went smoothly.

this was actually very easy:
- just back up your $HOME folder and a couple system files (xorg.conf, sources.list and such)
-reformat, install 7.04. install updates
-restore all your backed up files to their proper places
-start doing "sudo apt-get install xxx" for any applications you want to reinstall. since nearly all applications store their preferences in a ".xxx" folder in your $HOME, most should automatically know your settings and accounts from your previous set up.

---

