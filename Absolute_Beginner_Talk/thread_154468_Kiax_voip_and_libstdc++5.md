---
title: "Kiax voip and libstdc++5 ?"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-03
Hi,

Im trying to install Kiax, so I can use it with VoipBuster.

I have been using this guide:
[http://www.icsd.aegean.gr/students/cs00050/voipbuster.htm](http://www.icsd.aegean.gr/students/cs00050/voipbuster.htm)

But no matter what I do it keeps telling me that I need the libqt3c102-mt library. Then the guide tells me to do this:

> mkdir kiax.tmp
dpkg-deb --extract kiax_XXXdebian_i386 kiax.tmp
dpkg-deb --control kiax_XXXdebian_i386 kiax.tmp/DEBIAN
gedit kiax.tmp/DEBIAN/control

Now replace libqt3c102-mt (>= 3:3.3.3.2) with libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt
and finally

dpkg --build kiax.tmp

But still it keeps telling me that libqt3c102-mt library is needed.
When I try to install it with 

apt-get install libqt3c102-mt or apt-get install libstdc++5

It tells me I have a newer version?

Can anyone help me with this?

---

### Post by aktiwers on 2006-04-03
This is what it tells me when I try the apt-get things:

```
aktiwers@ubuntu:~$ sudo apt-get install libqt3c102-mt
Password:
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
aktiwers@ubuntu:~$ sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree... Done
libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aktiwers@ubuntu:~$ 
```

---

### Post by aktiwers on 2006-04-03
Oh got it to work now :)
I started all over for the 3 time(from the guide above) and now it works.

---

### Post by aktiwers on 2006-04-03
Really no suggestions?
I really need this bad.. any suggestions would be a help, as I have no idea what to do.

Thanks

---

### Post by Typhoon on 2006-04-03
I got Kiax to work by putting in a symbolic link.

ln -s <lib version in Ubuntu> <lib version that Kiax wants>

Do this in the /usr/lib directory.

I can't remember the details right now, but if you have problems you can pm me and I will look into it.

Edit: should have mentioned that it is .8.4 and I just used the binaries.

Cheers,
Typhoon

---

### Post by aktiwers on 2006-04-04
Thanks for the input Typhoon. I see I edited the wrong post, but a little longer above I said I actually got it installed! 
But yes, I cant make any phonecalls so fare. I read somewhere that I needed to install Asterisk, and set up some stuff there too, to make it work?

I would really appriciate your help if you have gotten it to work, and will try to PM you tomorrow.
Thanks..
  
...other inputs are still welcome :)

---

### Post by Typhoon on 2006-04-04
Well, I was surprised to see that you wanted Kiax for Voipbuster since I was under the impression that VB was a SIP service. I know that you can use it with a SIP phone, but it requires a Windows thing to sign up for the service and I haven't actually done it yet.

If this is right, and you do in fact want a SIP phone, then go for Ekiga. It is a great piece of software and you can register with multiple SIP providers. To get it, you need to add to your resources:

## Ekiga stable
deb [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) breezy main

VB, SipDiscount and some others offer free PC -> PSTN calls. I register with Free World Dialup to make calls to foreign toll free numbers and with Gizmo to make cheap PC -> PSTN calls to the USA. Ekiga rocks!

EDIT: I just looked at VB - it can take SIP calls - give Ekiga a try.

Cheers,
Typhoon

---

### Post by aktiwers on 2006-04-06
I just treid to install it this way, but I get some errors on apt-get.

