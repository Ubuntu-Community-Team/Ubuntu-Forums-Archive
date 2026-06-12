---
title: "Can anyone help me get ANKI the very cool looking Japanese learning software running?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-08-14
I really want to get ANKi, found here:

[http://repose.cx/anki/download/index.html](http://repose.cx/anki/download/index.html)

...running on my Xubuntu.

Now, the website says that ANKI requires PyQt4.2, which there is a deb for on the website. I  extracted that first, with no errors. (just a message that an earlier version is in the repo's).

Second step, downloaded and extracted the tgz file, got the following error:

mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/__init__.py' with `anki-0.3.2/libanki/anki/support/chinese/__init__.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/__init__.py' with `anki-0.3.2/libanki/anki/support/__init__.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/__init__.py' with `anki-0.3.2/libanki/anki/__init__.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/README' with `anki-0.3.2/libanki/emacs/README'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/graphs.py' with `anki-0.3.2/ui/graphs.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/importing.py' with `anki-0.3.2/ui/importing.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/sync.py' with `anki-0.3.2/ui/sync.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/__init__.py' with `anki-0.3.2/ui/__init__.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/setup.py' with `anki-0.3.2/mac/setup.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/modelproperties.py' with `anki-0.3.2/forms/modelproperties.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/importing.py' with `anki-0.3.2/forms/importing.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/displayproperties.py' with `anki-0.3.2/forms/displayproperties.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/deckproperties.py' with `anki-0.3.2/forms/deckproperties.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/cardlist.py' with `anki-0.3.2/forms/cardlist.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/addcards.py' with `anki-0.3.2/forms/addcards.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/preferences.py' with `anki-0.3.2/forms/preferences.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/__init__.py' with `anki-0.3.2/forms/__init__.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/about.py' with `anki-0.3.2/forms/about.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/main.py' with `anki-0.3.2/forms/main.py'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/.hgignore' with `anki-0.3.2/.hgignore'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/COPYING' with `anki-0.3.2/COPYING'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/ChangeLog.old' with `anki-0.3.2/ChangeLog.old'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/README' with `anki-0.3.2/README'
mv: will not overwrite just-created `/home/marshal/Desktop/anki-0.3.2/messages.pot' with `anki-0.3.2/locale/messages.pot'


Can anyone help me get this excellent looking program up and running. I am pretty newbie when it comes to installing something not all ready in the repos with out clear instructions.
thanks

---

### Post by GeeZor on 2007-08-14
try extracing in a different folder?

just a guess. need more info

---

### Post by Hospadar on 2007-08-14
You should be fine I think installing python qt4 from the repos, it's a little older but i doubt it will make a difference and it will be better in the long run.

You could either install "python-qt4" and "python-sip4" from synaptic, or on the command line you could do ```
sudo apt-get install python-qt4 python-sip4
```Then you should be able to build the source package for the actual software just fine.

If it gives you errors, after that, post em up, along with specifically what command generated them.

---

### Post by zazen666 on 2007-08-14
> **Hospadar said:**
> You should be fine I think installing python qt4 from the repos, it's a little older but i doubt it will make a difference and it will be better in the long run.

You could either install "python-qt4" and "python-sip4" from synaptic, or on the command line you could do ```
sudo apt-get install python-qt4 python-sip4
```Then you should be able to build the source package for the actual software just fine.

If it gives you errors, after that, post em up, along with specifically what command generated them.

Ok, so  Installed PYTHON-sip4 with the comand line code you gave me.

Second, I used xarchiver to extract the file to my home directory.
This is the FULL command output with errors (sorry its so long, not sure what is usefull to you)..

anki-0.3.2/tools/update_translations.sh
anki-0.3.2/tools/build_ui.sh
anki-0.3.2/locale/ja_JP/LC_MESSAGES/ankiqt.mo
anki-0.3.2/locale/messages.pot
anki-0.3.2/locale/ankiqt_ja_JP.po
anki-0.3.2/ankiqt.py
anki-0.3.2/icons/view_text.png
anki-0.3.2/icons/spreadsheet.png
anki-0.3.2/icons/player_pause.png
anki-0.3.2/icons/package_games_card.png
anki-0.3.2/icons/package_edutainment.png
anki-0.3.2/icons/multisynk.png
anki-0.3.2/icons/looknfeel.png
anki-0.3.2/icons/kpersonalizer.png
anki-0.3.2/icons/kanji.png
anki-0.3.2/icons/help.png
anki-0.3.2/icons/gohome.png
anki-0.3.2/icons/fonts.png
anki-0.3.2/icons/filesaveas.png
anki-0.3.2/icons/filesave.png
anki-0.3.2/icons/fileopen.png
anki-0.3.2/icons/filenew.png
anki-0.3.2/icons/fileimport.png
anki-0.3.2/icons/fileclose.png
anki-0.3.2/icons/exit.png
anki-0.3.2/icons/editdelete.png
anki-0.3.2/icons/edit.png
anki-0.3.2/icons/contents2.png
anki-0.3.2/icons/contents.png
anki-0.3.2/icons/configure.png
anki-0.3.2/icons/compfile.png
anki-0.3.2/icons/colorscm.png
anki-0.3.2/icons/bookmark.png
anki-0.3.2/icons/anki.png
anki-0.3.2/icons/add.png
anki-0.3.2/icons/folder_sound.png
anki-0.3.2/icons/image.png
anki-0.3.2/icons/sound.png
anki-0.3.2/icons/text_bold.png
anki-0.3.2/icons/text_italic.png
anki-0.3.2/icons/text_under.png
anki-0.3.2/icons/folder_image.png
anki-0.3.2/config.py
anki-0.3.2/CREDITS
anki-0.3.2/icons.qrc
anki-0.3.2/README
anki-0.3.2/ChangeLog.old
anki-0.3.2/COPYING
anki-0.3.2/.hgignore
anki-0.3.2/icons_rc.py
anki-0.3.2/README.development
anki-0.3.2/forms/main.py
anki-0.3.2/forms/about.py
anki-0.3.2/forms/__init__.py
anki-0.3.2/forms/preferences.py
anki-0.3.2/forms/sort.py
anki-0.3.2/forms/infodialog.py
anki-0.3.2/forms/addcards.py
anki-0.3.2/forms/addmodel.py
anki-0.3.2/forms/cardlist.py
anki-0.3.2/forms/changemap.py
anki-0.3.2/forms/deckproperties.py
anki-0.3.2/forms/displayproperties.py
anki-0.3.2/forms/importing.py
anki-0.3.2/forms/modelproperties.py
anki-0.3.2/forms/syncdeck.py
anki-0.3.2/mac/anki.icns
anki-0.3.2/mac/setup.py
anki-0.3.2/mac/make.sh
anki-0.3.2/ui/unsaved.py
anki-0.3.2/ui/about.py
anki-0.3.2/ui/__init__.py
anki-0.3.2/ui/lookup.py
anki-0.3.2/ui/main.py
anki-0.3.2/ui/sync.py
anki-0.3.2/ui/view.py
anki-0.3.2/ui/help.py
anki-0.3.2/ui/preferences.py
anki-0.3.2/ui/update.py
anki-0.3.2/ui/importing.py
anki-0.3.2/ui/graphs.py
anki-0.3.2/ui/exporting.py
anki-0.3.2/ui/status.py
anki-0.3.2/ui/addcards.py
anki-0.3.2/ui/cardlist.py
anki-0.3.2/ui/deckproperties.py
anki-0.3.2/ui/displayproperties.py
anki-0.3.2/ui/facteditor.py
anki-0.3.2/ui/modelchooser.py
anki-0.3.2/ui/modelproperties.py
anki-0.3.2/ui/tools.py
anki-0.3.2/designer/syncdeck.ui
anki-0.3.2/designer/main.ui
anki-0.3.2/designer/about.ui
anki-0.3.2/designer/preferences.ui
anki-0.3.2/designer/infodialog.ui
anki-0.3.2/designer/addcards.ui
anki-0.3.2/designer/sort.ui
anki-0.3.2/designer/addmodel.ui
anki-0.3.2/designer/cardlist.ui
anki-0.3.2/designer/changemap.ui
anki-0.3.2/designer/deckproperties.ui
anki-0.3.2/designer/displayproperties.ui
anki-0.3.2/designer/modelproperties.ui
anki-0.3.2/designer/importing.ui
anki-0.3.2/libanki/tools/translate.sh
anki-0.3.2/libanki/tools/tests.sh
anki-0.3.2/libanki/setup.py
anki-0.3.2/libanki/emacs/anki.el
anki-0.3.2/libanki/emacs/README
anki-0.3.2/libanki/anki/sync.py
anki-0.3.2/libanki/anki/sched.py
anki-0.3.2/libanki/anki/errors.py
anki-0.3.2/libanki/anki/emacs.py
anki-0.3.2/libanki/anki/__init__.py
anki-0.3.2/libanki/anki/stats.py
anki-0.3.2/libanki/anki/importing.py
anki-0.3.2/libanki/anki/samples/JLPT3+4 411 words.anki
anki-0.3.2/libanki/anki/samples/JLPT4 318 words.anki
anki-0.3.2/libanki/anki/samples/Heisig.anki
anki-0.3.2/libanki/anki/samples/JLPT2 657 words.anki
anki-0.3.2/libanki/anki/samples/Russian.anki
anki-0.3.2/libanki/anki/graphs.py
anki-0.3.2/libanki/anki/ids.py
anki-0.3.2/libanki/anki/deck.py
anki-0.3.2/libanki/anki/lang.py
anki-0.3.2/libanki/anki/fonts.py
anki-0.3.2/libanki/anki/cards.py
anki-0.3.2/libanki/anki/decorators.py
anki-0.3.2/libanki/anki/facts.py
anki-0.3.2/libanki/anki/models.py
anki-0.3.2/libanki/anki/support/japanese.py
anki-0.3.2/libanki/anki/support/__init__.py
anki-0.3.2/libanki/anki/support/chinese/unihan.pickle
anki-0.3.2/libanki/anki/support/chinese/pickle_unihan.py
anki-0.3.2/libanki/anki/support/chinese/__init__.py
anki-0.3.2/libanki/anki/support/chinese/README
anki-0.3.2/libanki/anki/utils.py
anki-0.3.2/libanki/anki/stdmodels.py
anki-0.3.2/libanki/anki/cardmodels.py
anki-0.3.2/libanki/anki/fields.py
anki-0.3.2/libanki/anki/locale/messages.pot
anki-0.3.2/libanki/anki/locale/libanki_ja_JP.po
anki-0.3.2/libanki/anki/locale/ja_JP/LC_MESSAGES/libanki.mo
anki-0.3.2/libanki/ChangeLog.old
anki-0.3.2/libanki/COPYING
anki-0.3.2/libanki/.hgignore
anki-0.3.2/libanki/ez_setup.py
anki-0.3.2/libanki/setup.cfg
anki-0.3.2/libanki/tests/__init__.py
anki-0.3.2/libanki/tests/test_sync.py
anki-0.3.2/libanki/tests/test_deck.py
anki-0.3.2/libanki/tests/test_importing.py
anki-0.3.2/libanki/tests/test_lang.py
anki-0.3.2/libanki/tests/test_model.py
anki-0.3.2/libanki/tests/test_sched.py
anki-0.3.2/libanki/tests/test_support.py
anki-0.3.2/libanki/tests/test_fonts.py
anki-0.3.2/libanki/tests/importing/text-4fields.txt
anki-0.3.2/libanki/tests/importing/text-2fields.txt
anki-0.3.2/libanki/tests/importing/test.mem
anki-0.3.2/libanki/tests/importing/test-v8.fc
anki-0.3.2/libanki/tests/importing/test-v8-jp.fc
anki-0.3.2/libanki/tests/importing/text-blank.txt
anki-0.3.2/libanki/tests/importing/fleurs.fc
anki-0.3.2/libanki/json2.py
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/__init__.py' with `anki-0.3.2/libanki/anki/support/chinese/__init__.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/__init__.py' with `anki-0.3.2/libanki/anki/support/__init__.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/__init__.py' with `anki-0.3.2/libanki/anki/__init__.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/README' with `anki-0.3.2/libanki/emacs/README'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/graphs.py' with `anki-0.3.2/ui/graphs.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/importing.py' with `anki-0.3.2/ui/importing.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/sync.py' with `anki-0.3.2/ui/sync.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/__init__.py' with `anki-0.3.2/ui/__init__.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/setup.py' with `anki-0.3.2/mac/setup.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/modelproperties.py' with `anki-0.3.2/forms/modelproperties.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/importing.py' with `anki-0.3.2/forms/importing.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/displayproperties.py' with `anki-0.3.2/forms/displayproperties.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/deckproperties.py' with `anki-0.3.2/forms/deckproperties.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/cardlist.py' with `anki-0.3.2/forms/cardlist.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/addcards.py' with `anki-0.3.2/forms/addcards.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/preferences.py' with `anki-0.3.2/forms/preferences.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/__init__.py' with `anki-0.3.2/forms/__init__.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/about.py' with `anki-0.3.2/forms/about.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/main.py' with `anki-0.3.2/forms/main.py'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/.hgignore' with `anki-0.3.2/.hgignore'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/COPYING' with `anki-0.3.2/COPYING'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/ChangeLog.old' with `anki-0.3.2/ChangeLog.old'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/README' with `anki-0.3.2/README'
mv: will not overwrite just-created `/home/marshal/anki-0.3.2/messages.pot' with `anki-0.3.2/locale/messages.pot'


Now, questions:
Do I need to start fresh and "purge" anki or something. how do I do that.
Or, after extracting, do I need to use the command line to "make" or something?

---

### Post by Hospadar on 2007-08-14
Well shoot, that's easier than I thought it would be.  Here's what you should do.  First, if you tried to extract it once already, delete the folder you extracted it to, and exctract a fresh copy, just get that folder in the archive onto your desktop.  I'm not sure what your extractor is doing (the error might be there) but let's try using the command line

I'm gonna copy the files to your home directory so they can live there (and not taking up space on your desktop

First I'm assuming you downloaded the .tgz file to your desktop so in a command line let's cd to it, copy it to your home directory, go there, remove the old files, and then extract the directory, cd into the extracted directory, and then start the application.
```
cd ~/Desktop
cp anki*.tgz ~
cd ~
rm -rf anki-0.3.2
tar -xzvf anki*.tgz
cd anki*
python ankiqt.py

```This program is actually a python script, hence why we need to use python to run it (And also why we don't need to compile anything with make).  If you want to make a shortcut on your desktop, right click on the desktop, "create launcher" and for "command" enter "python ~/anki-0.3.2/ankiqt.py"

After you are done, you can delete the .tgz files from your desktop and home directory if you want.

---

### Post by seshomaru samma on 2007-08-14
Edit : Never Mind........

---

### Post by Hospadar on 2007-08-14
Well they are providing .debs for python-qt4 and python-sip, not for their actual software, and those are both available from the repo

---

### Post by zazen666 on 2007-08-14
You Rock you rock you rock...

Did I say you rock?

That did it. Basically, when Iwas fooling around waitng for your replay, I found that if Icliked on the tgz, and selected "open with xarchive" I got the error(even after deleting the file) but if Iused the "extract to" option, no error.
Anyways, it is up and running now. This looks like a great program.
-thanks

---

### Post by zazen666 on 2007-08-14
just played with it a bit, and seems that it wont display a kanji when  click on the keyword:

should look like this..

[http://repose.cx/anki/shots.html](http://repose.cx/anki/shots.html)

but looks like this:

see attached photo.
It appers something on my computer is hinder the display? 


well, I have to sleep now. its late here in japan.
I will try again tomorrow.

Thanks again

---

### Post by zazen666 on 2007-08-14
Hello all,
I woke up today to give it another, and Iwas getting some new errors. I check the website and the just released anki 3.3 with the following read me file:

Anki for Linux
-------------------------------------

Prerequisites:

1. A recent python (2.4 should be fine)
2. libqt4.2+
3. python-qt/pyqt 4.2+

If your version of Debian/Ubuntu is not new enough, it will include an old
copy of python-qt. You must have at least python-qt 4.2 to run Anki.

For graph generation:

1. python-numpy (numpy)
2. python-matplotlib (matplotlib)

The most recent release of matplotlib is broken. Downgrade for now.

For furigana generation:

1. kakasi

To install:

1. cd; tar xzf ankiqt<...>.tgz
2. cd ankit<...>/libanki
3. sudo python setup.py install
4. cd ..; sudo python setup.py install
5. anki

For more information and the latest version, please see the website at:

[http://repose.cx/anki/](http://repose.cx/anki/)


So, it looks like I will need to start afresh? I'm gonna come back to this later today when I have some time, I'm just gonna post this here for now in case people are reading.
cheers

---

### Post by zazen666 on 2007-08-15
Well, I get all the way to INSTALL STEP FOUR, and I get the following error

Traceback (most recent call last):
  File "setup.py", line 6, in <module>
    import ankiqt
  File "/home/marshal/anki-0.3.3/ankiqt/__init__.py", line 6, in <module>
    from PyQt4.QtCore import *
RuntimeError: the sip module supports API v3.0 to v3.2 but the PyQt4.QtCore module requires API v3.4


and that I can't get any further. Does anyone have anyidea what to try next?
Thanks

---

### Post by Hospadar on 2007-08-15
Well you could certainly try installing the packages they provide and see if they give you better success than the packages from the repositories.

You might also try running the setup.py script that is in the anki folder you extracted.  ```
python /pathtofolder/setup.py
```

---

### Post by zazen666 on 2007-08-17
Hi all,
I finally got it working. You can see how on this forum:
[http://forum.koohii.com/viewtopic.php?pid=7870#p7870](http://forum.koohii.com/viewtopic.php?pid=7870#p7870)

Also, someone made a deb, although Ihave not tried it

---

