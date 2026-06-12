---
title: "Wine gives error for installing"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by smartygoldenfish on 2008-03-25
Hi..I tried to install wine using the following page:
[http://broersa.wordpress.com/2008/02/18/install-wine-in-ubuntu-gutsy/]("http://broersa.wordpress.com/2008/02/18/install-wine-in-ubuntu-gutsy/")

however i get error at the last step (sudo apt-get install wine)

[B]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable[/B]

Let me tell you the whole thing which i put in terminal:
[B]prateek@prateek-desktop:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/gutsy-winehq.list
--23:20:49--  [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/gutsy-winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184, 88.159.206.7, 2001:4de0:aaac:0:2456::2
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

100%[====================================>] 181           --.--K/s             

23:20:50 (19.20 MB/s) - `/etc/apt/sources.list.d/gutsy-winehq.list' saved [181/181]

prateek@prateek-desktop:~$ 
prateek@prateek-desktop:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
OK
prateek@prateek-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_IN
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
prateek@prateek-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages
prateek@prateek-desktop:~$ 
prateek@prateek-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_IN
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
prateek@prateek-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_IN
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
prateek@prateek-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages
prateek@prateek-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_IN
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
prateek@prateek-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages
[/B]

so what should i do now?

---

### Post by forrestcupp on 2008-03-25
There are a couple of possibilities.  First, the official directions to install Wine at winehq.org are different than the ones you followed.  Secondly, you may not have your Universe and Multiverse repos enabled, which may be needed for some dependencies.

First, go to System->Administration->Software Sources.  In the 'Ubuntu Software' tab, make sure all boxes are checked except the 'CD' box.  Then click the 'Third-Party Software' tab.  Highlight each entry that is for Wine and remove them one at a time.

Now close that window, and go to [Wine's official installation page](http://winehq.org/site/download-deb) and go by their instructions.

After doing all of that, there's no reason it won't work, unless you're not really using Gutsy.

---

### Post by battle_scarred on 2008-04-04
> **forrestcupp said:**
> There are a couple of possibilities.  First, the official directions to install Wine at winehq.org are different than the ones you followed.  Secondly, you may not have your Universe and Multiverse repos enabled, which may be needed for some dependencies.

First, go to System->Administration->Software Sources.  In the 'Ubuntu Software' tab, make sure all boxes are checked except the 'CD' box.  Then click the 'Third-Party Software' tab.  Highlight each entry that is for Wine and remove them one at a time.

Now close that window, and go to [Wine's official installation page](http://winehq.org/site/download-deb) and go by their instructions.

After doing all of that, there's no reason it won't work, unless you're not really using Gutsy.

I'm having the same problem- not being able to install WINE. 
I did the things you listed above, but when i type
```
root@john-desktop:~# apt-get install wine
```

I get: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libaudio2 but it is not installable

```

Even though I followed what you said.

---

### Post by broersa on 2008-04-21
Please check the following url, maybe they have the sollution:

[https://bugs.launchpad.net/ubuntu/+bug/154161](https://bugs.launchpad.net/ubuntu/+bug/154161)

When you google on the error message you get plenty of results.

Suc6 Andre Broers

---

