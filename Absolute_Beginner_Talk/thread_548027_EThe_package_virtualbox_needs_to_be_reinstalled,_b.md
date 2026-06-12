---
title: "E:The package virtualbox needs to be reinstalled, but I can't find an archive for it."
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Cloey64 on 2007-09-10
I installed Virtual Box on Fiesty Fawn but I had to quit out halfway through. Now I get the error message "E:The package virtualbox needs to be reinstalled, but I can't find an archive for it." whenever I try to install it. My update manager gives me that error and so does my synaptic package manager.

---

### Post by diatribe on 2007-09-10
I dont believe it is in the repos, re-download the .deb file and reinstall

---

### Post by Cloey64 on 2007-09-10
When I click on the package to install it says I do not have permission to access it or that it is corrupted and when I try through the Terminal I get this message:

dpkg: error processing VirtualBox_1.5.0_Ubuntu_edgy.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 VirtualBox_1.5.0_Ubuntu_edgy.deb

---

### Post by bodhi.zazen on 2007-09-10
LOL

You will need to remove it, then re-install

> sudo dpkg --remove --force-remove-reinstreq virtualbox

Then re-install Virtualbox if you like.

FYI, it does not "Freeze" you need to accept the license ...

On that window, hit the <tab> key to select "OK", then hit enter ...

---

### Post by Cloey64 on 2007-09-10
Thank you sooo sooo very much. That is exactly what I needed. I noticed that the install window stopped at that screen but I couldn't figure out how to press okay. Oh thank you soo much!

---

### Post by diatribe on 2007-09-10
lol good times :D

---

