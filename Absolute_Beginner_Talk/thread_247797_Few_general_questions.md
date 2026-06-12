---
title: "Few general questions"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by g0nzo on 2006-08-31
Hi!

I've just installed Ubuntu and got few questions:

- how can I install nvidia drivers for my graphic card? I tried downloading them from nvidia.com site (are Linux IA32 drivers correct if I'm using 32bit desktop version of ubuntu?), but when I run them I get error about missing "ld", which is supposed to belong to "binutils" package (which is installed). It suggests to add this "ld" thingy to PATH. How can I do that?

- how can I download .deb files? I was trying to download Opera, which I'm using in windows, but Kate editor kept popping out and I got error saying that saving .deb as binary file (or rather that it is binary file, can't remember) will result in corrupted file. So how should I download this file using Konqueror?

- to make almost any change in the system I need to enter my password, which is strange as I'm already logged in. I suspect it's because of some security reasons, but is it possible to turn it off at least until I finish configuring my system?

- when partitioning my system using ubuntu app during install it created ext3 and swap partitions, but also 2 very small, empty partitions (~2mb). Is it normal?

Thanks in advance!

---

### Post by OffHand on 2006-08-31
Use this guide to enable the universe and mulitverse repositories:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

> **g0nzo said:**
> Hi!

I've just installed Ubuntu and got few questions:

- how can I install nvidia drivers for my graphic card? I tried downloading them from nvidia.com site (are Linux IA32 drivers correct if I'm using 32bit desktop version of ubuntu?), but when I run them I get error about missing "ld", which is supposed to belong to "binutils" package (which is installed). It suggests to add this "ld" thingy to PATH. How can I do that?
Why don't use use the ones from the repositories? They do an excellent job.
> **g0nzo said:**
> 
- how can I download .deb files? I was trying to download Opera, which I'm using in windows, but Kate editor kept popping out and I got error saying that saving .deb as binary file (or rather that it is binary file, can't remember) will result in corrupted file. So how should I download this file using Konqueror?I might be wrong but I think Opera is in the repositories too.
> **g0nzo said:**
> 
- to make almost any change in the system I need to enter my password, which is strange as I'm already logged in. I suspect it's because of some security reasons, but is it possible to turn it off at least until I finish configuring my system?No, this is extremely insecure. You will get used to typing your password. What you want is one of the biggest security flaws in XP... use your computer for every day tasks as an administrator.
> **g0nzo said:**
> 
- when partitioning my system using ubuntu app during install it created ext3 and swap partitions, but also 2 very small, empty partitions (~2mb). Is it normal?

Thanks in advance!I do not know.

---

### Post by Titus A Duxass on 2006-08-31
1. use automatix to install nvidia drivers
2. Can't help you there
3. Goto the wiki for an explanation about Sudo, bypass it with sudo -i and enter your password.  You will stay as sudo until you type exit.
4. Never seen that before.

---

### Post by Anonii on 2006-08-31
2) Well, go to the .deb file link, right click, and "Save file as"... That will save the file somewhere on your PC (you chose) and you wont open it with the default application :/
The best way for .deb files is:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Good Luck :)

---

### Post by Ferri on 2006-08-31
> **g0nzo said:**
> Hi!
Hi

> **g0nzo said:**
> I've just installed Ubuntu and got few questions:

- how can I install nvidia drivers for my graphic card? I tried downloading them from nvidia.com site (are Linux IA32 drivers correct if I'm using 32bit desktop version of ubuntu?), but when I run them I get error about missing "ld", which is supposed to belong to "binutils" package (which is installed). It suggests to add this "ld" thingy to PATH. How can I do that?

This should help:
[http://www.ubuntuforums.org/showthread.php?t=204910&](http://www.ubuntuforums.org/showthread.php?t=204910&)
If you make a search using "nvidia" or "nvidia drivers" you will find a number of threads that also might be of interest for you.


> **g0nzo said:**
> - how can I download .deb files? I was trying to download Opera, which I'm using in windows, but Kate editor kept popping out and I got error saying that saving .deb as binary file (or rather that it is binary file, can't remember) will result in corrupted file. So how should I download this file using Konqueror?

You can use, from command line, wget [URL]/*.deb
You can also use konqueror or any web browser.


> **g0nzo said:**
> - to make almost any change in the system I need to enter my password, which is strange as I'm already logged in. I suspect it's because of some security reasons, but is it possible to turn it off at least until I finish configuring my system?

It is for security reasons. If you are working with KDE (you have mentioned Konqueror) you may work with most settings lauching the control centre running "sudo kcontrol" from command line, without having to give your password for every system setting. If you want to change settings that can be user-dependent (background, icons...) you must do it launching the control center as a normal user.

> **g0nzo said:**
> - when partitioning my system using ubuntu app during install it created ext3 and swap partitions, but also 2 very small, empty partitions (~2mb). Is it normal?

I'm not sure. Could you tell us how does look your fstab file (in /etc folder).

> **g0nzo said:**
> Thanks in advance!

You are wellcome.

---

### Post by g0nzo on 2006-08-31
Thanks!

I'm using Kubuntu, not Ubuntu (sorry for this mistake). The web page for managing repositories on Kubuntu doesn't exist, but I've managed to enable all repositories (however it's strange why some of them are not enabled by default).

Regarding nVidia drivers: the version in repositories is older than on the nVidia page, so, again, how can I add "ld" program to PATH variable? I'm installing version from repository right now (I hope it will work), but later I'd like to update it manually.

Opera is not available through repositories, but I've fixed Konqueror and now it shows option menu, where I can choose "save as", instead of automatically opening Kate. I couldn't right click on it and choose "save as" as it was perl file redirecting to .deb file. However when I click on the opera .deb file it opens Ark and shows following error: "The utility is not in your PATH. Please contact...". What's wrong?

As for this automatic login as superuser, thanks for explanation how to do it, but maybe your're right about getting used to type my password :)

Regarding unusual number of partitions: I think everything is ok in fstab (it show my 2 ntfs partitions, ext3, swap, cdrom and proc), but Disk & Filesystems app from System Settings shows additional 1kb partition on /dev/sda2. Everything works ok, so I'll probably just leave this alone :)

Is there Kubuntu equivalent of "gedit"? When I try to run "sudo Kate" and it runs, but I get errors like:

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
QObject::disconnect: Unexpected null parameter
QFile::open: No file name specified
~ScimInputContextPlugin()


What's wrong? I'm not yet advanced enough to use vim or emacs :)

---

### Post by OffHand on 2006-08-31
> **g0nzo said:**
> 
Regarding nVidia drivers: the version in repositories is older than on the nVidia page, so, again, how can I add "ld" program to PATH variable?
Newer isn't always better. For instance; xgl+compiz doesn't run with the driver from Nvidia but does work (very good I might add) with the drivers from the repos  :cool:

---

### Post by g0nzo on 2006-08-31
I've installed drivers from the repos and which graphic card should I choose now? I've got 7600GT and now I've got "nv" set as a card and a driver.

I can choose from Drivers branch: "nv", "nvidia" or from Manufacturers\NVIDIA branch: NVIDIA GeForce, NVIDIA GeForce (fbdev), NVIDIA GeForce 2, 3, 4, FX, DDR and 6800, Legacy, but there're no 7xxx card. When I press Test sometimes I get error and sometimes nothing (even for the same graphic card).

What should I choose? And what is compiz?

[EDIT] I've found tutorial about installing nvidia drivers and it works, however the screen looks stretched horizontally. I'm not sure if it's just fonts or the whole screen.

---

