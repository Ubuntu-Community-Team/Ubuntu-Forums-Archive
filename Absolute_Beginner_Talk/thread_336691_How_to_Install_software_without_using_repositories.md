---
title: "How to Install software without using repositories"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by subbu171 on 2007-01-11
HI i am a new user to Ubuntu.I find that to install softwares(such as my favorite vlc media player) i need to use the synaptic manager or the command in the terminal.But i don't have the internet at home.Is there any way to download softwares on a windows machine that i have at office and install it in the ubuntu machine that i have in home.

TIA
Subbu

---

### Post by jem7v on 2007-01-11
As long as they don't bring up any unexpected dependencies, yes.  You can usually find the .deb files for what you need on the web and then just put them on your removable media of choice and install them on the Ubuntu machine.  As long as dependencies are satisfied, installing a .deb is as easy as double clicking on the file and then pressing the Install button.

Here's a massive collection of .debs you can download: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) I've used this method a few times.

---

### Post by subbu171 on 2007-01-12
thanks a lot i have got the .deb package i needed to install.:)

---

### Post by Delkster on 2007-01-12
> **subbu171 said:**
> thanks a lot i have got the .deb package i needed to install.:)

Many packages *do* have external dependencies, however. In other words, many programs need some other programs to be installed in order to function or in order to provide some features. For example the VLC package may require some program libraries in order to play certain kinds of video or audio.

The point is that when a library provides certain functionality, all applications that need it will be able to just use the library for that, so every application doesn't need to implement the same functionality on their own. This makes developing the software easier and also saves disk space and memory. However, that also means that the programs aren't self-contained and thus require those other components in order to function.

If you have internet access, the package manager will automatically install those 'dependencies' for you, but if you install packages manually from a .deb file on a machine that isn't connected to the internet, you'll need to fetch them yourself.

The package description pages on [http://packages.ubuntu.com](http://packages.ubuntu.com) also list the dependencies of each package, so in principle you can go there and also download all packages your program depends on, just to be sure in case you don't already happen to have them all installed. The problem is that those other required packages may also be dependent on yet more packages. This is called the 'dependency hell' which the semi-automatic package manager is meant to solve.

Good luck, though, but actually extensive use of Ubuntu on a computer without Internet access may not be very convenient due to this very fact.

---

### Post by tonyr1988 on 2007-01-12
You may also want to check out these threads:

[Linky 1]("http://www.ubuntuforums.org/showthread.php?t=34113")
[Linky 2]("http://www.ubuntuforums.org/showthread.php?t=310020")

The second one might be easiest if you're doing a lot of installing. However, I haven't tried either method, so I'm not sure which one works best.

And you could always go through [http://packages.ubuntu.com](http://packages.ubuntu.com) as previously stated, but from experience, it's miserable for some things. Avoid at all costs. :)

---

