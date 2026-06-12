---
title: "Not all updates can be installed"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by milad on 2007-03-02
When i try to update ubuntu i see this message:

[I]Not all updates can be installed
run a distribution upgrade to install as many updates as possible

this can be caused by an incomplete upgrade, unofficial software packages or by running a development version. [/I]

does anybody know what this means and how i can fix it?

---

### Post by 23meg on 2007-03-02
Are you using Edgy? Do you have any extra repositories in your sources.list? Please post its contents.

---

### Post by xyz on 2007-03-02
[ADD REPOS DAPPER]("http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29")
[ADD REPOS EDGY]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29")

---

### Post by mcduck on 2007-03-02
If you are using the Update Manager, try with Synaptic instead. Perhaps some update needs to install additional packages or something. Update Manager doesn't do that.

So, open Synaptic, click 'Reload', and then 'Mark All Upgrades' and finally 'Apply'.

---

### Post by Bachstelze on 2007-03-02
```
sudo apt-get dist-upgrade
```

---

### Post by milad on 2007-03-03
Yes i am using edgy and here is my sources:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) edgy main restricted 
deb [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) edgy universe multiverse 
deb [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas all 

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse 

# Upstream Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main 

# Upstream Opera
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free 

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main 


#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

#XFarsiDic
deb [http://parsix.org/packages](http://parsix.org/packages) sid main

---

