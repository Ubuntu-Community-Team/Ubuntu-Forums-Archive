---
title: "XMMS Help"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by lavarock09 on 2005-08-09
Hey All,

I Am trying to Install XMMS on my Ubuntu Linux

I could have this wrong but, I have opened Terminal and typed

cd xmms-1.2.10
./configure
make
make install

I know this is wrong because I'm not telling it where the xmms-1.2.10 directory is.

So how do I do It,

The xmms-1.2.10 is in Desktop/My Documents/Downloads/XMMS/xmms-1.2.10

Thanks

Lavarock09

---

### Post by heimo on 2005-08-09
Is there a reason you want to compile XMMS yourself? You should probably use synaptic to install software. Or open terminal and type *sudo apt-get install xmms*

Sypaptic:
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

Ubuntu repository has XMMS:
[http://packages.ubuntu.com/hoary/sound/xmms](http://packages.ubuntu.com/hoary/sound/xmms)

Useful guide:
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by lavarock09 on 2005-08-09
thanks for the info on that, I'm only just learning, where can I download synaptic and how do I set it up, I'm extremely new to ubuntu and Linux

---

### Post by heimo on 2005-08-09
[QUOTE=lavarock09]thanks for the info on that, I'm only just learning, where can I download synaptic and how do I set it up, I'm extremely new to ubuntu and Linux[/QUOTE]

Synaptic is installed by default and you should be able to find it in a top menu - I think it's System->Administration->Synaptic Package Manager or something similar. It's the preferred way to install software on Ubuntu. There's lots of software available this way and it's the most convenient way to install, no need for that ./configure;make;make install stuff (compiling from source code).


EDIT: Be sure to check that unofficial Ubuntuguide, it's a great resource of information.

---

### Post by lavarock09 on 2005-08-09
when I start up synaptic I get this error

> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)


And How do I get it to find the XMMS Install stuff

---

### Post by heimo on 2005-08-09
On the applications menu (I think it's under system tools) is Terminal. Open that and type:

 ```
sudo apt-get update
sudo apt-get install xmms

``` 

Do you get the same errors? Do you know if you need proxy to connect to internet? Is your web browser working correctly and can you open one of those urls that are on error messages?

EDIT: Check preferences in Synaptic (proxy).

---

### Post by lavarock09 on 2005-08-09
when I run sudo apt-get update

i get this error

> E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


EDIT: Just to tell you, when I run sudo apt-get install xmms i get this error

> chris@linuxchris:~$ sudo apt-get install xmms
Reading package lists... Done
Building dependency tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package xmms has no installation candidate


---

### Post by heimo on 2005-08-09
First error was probably because you had some other application using dpkg-database (probably Synaptic) and latter was because update failed. Can you access for example [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) using your web browser? Did you have to enter proxy settings for your web browser? (you may need to do this to Synaptic, too)

---

### Post by lavarock09 on 2005-08-09
[QUOTE=heimo]First error was probably because you had some other application using dpkg-database (probably Synaptic) and latter was because update failed. Can you access for example [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) using your web browser? Did you have to enter proxy settings for your web browser? (you may need to do this to Synaptic, too)[/QUOTE]

I can access the site, it says index of /  ubuntu/

etc. and I have done all Proxy things

When i search for xmms in synaptic it comes up with xmms at the left hand side so it says

**All**
xmms

but when you click xmms it does nothing, 

do I have to drag something somewhere or what

---

### Post by heimo on 2005-08-09
[QUOTE=lavarock09]I can access the site, it says index of /  ubuntu/

etc. and I have done all Proxy things

When i search for xmms in synaptic it comes up with xmms at the left hand side so it says

**All**
xmms

but when you click xmms it does nothing, 

do I have to drag something somewhere or what[/QUOTE]

I don't use Synaptic, but I believe you will need to right-click, select for install and then hit Apply button - or something like that. :) I know you'll figure it out. No more those error messages?

---

### Post by lavarock09 on 2005-08-09
It seems to have installed it,

I just hope it works,

I will post again if it does, Thanks for all your help dude,

Lavarock09

---

### Post by heimo on 2005-08-09
Be sure to check this (for mp3 support):
[http://ubuntuforums.org/showthread.php?p=293119]("http://ubuntuforums.org/showthread.php?p=293119#post293119")

Or that Ubuntuguide I referred earlier.

---

### Post by lavarock09 on 2005-08-09
whenever I press play when trying to play an MP3 it just crashes the program

---

### Post by heimo on 2005-08-10
[QUOTE=lavarock09]whenever I press play when trying to play an MP3 it just crashes the program[/QUOTE]

Running the program from terminal (open terminal, type xmms [enter]) may give clues why this is happening. Have you tried playing the same file using other programs, like totem or rhythmbox?

---

### Post by lavarock09 on 2005-08-10
Thanks for all your help dude, but In the end I have scrapped the idea of xmms and have installed gstreamer0.8-mad and now music player plays mp3's

---

### Post by heimo on 2005-08-10
[QUOTE=lavarock09]Thanks for all your help dude, but In the end I have scrapped the idea of xmms and have installed gstreamer0.8-mad and now music player plays mp3's[/QUOTE]

No problem! End result is what matters - in this case: playing music without problems. Good you found a solution. :)

---

### Post by xmastree on 2005-08-10
Reading through all this, it sounds to me that you haven't enabled the extra repositories. Searching for xmms in synaptic should give a list of applications on the right side, like this:

[IMG]http://www.xmastree.34sp.com/ubuntu/xmms.png[/IMG] 

If yours shows nothing, then the application list isn't up to date.

Do [**this**](http://ubuntuguide.org/#extrarepositories) first, (don't forget step 6) then try again.

You're missing out on a lot of software if you don't.

---

