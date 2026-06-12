---
title: "Some Noobie Questions"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by hadem on 2006-01-31
Sorry, I have a few of noobie questions.

I have just found out about ubuntu today and so far what I know it sounds great.  I am sick of using Windows and have been sick of using Windows for quite some time now.  (Perfect time that I learned about ubuntu.)

So, on with the noobie questions:
1. What are GDM themes?
2. What is Metacity?
3. Does anyone have any links or suggestions to help me get ubuntu running on VMware?  I want to install it that way and get a feel for it before I dive head first.

Any other info/links that you have for ubuntu noobies (who don't want to be noobies for long) is greatly appreciated.

Thanks!  :)

---

### Post by aysiu on 2006-01-31
[QUOTE=hadem]1. What are GDM themes?[/quote] They're for the login screen.

> 
2. What is Metacity? I believe it's the window manager Gnome uses. Gnome is a full desktop environment. Metacity just manages the look and feel.

> 
3. Does anyone have any links or suggestions to help me get ubuntu running on VMware?  I want to install it that way and get a feel for it before I dive head first. Use [the live CD](http://mirror.yousendit.com/ubuntu/5.10/ubuntu-5.10-live-i386.iso). It doesn't affect your hard drive. It runs completely off the CD itself and your computer's RAM.

---

### Post by kaamos on 2006-01-31
1. Gdm themes modify the gnome login screen.
2. Metacity is the window manager used in gnome. So it skins window titlebars, manages window behaviour and such.
3. You can get the pre-made virtual machine image and use it in vmware [http://www.vmware.com/vmtn/vm/ubuntu.html](http://www.vmware.com/vmtn/vm/ubuntu.html)

Some links:
[http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html)
[http://ubuntuguide.org/](http://ubuntuguide.org/) (its for ubuntu 5.04 but most of the stuff is still ok)

---

### Post by hadem on 2006-01-31
That sounds simple enough.  Thanks for the very fast response.

One follow up question though, Live CD, can I download everything I need for that off of the ubuntu website?

---

### Post by hadem on 2006-01-31
I think I found out where I can get the Live CD from.

[http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/)  Right?

So, when I have the Live CD, I just put it in, and start up my PC and it does not install ubuntu, but lets me use it as if it were installed?

---

### Post by kaamos on 2006-01-31
Yes, thats right. Just remember to burn the iso as an image. [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by hadem on 2006-01-31
Thanks for all your help!  I really appreciate it.  :)

Now if only I had the Live CD with me right now.

(I am kind of bummed that I wont be able to play with ubuntu tonight because I don't have a super fast connection for downloading the Live CD.)

---

### Post by Rasymas on 2006-01-31
i don't want to create another topic so if you don't mind I'll post my problem here:

What do I have to do in order to get rid of these error messages?

```
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-backports Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-custom Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-custom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-extras Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-extras_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/madwifi Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_madwifi_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-backports Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-custom Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-custom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-extras Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-extras_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/madwifi Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_madwifi_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages)

```

I think smth not right in my repositories so please help me if you can ;)

---

### Post by Lord Illidan on 2006-01-31
Give us your sources.list

```
cat /etc/apt/sources.list
```

---

### Post by Rasymas on 2006-01-31
Here it is ```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb file:///home/arnoldas/gcc-3.4 ./

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe m ultiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted univer se multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-fr ee
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free no n-free

deb http://deb.opera.com/opera/ etch non-free
deb http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom b reezy-extras freenx madwifi
deb-src http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-cust om breezy-extras freenx madwifi

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe m ultiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted univers e multiverse
## created by arnieplanetremoved

```

btw... do you know how to check what is my IP now? cuz I have a dyn one and don't know where to look for it :)

---

### Post by Cesium on 2006-02-02
[QUOTE=Lord Illidan]Give us your sources.list

```
cat /etc/apt/sources.list
```[/QUOTE]

How do I get into my sources.list?  I get "permission denied."  Thanks.

<edit> Nevermind, I figured it out.

---

### Post by Cesium on 2006-02-02
[QUOTE=Rasymas]i don't want to create another topic so if you don't mind I'll post my problem here:

What do I have to do in order to get rid of these error messages?

```
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-backports Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-custom Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-custom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-extras Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-extras_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/madwifi Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_madwifi_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-backports Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-custom Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-custom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-extras Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-extras_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/madwifi Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_madwifi_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages)

```

I think smth not right in my repositories so please help me if you can ;)[/QUOTE]

[COLOR="Red"]Rasymas[/COLOR], check out this site.  This may help with your sources.list
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