```
aktiwers@ubuntu:~$ sudo gedit /etc/apt/sources.list
aktiwers@ubuntu:~$ sudo apt-get install Ekiga
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://pkg-voip.buildserver.net breezy/main Packages (/var/lib/apt/lists/pkg-voip.buildserver.net_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package Ekiga
aktiwers@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
aktiwers@ubuntu:~$ sudo apt-get update
Get:1 http://koti.mbnet.fi breezy/ Release.gpg [65B]
Get:2 http://security.ubuntu.com breezy-security Release.gpg [189B]
Ign http://people.ubuntu.com ./ Release.gpg
Get:3 http://security.ubuntu.com breezy-security Release [27,0kB]
Get:4 http://koti.mbnet.fi breezy/ Release [702B]
Get:5 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:6 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:7 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Get:8 http://kubuntu.org breezy Release.gpg [189B]
Ign http://people.ubuntu.com ./ Release
Get:9 http://pkg-voip.buildserver.net breezy Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:10 http://archive.ubuntu.com breezy-updates Release [30,9kB]
Hit http://kubuntu.org breezy Release
Ign http://people.ubuntu.com ./ Packages
Get:11 http://pkg-voip.buildserver.net breezy Release [2855B]
Hit http://people.ubuntu.com ./ Packages
Get:12 ftp://ftp.free.fr breezy Release.gpg
Ign http://deb.opera.com etch Release.gpg
Get:13 http://archive.ubuntu.com breezy-backports Release [19,6kB]
Ign http://deb.opera.com etch Release
Ign http://deb.opera.com etch/non-free Packages
Ign http://koti.mbnet.fi breezy/ Packages
Ign http://theli.free.fr ./ Release.gpg
Hit http://deb.opera.com etch/non-free Packages
Ign ftp://ftp.free.fr breezy Release.gpg
Hit http://archive.ubuntu.com breezy/main Sources
Ign http://pkg-voip.buildserver.net breezy Release
Get:14 http://security.ubuntu.com breezy-security/main Packages [45,7kB]
Hit http://kubuntu.org breezy/main Packages
Get:15 http://pkg-voip.buildserver.net breezy/main Packages [12,5kB]
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Get:16 ftp://ftp.free.fr breezy Release
Get:17 http://archive.ubuntu.com breezy-updates/main Packages [38,0kB]
Get:18 http://security.ubuntu.com breezy-security/restricted Packages [4458B]
Get:19 http://security.ubuntu.com breezy-security/main Sources [14,5kB]
Ign ftp://ftp.free.fr breezy Release
Get:20 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:21 http://archive.ubuntu.com breezy-updates/main Sources [18,2kB]
Get:22 http://security.ubuntu.com breezy-security/restricted Sources [960B]
Get:23 http://security.ubuntu.com breezy-security/universe Packages [31,9kB]
Get:24 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
Get:25 http://archive.ubuntu.com breezy-backports/main Packages [14,0kB]
Get:26 http://archive.ubuntu.com breezy-backports/restricted Packages [14B]
Get:27 http://archive.ubuntu.com breezy-backports/universe Packages [26,1kB]
Get:28 ftp://ftp.free.fr breezy/free Packages
Get:29 http://archive.ubuntu.com breezy-backports/multiverse Packages [1353B]
Ign ftp://ftp.free.fr breezy/free Packages
Ign http://theli.free.fr ./ Release
Get:30 ftp://ftp.free.fr breezy/non-free Packages
Ign ftp://ftp.free.fr breezy/non-free Packages
Get:31 ftp://ftp.free.fr breezy/free Sources
Ign ftp://ftp.free.fr breezy/free Sources
Get:32 http://security.ubuntu.com breezy-security/universe Sources [5007B]
Get:33 ftp://ftp.free.fr breezy/non-free Sources
Ign http://theli.free.fr ./ Packages
Ign ftp://ftp.free.fr breezy/non-free Sources
Hit ftp://ftp.free.fr breezy/free Packages
Hit ftp://ftp.free.fr breezy/non-free Packages
Hit ftp://ftp.free.fr breezy/free Sources
Hit ftp://ftp.free.fr breezy/non-free Sources
Hit http://theli.free.fr ./ Packages
Ign http://wine.sourceforge.net binary/ Release.gpg
Hit http://wine.sourceforge.net binary/ Release
Ign http://wine.sourceforge.net binary/ Packages
Hit http://wine.sourceforge.net binary/ Packages
Ign http://koti.mbnet.fi breezy/ Sources
Hit http://koti.mbnet.fi breezy/ Packages
Hit http://koti.mbnet.fi breezy/ Sources
Fetched 295kB in 3s (81,6kB/s)
Reading package lists... Done
W: GPG error: http://pkg-voip.buildserver.net breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A5E3A5A52ABFCB1
W: You may want to run apt-get update to correct these problems
aktiwers@ubuntu:~$ sudo apt-get update
Ign http://deb.opera.com etch Release.gpg
Ign http://deb.opera.com etch Release
Get:1 http://koti.mbnet.fi breezy/ Release.gpg [65B]
Get:2 http://pkg-voip.buildserver.net breezy Release.gpg [189B]
Get:3 http://kubuntu.org breezy Release.gpg [189B]
Get:4 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:5 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:6 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:7 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Ign http://deb.opera.com etch/non-free Packages
Hit http://archive.ubuntu.com breezy Release
Hit http://archive.ubuntu.com breezy-updates Release
Hit http://security.ubuntu.com breezy-security Release
Hit http://deb.opera.com etch/non-free Packages
Hit http://kubuntu.org breezy Release
Get:8 http://koti.mbnet.fi breezy/ Release [702B]
Hit http://pkg-voip.buildserver.net breezy Release
Hit http://archive.ubuntu.com breezy-backports Release
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://kubuntu.org breezy/main Packages
Ign http://pkg-voip.buildserver.net breezy Release
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://pkg-voip.buildserver.net breezy/main Packages
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Get:9 ftp://ftp.free.fr breezy Release.gpg
Ign http://koti.mbnet.fi breezy/ Packages
Ign http://koti.mbnet.fi breezy/ Sources
Ign ftp://ftp.free.fr breezy Release.gpg
Ign http://wine.sourceforge.net binary/ Release.gpg
Hit http://koti.mbnet.fi breezy/ Packages
Get:10 ftp://ftp.free.fr breezy Release
Hit http://koti.mbnet.fi breezy/ Sources
Ign ftp://ftp.free.fr breezy Release
Ign http://theli.free.fr ./ Release.gpg
Get:11 ftp://ftp.free.fr breezy/free Packages
Ign ftp://ftp.free.fr breezy/free Packages
Get:12 ftp://ftp.free.fr breezy/non-free Packages
Ign ftp://ftp.free.fr breezy/non-free Packages
Get:13 ftp://ftp.free.fr breezy/free Sources
Ign ftp://ftp.free.fr breezy/free Sources
Get:14 ftp://ftp.free.fr breezy/non-free Sources
Ign ftp://ftp.free.fr breezy/non-free Sources
Ign http://theli.free.fr ./ Release
Hit ftp://ftp.free.fr breezy/free Packages
Hit ftp://ftp.free.fr breezy/non-free Packages
Hit ftp://ftp.free.fr breezy/free Sources
Hit ftp://ftp.free.fr breezy/non-free Sources
Ign http://theli.free.fr ./ Packages
Ign http://people.ubuntu.com ./ Release.gpg
Ign http://people.ubuntu.com ./ Release
Ign http://people.ubuntu.com ./ Packages
Hit http://people.ubuntu.com ./ Packages
Hit http://theli.free.fr ./ Packages
Hit http://wine.sourceforge.net binary/ Release
Ign http://wine.sourceforge.net binary/ Packages
Hit http://wine.sourceforge.net binary/ Packages
Fetched 897B in 7s (116B/s)
Reading package lists... Done
W: GPG error: http://pkg-voip.buildserver.net breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A5E3A5A52ABFCB1
W: You may want to run apt-get update to correct these problems
aktiwers@ubuntu:~$ 
```

