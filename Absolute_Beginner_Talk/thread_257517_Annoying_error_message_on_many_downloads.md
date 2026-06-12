---
title: "Annoying error message on many downloads"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Zoolook on 2006-09-14
Hi,

I wanted to download the Microsoft TrueType core fonts, but get the error message

'msttcorefonts' is not available in any software channel
The application might not support your system architecture.

I get this with a lot of packages.  Java, the PDF viewer from Adobe.

What's the reason for this?

---

### Post by Metacarpal on 2006-09-14
Hello

In order to download some packages that are not a core part of Ubuntu (such as MS fonts and restricted media formats), you have to enable additional software repositories (download points).  [Here's a quick and easy way how]("http://www.psychocats.net/ubuntu/sources").

---

### Post by moore.bryan on 2006-09-14
*try*```
sudo apt-get install msttcorefonts
```* and post what happens.*

---

### Post by Zoolook on 2006-09-14
hallmr@hallmr-laptop:~$ sudo apt-get install msttcorefonts
Password:
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
hallmr@hallmr-laptop:~$
hallmr@hallmr-laptop:~$

---

### Post by moore.bryan on 2006-09-14
*check [http://www.cyberciti.biz/tips/linux-howto-install-truetype-freetype-and-msttcorefonts-fonts.html](http://www.cyberciti.biz/tips/linux-howto-install-truetype-freetype-and-msttcorefonts-fonts.html)*

---

### Post by Zoolook on 2006-09-14
> **Metacarpal said:**
> Hello

In order to download some packages that are not a core part of Ubuntu (such as MS fonts and restricted media formats), you have to enable additional software repositories (download points).  [Here's a quick and easy way how]("http://www.psychocats.net/ubuntu/sources").
[B]
I followed that and got this far...[/B]

hallmr@hallmr-laptop:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
hallmr@hallmr-laptop:~$ gksudo gedit /etc/apt/sources.list

(gedit:5486): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

**This opened in another window**

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by moore.bryan on 2006-09-14
*don't "gksudo" the gedit command, just ```
sudo gedit /etc/apt/sources.list
``` and make the changes.*

---

### Post by Zoolook on 2006-09-14
OK, trying that - although I did just cut 'n paste what was there.

---

### Post by Zoolook on 2006-09-14
**New error message.**

hallmr@hallmr-laptop:~$ deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
bash: deb: command not found
hallmr@hallmr-laptop:~$

**In fact I have had this with deb commands before.**

---

### Post by Zoolook on 2006-09-14
**Also the gedit command didn't work.  This still happens**

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by moore.bryan on 2006-09-14
*are you typing that line into term?  why?  that line should be in your /etc/apt/sources.list...*

---

### Post by moore.bryan on 2006-09-14
*wow... i've never seen that before... can you apt-get?*

---

### Post by Zoolook on 2006-09-14
> **moore.bryan said:**
> *wow... i've never seen that before... can you apt-get?*

I am not sure what that means.  What can I try?

As for your previous post, yes I realise I should be editing the sources.list not typing it into the terminal (sorry, serious n00b here) - but I don't even get that far anyway because of the error I posted.

---

### Post by Metacarpal on 2006-09-14
Hi Zoo

When you gksudo gedit /etc/apt/sources.list and it opens another window, highlight the contents of the new window, and paste over them.  Then save and close.

And gksudo is the right thing to use.  It's best to use gksudo for graphical apps, sudo for things that only happen in the terminal.  I know that's a little confusing right now, but it'll be best in the long run.

EDIT: after you save and close your sources.list, type this into the terminal:
```
sudo aptitude update
```

Then try installing the fonts again.

---

### Post by Zoolook on 2006-09-14
I see I have gotten into that terrible Windows habit - i.e. not reading things properly.

OK, did the commands and pasted the new data over my existing sources.list

When I relaunched the add/remove application, this error appeared

W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_main_binary-i386_Packages)

I ignored it and tried to install something previously giving me the original error message - namely Java Webstart, flash and the MS Fonts.

They're all currently downloading.

I guess this shows that enabling the restricted formats only via the Synaptic interface isn't enough and that you need this command line stuff to work properly.

I'd really like to get a grip with the command line - especially with moving and finding files.  I am not sure where things go by default quite often.

---

### Post by Metacarpal on 2006-09-15
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

I'm currently learning from there, myself.

As for your problem with the duplicate entry, do the
```
gksudo gedit /etc/apt/sources.list
```
thing again and look for a line ending with dapper-commercial or something similar.  Look for another line that says the same thing.  Delete one, save, close.  :)

---

### Post by moore.bryan on 2006-09-15
> **Metacarpal said:**
> It's best to use gksudo for graphical apps, sudo for things that only happen in the terminal.
*meta... i've never heard this; where did you hear about it?*

---

### Post by Metacarpal on 2006-09-15
> **moore.bryan said:**
> *meta... i've never heard this; where did you hear about it?*

From aysiu - [here's a link]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by moore.bryan on 2006-09-15
*interesting... from aysiu's site "3. There are also some graphical applications that simply will not run with the *[I]sudo command. Kate, for example, can be run as kdesu kate but cannot be run as sudo kate."  i'm not sure that's entirely true; i run kate all the time with sudo.  the rest of the article is very interesting reading and makes a lot of sense, even though i've never run into the problems aysiu discusses.  thanks for the link...
[/I]

---

