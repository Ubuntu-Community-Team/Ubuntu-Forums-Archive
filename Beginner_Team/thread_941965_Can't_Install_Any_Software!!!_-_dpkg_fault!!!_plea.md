---
title: "Can't Install Any Software!!! - dpkg fault!!! please help"
date: 2008-10-08
forum: Beginner Team
---

### Post by Carter0687 on 2008-10-08
Whenever I try and run synaptic program manager or install codecs, and on other occasions I get a message saying I have to manually run 'dpkg --configure -a' to correct the problem. Also when nothing seems running and I try and install a software program it says other software maangers are still running?, when there not. :confused::confused::confused:

---

### Post by Joeb454 on 2008-10-08
Open a Terminal by clicking Applications &#8594; Accessories &#8594; Terminal

Enter ```
sudo dpkg --configure -a
``` And then - when asked for your password - enter it, and do not worry that it's not accepting it, because it is, it just won't show you that.

Then when you have entered your password, hit enter.

That *should* fix the problem :)

---

