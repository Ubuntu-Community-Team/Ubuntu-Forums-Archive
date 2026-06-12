---
title: "Installing .rpm files?"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by neoltlink on 2005-12-18
Hi...
Does anybody have a link or something that tells how to install something that is .rpm?
I'm trying to install frostwire. Thanks. ;)

---

### Post by Leif on 2005-12-18
sudo apt-get alien
sudo alien frostwire.rpm
sudo dpkg -i frostwire.deb

the rpm and deb file names may require modifying, and it's also not guaranteed that the rpm will work flawlessly, but you gotta try to find out

---

### Post by Sutekh on 2005-12-18
You need *alien* to install .rpm packages.
```

sudo apt-get install alien 
sudo alien <packagename>.rpm
sudo dpkg -i <packagename>.deb

```
Isn't Frostwire in any repositories?
Ed: Seems it isn't

---

### Post by Evil Whisper on 2005-12-18
[http://www.ubuntuforums.org/showthread.php?t=80638&highlight=Frostwire](http://www.ubuntuforums.org/showthread.php?t=80638&highlight=Frostwire)

here you go a frostwire .deb file

install like this:

```

sudo dpkg -i FrostWire-4.9.34-0.i586.deb

```

as for installing stuff from rpm's you can try alien to convert them to .debs

```

sudo apt-get install alien

```

then you just do this to use alien

```

sudo alien name-of-rpm.rpm

```

then

```

sudo dpkg -i name-of-rpm.deb

```

Hope this helps,
- Evil Whisper

Edit: Sutekh finished replying before me :(

---

### Post by neoltlink on 2005-12-18
Awsome, thanks! :D

---

### Post by neoltlink on 2005-12-18
Bah, one more question:
When I download the frostwire rpm, should it just go to desktop or someplace else?
I downloaded it to the desktop and when I enter the code into the terminal it says File "frostwire-blah blah blah.rpm" not found".
EDIT"Meant to edit above post, sorry :P

---

### Post by Rackerz on 2005-12-18
You first have to tell the terminal to look in the desktop, you do this by typing

> cd ~/Desktop

---

### Post by Evil Whisper on 2005-12-18
If the rpm install fails there is a link to the .deb file in my post above but heres the direct link to the deb that **gubatron** posted in the other thread.

[http://72.36.161.90/~skyper/test/FrostWire-4.9.34-0.i586.deb](http://72.36.161.90/~skyper/test/FrostWire-4.9.34-0.i586.deb)

---

### Post by neoltlink on 2005-12-18
Alright, that part worked perfectly. :)
Now there are two .tar.gz files and one labled 'debian-binary'.
Don't really know where to go fromthat either, any help? ;)
First time I tried installing a program.

---

### Post by neoltlink on 2005-12-19
A bump before I fall asleep

---

### Post by Evil Whisper on 2005-12-19
uhm did you extract it?

If you extracted the .deb file dont :p

just CD to the directory where the .deb is and type this in console:

```

sudo dpkg -i FrostWire-4.9.34-0.i586.deb

```

---

### Post by neoltlink on 2005-12-19
Cool, got it now, thanks. :)

---

### Post by Daniel McLaws on 2005-12-28
[QUOTE=Sutekh]You need *alien* to install .rpm packages.
```

sudo apt-get install alien 
sudo alien <packagename>.rpm
sudo dpkg -i <packagename>.deb

```
Isn't Frostwire in any repositories?
Ed: Seems it isn't[/QUOTE]

I tried using the above commands to install plucker desktop, and got the following error message at the 2nd step:

danny@24-107-75-218:~$ sudo alien plucker-desktop-1.6.0.0-1.i386.rpm
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} plucker-desktop-1.6.0.0-1.i386.rpm":  at /usr/share/perl5/Alien/Package.pm line 449.

P.S., the rpm file was located in the same directory that I was in.  I'm not sure what the error message meant, or what to do about it. I am trying to install the plucker programs specifically, but in general would like to know how to install rpm files in general.  I would appreciate anyone's help out there. By the way, Ubuntu has been a learning experience, but a fun one. 

DJM

---

### Post by poofyhairguy on 2005-12-29
[QUOTE=Daniel McLaws]I tried using the above commands to install plucker desktop, and got the following error message at the 2nd step:

danny@24-107-75-218:~$ sudo alien plucker-desktop-1.6.0.0-1.i386.rpm
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} plucker-desktop-1.6.0.0-1.i386.rpm":  at /usr/share/perl5/Alien/Package.pm line 449.

P.S., the rpm file was located in the same directory that I was in.  I'm not sure what the error message meant, or what to do about it. I am trying to install the plucker programs specifically, but in general would like to know how to install rpm files in general.  I would appreciate anyone's help out there. By the way, Ubuntu has been a learning experience, but a fun one. 

DJM[/QUOTE]

Alien does not always work. Works for me like 70% of time. Thats why I often try to find more than one RPM (say a Mandrake, SUSE, and Fedora one) for the same app. Keep trying till one works.

---

