---
title: "[SOLVED] Flashplayer"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2007-12-15
It installed fine before, but today I reinstalled ubuntu and couldn't install it.

So I tried:
sudo apt-get install flashplayer-nonfree

and it mentions something about md5 checksum error

Should I just download flashplayer directly from adobe?

---

### Post by autocrosser on 2007-12-15
Try using Add/Remove & look for "Ubuntu-restricted-extras"--you will be asked to enable the extra repositories--you get MS fonts, mp3 codecs & much more---includes Flash-Player.....

That should get you past the problem---D/L & install is not recommended due to possible problems during a upgrade.

---

### Post by ubutufan on 2007-12-15
Try Applications>Add/Remove and in the search field type  "flash" (without quotations)

Mark adobe's file on the right pane for installation and that's it.

MD5 checksum is a method using algorithms to check if the file downloaded is correct or corrupted

---

### Post by piratesmack on 2007-12-15
hmm neither are working

---

### Post by RomeReactor on 2007-12-15
Hi. There's an error in the flashplugin-nonfree package. The fix should come soon as an update, but meanwhile you can either use Gnash, or see [this thread]("http://ubuntuforums.org/showthread.php?t=636397") to install a fixed flashplugin package.

---

### Post by autocrosser on 2007-12-15
OK-Menu>System>Administration>Synaptic & first goto Settings>Repositories. Make sure that you have  under Ubuntu Software all the boxes checked---after that close the box---next, search for Ubuntu-restricted-extras & check it to install.

Thanks RomeReactor--I was typing my post when yours came in--

---

### Post by piratesmack on 2007-12-15
nvm I figured it out

I went to the System>Preferences>software sources, clicked the "Updates" tab, and checked "Pre-released updates"

Then I opened the synaptic package manager and searched "flashplugin-nonfree," then installed it and  it worked

Thanks for all your help

---

### Post by piratesmack on 2007-12-15
Is it safe to just install all these prereleased updates?
Are they usually buggy?

---

### Post by RomeReactor on 2007-12-15
Well, I really can't say, but I imagine they still have to be inspected for inclusion in the regular repositories, so they *could* be buggy. I suggest you just grab the flashplugin package, install it, disable the "Proposed" repository and then run an update.

---

### Post by piratesmack on 2007-12-15
Yeah I probably should
thanks

---

