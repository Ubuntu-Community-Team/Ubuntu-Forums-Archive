---
title: "[SOLVED] have ubuntu and edubuntu both?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by lyndaj70 on 2007-10-28
Hello
I was wondering if there was a way to have BOTH Ubuntu and Edubuntu....:confused:

I want my kid to be able to log in under the edubuntu, but I want to keep ubuntu...

From what I can tell, edubuntu will uninstall the standard gnome desktop.

Is there a workaround to this without having another install of linux on my system?
Thanks in advance,
Lynda

---

### Post by p_quarles on 2007-10-28
Just noticed this after answering your similar question (which I think I misunderstood) in another thread.

Installing edubuntu will *not *uninstall the default desktop. And here's how I know. I opened a terminal (alt-F1) and entered the command:
```
sudo apt-get install edubuntu-desktop
```
And I got this in return:
```
0 upgraded, 247 newly installed, 0 to remove and 0 not upgraded.
Need to get 145MB of archives.
After unpacking 689MB of additional disk space will be used.
Do you want to continue [Y/n]?
```
I selected "n" because I don't need this package, but the output told me that it would remove 0 packages while installing the edubuntu environment. 

It will take a few minutes to download, but you can rest assured that it will *not *remove anything you currently have on your system.

---

### Post by Frak on 2007-10-28
If it wants to remove Ubuntu-Desktop, **Let It**.

ubuntu-desktop is a MetaPackage, which means its a plain text document that depends on random objects and configurations, but is not essential to the system.

---

### Post by lyndaj70 on 2007-10-29
Ok, I'm going to try it...

I will keep you posted on what happens....

Thanks so much!!!

~Lynda:)

---

### Post by lyndaj70 on 2007-10-29
Okay, here's what it says...

Will this remove my Openoffice 2.3?  I had to upgrade from 2.2 because of database issues...

Just want to make sure I won't have any unpleasant surprises..

Thx, Lynda

********************************


lynda@lynda-laptop:~$ sudo apt-get install edubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgsf-gnome-1-114 openoffice.org-filter-mobiledev
  openoffice.org-java-common guile-g-wrap libffi4 libreadline5-dev
  guile-1.6-dev guile-library libffi4-dev libgwrap-runtime0-dev g-wrap
  libncurses5-dev plib1.8.4c2 libgwrap-runtime0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  atomix atomix-data blt denemo dia-common dia-gnome dia-libs edubuntu-artwork
  edubuntu-artwork-usplash edubuntu-docs ekiga evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-exchange
  evolution-plugins gnome-icon-theme-gartoon gpaint kino openoffice.org-common
  openoffice.org-core openoffice.org-filter-mobiledev openoffice.org-gnome
  openoffice.org-gtk openoffice.org-java-common openoffice.org-style-human
  pessulus python-crypto python-imaging python-tcm python-tk scribus
  thin-client-manager-backend thin-client-manager-gnome xaos
Suggested packages:
  blt-demo tetex-bin evolution-dbg evolution-plugins-experimental
  evolution-data-server-dbg kinoplus mjpegtools ffmpeg python-crypto-dbg
  python-imaging-doc python-imaging-dbg ltsp-server tix scribus-template
  scribus-doc python-imaging-tk
Recommended packages:
  lilypond csound gsfonts-x11 openoffice.org openoffice.org-evolution
  spamassassin bogofilter openoffice.org-style-industrial
  openoffice.org-style-tango openoffice.org-style-crystal
  openoffice.org-style-andromeda openoffice.org-style-hicontrast nfs-common
  gksudo
The following packages will be REMOVED:
  openoffice.org-base openoffice.org-calc openoffice.org-core01
  openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u
  openoffice.org-core04 openoffice.org-core04u openoffice.org-core05
  openoffice.org-core05u openoffice.org-core06 openoffice.org-core07
  openoffice.org-core08 openoffice.org-core09 openoffice.org-core10
  openoffice.org-debian-menus openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome-integration openoffice.org-graphicfilter
  openoffice.org-headless openoffice.org-impress openoffice.org-javafilter
  openoffice.org-kde-integration openoffice.org-math
  openoffice.org-onlineupdate openoffice.org-pyuno openoffice.org-testtool
  openoffice.org-writer openoffice.org-xsltfilter
