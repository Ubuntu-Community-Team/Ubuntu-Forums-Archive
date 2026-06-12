---
title: "CONFUSED-Source list"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Joy on 2006-08-31
Hi,
I hve installed Dapper through live CD.I tried to install Automatix but in vain.I typed in terminal sudo gedit /etc/apt/sourec.list. I am getting-
(gedit:9459): Gdk-WARNING **: locale not supported by Xlib

(gedit:9459): Gdk-WARNING **: cannot set locale modifiers
your help will be appriciated

---

### Post by austin on 2006-08-31
it's     sources.list        
=> but I guess you have typed it right in the terminal?

So: gedit does not show you the file? You could try vi in order to go ahead, so it's 

sudo vi /etc/apt/sources.list

you would need to get yourself a vi-introduction from the web, but it's worth it in the long run

---

### Post by Joy on 2006-08-31
Thnak you Austin for your reply.As you said I typed in terminal & I got--
## sources.list
## General comments about the sources.list file
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Comment about the 'Update' repositories
## Comments about the role of the updates
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Comment on the 'Universe' repositories
## Comment about the support limitations of Universe & Multiverse
## repositories as well as licence restrictions and update policies.
## Please satisfy yourself as to your rights to use the software.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

## Comment on the 'Backports' repository
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Comment about update and security update limitations
@
"/etc/apt/source.list" 27L, 1451C                             1,1           Top
Have I to change source list to install Automatix? How? I am new to Linux
Thanks.

---

### Post by 3rdalbum on 2006-08-31
Add this line to the bottom of your sources.list:

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

I recommend you use the Nano text editor rather than Vi, as you'll probably be completely lost in Vi (as would I!)

After you've saved changes to the file, type the following into the terminal:

```
sudo apt-get update
sudo aptitude install automatix
```

If it gives you a warning about unauthenticated repositories, either ignore it or follow the directions on this page: [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_Ubuntu_6.06_Dapper_Drake]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_Ubuntu_6.06_Dapper_Drake")

---

### Post by xyz on 2006-08-31
According to my little experience, there's no need to change sources.list to install Automatix. However, after downloading/installing it, Automatix will ask you if you want it to alter your sources.list. At that point, it's up to you to agree or not according to your specific needs.
Also there's a great HowTo Automatix somewhere on the site. Good luck.
[http://www.getautomatix.com/](http://www.getautomatix.com/) Just follow the install guidelines here and, at some point, you'll be asked to add a deb to your sources.list...perhaps that's what you meant by "do I have to change my sources.list in order to install Automatix".

---

### Post by toasted on 2006-08-31
I have always accepted and let Automatix modify my sources list but it happens with me first thing after a clean install. That way there is no old news that will get lost. 

Automatix gets installed, sources list gets modded, codecs are installed, and im a happy camper :mrgreen:

---

### Post by Joy on 2006-08-31
Thanks 3rdalbum & xyz.At the end of my source list I pasted deb [http://www.getautometix.com/apt](http://www.getautometix.com/apt) dapper main and i close the window.and in terminal i typed sudo apt-get update i an getting-
joy@joy-desktop:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outFailed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

please help me to find out solution
Thanks

---

### Post by Joy on 2006-09-01
**bumps**

---

### Post by xyz on 2006-09-01
Hi-
I have no solution right now but those errors are due to connection problems to the repositories. It happens that servers are down for maintenance or other reasons and it happens quite regularly that one of them cannot be reached. Have you tried the 'apt-get' thingy several times over time?

---

### Post by Joy on 2006-09-01
Thanks xyz
I have tried.

---

### Post by xyz on 2006-09-01
> **Joy said:**
> Thanks 3rdalbum & xyz.At the end of my source list I pasted deb [http://www.getautometix.com/apt](http://www.getautometix.com/apt) dapper main and i close the window.and in terminal i typed sudo apt-get update i an getting-
joy@joy-desktop:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outFailed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

please help me to find out solution
Thanks


I really hope this is it! Take a look at the very 1st line up there in the quote where it says..."At the end of my source list I pasted deb http://www.getautometix.com/apt"...You "pasted" getautom**e**tix...and it is:

wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)

as you can see here:
[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

I really hope it is as simple as that!

---

### Post by Joy on 2006-09-01
Thank you xyz.I have installed automatix.
Cheers.

---

### Post by xyz on 2006-09-03
> **Joy said:**
> Thank you xyz.I have installed automatix.
Cheers.
 
Glad I could help...sometimes it doesn't take much!

---

