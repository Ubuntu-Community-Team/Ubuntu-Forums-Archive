---
title: "how to repair damaged repository"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Siddharth Yadav on 2007-06-20
i hav damaged my repository.....can some one please tell me how to restore it to default :(
i was tryng to add vlc source whn somthng went wrong....and plz tell me hw cn i deactivate the write protection on my windows drive...

---

### Post by irish_flu on 2007-06-20
please post the contents of the file:

/etc/apt/sources.list

and it'll be easier to tell what's going on with your repositories.

You can get this info by typing (in the command line)
gedit /etc/sources/apt

and cut-and-paste the contents here.

As for your Windows drive, we need to know more about what you're doing.  Are you mounting your Windows partition (local to the machine Ubuntu is on) in Ubuntu?

If so, there is not automatically support for writing to NTFS drives (which is probably how your windows partition is formatted) in Ubuntu.  Search the forums for "ntfs3g"; that's the package you'll want to use to enable write access to that drive.

If that's not what you were going for, tell us more about it and I'm sure somebody will be able to help.

---

### Post by Siddharth Yadav on 2007-06-20
i got--

(gedit:6986): Gdk-WARNING **: locale not supported by Xlib

(gedit:6986): Gdk-WARNING **: cannot set locale modifiers

when i gave the command 'gedit /etc/sources/apt'
and an empty window came up......and i have my windows drive mounted bt the write permission is disabled.....and i cant edit that in properties of the drive...coz the option is disabled too.:(

---

### Post by irish_flu on 2007-06-20
> **Siddharth Yadav said:**
> i got--

(gedit:6986): Gdk-WARNING **: locale not supported by Xlib

(gedit:6986): Gdk-WARNING **: cannot set locale modifiers

when i gave the command 'gedit /etc/sources/apt'
and an empty window came up......and i have my windows drive mounted bt the write permission is disabled.....and i cant edit that in properties of the drive...coz the option is disabled too.:(

Sorry, you got that empty window because it's been a long day and I can't type.

I should have said, the command you want is 
gedit /etc/apt/sources.list

Sorry about that...

---

### Post by NeoLithium on 2007-06-20
What error messages made you think that your repository list is broken? Can you try either of the following commands in a terminal window and paste the results:
```
 
sudo aptitude update 
or 
sudo aptitude upgrade

```

As well, the apt sources.list requires administrator permissions, so you'd need to use ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by irish_flu on 2007-06-20
> **NeoLithium said:**
> 
As well, the apt sources.list requires administrator permissions, so you'd need to use ```
gksudo gedit /etc/apt/sources.list
```

That's for editing, for cut-and-paste to the forum it's safer to do that without root privs.  ;)

---

### Post by Siddharth Yadav on 2007-06-20
got ths in the window


# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
[ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu)
[ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu)
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

---

### Post by Siddharth Yadav on 2007-06-20
got this--on entering neo's command

siddharth@siddharth-laptop:~$ sudo aptitude upgrade
Password:
E: Type 'ftp://ftp.videolan.org/pub/videolan/ubuntu' is not known on line 29 in source list /etc/apt/sources.list
E: Type 'ftp://ftp.videolan.org/pub/videolan/ubuntu' is not known on line 29 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by NeoLithium on 2007-06-20
There's a good walkthrough here: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)  to repair the sources.list, along with a nice guide lower down the page, as you mentioned you were looking at the VLC repos. Most of what you need can be found by just reading your way down that list.

Hopefully this helps :)

---

### Post by Siddharth Yadav on 2007-06-20
well...i tried to install amaroK by giving
sudo apt-get install amarok
and got--

Package amarok is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package amarok has no installation candidate

wats wrong?

---

### Post by NeoLithium on 2007-06-20
You probably don't have the repositories enabled, but here it goes.  You mentioned that you have dapper drake installed, so just follow along :)  You can copy and paste below when needed, as well:
```
gksudo gedit /etc/apt/sources.list
```
Copy and paste so that only what is listed below, is in your GEdit window
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

Save and close the editor window.  Now, in the terminal window, copy and paste this line:
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```

Then you have a new clean sources.list.  Now just type:
```
sudo aptitude update
```

Install away :)

---

