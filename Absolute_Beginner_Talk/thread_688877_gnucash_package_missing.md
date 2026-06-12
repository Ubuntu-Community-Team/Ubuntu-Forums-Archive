---
title: "gnucash package missing"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by corkscrew on 2008-02-05
I've managed to install ubuntu alongside xp everything seems to work ok. Installed all the 185 updates again ok.
I have now tried to install gnucash from add programs again it says installed ok. But when i try to access the help from within gnucash i get an error message saying that gnucash-docs package is not installed ?
how do i get this and install it it is not listed anywhere in the add/remove list

---

### Post by Linux_Man on 2008-02-05
Try typing this into the terminal:" sudo apt-get install gnucash-docs " and see if that fixes it the reason it isn't in add/remove is because it isn't a major package nor is it a dependency (something that GNU cash needs to have to run) it wouldn't be installed by default.

---

### Post by emarkd on 2008-02-05
Often packages like that are labelled "recommended" because the software will run without them.  When you mark packages for installation in Synaptic, there's an option there to install recommended packages.

---

### Post by corkscrew on 2008-02-05
hey thanks worked 1st time

---

