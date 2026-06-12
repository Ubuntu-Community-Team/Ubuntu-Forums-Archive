---
title: "i'm really loving this os!"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by robeec on 2006-06-16
but i cannot get video to play. i cannot get flashplayer to install, even from the root terminal. rpms aren't compatible, and w/ tar i dl the file to the desktop, double click the file,  go to the root terminal and type "./flashplayer-installer" as instructed but all i get is 'no such file'. i also cannot get windows' type media to play. also what package program installer should i be using? i've used the 'add & remove' under the application's menu, arch and adept.
thanks for any advice...robby

---

### Post by az on 2006-06-16
[QUOTE=robeec]but i cannot get video to play. i cannot get flashplayer to install, even from the root terminal. rpms aren't compatible, and w/ tar i dl the file to the desktop, double click the file,  go to the root terminal and type "./flashplayer-installer" as instructed but all i get is 'no such file'. i also cannot get windows' type media to play. also what package program installer should i be using? i've used the 'add & remove' under the application's menu, arch and adept.
thanks for any advice...robby[/QUOTE]
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Jagot on 2006-06-16
This link explains everything you've mentioned:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by the slayer on 2006-06-16
Then u should use easyubuntu! Very ice piece of software!
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by the slayer on 2006-06-16
[QUOTE=the slayer]Then u should use easyubuntu! Very nice piece of software!
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)[/QUOTE]

Just follow the guide, and u should be running in no time

---

### Post by robeec on 2006-06-16
thanks very nice ppl!
rc

---

### Post by Patrick-Ruff on 2006-06-16
interesting, good luck to you with Linux :D

---

### Post by robeec on 2006-06-16
when i try to dl EasyUbuntu at the terminal, i get:
"robeec@robeec-desktop:~$ wget [http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2](http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2)
--17:12:52--  [http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2](http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2)
           => `current.tar.bz2.2'
Resolving users.on.net... 203.16.214.35
Connecting to users.on.net|203.16.214.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 72,627 (71K) [application/x-tar]

100%[====================================>] 72,627        52.30K/s

17:12:54 (52.17 KB/s) - `current.tar.bz2.2' saved [72627/72627]

robeec@robeec-desktop:~$ tar -jxvf current.tar.bz2
EasyUbuntu_2006-06-17/
EasyUbuntu_2006-06-17/conf/
EasyUbuntu_2006-06-17/conf/hdparm.conf
EasyUbuntu_2006-06-17/AUTHORS
EasyUbuntu_2006-06-17/easyubuntu.glade
EasyUbuntu_2006-06-17/LICENSE
EasyUbuntu_2006-06-17/qtlogger.ui
EasyUbuntu_2006-06-17/README
EasyUbuntu_2006-06-17/packagelist-breezy.xml
EasyUbuntu_2006-06-17/qtwarning.ui
EasyUbuntu_2006-06-17/packagelist-breezy.pot
EasyUbuntu_2006-06-17/easyubuntu.png
EasyUbuntu_2006-06-17/qtabout.ui
EasyUbuntu_2006-06-17/EasyUbuntu/
EasyUbuntu_2006-06-17/EasyUbuntu/qtaboutauto.py
EasyUbuntu_2006-06-17/EasyUbuntu/detect.py
EasyUbuntu_2006-06-17/EasyUbuntu/qtfrontendauto.py
EasyUbuntu_2006-06-17/EasyUbuntu/qtloggerauto.py
EasyUbuntu_2006-06-17/EasyUbuntu/qtwarningauto.py
EasyUbuntu_2006-06-17/EasyUbuntu/__init__.py
EasyUbuntu_2006-06-17/EasyUbuntu/qtfrontend.py
EasyUbuntu_2006-06-17/EasyUbuntu/qtprocess.py
EasyUbuntu_2006-06-17/EasyUbuntu/gtkprocess.py
EasyUbuntu_2006-06-17/EasyUbuntu/gtkfrontend.py
EasyUbuntu_2006-06-17/EasyUbuntu/backend.py
EasyUbuntu_2006-06-17/packagelist-dapper.xml
EasyUbuntu_2006-06-17/qtfrontend.ui
EasyUbuntu_2006-06-17/packagelist-dapper.pot
EasyUbuntu_2006-06-17/easyubuntu.svg
EasyUbuntu_2006-06-17/easyubuntu.in
EasyUbuntu_2006-06-17/launchEU.sh
robeec@robeec-desktop:~$ cd EasyUbuntu_2006-XX-XX
bash: cd: EasyUbuntu_2006-XX-XX: No such file or directory
robeec@robeec-desktop:~$ sudo python easyubuntu.py"

