---
title: "libnotify-bin?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by dfrohardt on 2007-10-27
When trying to use Ubuntuzilla it will not run the .deb because the dependency libnotify-bin is not satisfied.

How would I go about fixing this?

---

### Post by linuxwizard on 2007-10-27
Install libnotify-bin through Synaptic. Than try Ubuntuzilla

---

### Post by dfrohardt on 2007-10-27
I tried to reinstall through the package manager and that didn't work.  I also completely uninstalled and the reinstalled libnotify and that did not work. 

I googled the problem and searched on the forums but I could not find anyone that had the same exact problem.

Is it possible that I need to reinstall Dapper?

---

### Post by dfrohardt on 2007-10-27
I got it.  I was updating libnotify1 and not libnotify-bin which was in a different repository.

Thanks for the help.

---

### Post by kostkon on 2007-10-27
> **dfrohardt said:**
> I got it.  I was updating libnotify1 and not libnotify-bin which was in a different repository.

Thanks for the help.

Indeed, [*libnotify-bin*]("http://packages.ubuntu.com/feisty/utils/libnotify-bin") is different from [*libnotify1*]("http://packages.ubuntu.com/feisty/libs/libnotify1") and you need to install it yourself. 

In my case, I needed to install *libnotify-bin* in order to get notifications from *Floola*. *X-Chat* also, from version 2.8.4 and later, is using it.

---

