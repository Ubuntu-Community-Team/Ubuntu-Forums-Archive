---
title: "Standard location for installing s/w"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by cls1chuck on 2006-05-03
Is there a 'standard' place to install software (esp. things like java, flash, etc.) when installing for all users?  Is it different for support s/w like java, vs. applications like Firefox or, say, a media player?
Thanks in advance!

---

### Post by jazzmuzik on 2006-05-03
When you install deb packages from the repositories, all that is taken care of for you. Software is installed for all users by default. Generally, programs are in /usr/bin

---

### Post by cls1chuck on 2006-05-03
I was thinking when installing things from the cmd line.  Sometimes when installing, say, Java plugin, the instructions say to do it from a cmd line.
Thanks!

---

### Post by mostwanted on 2006-05-03
You might want to take a look at this:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by jazzmuzik on 2006-05-03
Even java is packaged as a deb file. There are two as I recall: Blackdown Java and Sun's Java. Whether you install from Synaptic or at the command line with apt-get, they both are installing deb files and the install location is predetermined within the package.

If you are doing some programming or advanced stuff, yeah, you can install things wherever you want, but otherwise that method (installing anywhere) would create a real mess.

---

### Post by mjm115 on 2006-05-03
[QUOTE=mostwanted]You might want to take a look at this:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)[/QUOTE]


mostwanted is right.  Usually, you shouldn't have to go command line unless absolutely necessary.  Synaptic (the software installer) will take care of everything for you.

---

### Post by cls1chuck on 2006-05-03
Are you saying I could have done this for java instead of the following?  This is where my question originally came from; I was following the installation instructions at Sun's site ([http://www.java.com/en/download/help/5000010500.xml#selfextracting]("http://www.java.com/en/download/help/5000010500.xml#selfextracting")).  They say in short:
===
To install the Linux (self-extracting) file
Follow these instructions:
   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/
      Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
===
of course I used sudo instead, but as for the rest, I followed it instead of using apt-get or synaptic pgk mgr.  Wish I'd known that before! :D

---

### Post by macdo on 2006-05-03
FWIW, I normally install things that are not debs in /opt/. So /opt/firefox for Firefox 1.5, /opt/thunderbird/ for Thunderbird 1.5, and so on.

---

### Post by cls1chuck on 2006-05-03
How does one find if an app is a ".deb"?  I see links for .RPM (Red Hat), but usually not .deb?  One of the hardest things for me is knowing what to search for in the various repositories in Pkg Mgr.

---

### Post by macdo on 2006-05-03
Once you know what you're looking for, use the "search" function in your package manager. Try searching on the name, and if that doesn't work, type in some key words. If you wanted a music player, for example, you might start by typing in "Windows Media Player" - obviously, that's not in the repositories. But if you just type in "music player", then a whole load of alternative programs would appear. 
If you're really stuck, you can install rpm (at your own risk: there's no guarantee that they'll work!) by installing alien on your system, ```
sudo apt-get install alien
```
then using the command ```
sudo alien -i /path/to/my/package.rpm
```
Before you do that, I'd suggest that you search the web with google by typing "nameofprogram .deb". There are often kind people who have uploaded pre-packaged packages!

---

