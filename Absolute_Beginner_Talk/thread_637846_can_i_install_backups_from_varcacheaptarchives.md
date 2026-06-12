---
title: "can i install backups from /var/cache/apt/archives"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by quantum2222 on 2007-12-11
hi their people now i am a complete ubuntu person its been months i touched windows 

i was wondering if i copy all .deb packages from /var/cache/apt/archives to a secure place lika a pen drive or anything and format my ubuntu partitions in case of error or like giving it more space(changing partition table) and all that  , reinstall it could i justt double click these .deb packages to install my pre downloaded softwares through synaptics this way i could also help my friend who is keen on trying on linux but doesnt have internet connection on his machine

is this possible please reply i am a newbie but keen on learning this amazing OS:):popcorn:

---

### Post by shafin on 2007-12-11
you can install the package AptOnCD and convert all packages on the cache folder to a CD repository.Then whenever you insert the CD,you can use it as a repository.

Now,to answer your question,you can do this,but depending on dependencies,some packages will be needed to be installed in particular combinations and some might will not be installable.Just use AptOnCD.Even if you do not have a CD burner,you can get a CD image and burn from another place

---