or if i dl to the desktop, i get the same 'no such file...'.
helllllp! (i bet i'm doing something wrong but i cannot figure it out)
rc

---

### Post by bollix47 on 2006-06-16
Try installing python thru synaptic package manager.

---

### Post by bruce89 on 2006-06-16
[QUOTE=bollix47]Try installing python thru synaptic package manager.[/QUOTE]
But, python is always installed.  Try ```
sudo apt-get install ubuntu-desktop
``` to make sure everything is installed that should be.

---

### Post by robeec on 2006-06-16
[QUOTE=bruce89]But, python is always installed.  Try ```
sudo apt-get install ubuntu-desktop
``` to make sure everything is installed that should be.[/QUOTE]
oot@robeec-desktop:~# sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@robeec-desktop:~#

i'm up-to-date...but still can't get EasyUbuntu to install.
rc

---

### Post by bollix47 on 2006-06-16
Yes, sorry about that.

You're downloading the nightly version and the XX-XX will be numbers not X's.

---

### Post by robeec on 2006-06-16
[QUOTE=bollix47]Yes, sorry about that.

You're downloading the nightly version and the XX-XX will be numbers not X's.[/QUOTE]
i'm clueless as to what you mean.

---

### Post by bollix47 on 2006-06-16
The command you typed in the terminal

cd EasyUbuntu_2006-XX-XX

is not what you want.  The 2006-XX-XX refers to the date it was built.

e.g. EasyUbuntu_2006-06-15 if it was built yesterday.

Type ls -l in a terminal window and you should see what you need to replace the cd entry.

I just downloaded and it's EasyUbuntu_2006-06-17

Actually that package doesn't seem to be complete so I would start over again and this time download the stable version.

---

### Post by robeec on 2006-06-16
"Actually that package doesn't seem to be complete so I would start over again and this time download the stable version."
which one's stable? thanks, robby

---

### Post by Jagot on 2006-06-16
[QUOTE=robeec]which one's stable? thanks, robby[/QUOTE]

The top one on this page:

[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

---

### Post by robeec on 2006-06-16
now i'm getting this:
"robeec@robeec-desktop:~$ wget [http://robotgeek.org/eu/easyubuntu-3.01.tar.gz](http://robotgeek.org/eu/easyubuntu-3.01.tar.gz)
--18:11:26--  [http://robotgeek.org/eu/easyubuntu-3.01.tar.gz](http://robotgeek.org/eu/easyubuntu-3.01.tar.gz)
           => `easyubuntu-3.01.tar.gz'
Resolving robotgeek.org... 69.56.131.114
Connecting to robotgeek.org|69.56.131.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 111,173 (109K) [application/x-tar]

100%[================================================================================>] 111,173      386.72K/s

18:11:26 (386.37 KB/s) - `easyubuntu-3.01.tar.gz' saved [111173/111173]

robeec@robeec-desktop:~$ tar -zxf easyubuntu-3.01.tar.gz
robeec@robeec-desktop:~$ cd easyubuntu
robeec@robeec-desktop:~/easyubuntu$ sudo python easyubuntu.pyrun
Password:
python: can't open file 'easyubuntu.pyrun': [Errno 2] No such file or directory
robeec@robeec-desktop:~/easyubuntu$"

---

### Post by Jagot on 2006-06-16
You typed:

```
sudo python easyubuntu.pyrun
```

Whereas it should be:

```
sudo python easyubuntu.py
```

---

### Post by robeec on 2006-06-16
oooooooooh, got it...lol! seems 8th time's the charm! 
Thanks--you ppl rule!

---

### Post by robeec on 2006-06-16
should i check every item in each tab?

---

### Post by tronica on 2006-06-16
i would just check what you need. so if theres anything on there that would benefit you, get it.

---

### Post by robeec on 2006-06-16
i'm afraid if i 'ok'  EasyUbuntu it'll go away and never come back. i love the feel of this version of linux. i had linspire but i wasn't crazy about that version. i wanted red hat but somebody offered me ubuntu --so i figured it would be good being based on debian.

---

### Post by robeec on 2006-06-17
i still don't have flashplayer and WinMedia type video, but i'm gonna take it one day at a time. 

okay, but one really stooopid question: should EasyUbuntu be actually installed and shouldn't it show in one of the (sub) menus?
thanks guys! robby

---

### Post by robeec on 2006-06-17
i just dl-ed flashplayer (tar) again to a desktop, and typed "sudo dpkg i-flashplayer" and i got this back...anybody can explain this to me (like i'm a toddler)?

robeec@robeec-desktop:~$ sudo dpkg i-flashplayer
Password:
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
robeec@robeec-desktop:~$

---

### Post by Belathor on 2006-06-17
You can install flash from synaptic and it will be alot easier. Just go into synaptic and click settings --> repositories. Then click 'add' from there you should be able to check 'Community maintained (universe)' and 'Non-free (multiverse)'.

Once you have enabled them, reload synaptic and search for flash. You should see a package called "flashplugin-nonfree". Click on it and mark it for installation. Then click apply.

This also should help if you want to install anything (including .deb's): [http://psychocats.net/ubuntu/installingsoftware.php]("http://psychocats.net/ubuntu/installingsoftware.php")

---

### Post by robeec on 2006-06-18
when i go to update repositories, i get this:
the following problems were found on your system:
W: GPG error: [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466

i cannot even get streaming audio...and i need to hear howard stern tomorrow! help!
thanks, robby

---

### Post by Jason_25 on 2006-06-18
[QUOTE=robeec]when i go to update repositories, i get this:
the following problems were found on your system:
W: GPG error: [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466

i cannot even get streaming audio...and i need to hear howard stern tomorrow! help!
thanks, robby[/QUOTE]
That's because whatever script you used added unofficial repositories.  If you would have taken the advice from the first posts of the experienced users you would not have had this problem.  You do not need third party scripts to do anything in this os.

---

### Post by robeec on 2006-06-18
i only followed the link's direction: open synaptic, click on settings--->repositories---> etc. i followed every 'experienced' person's advice and still no video--which says less about me following direction than it does about the 'experienced' advice! you seem testy! thanks for the bad attitude.

---

### Post by bruce89 on 2006-06-18
[QUOTE=Jason_25]That's because whatever script you used added unofficial repositories.  If you would have taken the advice from the first posts of the experienced users you would not have had this problem.  You do not need third party scripts to do anything in this os.[/QUOTE]
It helps new users, but I find this sort of thing messes everything up, and it replaces the gb.archive.ubuntu.com with the generic archive.ubuntu.com, which is annoying.  Installing the stuff manually doesn't take long anyway.

---

### Post by Lord Illidan on 2006-06-18
A hint for you on the command line.

When you are entering a command, such as, python EasyUbuntu, etc, after typing the first few letters, press TAB. This will activate the autocompletion feature. So you don't have to type in long file names.

Good Luck, may the force be with ya..

Try install flash player again from the flash website.

---

### Post by nalmeth on 2006-06-18
A couple good links for you:
[Howto Install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing.html")
[Almighty Automatix]("http://www.ubuntuforums.org/showthread.php?t=177646")

I know you've used EasyUbuntu already, but I'm sure you'll find good use for the extra stuff you can get in automatix.

---

### Post by robeec on 2006-06-18
thanks bud!:D

---

