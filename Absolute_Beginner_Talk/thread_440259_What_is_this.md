---
title: "What is this?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-05-11
Sometimes, when I try to un-install something, Synaptic will tell me that in addition to getting rid of the program I don't want, it's gonna delete something called "ubuntu-desktop" too.  I did a search on it in Synaptic and it says it's a pretty important program.  The problem is that I REALLY want to remove this one program which refuses to die without taking ubuntu-desktop with it.  

My question to all of you is...

What the heck is "ubuntu-desktop"?  And what's it's signifigance to the system?

Thanks in advance!

~Link

---

### Post by Cypher on 2007-05-11
Ubuntu-desktop is the default GNOME window manager in Ubuntu. This includes GDM. You don't want to delete it unless you've installed Kubuntu-desktop and use KDE as your window manager.

What program are you trying to remove??

---

### Post by locke.dragon on 2007-05-11
I'm trying to completely get rid of Compiz.  I accidentally screwed up my default installation and want to completely remove it so I can re-install.  At the moment, I can't delete any of the compiz stuff without deleting "ubuntu-desktop".  If it makes any difference, I have Beryl and Emerald installed and running.

---

### Post by Snowcat on 2007-05-11
Cypher, not exactly. ubuntu-desktop is a meta-package, which basically means it contains nothing except a kind of list of what should be installed (you could say that it depends on a whole bunch of packages). The main use for this is when upgrading the system - this package keeps everything in check, updating the more important packages along with it.

What this means is that, while ubuntu-desktop can be safely removed, it should be reinstalled before any major upgrades, or strange things might happen. It also means that whatever program was uninstalled (and ubuntu-desktop with it) would also have to be reinstalled before the update.

---

### Post by locke.dragon on 2007-05-11
So I'm not going to see any bad side-affects (sp) from un-installing it right?

---

### Post by Snowcat on 2007-05-11
Theoretically, no, unless whatever program you are trying to uninstall is too important and will break stuff when removed. Compiz doesn't seem like that kind of application, but I wouldn't swear on it.

---

### Post by locke.dragon on 2007-05-11
i just tried it a minute ago and it worked perfectly.  the only problem is that i found out that "compiz-gnome" is a broken package.  could anyone tell me how to fix this?  it's the last thing i need.

---

### Post by Snowcat on 2007-05-11
The package 'compiz' is another meta-package, one that installs compiz-gnome, compiz-gtk, compiz-core and compiz-plugins. These four packages together make up "Compiz" as a complete environment. I guess you should remove all four packages, to actually have no trace of Compiz installed on your system. Once again, I've never tried this, but hopefully it shouldn't do anything terrible (as long as you're using a different window manager, like metacity, when doing it).

---

### Post by locke.dragon on 2007-05-11
i already un-installed everything and then attempted a re-install.  it installed everything but compiz-gnome automatically.  when i use
```

sudo apt-get install compiz-gnome

```
i get
```

link@aperturescience:~$ sudo apt-get install compiz-gnome
Password:
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
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but 1:0.5.0-0ubuntu1 is to be installed
E: Broken packages
link@aperturescience:~$ 

```

any ideas?

EDIT:

oh.  i forgot to mention something.  un-installing ubuntu-desktop allows me to remove all of the compiz entried from synaptic, but when i try to re-install ubuntu-desktop, it insists it need to re-install all the compiz packages.  the only problem is that it won't install compiz-gnome for some reason and this makes the entire program in-operable.

---

### Post by Snowcat on 2007-05-11
Is your sources.list properly updated? All compiz files should be version 1:0.3.6-1ubuntu13, not 1:0.5.0-0ubuntu1 (at least that's what I have).

---

### Post by locke.dragon on 2007-05-11
i'm not sure if it is or not.  how do i update it?

---

### Post by DarkN00b on 2007-05-11
It is perfectly safe to remove ubuntu-desktop, it won't harm your system at all. I've done it and my laptop is wtill working perfectly. If you ever do a dist-upgrade though, you'll need to reinstall ubuntu-desktop.

---

### Post by Snowcat on 2007-05-11
This is a standard sources.list file for Feisty, taken from [here]("http://www.psychocats.net/ubuntu/sources"):

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

Open /etc/apt/sources.list with gedit (or nano or whatever you like, with root permissions) and replace the contents with this. You might want to create a backup copy first. I assume that you haven't added any extra repositories before, so there's no need to also add those to the new file.

Now, open Synaptic and 'reload' your package list.

---

### Post by locke.dragon on 2007-05-11
i did everything mentioned on that site and it still doesn't work.  i was able to get some extra system updates tho!  :D

---

### Post by locke.dragon on 2007-05-11
it still gives me this...
```

link@aperturescience:~$ sudo apt-get install compiz-gnome
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
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but 1:0.5.0-0ubuntu1 is to be installed
E: Broken packages
link@aperturescience:~$ 

```

---

### Post by Snowcat on 2007-05-11
Odd... What version of compiz-gtk is currently installed on your computer (and what is the latest version)? Does it see a version of compiz-gnome? (I know the package is broken, but does it see a latest package which it tries, and fails, to upgrade to?)

---

### Post by locke.dragon on 2007-05-11
hmmm.  maybe i should have mentioned i'm a linux noob.  :P  could you tell me how to check that stuff?

---

### Post by Snowcat on 2007-05-11
No problem ;-)

In Synaptic, each package has an "Installed Version" and a "Latest Version" numbers (which appear right after its name, in the graphical interface). Check for both compiz-gtk and compiz-gnome, what each of these numbers is. Usually, if a certain program is installed and up-to-date, both numbers should be identical. If a program is not installed at the moment, the "Installed Version" field should be blank.

Edit: I just realized you've been using the command line. Maybe, for now, you should use the graphical interface?

---

### Post by locke.dragon on 2007-05-11
> **Snowcat said:**
> No problem ;-)

