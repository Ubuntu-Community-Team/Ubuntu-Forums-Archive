---
title: "Oops... What'd I do now?  Plus a quick question."
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by WackToMack on 2005-12-26
Hello everyone.  I was messing with Ubuntu like I always do, well, actually I was messing with Synaptic trying to figure out how it works, when I... well... I don't really know what I did.  But I know I did something because whenever I open up Synaptic again I get this error message :

W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

Anyone know what it means and how to fix it? :confused:  Synaptic still works normally, but I wanna make sure I didn't mess anything up before I start to go package crazy again.

Also, sometimes when I download and install programs using Synaptic, they don't show up in my "Applications" menu.  Most of the time however after I make a reboot of my system they do show up.  The last program did not however.  I had downloaded and installed Epiphany Web Browser and GIMP.  Both did not show up in the "Applications" menu.  After a reboot, I found GIMP in the menu under "Graphics", where it's supposed to be, but Epiphany was not under Internet.  After some more searching, I finally found it in Debian under Net, but it's missing it's icon.  Why is it located there and not in my normal "Internet" menu?  Anyway to fix this?  Thanks in advance for the help.

---

### Post by ardchoille on 2005-12-26
[QUOTE=WackToMack]Hello everyone.  I was messing with Ubuntu like I always do, well, actually I was messing with Synaptic trying to figure out how it works, when I... well... I don't really know what I did.  But I know I did something because whenever I open up Synaptic again I get this error message :

W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

Anyone know what it means and how to fix it? :confused:  Synaptic still works normally, but I wanna make sure I didn't mess anything up before I start to go package crazy again.

Also, sometimes when I download and install programs using Synaptic, they don't show up in my "Applications" menu.  Most of the time however after I make a reboot of my system they do show up.  The last program did not however.  I had downloaded and installed Epiphany Web Browser and GIMP.  Both did not show up in the "Applications" menu.  After a reboot, I found GIMP in the menu under "Graphics", where it's supposed to be, but Epiphany was not under Internet.  After some more searching, I finally found it in Debian under Net, but it's missing it's icon.  Why is it located there and not in my normal "Internet" menu?  Anyway to fix this?  Thanks in advance for the help.[/QUOTE]
You can open a term and run

```

sudo apt-get update

```

That will update your sources, this usually gets rid of the annoying message for me.

When you install an app and it doesn't show in the menus, open a term and do:

```

killall gnome-panel

```

That will cause the gnome panel to restart and usually updates the menus.

You can use the menu editor to edit (add new items or hide undesired ones) the menus.

---

### Post by WackToMack on 2005-12-26
Ok... new problem... When I used this code that you gave me...

```
sudo apt-get update
```

This is what happened :

Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release.gpg
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [19.6kB]
Get:7 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:8 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Get:10 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:11 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:12 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:13 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
99% [Waiting for headers]

And... now it's stuck at that and won't move...

---

### Post by ardchoille on 2005-12-26
Well, you can let it continue, or you can press CTRL+C to quit it, the delay could be due to lot of traffic at the site it is trying to access. I find that stopping it and re-starting it after a few minutes usually works. But, it's nothing to be alarmed about.

---

### Post by WackToMack on 2005-12-26
Update...

This is now what has appeared...

Err [http://public.planetmirror.com](http://public.planetmirror.com) breezy Release.gpg
  Connection failed [IP: 203.16.234.90 80]
Ign [http://public.planetmirror.com](http://public.planetmirror.com) breezy Release
99% [Connecting to public.planetmirror.com (203.16.234.90)]

Still nothing to sweat over or what?

---

### Post by rikai on 2005-12-30
[QUOTE=WackToMack]Update...

This is now what has appeared...

Err [http://public.planetmirror.com](http://public.planetmirror.com) breezy Release.gpg
  Connection failed [IP: 203.16.234.90 80]
Ign [http://public.planetmirror.com](http://public.planetmirror.com) breezy Release
99% [Connecting to public.planetmirror.com (203.16.234.90)]

Still nothing to sweat over or what?[/QUOTE]

I've been having the exact same symptoms.
seems to me like theres something up with the planetmirror mirror.
I have:
> deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free
in my /etc/apt/sources.list, and it was giving me errors as well.
I just commeneted it out with a ## until i heard more news about it.

---

