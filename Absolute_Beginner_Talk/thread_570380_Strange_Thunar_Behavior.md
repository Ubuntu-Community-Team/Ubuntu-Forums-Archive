---
title: "Strange Thunar Behavior"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-10-08
I'm Using Xubuntu 7.10, and yesterday Thunar started acting strangely:

When I right-click on a file or folder in the main browser interface, nothing happens. If I DOUBLE-right-click, the context menu comes up as usual. Right-clicking works normally in the sidebar. 

As an a-side, as I'm not sure if this is related. I had kubuntu-desktop installed for a couple days, out of curiosity, and I purged it around the same time this started happening. I do not have ubuntu-desktop or nautilus installed at all.

---

### Post by sunexplodes on 2007-10-08
Anything?

---

### Post by scrooge_74 on 2007-10-08
Maybe during the purge you lost something.

Check on synaptic and see if you have anything that belongs to Xfce been uninstalled

Or tell synaptic to reinstall xubuntu-desktop

---

### Post by mali2297 on 2007-10-08
Try to reset the settings. 

The configuration files for xfce and thunar are located under the hidden directory *.config*. Move them to a backup folder and restart X.

---

### Post by sunexplodes on 2007-10-09
Okay, I've reset my settings, and I've gone so far as to aptitude reinstall thunar, but nothing has changed. any other ideas, short of reinstalling xubuntu-desktop?

---

