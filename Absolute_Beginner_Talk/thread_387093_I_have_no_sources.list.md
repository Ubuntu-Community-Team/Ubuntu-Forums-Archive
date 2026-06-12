---
title: "I have no sources.list"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-03-17
I am running Ubuntu 5.10 Breezy Badger on an 'Old World' Apple PowerBook G3 Wallstreet.  It runs alright, however I want to upgrade it to a newer version.  Because it is an 'Old World Mac', I have not been able to figure out how to install a newer version using installation CDs (You need to go through a Ubuntu-version-specific process before installing on an 'Old World Mac').

Anyway, I want to install the newer version of Ubuntu using the Update Manager, however I have never gotten the 'Upgrade' choice.  I also discovered that when I go to "gksudo gedit /etc/apt/sources.list" it opens as a blank page.

Why is this? Does anyone know how I can upgrade to the new version while running Ubuntu? I have been told that I should change stuff in the sources.list file, but there is nothing there.

Thanks

---

### Post by ardchoille42 on 2007-03-17
> **mdknaebel said:**
> I am running Ubuntu 5.10 Breezy Badger on an 'Old World' Apple PowerBook G3 Wallstreet.  It runs alright, however I want to upgrade it to a newer version.  Because it is an 'Old World Mac', I have not been able to figure out how to install a newer version using installation CDs (You need to go through a Ubuntu-version-specific process before installing on an 'Old World Mac').

Anyway, I want to install the newer version of Ubuntu using the Update Manager, however I have never gotten the 'Upgrade' choice.  I also discovered that when I go to "gksudo gedit /etc/apt/sources.list" it opens as a blank page.

Why is this? Does anyone know how I can upgrade to the new version while running Ubuntu? I have been told that I should change stuff in the sources.list file, but there is nothing there.

Thanks

Let's make sure you indeed do not have a sources.list. Open a terminal and type:
```

ls -la /etc/apt/sources.list

```

If it returns
```

-rw-r--r-- 1 root root 808 2007-03-13 17:15 /etc/apt/sources.list

```
then you do have a sources.list. If this is the case, then be sure you aren't making any typing mistakes when you type "gksudo gedit /etc/apt/sources.list"

If it returns something like
```

ls: /etc/apt/sources.list: No such file or directory

```

Then you have a problem that can be easily fixed by using [this site]("http://www.ubuntu-nl.org/source-o-matic/").

---

### Post by mdknaebel on 2007-03-17
Ok, it looks like I really do not have one... I will try that site

Thanks

---

### Post by mdknaebel on 2007-03-17
WAIT... umm, what do I do once I get to the page where there is just text, after I put in the info that is wants??

Thanks

---

### Post by ardchoille42 on 2007-03-17
> **mdknaebel said:**
> WAIT... umm, what do I do once I get to the page where there is just text, after I put in the info that is wants??

Thanks

Run:
```

gksudo gedit /etc/apt/sources.list

```

copy the text from that site page and paste it into your gedit, then save the file and you're done :)

Don't forget to run:
```

sudo apt-get update

```

to update your sources.

---

### Post by mdknaebel on 2007-03-17
hmm, well I get an error message when I try to save the file, it says it cannot be saved...

Any Ideas?

This is the code it made:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

Thanks

---

### Post by ardchoille42 on 2007-03-17
> **mdknaebel said:**
> hmm, well I get an error message when I try to save the file, it says it cannot be saved...

Any Ideas?

This is the code it made:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

Thanks

What is the error message you get when you try to save that file?

---

### Post by Space Cowboy on 2007-03-17
Did you save it as root? You might need to start gedit as root (do 'sudo gedit'). 

EDIT: Nvm I didn't read sorry.

---

### Post by ardchoille42 on 2007-03-17
> **Space Cowboy said:**
> Did you save it as root? You might need to start gedit as root (do 'sudo gedit').

Please do not use sudo with graphical apps, it can cause login problems. Use gksudo with graphical apps.
[Here]("http://www.psychocats.net/ubuntu/graphicalsudo") is an explanation of this.

---

### Post by Space Cowboy on 2007-03-17
> **ardchoille42 said:**
> Please do not use sudo with graphical apps, it can cause login problems. Use gksudo with graphical apps.
[Here]("http://www.psychocats.net/ubuntu/graphicalsudo") is an explanation of this.

I was wondering about that. I had always seen people say to do gksudo gedit, and I had done so but forgot one day and it did the same thing, so I assumed it didn't matter. Sorry to provide misinformation.

---

### Post by mdknaebel on 2007-03-17
well, so far, sudo gedit /etc/apt............ has worked. it saved just fine, and i was given updates.

Thanks!

---

### Post by ardchoille42 on 2007-03-17
> **mdknaebel said:**
> well, so far, sudo gedit /etc/apt............ has worked. it saved just fine, and i was given updates.

Thanks!

In the future, try not to use sudo with gui apps.. it can cause problems. Try to get into the habit of using gksudo with gui apps and reserving sudo for command line only.

---

