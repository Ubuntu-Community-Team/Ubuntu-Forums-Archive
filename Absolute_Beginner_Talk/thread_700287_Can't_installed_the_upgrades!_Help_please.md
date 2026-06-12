---
title: "Can't installed the upgrades! Help please"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by RRanciDD on 2008-02-18
Like the title suggest, I'm having a little problem with upgrading..

[http://xs224.xs.to/xs224/08081/screenshot172.png](http://xs224.xs.to/xs224/08081/screenshot172.png)

---

### Post by RRanciDD on 2008-02-18
sorry for the bad english I was in a hurry :guitar:

---

### Post by tdrusk on 2008-02-18
Is this on a new install?

If so, go to system>administration>software sources and enable them.

---

### Post by RRanciDD on 2008-02-18
well this isn't a new install... but I'll check it anyway!

---

### Post by RRanciDD on 2008-02-18
could it be because of automatix?

---

### Post by RRanciDD on 2008-02-18
it says something of a broken package and when I'm going to install it or fix it it does that error message.

---

### Post by PmDematagoda on 2008-02-18
This would be rather difficult, but could you please post line 16813 and a few lines next to it of the file mentioned by opening it using:-
```
gedit /var/lib/dpkg/status
```

---

### Post by RRanciDD on 2008-02-18
Package: ttf-sjfonts
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 220
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: all
Source: sjfonts
Version: 2.0.2-1ubuntu1
Depends: defoma
Recommends: x-ttcidfont-conf
Conffiles:
 /etc/defoma/hints/ttf-sjfonts.hints 7085aac1e35ed2c2b9d2d355ccee1c69
Description: Some Juicy Fonts handwriting fonts
 This package contains two handwriting fonts created by Steve Jordi,
 Delphine and SteveHand, in TrueType format.
Original-Maintainer: Daniel Schepler <schepler@debian.org>

Package: ghostscript-x
Status: install ok installed
Priority: optional
Section: text
Installed-Size: 148
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: ghostscript
Version: 8.61.dfsg.1~svn8187-0ubuntu3.3
Replaces: gs-esp-x (<< 8.60)
Provides: gs-esp-x
Depends: libc6 (>= 2.6-1), libice6 (>= 1:1.0.0), libsm6, libx11-6, libxext6, libxt6, ghostscript (>= 8.60)
Conflicts: gs-esp-x (<< 8.60), ghostscript (<< 8.60)
Description: The GPL Ghostscript PostScript/PDF interpreter - X Display support
 Ghostscript is used for PostScript/PDF preview and printing.  Usually as
 a back-end to a program such as ghostview, it can display PostScript and PDF
 documents in an X11 environment.
 .
 The Ghostscript home page is at [http://www.ghostscript.com/](http://www.ghostscript.com/)
 .
 This package contains the Ghostscript output device for X11. It is in
 a separate package to allow the main package (ghostscript) to be installed
 on X-less servers.
Original-Maintainer: Masayuki Hatta (mhatta) <mhatta@debian.org>


It's starts there... do I have do erase those lines?

---

### Post by RRanciDD on 2008-02-18
:(

---

### Post by Anicka on 2008-02-18
Could you in the terminal run the command ```
dpkg -C
``` It should tell if there is a problem. If it says you have broken packages, you can try these to commands```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by PmDematagoda on 2008-02-18
Not very sure about this since it involves removing the file in question, so **first make a backup of the status file** before removing the file. After you have made a backup of the status file in a safe location, just remove the file using:-
```
sudo rm /var/lib/dpkg/status
```

Then execute:-
```
sudo apt-get update
```
if that has not fixed your problem then just copy the backup of the status file back to where it belongs.

---

### Post by RRanciDD on 2008-02-18
tiago@tiago-desktop:~$ dpkg -C
dpkg: parse error, in file `/var/lib/dpkg/status' near line 16813 package `python-cups':
 missing version
tiago@tiago-desktop:~$ sudo apt-get -f install
[sudo] password for tiago:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-cups
The following NEW packages will be installed:
  python-cups
0 upgraded, 1 newly installed, 0 to remove and 34 not upgraded.
19 not fully installed or removed.
Need to get 0B/74.5kB of archives.
After unpacking 279kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 16813 package `python-cups':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
tiago@tiago-desktop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 16813 package `python-cups':
 missing version

---

### Post by Bachstelze on 2008-02-18
Image removed since it was way too large.

@PmDematagoda > when you see large images like this posted in messages, don't hesitate to "remove" them (i.e. remove the IMG tags so just the link appears), they're definitely against the forum rules.

---

### Post by RRanciDD on 2008-02-18
lol it didn't work I didn't do a backup... now I'm really screwed :(

---

### Post by RRanciDD on 2008-02-18
> **HymnToLife said:**
> Image removed since it was way too large.

@PmDematagoda > when you see large images like this posted in messages, don't hesitate to "remove" them (i.e. remove the IMG tags so just the link appears), they're definitely against the forum rules.

could you at least help them?

---

### Post by PmDematagoda on 2008-02-18
> **HymnToLife said:**
> Image removed since it was way too large.

@PmDematagoda > when you see large images like this posted in messages, don't hesitate to "remove" them (i.e. remove the IMG tags so just the link appears), they're definitely against the forum rules.

Oh, I did not know that. Thank you HymnToLife, I will remember that:).

---

### Post by Anicka on 2008-02-18
I would not manually touch the /var/lib/dpkg/status file, it tells the system which program that are installed. But updating the index is a good idea```
sudo apt-get update
```

Edit: Too late, I'm afraid...

---

### Post by RRanciDD on 2008-02-18
I've done everything and I just made a mess of the status file, so if anyone could help me there to I'll apreciate

---

### Post by RRanciDD on 2008-02-18
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.

I think I've got to reinstall it :(

---

### Post by PmDematagoda on 2008-02-18
> **RRanciDD said:**
> lol it didn't work I didn't do a backup... now I'm really screwed :(

What are the problems you are facing now?

Also, how did you miss the bold letters telling you to backup?

---

### Post by Anicka on 2008-02-18
With the alternative cd, there is an option when you boot from it to "fix broken installation" or something like that, maybe you could try it...

---

### Post by RRanciDD on 2008-02-18
well I'll try that with the cd... 

I didn't do a backup because I didn't know how, but anyways, can I recover that status file? or something of the sort?

---

### Post by Anicka on 2008-02-18
Delete in linux means "delete" and not "moved to the dustbin". So the file is gone. If you don't understand an instruction, be safe and ask. There are many lists of basic commands on the web, try google-ing for one.

---

### Post by RRanciDD on 2008-02-18
ok, it was my mistake. But can anybody help with that list? can't the system do another one?

---

### Post by Anicka on 2008-02-18
What happens if you run```
sudo apt-get install
```

---

### Post by RRanciDD on 2008-02-18
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.

---

### Post by Slorg on 2008-02-18
I always have the same problem.
when I update it it give an error, and then I reboot it and my system is ****** up.

I can't get an linux now anyway due to install problems <.<

---

### Post by RRanciDD on 2008-02-18
I had a problem now two problems :(

I think i'm going to re-install it but since is my "work" computer it's going to be a few weeks to have time to it.

Hope that somebody help before :(

---

### Post by philinux on 2008-02-18
[http://www.debianhelp.co.uk/debianproblem.htm](http://www.debianhelp.co.uk/debianproblem.htm)

Scroll down the page for the bit about 

**Recover package selection data**

---

### Post by RRanciDD on 2008-02-18
will try :)

---

### Post by RRanciDD on 2008-02-18
> **philinux said:**
> [http://www.debianhelp.co.uk/debianproblem.htm](http://www.debianhelp.co.uk/debianproblem.htm)

Scroll down the page for the bit about 

**Recover package selection data**



Thank you mate... I discover that there was an old status file it save my life :)

Thank you to everybody to the help especially the one that said that my image has too large, you rock:guitar:

---

### Post by philinux on 2008-02-18
> **RRanciDD said:**
> Thank you mate... I discover that there was an old status file it save my life :)

Thank you to everybody to the help especially the one that said that my image has too large, you rock:guitar:

Nice one, saved a reinstall then :)

---

