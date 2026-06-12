---
title: "Installing from source"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-05-21
Hi,

I'm trying to install a program from source using the guide from [psychocat]("http://www.psychocats.net/linux/installingsoftware.php") but I can't get past ./configure. It tells me there is no such directory! What am I missing? 

Thanks!

EDIT: Here is my terminal code:

```
kyle@k8nvm:~$ tar -xvzf mnemosyne-0.9.2.tgz
mnemosyne-0.9.2/AUTHORS
mnemosyne-0.9.2/ChangeLog
mnemosyne-0.9.2/LICENSE
mnemosyne-0.9.2/README
mnemosyne-0.9.2/mnemosyne/
mnemosyne-0.9.2/mnemosyne/core/
mnemosyne-0.9.2/mnemosyne/core/mnemosyne_core.py
mnemosyne-0.9.2/mnemosyne/core/__init__.py
mnemosyne-0.9.2/mnemosyne/core/mnemosyne_log.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/
mnemosyne-0.9.2/mnemosyne/pyqt_ui/main_frm.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/main_frm.ui
mnemosyne-0.9.2/mnemosyne/pyqt_ui/add_items_frm.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/add_items_frm.ui
mnemosyne-0.9.2/mnemosyne/pyqt_ui/import_frm.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/import_frm.ui
mnemosyne-0.9.2/mnemosyne/pyqt_ui/config_dlg.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/activate_categories_dlg.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/mnemosyne
mnemosyne-0.9.2/mnemosyne/pyqt_ui/config_frm.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/config_frm.ui
mnemosyne-0.9.2/mnemosyne/pyqt_ui/activate_categories_frm.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/activate_categories_frm.ui
mnemosyne-0.9.2/mnemosyne/pyqt_ui/clean_duplicates.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/export_dlg.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/export_frm.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/export_frm.ui
mnemosyne-0.9.2/mnemosyne/pyqt_ui/edit_items_dlg.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/edit_item_dlg.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/edit_items_frm.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/edit_items_frm.ui
mnemosyne-0.9.2/mnemosyne/pyqt_ui/product_tour_dlg.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/edit_item_frm.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/edit_item_frm.ui
mnemosyne-0.9.2/mnemosyne/pyqt_ui/product_tour_frm.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/product_tour_frm.ui
mnemosyne-0.9.2/mnemosyne/pyqt_ui/__init__.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/main_dlg.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/add_items_dlg.py
mnemosyne-0.9.2/mnemosyne/pyqt_ui/import_dlg.py
mnemosyne-0.9.2/mnemosyne/__init__.py
mnemosyne-0.9.2/mnemosyne/version.py
mnemosyne-0.9.2/pixmaps/
mnemosyne-0.9.2/pixmaps/edit.png
mnemosyne-0.9.2/pixmaps/edit_add.png
mnemosyne-0.9.2/pixmaps/fileimport.png
mnemosyne-0.9.2/pixmaps/mnemosyne.png
mnemosyne-0.9.2/pixmaps/filenew.png
mnemosyne-0.9.2/pixmaps/filesave.png
mnemosyne-0.9.2/pixmaps/fileexport.png
mnemosyne-0.9.2/pixmaps/configure.png
mnemosyne-0.9.2/pixmaps/editclear.png
mnemosyne-0.9.2/pixmaps/filesaveas.png
mnemosyne-0.9.2/pixmaps/fileopen.png
mnemosyne-0.9.2/pixmaps/editdelete.png
mnemosyne-0.9.2/pixmaps/exit.png
mnemosyne-0.9.2/pixmaps/contents.png
mnemosyne-0.9.2/setup.py
kyle@k8nvm:~$ cd mnemosyne-0.9.2
kyle@k8nvm:~/mnemosyne-0.9.2$ ./configure
bash: ./configure: No such file or directory

```

---

### Post by bluevoodoo1 on 2006-05-21
Where's the file you're trying to configure? home? Desktop? Other folder?

---

### Post by Belathor on 2006-05-21
home

---

### Post by aysiu on 2006-05-21
Post the output of these commands (in this order): ```
cd
ls
./configure
```

---

### Post by Belathor on 2006-05-21
```
kyle@k8nvm:~/mnemosyne-0.9.2$ cd
kyle@k8nvm:~$ ls
Desktop                       gpg                  My Documents
easyubuntu                    Linux Distro's       SetupRecallPlus.exe
easyubuntu-3.0-beta.tar.gz.3  mnemosyne-0.9.2      sources.list.backup
easyubuntu-3.0-beta.tar.gz.4  mnemosyne-0.9.2.tgz  sources.list.backup~
Examples                      Music
kyle@k8nvm:~$ ./configure
bash: ./configure: No such file or directory

```

---

### Post by bluevoodoo1 on 2006-05-21
did you unzip or untar it? You can do with the right click menu.

you will have to change directories using the "cd" command to get inside the folder that is created after you unzip/untar it.

```
:~$ cd foldername
:~/foldername$ ./configure
```

What program is this? Is it not available with Synaptic?

EDIT: Is that the folder? mnemosyne-0.9.2 ? if so...

```
cd mnemosyne-0.9.2 
./configure
```

---

### Post by aysiu on 2006-05-21
mnemosyne isn't a normal compile from source.

