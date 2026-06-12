---
title: "RPM - Installing new software"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by criminal on 2005-12-01
Hey everyone,

I have finally taken the step from Windows to Linux, after getting tired of the poor security, stability and functionality of Windows. Though now I have to learn a new Operating System all over.

The installation went well, most of my hardware was detected and drivers installed. It seems that the screen drivers still needs to be installed.

Now I have downloaded something from the internet, and tried to install it. But when logging into a terminal, and type rpm -i <filename>, I get an error saying command not found.

When I type rp and press tab, all I get is rpcclient, rpcinfo and rpl8, but no rpm.

Any suggestions would be helpful.

Kind regards,
Anton Botha

---

### Post by xmastree on 2005-12-01
You should use .deb files rather than .rpm as ubuntu doesn't use that format.

Isn't what you're looking for available via synaptic?

If you really have to use an rpm, you can use alien to convert it to .deb format.

---

### Post by criminal on 2005-12-01
Hey xmastree,

Well I am very new to Linux, but I have heard synaptic, though the program I want to download would most probably not be there, but if you can tell me where to look for synaptic I can have a look.

Also where can I get alien to convert it?

Kind regards,
  Anton Botha

---

### Post by nitricacid on 2005-12-01
You could try to find the app in the Synaptice package manager but if it isn't in there then you could always install RPM(along with librpm4) and extract the RPM package and then just manually install all the files to their corresponding files on your harddrive.

---

### Post by xmastree on 2005-12-01
Synaptic and alien shoud already be on your system. Synaptic is under the System menu, alien just runs from a terminal, try typing it (alien) in and see what happens. If it's not there, use synaptic to install it.

---

### Post by criminal on 2005-12-01
Ok found the Synaptic, but when starting it I get the following:

> W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)


Please inform.

Kind regards,
  Anton Botha

---

### Post by nitricacid on 2005-12-01
Wow! I think your sources.list is a little messed up.


open a terminal and type 
```
sudo gedit /etc/apt/sources.list
```

Then replace everything in the text file that opens with the following and save.
```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb-src http://archive.ubuntu.com/ubuntu/ breezy main universe restricted

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted

deb http://security.ubuntu.com/ubuntu/ breezy-security universe
deb-src http://security.ubuntu.com/ubuntu/ breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy multiverse main universe restricted
deb-src http://archive.ubuntu.com/ubuntu/ breezy multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse

```

Close the document and in the terminal type
```
sudo apt-get update
```

then 
```
sudo apt-get upgrade
```

then
```
sudo apt-get dist-upgrade
```
just to make sure all your files are up-to-date.

---

### Post by xmastree on 2005-12-01
I'll let someone else answer this, as I'm not using breezy yet, but I have seen posts here relating to broken repositories. :confused:

Look through the breezy specific forums, you might find the answer there.

Edit: Or maybe the Repository support forum
[http://www.ubuntuforums.org/forumdisplay.php?f=41](http://www.ubuntuforums.org/forumdisplay.php?f=41)

---

### Post by criminal on 2005-12-01
Hey everyone,

Thank you for all your replies, have to say this is great, especially the help you have given me.

I updated my sources.list, also found and installed rpm and alien.

Big Ups to all of you.

Kind regards,
  Anton Botha

P.S Will probably pick your brains alot more.

---

### Post by criminal on 2005-12-01
Hmm, still have problems.

if anyone could contact me on msn via [email]the_gen_x@hotmail.com[/email], that would be great.

Kind regards,
  Anton Botha

---

### Post by nitricacid on 2005-12-01
Sorry M8, i don't use and thing under the name Microsoft.
what exactly is the problem now?
if its the RPM file extracting just rite click on it and then click extract here (granted you installed RPM from synaptic).

---

### Post by criminal on 2005-12-01
Trying to convert it to a .deb file with alien, but it says I must log in as root.

Also I got it extracted, so I could prabably use it like that.

Kind regards,
  Anton botha

---

### Post by nitricacid on 2005-12-01
Never used Alien so i can't help you there.

The RPM file i told you to install was so you could extract RPM files.
what are the folder names that it extracted?

---

### Post by aysiu on 2005-12-01
Read this:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by criminal on 2005-12-01
Ok got it converted using sudo, at least. Now how do I install the .deb file ?

Kind regards,
  Anton Botha

---

### Post by arnieboy on 2005-12-01
[QUOTE=criminal]Trying to convert it to a .deb file with alien, but it says I must log in as root.

Also I got it extracted, so I could prabably use it like that.

Kind regards,
  Anton botha[/QUOTE]
add a **sudo** before the alien command

---

### Post by criminal on 2005-12-01
Hey everyone,

Got it installed, excellent.

Now just I need to figure out how to make a link to the menu.

Anton

---

### Post by nitricacid on 2005-12-01
i believe all you have to do is place a link in the /usr/share/applications folder

---

