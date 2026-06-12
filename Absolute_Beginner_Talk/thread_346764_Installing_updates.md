---
title: "Installing updates"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-01-26
When installing updates on dapper is it safe to just click the little orange square in the upper right hand corner and then install all updates, a la windows, or does Linux/Ubuntu require you to be more knowledgeable and selective in which updates you install? I have done this twice and it killed the OS each time. Now I am a'scared of updates. This may be a hardware related problem. Your opinions please?

---

### Post by lamego on 2007-01-26
Usually you don't need to be careful with the updates, unless there is some broken update (which happens) with the kernel or with your graphics driver, on that case you may not be able to login into the graphical manager after the upgrade.
If that happens you just need to check the forum, there is usually a warning on the top with instructions how to fix the problem.

Those are rare situations...

---

### Post by citizenofnowhere on 2007-01-26
Hi!

Things to be careful about when updating - pretty much anything that starts with "kernel", "linux". The reason being that when you upgrade those packages in Dapper (they are the very basis of your system) the program that refreshes your bootup sequence gets a little wonky. I've had problems booting up when upgrading kernels before.

Other than that you should be ok. Other packages that affect your system startup are "gdm", "kdm" but I've never had problems with these and can't remember the last time I saw an upgrade that wasn't part of a new release.

If you want to say upgrade from Dapper to Edgy (which is a good idea) that should be pretty safe as well - I did that.

But unless you've made manual changes to files somewhere I suggest to just backup your "home" folder and reinstall. 

Here is a useful guide for backing up stuff: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

It shows you how to backup just a few folders. 

Tip: It's not a bad idea to have your "home" folder on a separate partition (here's how: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)) - that way if you need to reinstall all your settings are safe :) Just make sure you remember to tell the installer to NOT wipe the partition.

If you're determined not to download all your programs again, use this how-to to backup all your programs onto a cd:

[http://www.ubuntugeek.com/create-backup-of-all-installed-packages-using-aptoncd-in-ubuntu.html](http://www.ubuntugeek.com/create-backup-of-all-installed-packages-using-aptoncd-in-ubuntu.html)

---

### Post by paydaydaddy on 2007-01-26
Thanks. When I have more time I will read through the info.

---

