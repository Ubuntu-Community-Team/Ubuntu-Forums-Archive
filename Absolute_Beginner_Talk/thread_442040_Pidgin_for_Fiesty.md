---
title: "Pidgin for Fiesty"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by vsugadhan on 2007-05-13
How do I install pidgin 2.0.0 final release??? I downloaded the source code from the pidgin website. If possible could someone up a deb file..?

---

### Post by mejy on 2007-05-13
Check out the various packages at [http://www.getdeb.net/search.php?keywords=pidgin]("http://www.getdeb.net/search.php?keywords=pidgin") .

---

### Post by Niels81 on 2007-05-13
My pidgin starts at start-up, and yet i can't find it at the System/Preferences/Sessions. 

How can i prevent this pidgin to start during the start of my computer?

---

### Post by tabithaboof on 2007-05-13
Try "system - preferences - sessions" and untick pidgin?

---

### Post by Niels81 on 2007-05-13
That's my point, i can't find it there.

---

### Post by ajack on 2007-05-16
Is it possible to get Pidgin installed in Fiesty as an update?  How do we go about it if it's possible to do such a request?

---

### Post by tabithaboof on 2007-05-16
I think its very likely that pidgin will be included in Gusty as standard.

---

### Post by djmaxmalta on 2007-06-09
where can i get pidgin as till now i have and it is conflicking with gaim and i want to get rid of gaim and have pidgin

---

### Post by diatribe on 2007-06-09
getdeb.net has a package that you can download, then sudo apt-get remove gaim

---

### Post by djmaxmalta on 2007-06-10
> **diatribe said:**
> getdeb.net has a package that you can download, then sudo apt-get remove gaim

it didnt work! gaim is still there  do i have to go on the live cd to remove it???

---

### Post by MenZa on 2007-06-10
The problem with Gaim, is that it's part of the meta package ubuntu-desktop (if I recall correctly). I have Pidgin installed alongside Gaim, and it's running without any problems, so personally I think I'd just ignore Gaim and install Pidgin with it.

---

### Post by djmaxmalta on 2007-06-10
> **MenZa said:**
> The problem with Gaim, is that it's part of the meta package ubuntu-desktop (if I recall correctly). I have Pidgin installed alongside Gaim, and it's running without any problems, so personally I think I'd just ignore Gaim and install Pidgin with it.

how did you do it? is in synaptic pidgin?

---

### Post by soro2005 on 2007-06-11
You can use Schmidtke's repository if you want to install it through aptitude or apt-get. Here: [http://ubuntuforums.org/showthread.php?t=437239](http://ubuntuforums.org/showthread.php?t=437239) (first post).

It's also on [GetDeb]("http://www.getdeb.net/release.php?id=955").

Does anyone else have the impression that the auto away and auto back from away functions don't really work without major delays in Pidgin? Or is it just my computer?

---

### Post by martinw89 on 2007-06-12
I am, for some reason, having problems installing the pidgin .deb file mentioned in this thread.  This is what trying to install the package spits out:```
sudo dpkg -i pidgin_2.0.0-1_i386.deb
Password:
Selecting previously deselected package pidgin.
dpkg: regarding pidgin_2.0.0-1_i386.deb containing pidgin:
 pidgin conflicts with gaim
  gaim (version 1:2.0.0+beta6-1ubuntu4) is installed.
dpkg: error processing pidgin_2.0.0-1_i386.deb (--install):
 conflicting packages - not installing pidgin
Errors were encountered while processing:
 pidgin_2.0.0-1_i386.deb
```
It looks like I need to remove gaim, but as previously mentioned, I can't because it's part of the desktop meta package.  Any thoughts on the matter?  Thanks in advance

---

### Post by soro2005 on 2007-06-12
You can divert the official package, so you don't have to remove it, but it also doesn't get in the way of your pidgin installation. Something like:
```
sudo dpkg-divert --rename --divert /usr/bin/gaim.ubuntu /usr/bin/gaim
```
That's two dashes before rename and the second divert.Then install pidgin.
If, at some point, you want to get back to the normal gaim package, you have to remove the diversion with something like:
```
sudo dpkg-divert --rename --remove /usr/bin/gaim
```
There may be an issue though once Ubuntu decides to use the pidgin package instead of gaim.

You can also use the repo I've mentioned two posts above, and I think I've seen another repo somewhere on the forums which apparently takes care of the gaim - pidgin - conflict as well. So you may want to look out for that one.

---

### Post by jariku on 2007-06-13
Any news on whether pidgin (and pidgin-otr) will be available for Feisty?

I've checked the Launchpad and unfortunately it only has packages for Gusty. I already have pidgin installed, but I'd like to see it in the official repos.

---

### Post by soro2005 on 2007-06-13
Schmidtke has an unofficial repository that has Pidgin and OTR for Feisty. Among other useful things, bu the way. You can put that onto your sources list, and you can install PIdgin as if it were in the Feisty repositories. Once it's really in the Feisty repositories, I guess synaptic and apt-get will be smart enough to see it's two times the same, and Schmidtke will probably also do what's appropriate. Read here:

[http://ubuntuforums.org/showthread.php?t=437239](http://ubuntuforums.org/showthread.php?t=437239)

---

### Post by jariku on 2007-06-20
> **soro2005 said:**
> Schmidtke has an unofficial repository that has Pidgin and OTR for Feisty. Among other useful things, bu the way. You can put that onto your sources list, and you can install PIdgin as if it were in the Feisty repositories. Once it's really in the Feisty repositories, I guess synaptic and apt-get will be smart enough to see it's two times the same, and Schmidtke will probably also do what's appropriate. Read here:

[http://ubuntuforums.org/showthread.php?t=437239](http://ubuntuforums.org/showthread.php?t=437239)

This is exactly what I have done already, thank you. But what I was wondering was if Pidgin will be backported, not how to add external repositories.

---