As you can see I first added the thing to my recources, and then ran sudo apt-get install Ekiga. But then it tells me to run apt-get update and I did, but it tells me to do it again, and again. Any Idea what to do? 
I really wanna get going and make some calls soon :)

I dont even know what SIP is, I just want to be able to make free calls on linux, like I could on XP  with voipbuster :)

Thanks for all your help so fare.

---

### Post by Matthew Bartram on 2006-05-20
I also had problems trying to add the repository via gedit of the sources.list file.

Under synaptic, settings, repositries, add, custom, I added the repository
> deb [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) breezy main
and synaptic found it happily.

It has an authentication problem, a fix is suggested [here]("http://ubuntuforums.org/showthread.php?t=146453&highlight=ekiga+breezy"), but didn't work for me. It doesn't matter anyway - you can just ignore the authentication unless you're paranoid ;-).

---

### Post by marcoho on 2006-06-17
Try this exelent ubuntu and debian repository about voip:

deb [http://pkg-voip.buildserver.net/ubuntu/](http://pkg-voip.buildserver.net/ubuntu/)
for breezy dapper and edgy

I install [http://pkg-voip.buildserver.net/ubuntu/pool/main/k/kiax/kiax_0.8.51.dfsg-1.breezy.1835_i386.deb](http://pkg-voip.buildserver.net/ubuntu/pool/main/k/kiax/kiax_0.8.51.dfsg-1.breezy.1835_i386.deb)

with no problems.

---

