---
title: "how to install software apps?"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by georgeb1951 on 2006-03-17
just installed ubuntu.  
first very interesting...but the OS installs very easily but applications don't seem to have installers like windows installers...more complicated...so 
second i have the highest level of ignorance of this OS that is possible
three how does one install software like:
i tried to  install wine (i'd like to use Visual foxpro on linux) got the package(whatever that is) and tried to install using synaptic package manager and and got "depends: libstdc++6 but it is not instalable"

four can i install mysql 5.0 using the packagemanager

five what's a good Dummy's book for ubuntu??
TIA
GAB

---

### Post by John.Michael.Kane on 2006-03-17
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)
[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)
[http://makuchaku.info/amnesty/](http://makuchaku.info/amnesty/)

[http://www.winehq.com/site/howto](http://www.winehq.com/site/howto)
[http://www.witch.westfalen.de/Wine-HOWTO/book1.html](http://www.witch.westfalen.de/Wine-HOWTO/book1.html)
[http://www.linux-militia.net/howtos/WineHowto.html](http://www.linux-militia.net/howtos/WineHowto.html)

[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by Mustard on 2006-03-17
I think you might be jumping into the deep end, by installing a new operating system and then trying to do some of the more difficult installations without any prior knowledge of how the system works.

Wine is quite difficult to work with, from my experience, and would require some study to get it doing what you want it to do.  If you still have windows installed, you are probably better off running windows programs in windows.  At least until you have studied how wine works.  If you don't have access to windows, then I would put off doing the more more complex stuff until you have a basic understanding of the operating system.

When you say a good Dummy's book for Ubuntu what type of things are you looking for information on?  There are various online tutorials on the command line, using synaptic etc.  If you pick something specific someone can show you a link that can help.

---

### Post by georgeb1951 on 2006-03-19
1. thanks for the list it's great
2. i do better in a full immersion environment so i tend to jump into the deep end on a regular basis.
thanks for the responses
GAB

---

### Post by az on 2006-03-19
[QUOTE=georgeb1951]just installed ubuntu.  
first very interesting...but the OS installs very easily but applications don't seem to have installers like windows installers...more complicated...so 
second i have the highest level of ignorance of this OS that is possible
three how does one install software like:[/QUOTE]


This is free-libre open-source software.  That means that the way the applications are developed is by allowing others to build on existing code without restrictions.  The software is not property.

The software is developed and interfaces together at the source level.  Since it is inconvenient to download the source and compile everything, each linux distribution compiles everything using the current toolchain so that you don't have to.  You are completely free to get the source for just about any free-libre application, read the file that describes what libraries it needs (and install them) and then compile the app with your own toolchain.  This will work.

Since different distributions have different shared libraries and different version of the toolchain (compiler suite and accessories) it is not usually possible to compile something for, say, Suse and then install it in Ubuntu.  You would have to compile it for Ubuntu for it to work.

That's why there is no installer.  But there are centralised repositories.

Use synaptic (it is a pckage management apllication).  You search synaptic for the application you want, mark it for installation and then tell it to install and it will download all the needed packages from the repositories and install them for you.  This is easier than using package installers like in windows.  A heck of a lot safer, too, since everything that enters the repos must be free-libre software and have a maintainer to look after it.

See the howto on adding repositories to synaptic.
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

You will have access to many more packages by adding the universe repository to your list.

---

