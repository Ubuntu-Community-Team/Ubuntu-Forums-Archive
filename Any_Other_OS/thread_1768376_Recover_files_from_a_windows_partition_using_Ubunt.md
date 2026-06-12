---
title: "Recover files from a windows partition using Ubuntu 10.10 Live CD"
date: 2011-05-26
forum: Any Other OS
---

### Post by thejiggler on 2011-05-26
Hi
I'm relatively new to this so please excuse me if this doesn't make sense or I use incorrect terminology.

I'm trying to retrieve files from a windows partition that suddenly died. I am using an Ubuntu 10.10 Live CD. I have managed to copy most of the files to a USB stick using the terminal. I'm having difficulties with the files that were originally "hidden" in the windows partition. When I try to copy them as sudo it says "permission denied". I have tried to change owner of these files using the "chown" command only to be told that the username I enter is invalid. I hope this makes sense. If someone knows a way to do this, that'd be great - then I can finally ditch windows forever.
Cheers

---

### Post by ppv on 2011-05-26
Can you not use file explorer Nautilus when running Ubuntu in live cd mode. In that in the left pane you should see your Windows partition, just click on it and it opens up in the right pane. From there you could copy all the files that you want. The hidden files for Windows should also most likely appear without having to change settings. You may press ctrl+h to toggle display of hidden files, but this is for Ubuntu hidden files.

---

### Post by wolfen69 on 2011-05-26
Did you try doing
```
sudo su
```
then 
```
nautilus
```
???

---