In Synaptic, each package has an "Installed Version" and a "Latest Version" numbers (which appear right after its name, in the graphical interface). Check for both compiz-gtk and compiz-gnome, what each of these numbers is. Usually, if a certain program is installed and up-to-date, both numbers should be identical. If a program is not installed at the moment, the "Installed Version" field should be blank.

this is what it looks like for me.

> 
compiz-gnome |                             | 1:0.3.6-1ubuntu13
compiz-gtk       | 1:0.5.0-0ubuntu1 | 1:0.5.0-0ubuntu1


---

### Post by Snowcat on 2007-05-11
Ah, your compiz-gtk version is not what it should be, which is why compiz-gnome won't install. Have you played around with compiz?

Looking around, I see you have, and have asked about it in another thread.

Did you keep this repository in your sources.list?

deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty eyecandy

If so, you should remove it (and compiz-gtk), and reload your package list. Hopefully, Synaptic should now tell you that the latest version is 0.3.6 something.

---

### Post by locke.dragon on 2007-05-11
after updating the sources list, that one isn't in the repo list anymore.

---

### Post by Snowcat on 2007-05-11
I don't understand. You have no package named 'compiz-gtk' anymore? What about the other compiz packages? If your sources list is right, you **should** have all of those.

---

### Post by locke.dragon on 2007-05-11
no.  sorry.  i meant that
> 
deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty eyecandy

isn't there anymore.  sorry about that.  -blushes-

---

### Post by Snowcat on 2007-05-11
Great, OK. Now, uninstall 'compiz-gtk', reload your package list, and check what is the latest version available for it. If it's 1:0.3.6... you can probably install compiz-gnome and ubuntu-desktop, and everything should be fine :)

---

### Post by locke.dragon on 2007-05-11
hey!  that did it!  :D  the compiz effects work now, the only problem left is that none of my window decorators work.  i can't see the minimize, restore, or close buttons.  i only see the window.  :P  any fix for this?

---

### Post by Snowcat on 2007-05-11
As I don't use a compositing manager, this is beyond me. But there are quite a few threads about this exact problem in the forums, so you should have no problem finding a solution.

Glad to have been of assistance :)

---

### Post by locke.dragon on 2007-05-11
thanks for the help!  :D  and i'll do a few searches later.  thanks again.  you're awesome.

---

### Post by compmodder26 on 2007-05-11
What video card do you have?  If it is an nvidia, try adding this line:

Option "AddARGBGLXVisuals" "True"

Under the "Screen" section in your xorg.conf.

---

### Post by locke.dragon on 2007-05-11
i'm not positive about the video card.  it's a laptop though.  i haven't heard of too many dells that have nvidia cards.  i may just be horribly wrong though.

---

