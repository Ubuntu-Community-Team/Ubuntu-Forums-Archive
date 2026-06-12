---
title: "How to install Xubuntu deleting existing Ubuntu ?"
date: 2008-03-17
forum: Apple PPC Users
---

### Post by spystyle on 2008-03-17
Hello from Maine,

I have installed Ubuntu onto a G3 slot loading Mac. I decided to try Xubuntu instead, so I boot the Xubuntu live CD, click "install" then tell the partitioner to "Guided - use entire disk". But I get an error as if it doesn't want to overwrite the existing Ubuntu installation : 

"The ext3 file system creation in partition #3 of IDE1 master (hda) failed"

Please advise :)

Thank you,
Craig

---

### Post by driven1 on 2008-03-17
If you already have ubuntu desktop installed, there is no need to reinstall everything for xubuntu

```
sudo aptitude install xubuntu-desktop
```

this will install xubuntu without wiping everything out i.e. additional apps codecs and the like...

once you have xubuntu installed, at login, simply click on options and choose xfce as your session. You can even make it the default. This way you can try it without total disruption. Then, if you decide you want to stay with xubuntu, simply remove ubuntu-desktop leaving only the xub... 

```
sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove
```

---

### Post by spystyle on 2008-03-17
Thank you :)

I will try that now :)

---

### Post by spystyle on 2008-03-17
Oh h3ll

I don't know where to type those commands, I tried typing them in a terminal and it didn't work...

EDIT

OK, I tried logging into terminal instead of desktop and it seems to be working :)

---

### Post by spystyle on 2008-03-17
Hey it worked a treat :)

Thank you for the support, you are obviously a super guru :)

Within a matter of minutes I was running Xubuntu instead of Ubuntu, this type of flexibility really leaves me with a positive impression of Linux :)

I am becoming a Linux believer :)

Cheers,
Craig

---

