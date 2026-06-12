---
title: "uninstall core programs"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by SpinningAround on 2007-11-01
I don't want some of the packages that come with ubuntu like bittorrent and serpentine problem with this is that if I chose to uninstall these do synaptic want to remove ubuntu-desktop among other things. Is it safe to uninstall them or can it cause problems?


Also I notice if I install a program I get the necessary libs for it but when I uninstall it do I only uninstall the package and not the libs. So how do I remove all the libs that I ain't have any use for?

---

### Post by jayaramk on 2007-11-01
to remove those programs which you do not use u can use the synaptic package manager and mark for removal only that particular application..... if u remove the ubuntu-desktop... u loose your complete desktop GUI and you get only the terminal thats is its a pure CLI....

and once you install any program ands find it in the synaptic package manager.... there are two options always present in it... 
1. mark for removal-only removes the applciation
2. marks for complete removal-remover the application along with the libraries it downloaded!!!!

---

### Post by Rich78 on 2007-11-01
Are the libraries often shared?

In other words if you uninstall the app and the libraries is it likely to break things?

---

### Post by SpinningAround on 2007-11-01
Here is a image what happens when I try to remove bittorrent using removal-only.
Swedish Interface
[[img]http://pici.se/thumbs/t_WzOuldgXd.gif[/img]](http://static.pici.se/pictures/WzOuldgXd.png)

---

### Post by SpinningAround on 2007-11-01
> **Rich78 said:**
> Are the libraries often shared?

In other words if you uninstall the app and the libraries is it likely to break things?

Unsure if they are shared or not but if they are installed together with a other program, wouldn't it be safe to remove them when you remove that program?

---

### Post by rsambuca on 2007-11-01
> **jayaramk said:**
> to remove those programs which you do not use u can use the synaptic package manager and mark for removal only that particular application..... if u remove the ubuntu-desktop... u loose your complete desktop GUI and you get only the terminal thats is its a pure CLI....

and once you install any program ands find it in the synaptic package manager.... there are two options always present in it... 
1. mark for removal-only removes the applciation
2. marks for complete removal-remover the application along with the libraries it downloaded!!!!

INCORRECT!!!

You are safe to remove these unwanted packages.  The 'ubuntu-desktop' is NOT your gui, so do not worry.  The 'ubuntu-desktop' is a meta-package that simply is a list of packages/dependencies.  It is basically the set of basic programs that the Ubuntu developers have installed by default.  

The only catch is, when you want to upgrade to the next version of Ubuntu, you will have to re-install the ubuntu-desktop meta-package first.  This will get you to the default setup for the upgrade process.

After removing a package, you can run "sudo apt-get autoremove" in a terminal and it will get rid of any orphaned dependencies you no longer need.

---

### Post by shmengie on 2007-12-30
> **rsambuca said:**
> INCORRECT!!!

You are safe to remove these unwanted packages.  The 'ubuntu-desktop' is NOT your gui, so do not worry.  The 'ubuntu-desktop' is a meta-package that simply is a list of packages/dependencies.  It is basically the set of basic programs that the Ubuntu developers have installed by default.  

The only catch is, when you want to upgrade to the next version of Ubuntu, you will have to re-install the ubuntu-desktop meta-package first.  This will get you to the default setup for the upgrade process.

After removing a package, you can run "sudo apt-get autoremove" in a terminal and it will get rid of any orphaned dependencies you no longer need.

obviously, rsamuca has a lot of beans, so i think he probablyt knows what he's talking about. to be safe, though, can anyone confirm that uninstalling ubuntu-desktop is non-fatal? i'm looking to remove serpentine, but am not looking to hose my gui or my system.

thx!

---

### Post by LaRoza on 2007-12-30
> **shmengie said:**
> obviously, rsamuca has a lot of beans, so i think he probablyt knows what he's talking about. to be safe, though, can anyone confirm that uninstalling ubuntu-desktop is non-fatal? i'm looking to remove serpentine, but am not looking to hose my gui or my system.

thx!

ubuntu-desktop is a meta package. If you uninstall any part of it, it is uninstalled so to speak. It doesn't take every component with it though. It is like the Beatles, take John away, the Beatles don't exist, but the others are there.

Beans don't mean anything :) Even mine.

---

### Post by shmengie on 2007-12-30
so, if i understand correctly, 'ubuntu-desktop' is just the name the developers gave to a certain pre-packaged set of apps, yes? so, uninstalling serpentine, for example, doesn't break the desktop. it just breaks up the set of core 3rd party apps the developers feel should be in all base installs of ubuntu.

that sum it up about right?

---

