---
title: "Errors updating after fresh install"
date: 2006-06-13
forum: Apple PPC Users
---

### Post by hawkbane on 2006-06-13
hey all!

Here is my situation.  The school that I work for gave me a blue G4 which I have just recently installed Dapper on using the alternate install mini disk.  After the install is done, when I go to update I get the following error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb)
  403 Forbidden [IP: 85.133.25.7 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.10.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.10.3-0ubuntu1_all.deb)
  403 Forbidden [IP: 85.133.25.7 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.10.3-0ubuntu1_powerpc.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.10.3-0ubuntu1_powerpc.deb)
  403 Forbidden [IP: 85.133.25.7 80]

.... and etc all the way through the updates.  
_____________________________________

Then I tried to update what I needed through the Synaptic Package Manager and when I do a refresh of the repository I also get 403 Forbidden errors from all the 
us.archive.ubuntu.com server.

Any ideas what this could be?
Thanx guys!

---

### Post by hawkbane on 2006-06-14
UPDATE:  I can browse to the files in a web browser, and I have access to read and download them.  I also get 403 errors when trying to connect to security.ubuntu.com servers as well.  Any ideas whatsoever would be great!

---

### Post by nettle on 2006-06-21
Yep, I get errors too, trying to install the build-essential packages.  Bummer, I was hoping to have a Linux environment with development tools.  Imagine that.  Looks like the packages I want don't exist on the server, i.e., a gcc compiler and make utility:

[http://us.archive.ubuntu.com/ubuntu/pool/main/g/](http://us.archive.ubuntu.com/ubuntu/pool/main/g/)
[http://us.archive.ubuntu.com/ubuntu/pool/main/m/](http://us.archive.ubuntu.com/ubuntu/pool/main/m/)
~~~~~~~~~~~~~~~~~~~

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.6-0ubuntu20_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.6-0ubuntu20_i386.deb)
  403 Forbidden [IP: 146.137.96.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/cpp-4.0_4.0.3-1ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/cpp-4.0_4.0.3-1ubuntu5_i386.deb)
  403 Forbidden [IP: 146.137.96.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/g++-4.0_4.0.3-1ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/g++-4.0_4.0.3-1ubuntu5_i386.deb)
  403 Forbidden [IP: 146.137.96.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/make/make_3.80+3.81.b4-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/make/make_3.80+3.81.b4-1_i386.deb)
  MD5Sum mismatch

---

### Post by footware on 2006-06-24
Hello !

Try to change all "*http://*" by "*ftp://*" in "*etc/apt/sources.list*" file.

---

### Post by SteveGeorge on 2006-06-24
Not sure why you're getting a specific forbidden for those URL's.  If you can browse to them then it's not a network issue.

It could be that the server is overloaded.  You could try using a Mirror, for example I use the UK mirrors.  You can build a sources list at this site [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by mannheim on 2007-01-24
I think it must be a temporary glitch. I've had edgy installed since it was released. Today, I have exactly the "403 Forbidden" message trying to update libc6. Yesterday I upgraded another machine no problem. I'd just wait a few hours and try again.

---

### Post by mdz on 2007-01-24
> **hawkbane said:**
> hey all!

Here is my situation.  The school that I work for gave me a blue G4 which I have just recently installed Dapper on using the alternate install mini disk.  After the install is done, when I go to update I get the following error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb)
  403 Forbidden [IP: 85.133.25.7 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.10.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.10.3-0ubuntu1_all.deb)
  403 Forbidden [IP: 85.133.25.7 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.10.3-0ubuntu1_powerpc.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.10.3-0ubuntu1_powerpc.deb)
  403 Forbidden [IP: 85.133.25.7 80]

.... and etc all the way through the updates.  
_____________________________________

Then I tried to update what I needed through the Synaptic Package Manager and when I do a refresh of the repository I also get 403 Forbidden errors from all the 
us.archive.ubuntu.com server.

Any ideas what this could be?
Thanx guys!

This is a temporary situation with the archive server, which will be resolved within the next couple of hours.  Please be patient and do not make any unnecessary changes to your system.

---

### Post by Robor on 2007-01-24
Thanks for the reply mdz...  I was getting these errors yesterday afternoon and again this morning.  Glad the problem will be fixed soon.

On a side note, thanks for helping create the best Linux distro around!  :D

---

### Post by dr.jackal on 2007-02-25
Hi,
I'm having the same problem only with me it's permanent. When I try to download updates via synaptic or in the commandline "sudo aptitude update" I get the error:

W: Beim Herunterladen der Datei »[http://security.ubuntu.com/ubuntu/pool/main/e/ekiga/ekiga_2.0.1-0ubuntu6.1_i386.deb«](http://security.ubuntu.com/ubuntu/pool/main/e/ekiga/ekiga_2.0.1-0ubuntu6.1_i386.deb«) ist ein Fehler aufgetreten:
  403 Forbidden


W: Beim Herunterladen der Datei »[http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5-0.6ubuntu0.5_i386.deb«](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5-0.6ubuntu0.5_i386.deb«) ist ein Fehler aufgetreten:
  403 Forbidden


...etc

I also did 
```
gpg --keyserver subkeys.pgp.net --recv KEY
```
and
```
gpg --export --armor KEY | sudo apt-key add -
```
with the corresponding keys. What am I doing wrong?? 
Thanks a lot for your help.

---

