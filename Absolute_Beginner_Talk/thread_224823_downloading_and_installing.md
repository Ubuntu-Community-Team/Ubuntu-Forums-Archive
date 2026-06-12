---
title: "downloading and installing"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by bobanshirl on 2006-07-28
I have got Dapper installed,I can get on line,my printer works and at this moment everything is rosy,I would like to know how to download programs and install software,ie from a CD and also at the moment I am downloading over 100 updates do I have to do anything after installing them.Thanks.

---

### Post by benuski on 2006-07-28
You don't have to do anything to the updates, they just install themselves. 

Also, in Linux you don't really install software from cds.  You download it from the repositories, and then it sets itself up, or you download it from the internet.  [This]("http://www.ubuntuforums.org/showthread.php?t=179797") post gives a lot of good information about the various installation processes.

---

### Post by davebgimp on 2006-07-28
> **bobanshirl said:**
> I have got Dapper installed,I can get on line,my printer works and at this moment everything is rosy,I would like to know how to download programs and install software,ie from a CD and also at the moment I am downloading over 100 updates do I have to do anything after installing them.Thanks.

As far as the updates go...no. Updated kernels will be used the next time you boot, everything else shouldn't require any additional work.

As far as installing programs, Synaptic for Gnome, Adept for Kubuntu. As far as a CD goes, it depends on what it is. Chances are, for Linux apps, you'll be moving the files local and compiling or running a script... it depends is what I'm trying to say.

---

### Post by Rumor on 2006-07-28
The updates might require a reboot, but nothing more than that.

You can install programs from the applications menu by clicking Applications Add/Remove. 

You can install programs through synaptic Click System > Administration > Synaptic Package Manager. Synaptic has a good search function. You want to install a solitaire game, for example, click search and enter solitaire. The results will display for you to browse and you can simply check off what you want to install.

You can install through the command line as well using "apt-get install name-of-program"

---

### Post by davebgimp on 2006-07-28
> **Rumor said:**
> You can install through the command line as well using "apt-get install name-of-program"

**sudo** apt-get install name-of-program ;)

---

