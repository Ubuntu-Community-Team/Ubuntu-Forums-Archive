---
title: "Can I remove Automatix Repositories from sources.list?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2006-08-30
Hi all,

I had Automatix installed but decided to remove it. Can I remove the Automatix Repositories form my sources list without screwing anything up?

They are the last three lines (I can't give you a screen-shot as I am on another comnputer right now), and look like this:

### Automatix Repositories ###
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
## created by automatixrepo3
deb [http://theli.free.fr/packages](http://theli.free.fr/packages) dapper listen

TIA for your time,

Kent

---

### Post by msak007 on 2006-08-30
Removing the repositories won't hurt your system - the sources file only tells your system where to install software from and where to get updates so it's more like a directory. Alternatively, you can comment out the lines by appending a # at the beginning of the line rather than completely remove them so that you can simply uncomment them later if you decide you want to install Automatix again. The choice is up to you, but the end result is the same and won't hurt your system. Just make sure you do a
```
sudo aptitude update
``` once you've made any changes to update the sources on your machine.

---

### Post by Carbonfish on 2006-08-30
Thanks msak007,

That's what I thought, but just wanted some reassurance.

Kent

---

