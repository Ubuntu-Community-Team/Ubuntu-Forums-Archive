---
title: "backup your pc"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by spamalot on 2007-06-11
hey!

i've been trying to look for a nice and easy  backup gui. i've tried 2 (see below), each failing in their own way. could someone kindly suggest another tool or fixes? thanks!

*keep* seems perfect except i ran into this error upon backing up:
An error occured making /home/er backup:
Fatal Error: Destination directory /media/IOMEGA_HDD exists, but does not look like a rdiff-backup directory. Running rdiff-backup like this could mess up what is currently in it. If you want to update or overwrite it, run rdiff-backup with the --force option.

*fwbackup* at [http://www.diffingo.com/content/view/12/45/lang,en/:](http://www.diffingo.com/content/view/12/45/lang,en/:) 
doing ./install.sh returns

[: 49: ==: unexpected operator
[: 49: ==: unexpected operator
[: 49: ==: unexpected operator
Invalid choice. Please type "y" for yes, and "n" for no.
-ne Continue? [y/N]
./install.sh: line 32: 14370 Segmentation fault      (core dumped) sh /usr/bin/fwbackups-uninstall
Creating directories...
mkdir: cannot create directory `/etc/fwbackups': File exists
mkdir: cannot create directory `/usr/share/fwbackups': File exists
mkdir: cannot create directory `/usr/lib/python2.4/site-packages/fwbackups': File exists
Copying files...
cp: target `/etc/security/console.apps/' is not a directory: No such file or directory
cp: cannot stat `./usr/lib/python2.4/site-packages/fwbackups/*': No such file or directory
Creating symbolic links...
ln: creating symbolic link `/usr/bin/fwbackups' to `/usr/bin/consolehelper': File exists
ln: creating symbolic link `/usr/bin/fwbackups-run' to `/usr/bin/consolehelper': File exists
You can later remove fwbackups at any time by running in a terminal:
$       fwbackups-uninstall

---

### Post by ramjet_1953 on 2007-06-11
I have a laptop, so I decided to buy another hard drive and install it in one of those small enclosures that have a USB port.

I downloaded Ghost for Linux (G4L), which is an iso and burnt the iso to a CD.

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

To do a complete 1:1 backup, I just boot from the G4L CD and choose the option to do a local clone of my HDD.

Works like a charm and produces an exact copy, including GRUB.

Regards,
Roger :cool:

---

### Post by Jim Darrough on 2007-06-16
I have a small question. I want to clone my Ubuntu Edgy hard drive to an external USB drive with an old copy of Dapper on it. I will then upgrade my Edgy drive to Fiesty. Will the Ghost application cited above allow me to do that?

---

### Post by razeshkale on 2007-06-18
I downloaded g4l-v0.22.devel.tar.gz from [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l) and i cant do anything with that?

Does anyonw knows how to Burn ISO of this file for G4L backup?
Even i got Error on Extracting this file...
Error is
:: screen shot

---