The following NEW packages will be installed:
  atomix atomix-data blt denemo dia-common dia-gnome dia-libs edubuntu-artwork
  edubuntu-artwork-usplash edubuntu-desktop edubuntu-docs ekiga evolution
  evolution-common evolution-data-server evolution-data-server-common
  evolution-exchange evolution-plugins gnome-icon-theme-gartoon gpaint kino
  openoffice.org-common openoffice.org-core openoffice.org-filter-mobiledev
  openoffice.org-gnome openoffice.org-gtk openoffice.org-java-common
  openoffice.org-style-human pessulus python-crypto python-imaging python-tcm
  python-tk scribus thin-client-manager-backend thin-client-manager-gnome xaos
0 upgraded, 37 newly installed, 30 to remove and 0 not upgraded.
Need to get 48.0MB/103MB of archives.
After unpacking 211MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by lyndaj70 on 2007-10-29
> **p_quarles said:**
> Just noticed this after answering your similar question (which I think I misunderstood) in another thread.

Installing edubuntu will *not *uninstall the default desktop. And here's how I know. I opened a terminal (alt-F1) and entered the command:
```
sudo apt-get install edubuntu-desktop
```
And I got this in return:
```
0 upgraded, 247 newly installed, 0 to remove and 0 not upgraded.
Need to get 145MB of archives.
After unpacking 689MB of additional disk space will be used.
Do you want to continue [Y/n]?
```
I selected "n" because I don't need this package, but the output told me that it would remove 0 packages while installing the edubuntu environment. 

It will take a few minutes to download, but you can rest assured that it will *not *remove anything you currently have on your system.
How do you get your code and printouts to show up in the separate boxes like that?

---

### Post by overdrank on 2007-10-29
> **lyndaj70 said:**
> How do you get your code and printouts to show up in the separate boxes like that?

You can put code tags on them like this ```
  in the tool bar of the message  
```

---

### Post by p_quarles on 2007-10-29
It looks like it wants to replace your OpenOffice.org packages. Notice that while it says it will uninstall some, it will reinstall different versions of the same packages.

Are you doing this on your desktop or laptop? According to your sig, you have 7.10 on your desktop, and OOo 2.3 comes installed with 7.10. It's possible that if you upgraded to 2.3 before the new Ubuntu was released, it's trying to replace your custom installation with the normal Ubuntu version. 

Anyway, it's not going to get rid of OpenOffice, just replace it. If you want to skip that, you can: just make a note of all the packages from this list:
```
 The following NEW packages will be installed:
  atomix atomix-data blt denemo dia-common dia-gnome dia-libs edubuntu-artwork
  edubuntu-artwork-usplash edubuntu-desktop edubuntu-docs ekiga evolution
  evolution-common evolution-data-server evolution-data-server-common
  evolution-exchange evolution-plugins gnome-icon-theme-gartoon gpaint kino
  openoffice.org-common openoffice.org-core openoffice.org-filter-mobiledev
  openoffice.org-gnome openoffice.org-gtk openoffice.org-java-common
  openoffice.org-style-human pessulus python-crypto python-imaging python-tcm
  python-tk scribus thin-client-manager-backend thin-client-manager-gnome xaos
```
Then, use Synaptic to search for all of these packages except the ones that have to do with OpenOffice. Then you'll have all the educational materials from Edubuntu and will have skipped re-downloading OpenOffice.(or you can just run "sudo apt-get install" followed by the names of all those packages)

As for code boxes, you just need to wrap these tags around the text (except with no spaces:
[ code ] text text text [ / code ]

---

### Post by lyndaj70 on 2007-10-30
I've been playing with this on my laptop... Vista destroyed my virtual machine copy of ubuntu so I'm in the process of installing a straight copy... so until I get cracking my destop isn't getting used cause I am seriously ticked at Vista.... Started acting retarded, froze, and when I restarted my virtual Ubuntu was gone (though VirtualBox was still there..) -- strange and a definite first for me...

May just wait and do it on the desktop, which is "really" where I need it anyway.....  And Vista is getting crammed into a "virtual box" so it can't cause any more problems (stupid resource-hungry monster grumble grumble)..

---

### Post by lyndaj70 on 2007-11-03
I did it on my desktop.....

It installed edubuntu, and when I logged out and back in my window theme had changed to edubuntu default.  

When I open firefox my home page is now edubuntu.

I have more proggies, and my theme was easy to restore, and it did not effect my desktop image.

On the kid's side, after installing I created her user account, so she got the colorful theme as well as the edubuntu desktop image.

So yes, edubuntu and and ubuntu are basically the same except for different more kid-friendly apps and some colorful new themes lol!

Thanks, guys! I appreciate all of your advice.
~L

---

