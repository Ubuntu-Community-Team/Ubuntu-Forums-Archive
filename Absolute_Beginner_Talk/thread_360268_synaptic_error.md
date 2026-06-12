---
title: "synaptic error"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Patrickvv on 2007-02-12
ok hello all frist ofim not new to linux nor new to ubuntu but lately weird things has been happening in synaptic. i cannot specify the error exactly but here's the low down

[http://www.linuxforums.org/forum/ubuntu-help/85226-error-synaptic.html](http://www.linuxforums.org/forum/ubuntu-help/85226-error-synaptic.html)

so basically my synaptic is dead cos nothing can be installed.Note that all repos are ticked and applied.

lookinf for solutions..

thanking all


patrickvv

---

### Post by riven0 on 2007-02-13
Did you check for broken packages? I think it's under Status in Synaptic. If no broken packages, close down synaptic, open the terminal and try to force install whatever package is giving you problems. So, it'll be something like:

> sudo apt-get install -f *package_name*

---

### Post by Patrickvv on 2007-02-13
no there's nothing broken (if there were synaptic would have told me)
its just that when i want to install something i get errors.Now i cant specify the error exactly cos they are different..Like for ex : VLC ..when i would try to install it i get error,nearly everything you name it.

any suggestions ?

---

### Post by lamego on 2007-02-13
Please post here the full output of your apt-get install command.

---

### Post by Patrickvv on 2007-02-13
here you go
root@patrick-desktop:/home/patrick# apt-get install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 103 not upgraded.

---

### Post by Patrickvv on 2007-02-14
i think im gonna format my HD and install 6.10..thanks anyways

---

