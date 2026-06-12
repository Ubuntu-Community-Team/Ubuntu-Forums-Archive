---
title: "Installing Xine lib"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-03
What is the proper command and options to install xine-lib-1.1.7?  And is it installed before Xine-ui, or after Xine-ui?
Thanks.

---

### Post by Perfect Storm on 2008-01-03
It takes care of its own dependency - when installing via synpatic/aptitude/apt-get



```
sudo aptitude install xine-ui
```

should be sufficient.

---

### Post by jhvillegas2 on 2008-01-03
Thanks for the tip, but I got an error in the process of installation that reads:

Couldn't find any package whose name or description matched "xine-ui".

Hmm, what to do?  Any ideas, please?

John

---

### Post by taurus on 2008-01-03
Check your repos to make sure you have enable them.  Click System -> Administration -> Synaptic Package Managers -> Settings -> Repositories and put a check mark in front of all the repos (lines) except the last one, Source code and the CDROM at the bottom window.  Close it and press Refresh.  Now, just type xine in the Search field and install xine from there or from a terminal if you wish.  Don't forget to shutdown synaptic first before you install xine from a terminal.

---

