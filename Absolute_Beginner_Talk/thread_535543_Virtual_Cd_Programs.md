---
title: "Virtual Cd Programs"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-08-26
Hey there. I have a few iso images that I want to keep on the hard drive for faster movement between the hard drive and the image. Is there any programs that run them virtually much like dameon tools for windows? I'd appreciate any help or ideas! Thanks! :)

---

### Post by chrome307 on 2007-08-26
You could try Acetone ISO

[http://www.acetoneteam.org/acetoneiso-gnome.html](http://www.acetoneteam.org/acetoneiso-gnome.html)

[img]http://kde-apps.org/CONTENT/content-pre1/44805-1.png[/img]

[IMG]http://kde-apps.org/CONTENT/content-pre2/44805-2.png[/IMG]

[IMG]http://kde-apps.org/CONTENT/content-pre3/44805-3.png[/IMG]

---

### Post by Tumpster on 2007-08-26
Thanks man, I'll give it a try, I appreciate it!

---

### Post by Tumpster on 2007-08-31
Acetone is not working for some reason. I Loaded it by downloading the .deb version and installing. It says it's starting it and i can see the box in the bottom and then it disappears ANy ideas?

---

### Post by tomcheng76 on 2007-08-31
you only need command line to mount iso
first, make a mount point ,u can call it as virtual drive 
```
 sudo mkdir /media/iso 
```
second, you can start to mount it :-)
```
 sudo mount <youriso> /media/iso -o loop 
```

please let me know if you have further questions

---

### Post by julian67 on 2007-08-31
> **Tumpster said:**
> Acetone is not working for some reason. I Loaded it by downloading the .deb version and installing. It says it's starting it and i can see the box in the bottom and then it disappears ANy ideas?

check the dependencies, particularly the version of fuseiso mentioned on their website and also that you have  libqt4-core and libqt4-gui installed. You can just   sudo apt-get install the list of dependencies to be certain you have everything. I did this and now the application starts ok. Haven't used it yet though....

---

### Post by aitorcalero on 2007-08-31
> **Tumpster said:**
> I'd appreciate any help or ideas! Thanks! :)

This script works very well for me:

```

#!/bin/bash
#
# nautilus-mount-iso

gksudo -u root -k /bin/echo "got r00t?"

sudo mkdir /media/"$*"

if sudo mount -o loop -t iso9660 "$*" /media/"$*"
then
        if zenity --question --title "ISO Mounter" --text "$* Successfully Mounted.
        
        Open Volume?"
        then
                nautilus /media/"$*" --no-desktop
        fi
        exit 0
else
        sudo rmdir /media/"$*"
        zenity --error --title "ISO Mounter" --text "Cannot mount $*!"
        exit 1
fi

```

You only need to create it in your home path:
~/.gnome2/nautilus-scripts
and give it execution rights (either with chmod +x or right-click properties)

With ISO file selected you can use it with right mouse button, scripts menu.

---

### Post by julian67 on 2007-08-31
@aitorcalero and tomcheng76

AcetoneISO is not just for mounting iso images, otherwise of course a script or simple command, or even native functionality of Nautilus or VLC media player is fine. Unfortunately not every disk image is an iso, there are also MDF, NRG, BIN, NRG and also cue + bin and cue + nrg and a few others too, so a tool like this is useful for many people and is probably very nice for people coming from Windows who are not used to using the terminal.

---

### Post by bulletxt on 2007-08-31
@Tumpster


1) first of all intall all dependencies as clearly written on [www.acetoneteam.org](www.acetoneteam.org)

2) are you by chance running a 64 bit operating system? if yes then do this also as written on manual:


 64-bit users

Install a package then:
-install libqt4-dev
-download AcetoneISO2-generic-src.tar.gz (Source download), uncompress,
enter src dir and compile:
qmake-qt4
make
Then replace /usr/bin/acetoneiso2 with the new acetoneiso2 file in src directory.

