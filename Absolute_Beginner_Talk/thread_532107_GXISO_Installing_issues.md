---
title: "GXISO Installing issues"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by streetsurfer on 2007-08-22
This was asked in very very old threads but nobody had given a reply :(
When i try run sudo python setup.py install

i get this error at the end

--------------------
sh: xgettext: not found
sh: msgmerge: not found
sh: msgfmt: not found
sh: msgmerge: not found
sh: msgfmt: not found
/usr/lib/python2.5/distutils/dist.py:263: UserWarning: Unknown distribution option: 'windows'
  warnings.warn(msg)
running install
running build
running build_py
running build_scripts
running install_lib
running install_scripts
changing mode of /usr/bin/gxiso.py to 755
running install_data
error: can't copy 'po/tmp/fr/gxiso.mo': doesn't exist or not a regular file

does this mean i am missing some installed files??
thanks in advanced

---

### Post by runemaste644 on 2007-09-16
Look for xgettext, msgmerge, and msgfmt in Synaptic. That might help.

---

### Post by runemaste644 on 2007-09-16
Or just try to install Python from Synaptic...

---

### Post by JacquesBouman on 2008-05-23
You can just run the gxiso.py script in the src folder.

---

### Post by Vock on 2008-07-16
Um... kinda of dumb question, but after you run the python script, how do you actually run the program???

---

