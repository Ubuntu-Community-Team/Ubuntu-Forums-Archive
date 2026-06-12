---
title: "Installation, Mouse, DeCSS Help"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by Glass_Onion on 2006-01-13
Hey all,
I've had Ubuntu installed for awhile now and am starting to use it more and more. I am getting to the point where I want to start using it as much as possible. 

First thing I'm going to ask for help for is on my mouse. I'm not really expecting their to be anything but it's worth asking, right?  One small thing that's still taking time to get used to is to not use the forward and backward buttons on my mouse since they don't work like they should. The forward one works the same way as right click and the backwards one works in whatever way it sees fit. It's a Logitech LX7 so I'm just wondering if anybody knows of any Third party drivers since I can't find any by Logitech.

Second thing I'm not sure if it's ok or not to ask about, but it's the DeCSS thing, I couldn't find anything about it in the rules though. I've tried a couple of things to get it on my computer and none of them are completling the set up. I've been playing around with Google and I'm not finding anything particually usefull so does anybody here know any websites that will guide me through step by step with everything I need to set it up? If this is illegal to talk about due to the whole US law jazz then I'll delete this bit if a mod or admin asks me to. My prefarred media player is VLC aswell btw if that makes any difference.

I also can't install anything new from the Package Manager. It's telling me to go into the advanced settings as I'll need to uninstall something for it. When I got their it says something about a broken package and using the broken filter to find it. After ok'n that I get the following message. Can anybody tell me what's going on here and what I need to do to possibly fix it? 

```
W: Couldn't stat source package list ftp://ftp.nerim.net unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-i386_Packages) - stat (2 No such file or directory)

```

Thanks in advance for any help you can provide.

EDIT: In case it's needed I'm using Ubuntu 5.10 Breezy Badger.

---

### Post by Zelut on 2006-01-13
I'm not sure about your mouse issue but I can tell you about DeCSS.  Try this:

/usr/share/doc/libdvdread3/examples/install.css.sh (for DVD css support).

Also, your issue about the repositories... you'll want to remove that from your sources.list (etc/apt/sources.list).  You can check out a wiki about that [here]("http://wiki.ubuntu.com/SourcesList") or also use the [source-o-matic]("http://ubuntulinux.nl/source-o-matic") for all the sources you'll need.  (The error is that it isn't connecting to that site, which isn't suggested anyway.)

---

### Post by Glass_Onion on 2006-01-13
Ok I've updated my source.list and backed it up like the first link said. 

I've installed that file under libdvdread3 and DVDs still refuse to work. I used the command line 'sudo apt-get install /usr/share/doc/libdvdread3/examples/install.css.sh'. The Terminal gives me the following errors.

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package

---

### Post by kingsidy on 2006-01-13
the libdvdcss2.deb it attached to the post. download and install to play dvds.

---

### Post by Glass_Onion on 2006-01-13
Thanks for the file. I've just tried installing that one and I'm getting a simmiler response with a lot of  'stat (2 No such file or directory)' errors again. I'm guessing this isn't normall?

EDIT: fixed some spelling.

---

### Post by Zelut on 2006-01-13
Perfect.  Either use his attached file or, I should have been more clear in my instructions.  The path that I included in my original email was actually a file that will retrieve and install CSS for you.  Try this:

cd /usr/share/doc/libdvdread3/examples/
sudo ./install-css.sh

---

### Post by kingsidy on 2006-01-13
extract the libdvdss archive i attached. to do that right click on it then select extract. then fire up the terminal and change to the directory that contains the deb package and type in:> sudo dpkg -i libdvdcss2_1.2.9-1_i386.deb


---

### Post by Glass_Onion on 2006-01-13
Ah yeah, Now it's working. Thanks for those two commands Kuyaedz! 
Also thank you kingsidy for trying to help.

---