NOTE: if you get an error when doing qmake-qt4, simply type qmake.


last but not least, telling a user to mount an ISO from terminal isn't a good solution for progress. Ubuntu is doing its best to avoid using a terminal and some of you to mount a simple iso tell a user to open a terminal, honestly this is mad.
as someone else said AcetoneISO2 doesn't support only ISO and these days especially with games ISO format isn't used very much, not to mention that AcetoneISO does a LOT of other things :)

---

### Post by Tumpster on 2007-09-01
So i "sudo apt-get install" em all and when I try one I get this:

craig@craig-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: gcc (>= 4:4.1.1) but 4:4.0.3-1 is to be installed
                   Depends: g++ (>= 4:4.1.1) but 4:4.0.3-1 is to be installed
E: Broken packages


It dosen't happen for all of em but this is the only one. Any ideas?

---

### Post by bulletxt on 2007-09-02
I'm not a package expert but I can tell You is to please use Synaptic to install packages as it helps you out in these situations fixing dependencies.

if you are running ubuntu feisty and haven't any strange repositories use Synaptic and you  shouldn't have problems ;)

---

### Post by npumcrisz on 2007-09-05
Followed steps on acetoneiso2 website and still problems.

1- I can't locate the directory /dev/fuse

2-installed on dependencies  but still can't run package. 

What am I doing wrong?

---

### Post by bulletxt on 2007-09-06
if you are running Ubuntu Feisty 32 bit and have installed fuse-utils there must be a /dev/fuse file.

---

### Post by npumcrisz on 2007-09-06
> **bulletxt said:**
> if you are running Ubuntu Feisty 32 bit and have installed fuse-utils there must be a /dev/fuse file.

I downloaded 6.x LTS should I have downloaded the 7.x version?

---

### Post by bulletxt on 2007-09-06
yep, fuseiso requires libfuse 2.6 or greater and your version is too old :)

---

### Post by npumcrisz on 2007-09-06
True ugraded to Feisty and everything is now okay

---

### Post by parvinder on 2007-09-06
I installed the fuse-utils and fuseiso and the acetoneiso but still when I click on it from the applications menu it's says starting but then disappears........ what's wrong here!

Note: installed on Feisty Fawn......

---

### Post by Tumpster on 2007-09-07
Works for me on fiesty

---

### Post by bulletxt on 2007-09-07
> **parvinder said:**
> I installed the fuse-utils and fuseiso and the acetoneiso but still when I click on it from the applications menu it's says starting but then disappears........ what's wrong here!

Note: installed on Feisty Fawn......



You must tell me if you are on a 64 bit OS.

also be sure to have installed libqt4-gui

---

### Post by johnnyw on 2007-09-08
what am I doin wrong??

i get:

> acetoneiso2: symbol lookup error: acetoneiso2: undefined symbol: _ZN12QApplicationC1ERiPPci


i am not on 64

---

### Post by bulletxt on 2007-09-09
to be honest I really don't know. at this point there is only one thing left to do:


-install libqt4-dev
-download AcetoneISO2-generic-src.tar.gz  1.0.2(Source download), uncompress,
enter src/ dir and compile:
qmake-qt4
make
Then replace /usr/bin/acetoneiso2 with the new acetoneiso2 file in src directory.

NOTE: if you get an error when doing qmake-qt4, simply type qmake.

---

### Post by mongoose_za on 2008-01-01
[LIST]
Hi

[LIST]
[*]I'm on 32bit Fiesty

[*]I'm using acetone and i installed the package. Then i ran the commands in the README
    ([http://www.acetoneteam.org/gutsy-readme.txt](http://www.acetoneteam.org/gutsy-readme.txt))

[*]I figured it should all be okay now but when i try open acetone via Accessories>AcetoneISO2 it shows that it's starting on the taskbar but then it immediatly closes. I added the script that was provided earlier in this Thread and when i right click on my ISO and select"open with acetoneISO2" it doesn't open either:(
any ideas?
[/LIST]

---