This is what the README file says: ```
INSTALLATION:

-Make sure you have Python 2.4
-Make sure you have PyQt (http://www.riverbankcomputing.co.uk/pyqt/index.php)
 installed.
-If you want to import XML, also install PyXML (http://pyxml.sourceforge.net)
-Type 'python setup.py install' as root.
-Run the application by typing 'mnemosyne'.
-To run the SuperKaramba widget, copy the mnemosyne_superkaramba directory 
 to wherever you keep your superkaramba themes. Run superkaramba, and
 point it to superkaramba_mnemosyne.theme. SuperKaramba 0.33 or higher is
 required.
``` So you want to ```
sudo apt-get update
sudo apt-get install python2.4 pyqt-tools
cd ~/mnemosyne-0.9.2.
sudo python setup.py install
```

---

### Post by user1397 on 2006-05-21
[quote=bluevoodoo1]```
cd mnemosyne-0.9.2 
./configure
```[/quote] Belathor already tried that...
(look at first post)

---

### Post by Belathor on 2006-05-21
[QUOTE=aysiu]mnemosyne isn't a normal compile from source.

This is what the README file says: ```
INSTALLATION:

-Make sure you have Python 2.4
-Make sure you have PyQt (http://www.riverbankcomputing.co.uk/pyqt/index.php)
 installed.
-If you want to import XML, also install PyXML (http://pyxml.sourceforge.net)
-Type 'python setup.py install' as root.
-Run the application by typing 'mnemosyne'.
-To run the SuperKaramba widget, copy the mnemosyne_superkaramba directory 
 to wherever you keep your superkaramba themes. Run superkaramba, and
 point it to superkaramba_mnemosyne.theme. SuperKaramba 0.33 or higher is
 required.
``` So you want to ```
sudo apt-get update
sudo apt-get install python2.4 pyqt-tools
cd ~/mnemosyne-0.9.2.
sudo python setup.py install
```[/QUOTE]

Thanks for that, Aysiu! Unfortunately now it still won't run!

```
kyle@k8nvm:~$ mnemosyne
Traceback (most recent call last):
  File "/usr/bin/mnemosyne", line 10, in ?
    from qt import *
ImportError: No module named qt

```

Thanks for all your help everyone, sofar!

---

### Post by bluevoodoo1 on 2006-05-21
[QUOTE=erik1397]Belathor already tried that...
(look at first post)[/QUOTE]

Yes, the terminal code was added after I had edited my post.

---

### Post by Belathor on 2006-05-21
So, do I still need to do that ./configure business to get the program working?

---

### Post by bluevoodoo1 on 2006-05-21
[QUOTE=Belathor]So, do I still need to do that ./configure business to get the program working?[/QUOTE]


no

---

### Post by aysiu on 2006-05-21
[QUOTE=Belathor]So, do I still need to do that ./configure business to get the program working?[/QUOTE] You might have to for [PyQT](http://www.riverbankcomputing.co.uk/pyqt/index.php). I thought PyQT-tools would do the trick, but I guess not.

The PyQT link is another .tar.gz with this README file: ```
                    PyQt - Python Bindings for the Qt Toolkit


INTRODUCTION

These are the Python bindings for Qt.  You must also have the SIP Python
bindings generator installed.

The homepage is http://www.riverbankcomputing.co.uk/pyqt/.

The homepage of SIP is http://www.riverbankcomputing.co.uk/sip/.


COMMERCIAL VERSION

If you have the Commercial version of PyQt then you should also have a
license file that you downloaded separately.  The license file must be copied
to the "sip" directory before starting to build PyQt.


INSTALLATION

Check for any other README files in this directory that relate to your
particular platform.  Feel free to contribute a README for your platform or to
provide updates to any existing documentation.

The first step is to configure PyQt by running the following command.

	python configure.py

This assumes that the correct Python interpreter is on your path.  Something
like the following may be appropriate on Windows.

	c:\python23\python configure.py

If you have multiple versions of Python installed then make sure you use the
interpreter for which you wish to generate bindings for.

The configure.py script takes many options.  Use the "-h" command line option
to display a full list of the available options.

The next step is to build PyQt using your platform's make command.

	make

The final step is to install PyQt by running the following command.  (Depending
on your system you may require root or administrator privileges.)

	make install


THE REST OF THE DISTRIBUTION

The "examples2" and "examples3" directories contain some examples (for Qt v2.x
and Qt v3.x respectively) of Python scripts, including versions of the standard
Qt tutorials and examples.

The "doc" directory contains SGML and HTML documentation for the bindings.
This documentation includes a section describing the differences visible to
the Python programmer between this and the previous version - please read it.


Phil Thompson
phil@riverbankcomputing.co.uk
```

---

### Post by Belathor on 2006-05-21
I managed to get it working by downloading the python 2.4 qt related packages from Synaptic. Thanks very very much for helping me through installing my first program from source!!!

---

### Post by aysiu on 2006-05-21
[QUOTE=Belathor]I managed to get it working by downloading the python 2.4 qt related packages from Synaptic. Thanks very very much for helping me through installing my first program from source!!![/QUOTE] Glad you got it working. Can you post exactly what your steps were (the name of the QT-related packages), just in case someone else wanting to install this application stumbles on this thread a few weeks from now?

---

### Post by Belathor on 2006-05-21
python2.4-qt3
python2.4-qtext

---

### Post by aysiu on 2006-05-21
Thanks.

---

