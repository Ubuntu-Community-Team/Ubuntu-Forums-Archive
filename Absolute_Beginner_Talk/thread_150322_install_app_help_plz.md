---
title: "install app help plz"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by Chyper on 2006-03-25
ubuntu:~$ cd Desktop/
ubuntu:~/Desktop$ sudo rm -r gxiso-1.5
Password:
ubuntu:~/Desktop$ tar -xvzf gxiso-1.5.tar.gz
gxiso-1.5/
gxiso-1.5/po/
gxiso-1.5/po/fr.po
gxiso-1.5/po/it.po
gxiso-1.5/po/POTFILES.in
gxiso-1.5/src/
gxiso-1.5/src/gxiso.glade
gxiso-1.5/src/gxiso.py
gxiso-1.5/src/gxiso.png
gxiso-1.5/src/gxiso.gladep
gxiso-1.5/src/gxiso_save.py
gxiso-1.5/src/__init__.py
gxiso-1.5/NEWS
gxiso-1.5/TODO
gxiso-1.5/LICENSE
gxiso-1.5/README
gxiso-1.5/PKG-INFO
gxiso-1.5/gxiso.ico
gxiso-1.5/gxiso.nsi
gxiso-1.5/setup.cfg
gxiso-1.5/MANIFEST.in
gxiso-1.5/build.bat
gxiso-1.5/AUTHORS
gxiso-1.5/setup.py
gxiso-1.5/ChangeLog
ubuntu:~/Desktop$ cd gxiso-1.5
ubuntu:~/Desktop/gxiso-1.5$ sudo python setup.py install
sh: xgettext: command not found
sh: msgmerge: command not found
sh: msgfmt: command not found
sh: msgmerge: command not found
sh: msgfmt: command not found
/usr/lib/python2.4/distutils/dist.py:236: UserWarning: Unknown distribution option: 'windows'
  warnings.warn(msg)
running install
running build
running build_py
creating build
creating build/lib
creating build/lib/gxiso
copying src/gxiso.py -> build/lib/gxiso
copying src/gxiso_save.py -> build/lib/gxiso
copying src/__init__.py -> build/lib/gxiso
running build_scripts
creating build/scripts-2.4
copying and adjusting src/gxiso.py -> build/scripts-2.4
changing mode of build/scripts-2.4/gxiso.py from 644 to 755
running install_lib
running install_scripts
copying build/scripts-2.4/gxiso.py -> /usr/bin
changing mode of /usr/bin/gxiso.py to 755
running install_data
error: can't copy 'po/tmp/fr/gxiso.mo': doesn't exist or not a regular file
ubuntu:~/Desktop/gxiso-1.5$

---

### Post by dcstar on 2006-03-25
[QUOTE=Chyper]
......
gxiso-1.5/README
......[/QUOTE]
And what does it say in that file?

---

### Post by Chyper on 2006-03-25
what ?

 	gXiso is graphical tool to extract and/or upload xbox iso images to xbox.
	
system ?

	It's written in python, and thus is very portable. 
	It has been tested on Linux and Windows.
	
dependancies ?

	GTK 2.4, PyGTK 2.0
	
how to install ?

	Windows:
	use the binary installlers.
	You MUST have winrar installed in c:\program files\winrar for
	RAR support.

	linux:
	sudo python setup.py install
	You MUST have unrar (or better: rar) installed for RAR support.
	
notes: 
	* xbox has to be started (ahem) and running a FTP server to receive files.
	* when using avalaunch: disable boost mode and free root space
	* if you erase files or destroy your xbox: WE ARE NOT RESPONSIBLE !
	* USE AT YOU OWN RISK !
	* do not use with copyrighted material.
	* use with this: [http://www.pouet.net/prod.php?which=10586](http://www.pouet.net/prod.php?which=10586)
 
send feedback: kassoulet gmail com

---

### Post by Chyper on 2006-03-25
And?

---

### Post by Chyper on 2006-03-27
:/

---

### Post by kassoulet on 2008-05-13
You need to install the 'gettext' package

---

### Post by PDG1 on 2008-07-09
oh my... you have no clue how much this helped me

Thanks

---

