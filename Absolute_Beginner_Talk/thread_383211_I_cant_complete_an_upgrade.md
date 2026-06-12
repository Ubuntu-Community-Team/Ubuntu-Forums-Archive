---
title: "I cant complete an upgrade"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by pilot550 on 2007-03-13
I try and install my updates and I get this:

steve@VAIO:~$ sudo apt-get upgrage
E: Invalid operation upgrage
steve@VAIO:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up console-setup (1.13ubuntu8) ...
DESTROY created new reference to dead object ' Qt::VBoxLayout' during global destruction.
dpkg: error processing console-setup (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 console-setup
 ubuntu-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)


I tried running "sudo dpkg --configure -a" and I get this:

steve@VAIO:~$ sudo dpkg --configure -a
Setting up console-setup (1.13ubuntu8) ...
DESTROY created new reference to dead object ' Qt::VBoxLayout' during global destruction.
dpkg: error processing console-setup (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 console-setup
 ubuntu-minimal

What can I do? I'm lost.

---

### Post by MrWizard on 2007-03-13
Hi.  I do believe that the kernel version was updated (2.6.20.10.6).  However, even though it says that there is a new linux-restricted-modules-generic package available, I believe that is just a meta package that should point to linux-restricted-modules-2.6.20-10-generic, to correspond with the new kernel release.  However, that package is not available in the repository.  I only see linux-restricted-modules-2.6.20-9-generic.

I first noticed a problem when my computer went haywire when loading XGL.

P.S.  Just wait, and it'll probably sort itself out.  My guess is that the proper package will be added to the repo soon :)

---

### Post by pilot550 on 2007-03-13
> **MrWizard said:**
> Hi.  I do believe that the kernel version was updated (2.6.20.10.6).  However, even though it says that there is a new linux-restricted-modules-generic package available, I believe that is just a meta package that should point to linux-restricted-modules-2.6.20-10-generic, to correspond with the new kernel release.  However, that package is not available in the repository.  I only see linux-restricted-modules-2.6.20-9-generic.

I first noticed a problem when my computer went haywire when loading XGL.

P.S.  Just wait, and it'll probably sort itself out.  My guess is that the proper package will be added to the repo soon :)

Thanks. I'll wait it out.

---

### Post by AnimeUnrivaled on 2007-03-14
While I've noticed the same thing with the kernel, I don't believe that's the problem.

I've had the same exact problem with ubuntu-minimal and console-setup (same error messages) for a solid week now.

It hasn't actually prevented any upgrading from happening. All packages will upgrade correctly, and then I'll get the error messages for ubuntu-minimal and console-setup. It's really annoying because I get the feeling something might break in the future and, if nothing else, error messages aren't cool :p.

---

### Post by avintaquin on 2007-03-14
I have the same problem on Feisty.  Upgrades are coming fast and furious.  First it was the same two packages as mentioned above, but after another upgrade round today, cupsys just joined the ranks of the craped out packages.  So now I can't print.
I think your feeling that something else might break is correct because that seems to be whats happened to me.

---

### Post by MrWizard on 2007-03-14
Well my problem was fixed with last night's upgrade - the missing package showed up and the problems went away.

---

### Post by melissawm on 2007-04-04
Same problem here with console-setup and ubuntu-minimal. Hope it gets fixed soon...

---

### Post by melissawm on 2007-04-11
Still no luck... Help anyone?

---

### Post by pppetter on 2007-04-11
> **pilot550 said:**
> I try and install my updates and I get this:

steve@VAIO:~$ sudo apt-get upgrage
E: Invalid operation upgrage
steve@VAIO:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up console-setup (1.13ubuntu8) ...
DESTROY created new reference to dead object ' Qt::VBoxLayout' during global destruction.
dpkg: error processing console-setup (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 console-setup
 ubuntu-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)


I tried running "sudo dpkg --configure -a" and I get this:

steve@VAIO:~$ sudo dpkg --configure -a
Setting up console-setup (1.13ubuntu8) ...
DESTROY created new reference to dead object ' Qt::VBoxLayout' during global destruction.
dpkg: error processing console-setup (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 console-setup
 ubuntu-minimal

What can I do? I'm lost.

How about doing
> sudo apt-get dist-upgrade
That's what you are suppose to do, not just upgrade!

I don't know if it will solve your problem, but it's atleast worth a try (and don't forget using dist-upgrade in the future).

---

### Post by avintaquin on 2007-04-11
I was able to get rid of the offending packages by:
> sudo dpkg --purge ubuntu-minimal
sudo dpkg --purge console-setup

packages seem to upgrade fine now.

---

### Post by zvacet on 2007-04-11
First of all you done upgrade with metod wich is not recomended.If you want to do it that way this is giude 
[https://help.ubuntu.com/community/FeistyUpgradesManual]("https://help.ubuntu.com/community/FeistyUpgradesManual")

---

### Post by melissawm on 2007-04-12
[avintaquin]("http://ubuntuforums.org/member.php?u=69770"), that worked, thanks.

pppetter, that did not help, i was doing just that.

zvacet, we are not doing a full upgrade, we are (in my case) inside a fresh install of feisty and trying to do regular upgrades...

---

### Post by unregistr3d on 2007-04-23
I think there must be an other solution as "dpkg --purge", because i would like to keep the cupsys package.......
and i'am not happy if i must uninstall gdm:

Fehler traten auf beim Bearbeiten von:
 cupsys
 hplip
 console-setup
 ifupdown
 ubuntu-minimal
 man-db
 ubuntu-standard
 bluez-cups
 cupsys-driver-gutenprint
 cupsys-driver-gimpprint
 gdm
 cupsys-bsd
 ubuntu-desktop

please help!

EDIT: after deleting the /var/lib/dpkg/info/cupsys.postinst (the script which returned the error), everything worked fine ;)
thx

Mfg, unregistr3d

---

### Post by avintaquin on 2007-04-23
Somebody correct me if I am wrong, but I think that purge removes uninstalled packages it doesn't uninstall already installed ones.  The error comes from not being able to configure the packages because they are corrupted or buggy or something.  By removing them they can be downloaded again (hopefully updated from the ones that were a problem) during the regular upgrade process and installed.  If cupsys is currently installed and working purging the package out of dpkg won't effect it.

---

### Post by avintaquin on 2007-04-23
If it were me I think i would "dpkg --configure -a" first and then purge what is left.  But  keep in mind that I am a novice myself.

---

