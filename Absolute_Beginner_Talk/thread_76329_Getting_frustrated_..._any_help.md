---
title: "Getting frustrated ... any help?"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by MartinAustin on 2005-10-15
Hi,

I just did a fresh install of Ubuntu, and I am going through UbuntuGuide.org to try to install something (ANYTHING, at this point!).  I tried the chat on IRC, but no one seems to be awake.

This is what I get when I try to install, pretty much anything:

```
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  azureus: Depends: libcommons-cli-java but it is not going to be installed
           Depends: liblog4j1.2-java but it is not going to be installed
           Depends: libswt-gtk-3.1-java but it is not going to be installed
           Depends: sun-j2sdk1.5 but it is not installable or
                    java2-runtime but it is not installable
  opera: Depends: libqt3-mt (>= 3.3.4) but it is not installable or
                  libqt3c102-mt (>= 3.3.4) but it is not going to be installed
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dist s_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory )
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s olution).

```

This is trying sudo apt-get isntall azureus

I'm loving the interface features of Ubuntu so far, but if it's going to be this much of a pain in the ass to install *anything*, then maybe it's not right for me.  I hope it is right for me though, 'cause I'm tired of Windows.

I am also a bit confused as to why most anything I try to install requires similar libraries, yet they are not already installed in Ubuntu?  I did sudo apt-get update, but that didn't seem to do anything.

Thanks in advance for listening to what I'm sure is a common rant,  but from a genuinely interested user.

---

### Post by aysiu on 2005-10-15
Well, I'll tell you first that azureus is not "anything." "Anything" would be something like mozilla-thunderbird or kolourpaint. Azureus depends on Java, which makes things a bit more complicated. Also, the Ubuntu Guide is a bit outdated now, as Ubuntu's in sort of a transitional period--for example, the mirrormax repositories are no longer valid.

Try following these directions:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by aysiu on 2005-10-15
It looks as if Arnieboy may have your solution:

[HOWTO: Installing Azureus on Breezy](http://www.ubuntuforums.org/showthread.php?t=75272)

---

### Post by Kokanee on 2005-10-15
It looks like there are broken pakages.  You need to fix that before *anything* else will install.

```
sudo apt-get -f install
```

---

