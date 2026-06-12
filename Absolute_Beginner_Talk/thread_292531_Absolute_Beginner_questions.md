---
title: "Absolute Beginner questions"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by storybookscribe on 2006-11-03
Someone installed Fedora on my friends pc, removing Windows XP.  He doesn't like Fedora and there's something wrong with his XP disk that it's not bootable anymore.  So here's my question.

Not even knowing about Linux until a few days ago, I researched and found a general consensus that Ubuntu would be a good option for my friend.  I would like to uninstall Fedora and install Ubuntu for him.  Unfortunately, I'm not versed in Linux and the lingo.  (To me a grub is something bird's eat.) (Hoary and gnome are also unknown.):confused: 

We don't have any disks to work with to uninstall Fedora.  Is there a way to install Ubuntu over Fedora without any repercussions?  If so, once Ubuntu is installed, is there anything I need to/can do to make sure Fedora is gone?  Also, any sites you might have that I can learn more about Linux and how it works and how I can learn the coding would help, too.

Eventually, he would like to have a dual boot with Windows and Ubuntu.  (I'll have to learn how to do this, too.)

This is someone's chance at sainthood here, to help an absolute beginner.  Thanks for any help you can offer.

---

### Post by Arisna on 2006-11-03
Alright, let me begin by explaining a little lingo:

GRUB -- A common, modern bootloader for GNU/Linux that can also load other operating systems such as Microsoft Windows.  It is the piece of software that is responsible for loading essential system files (i.e., the Linux kernel, which controls your hardware) and then passing control to your GNU/Linux installation.

Hoary Hedgehog -- The "codename" for a previous release of Ubuntu.  Just a catchy version number, really.  The current stable release is called Edgy Eft, and another version called Dapper Drake came right before Edgy but is being supported for several years instead of the usual year and a half.

GNOME -- A common desktop environment for GNU/Linux and other UNIX-like operating systems.  It is the graphical environment on many systems and contains software such as a web browser, an e-mail client, a graphical terminal tool, an office suite, etc.  Alternatives to GNOME that provide essentially the same functionality also exist, such as KDE and XFCE.

Now, to your installation question.  Simply installing over Fedora will cause no problems, provided, of course, that you no longer want Fedora.  There is no need to verify that Fedora is completely gone, as it will definitely be gone when you format the hard drive to install Ubuntu.

I'm afraid I don't really have any suggestions for sites to learn lots of details about GNU/Linux in one place--I've learned by trying lots of distributions and reading lots of material, personally.

---

### Post by storybookscribe on 2006-11-04
**Arisna**,

Thanks for taking the time to help.  I'm a wiz at Windows and am sure I won't have any problem learning Linux, I'm just at the beginning stage of it.  I plan to buy the Official Ubuntu Book tomorrow and hope that helps.

Are there any steps I need to take *before* downloading Ubuntu over Fedora?  You mentioned formating the hard drive to install Ubuntu.  Will Ubuntu do this automatically or is there something I need to do first?:-k

---

### Post by Tamil on 2006-11-04
[QUOTE=storybookscribe]Will Ubuntu do this automatically or is there something I need to do first?[/QUOTE] Ubuntu can do it automatically. See [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Read the following excellent guides
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by storybookscribe on 2006-11-04
**Tamil**,  Thanks for helping.  The sites you listed will get read.  

Another question:  I just read the sticky thread that media players won't play automatically.  This is something he does a lot.  He uses RealPlayer and Windows Media to listen to online radio stations.  He also watches DVD's.  

What do I have to do to get these working for him after installing Ubuntu?

---

### Post by Tamil on 2006-11-04
> **storybookscribe said:**
> I just read the sticky thread that media players won't play automatically You have to install [Multimedia Codecs](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Codecs) or VLC media player

---

### Post by storybookscribe on 2006-11-04
**Tamil**,

I looked at that link.  So, installing that will cause links to Real Player to play automatically when he clicks on them?  And DVD's to play automatically?

I see it doesn't work for Windows Media so I'll have to find a way to make that happen.

Another question:  When downloading Ubuntu, it talks about burning a CD.  He could do that with Windows XP.  Will it automatically be able to do it with Ubuntu?  Any other tips/advice/things to be aware of before I go across the hall and install Ubuntu?  Hoping for a download, reboot and ready to use experience here!

---

### Post by storybookscribe on 2006-11-04
:::bump:::  Sorry.  Just need to get answers to my last post in order to help my friend tonight.  I apologize if "bumping" a thread is rude.  :oops: [-X

---

### Post by Sef on 2006-11-04
> The current stable release is called Edgy Eft, and another version called Dapper Drake came right before Edgy but is being supported for several years instead of the usual year and a half.

Dapper is the stable version.  Edgy is the unstable version, i.e. testing version.  Dapper will not have the latest packages, but they will work.  Edgy will have the latest packages, but they could have problems working since they are so new.


> [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Read this to [dual boot]("http://users.bigpond.net.au/hermanzone/").

> When downloading Ubuntu, it talks about burning a CD. He could do that with Windows XP.

To burn an iso in Windows, read [How can I Write ISO Files to CD]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm").

---

### Post by NeoLithium on 2006-11-04
> **storybookscribe said:**
> **Tamil**,

I looked at that link.  So, installing that will cause links to Real Player to play automatically when he clicks on them?  And DVD's to play automatically?

I see it doesn't work for Windows Media so I'll have to find a way to make that happen.

Another question:  When downloading Ubuntu, it talks about burning a CD.  He could do that with Windows XP.  Will it automatically be able to do it with Ubuntu?  Any other tips/advice/things to be aware of before I go across the hall and install Ubuntu?  Hoping for a download, reboot and ready to use experience here!

For the windows media, do you mean .wmv extensions and the like? Using automatix2 ([http://www.getautomatix.com](http://www.getautomatix.com)) and getting the codecs lets you play most extensions that I've required in the media players. I don't use realplayer very much (if at all); but I believe it kicks in right away by clicking on those files.

For the CD Burning; even though it's burnt in windows; it should still load up right on boot for you.

---

