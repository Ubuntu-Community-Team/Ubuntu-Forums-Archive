---
title: "uninstalling a program"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by Cubicegg on 2006-01-13
i have installed hula but want to know how do i uninstall this and restart, or do i just install back over it?

also can you explain what a repositary is - thanks :)

---

### Post by dcast on 2006-01-13
how did you install hula? you can use synaptic package manager so in terminal type "sudo synaptic" then enter your password at the prompt or in the terminal use "apt-get -r hula" (i think). A repository is where you can download programs to be installed by synaptic.

---

### Post by Mr_Grieves on 2006-01-13
You may remove software via Synaptic or via
```

sudo dpkg -r packagename

```
You also might wanna check this out: [https://wiki.ubuntu.com/forum/software/CheckInstall](https://wiki.ubuntu.com/forum/software/CheckInstall)

You could say that a repository is a place where software is stored.
Adding a repository in Synaptic for example makes the software there available to you. Read more here:  [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Delkster on 2006-01-13
Repositories are explained in the Ubuntu wiki at [https://wiki.ubuntu.com/Repositories](https://wiki.ubuntu.com/Repositories)

When you install an application with the Synaptic package manager or via the 'Add Application' item in the Ubuntu menu, it'll fetch the application package for you. Ubuntu on your computer knows where to get such applications because it knows the locations of the official Ubuntu repositories on the 'Net and possibly on the Ubuntu CD if you use that, and those repositories can in turn tell Ubuntu on your computer what packages are available from them.

That way Ubuntu can show you a list of packages available from the repositories and get and install them for you when you click on them. Likewise, when updates become available for the packages you have installed, the package management system on your computer can automatically find out about the available updates and thus offer easy and painless software updates.

By default the official Ubuntu repositories are enabled (so package management on your system knows about the software available in those repositories and can install and update software from them) but it's also possible to add other repositories that have software you need. Some third parties may make software not included in the official Ubuntu distribution available through their own repository.

Hopefully that serves to explain it a bit. Such software repositories certainly aren't a familiar concept for most people more familiar with Windows (I make the risky assumption that you're one of them).


How you'd go about reinstalling the application and 'starting over' depends on what you really want to do. Why do you want to start over? Hula is a server package so I assume that it only uses global configuration files (not user-specific ones like desktop software generally does). If you mark the package for `complete removal' in Synaptic, it'll also remove global configuration files and thus allows you to restart from the default configuration if you reinstall the package afterwards. The plain `remove' option removes program files but leaves the configuration intact.

If you installed hula from a third party (i.e. not through the package management tools like Synaptic or command-line package management tools or somesuch), the way to go about restarting completely with the piece of software depends on how you installed it. Generally it's easiest to install software from the Ubuntu repositories with the package management tools if the package is available from them.

---

