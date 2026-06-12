---
title: "How can i install stuff on Ubuntu ? do i have to bow !?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Forked Tongue on 2008-01-24
Excuse me iam trying to run Youtube on my Ubuntu but unfortunately its asking me for a Flash Player ... now the issue is :(

After i go to this screen i download the file lol

[[img]http://xs223.xs.to/xs223/08045/youtubeerror836.png[/img]](http://xs.to)

but unlike Windows ... it does not Install when i double click on it :/

What am i supposed to do please

"PS: please keep in note that iam a total 100% Noob here"

Forked ....

---

### Post by emarkd on 2008-01-24
The easiest, most convenient way to install things in Ubuntu is by using Synaptic.  Click on System > Administration > Synaptic.

Next, make sure all of the repositories are enabled for you.  Click on the Settings menu and select repositories.  Click all the boxes except the source code. and hit Save.

Next, refresh the local cache by clicking the Reload toolbar button.  After it refreshes, hit Search and find flashplugin-nonfree.  Right click on it and select Mark for Installation.  Then, hit Apply at the top and wait for Ubuntu to do the rest!

---

### Post by Forked Tongue on 2008-01-24
> **emarkd said:**
> The easiest, most convenient way to install things in Ubuntu is by using Synaptic.  Click on System > Administration > Synaptic.

Next, make sure all of the repositories are enabled for you.  Click on the Settings menu and select repositories.  Click all the boxes except the source code. and hit Save.

Next, refresh the local cache by clicking the Reload toolbar button.  After it refreshes, hit Search and find flashplugin-nonfree.  Right click on it and select Mark for Installation.  Then, hit Apply at the top and wait for Ubuntu to do the rest!

Allrighty ill do that right now and see what happens :)

Much appreciated "emarkd" :D

Forked

---

### Post by RomeReactor on 2008-01-24
Hi. In Ubuntu 7.10, installing Flash is as easy as going to a site that requires it and Firefox will install it for you. However, the flashplugin-nonfree package in the repositories has a bug; download [this fixed package]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466"), close Firefox, and double click on the downloaded package to install. Then open Firefox again and see if Flash works now. More information on the bug [here]("http://ubuntuforums.org/showthread.php?t=636397").

EDIT: Posted late. See if the flashplugin-nonfree package in the repositories is now fixed; if not, download the package.

---

### Post by spiderbatdad on 2008-01-24
the instruction for that package are on the same page if you scroll down a little. For Ubuntu you would dl the tar.gz. open a terminal and, if you saved the package to your desktop,:```
cd Desktop
```note capital "D" You may have to go back to desktop and click on the package, then click extract here. Then back in the terminal cd into the file of the same name as the package and type ./flashplayer-installer. I'm shooting  from the hip here, as I did not re-read the instructions on that download page, but they are very simple. One type of package you can install by just clicking on is the .deb, that is a package that ends in .deb. Also, I believe that is newer than the synaptic package,

---

### Post by mr_ed on 2008-01-24
Check this out:  [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

If it doesn't work, open up Synaptic (System->Administration->Synaptic Package Manager) and search for flash.  If flashplugin-nonfree shows up, select it and install.

If it doesn't... make sure you have all the checkboxes checked in Settings->Repositories and try again.

---

### Post by spiderbatdad on 2008-01-24
BTW. once you install a downloaded package, you can throw it away if you like, or create a folder in which to store downloaded & installed packages. Like: open your home directory, select File>>Create Folder. Then name it. Then you can drag the package from the desktop and drop it in your folder.

---

