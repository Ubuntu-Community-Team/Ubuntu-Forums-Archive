---
title: "Package broke can't uninstall need help"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by waldorsockbat on 2007-04-13
OK first off I am the noobist of noobs  in regards to Kubuntu so please don't leave out any detail.

 Here's the problem, I downloaded avg free .deb file(probably my first mistake) and right clicked Kubuntu/ package menu/ install. nothing happened, I tried to find it using Adept, that's when I found the package was broken. Now I can't uninstall, tried reinstalling but can't do that either and I can't update until I uninstall avg.

btw I have fiesty on a dual boot with mediacenter05

So please have mercy on this poor stupid noob and help me fix this..

---

### Post by amohanty on 2007-04-13
Try this: (bear in mind I dont use kubuntu so am on total recall)

In your menus, hunt down something called **kynaptic**
That will bring up a password entry dialog. enter your password.
then click on the **Custom** botton on the bottom left
in the menu above select **Broken**
Something should show up on the right.
Right click on it and select **Completely Remove...**
Click on Apply on the tool bar

and you should be good to go.

HTH
AM

---

### Post by houstonbofh on 2007-04-13
The old motto "Research first, rather than fix later" applies here.  Many people have had issues with AVG.  I have not seen a successful removal.  Most give up and reinstall.  Sorry...

---

### Post by waldorsockbat on 2007-04-13
> **amohanty said:**
> Try this: (bear in mind I dont use kubuntu so am on total recall)

In your menus, hunt down something called **kynaptic**
That will bring up a password entry dialog. enter your password.
then click on the **Custom** botton on the bottom left
in the menu above select **Broken**
Something should show up on the right.
Right click on it and select **Completely Remove...**
Click on Apply on the tool bar

and you should be good to go.

HTH
AM


Sorry there is no such animal. The closest I can find is add/remove programs but it gives an error when I try remove. But thank you for the suggestion.

Yes I now know I should have read more about avg, I really don't want to re-install and go through the whole nvidia driver pain in the.... well you know what I mean.. There has to be a way around this out there somewhere???

---

### Post by Outrunner on 2007-04-13
> **waldorsockbat said:**
> Sorry there is no such animal. The closest I can find is add/remove programs but it gives an error when I try remove. But thank you for the suggestion.

Yes I now know I should have read more about avg, I really don't want to re-install and go through the whole nvidia driver pain in the.... well you know what I mean.. There has to be a way around this out there somewhere???

What you're looking for is Adept, Synaptic is for Gnome(and Kynaptic doesn't exist but it would have been a good name I guess)

---

### Post by amohanty on 2007-04-13
Ok try this:

copy down the name of the package that you installed - everything before the .deb

at the grub menu (you may have to press ESC at bootup when it prompts you to to get to the grub menu)

- select the one that says recovery
you will be presented with a login prompt (text only)
- login
then try:

dpkg -P packagename

Try it without the version numbers in the name. Post the name and I can give you a few good guesses.

HTH
AM

---

### Post by waldorsockbat on 2007-04-13
> **amohanty said:**
> Ok try this:

copy down the name of the package that you installed - everything before the .deb

at the grub menu (you may have to press ESC at bootup when it prompts you to to get to the grub menu)

- select the one that says recovery
you will be presented with a login prompt (text only)
- login
then try:

dpkg -P packagename

Try it without the version numbers in the name. Post the name and I can give you a few good guesses.

HTH
AM


OK I that did not work. it is telling me that avg is not installed..

ran the command in terminal and got this..hope its what you need.

:~$ dpkg -p avg75fld
Package: avg75fld
Section: utils
Maintainer: Radek Vykydal <radek.vykydal@grisoft.cz>
Architecture: i386
Version: 7.5.45_a0973
Provides: avglinux, avggui
Depends: python (>= 2.0), python-gtk2 (>= 2.0), python-glade2 (>= 2.0)
Conflicts: avg71fld
Size: 35006356
Description: Free edition of antivirus solution with GUI.
  This package contains the binary release of AVG Anti-Virus
  for x86 Linux and graphical user interface avggui.

---

### Post by waldorsockbat on 2007-04-13
bump

---

### Post by amohanty on 2007-04-13
You then need to do:
**sudo dpkg -Pavg75fld**

See if that works from a regular terminal.

AM

---

### Post by amohanty on 2007-04-13
> **Outrunner said:**
> What you're looking for is Adept, Synaptic is for Gnome(and Kynaptic doesn't exist but it would have been a good name I guess)


[http://packages.ubuntu.com/breezy/admin/kynaptic](http://packages.ubuntu.com/breezy/admin/kynaptic)

Used to be there till about 5.10 which sounds about right for the last time I used KDE :)

---

### Post by waldorsockbat on 2007-04-13
Here is what I got with  sudo dpkg -P avg75fld




:~$ sudo dpkg -P avg75fld
(Reading database ... 77567 files and directories currently installed.)
Removing avg75fld ...
Uninstalling 'avgd' service initscripts...
rm: cannot remove `/etc/init.d/avgd': No such file or directory
dpkg: error processing avg75fld (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 avg75fld

---

### Post by amohanty on 2007-04-13
Ok they try to force reomve

**sudo dpkg -P --force avg75fld**

Please keep in mind that the --force options is a very, very dangerous options and is to be used only to get out of previous dangerous operations :)

AM

---

### Post by waldorsockbat on 2007-04-13
:~$ sudo dpkg -P --force avg75fld
Password:
dpkg: unknown force/refuse option `avg75fld'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by amohanty on 2007-04-13
Oops sorry for the typo. try:

sudo dpkg -P --force-all avg75fld

AM

---

### Post by waldorsockbat on 2007-04-13
:~$ sudo dpkg -P --force-all avg75fld
(Reading database ... 77567 files and directories currently installed.)
Removing avg75fld ...
Uninstalling 'avgd' service initscripts...
rm: cannot remove `/etc/init.d/avgd': No such file or directory
dpkg: error processing avg75fld (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 avg75fld

---

### Post by amohanty on 2007-04-13
OK first off if we are using this, you dont need to reboot everytime -if youa re doing it. :)

So lets fake the damn file then:

> 
sudo -s

echo test >> /etc/init.d/avgd
dpkg -P --force-all avg75fld


sudo -s gives you a root shell. ber very very carefule what you type in there.

AM

---

### Post by waldorsockbat on 2007-04-13
:~$ sudo -s
:~#:~# echo test >> /etc/init.d/avgd
:~# dpkg -P --force-all avg75fld
(Reading database ... 77567 files and directories currently installed.)
Removing avg75fld ...
Uninstalling 'avgd' service initscripts...
Unregistering 'avgd' service ...
 Removing any system startup links for /etc/init.d/avgd ...
Purging configuration files for avg75fld ...



YES YES YES YES YES!!!!!!!! YOU ARE DA MAN....LOL

That did it thank you for taking the time to help me with this... Now lets see what kind of trouble I get into installing Mythtv. I want to switch over full time and use this a my media center/media server. I hope to have this all sorted out by the time there is a driver  for my Creative Xfi 

Thanks again for the  quick replies and  btw no I wasn't re-booting every time.

---

### Post by amohanty on 2007-04-13
glad to be of help.

---

