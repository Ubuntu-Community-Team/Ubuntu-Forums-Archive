---
title: "/usr/bin/ld: cannot find -lblas-3"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by vroy on 2007-02-15
Hi,
    while I was trying to install a package in R, I got this error message
/usr/bin/ld: cannot find -lblas-3 

To fix this problem I think I've to install something, which I can't figure out. Can you please help me? I'm using edgy in ubuntu.

---

### Post by Maestro23 on 2007-02-15
May need to enable extra repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then install the package via Synaptic(GUI) or apt-get(command line)

Some links that will help you in the future:

Installing stuff in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Good luck.

---

### Post by vroy on 2007-02-15
Hi, 
    Thanks. But, my sources.list file is edited already and repositories are enabled. But, I can't figure out which package to install.

---

### Post by po0f on 2007-02-15
vroy,

[refblas3](http://packages.ubuntu.com/edgy/libs/refblas3). and possibly [refblas3-dev](http://packages.ubuntu.com/edgy/devel/refblas3-dev).

---

### Post by vroy on 2007-02-16
Thanks,
               I installed refblas3 and refblas3-dev and I'm not getting the previous error anymore, but instead I'm getting the following message
/usr/bin/ld: cannot find -lgfortran
Both g77 and g77-3.4 is installed in my laptop. Can anybody please tell me which package should I install?

---

### Post by vroy on 2007-02-16
I could fix it with
apt-get -y install gfortran

---

### Post by Robsteranium on 2008-06-06
> **vroy said:**
> apt-get -y install gfortran

I should've guessed!

Too bad you can't *thank* people in the archive... Cheers vroy

---

