---
title: "Getting settings from older installation"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-04-03
Hi, I just re-installed Ubuntu to give it more space, and my previous installation is still there. I have backed up all of my personal files, but I was wondering if there was a way to retrieve my settings (such as GAIM profiles, Firefox bookmarks, and Evolution mail settings) from the other installation before I delete it. Any help would be greatly appreciated. Thanks!!

---

### Post by zvacet on 2007-04-03
Open your home folder>view>show hidden folders

---

### Post by brennydoogles on 2007-04-03
> **zvacet said:**
> Open your home folder>view>show hidden folders

What all would I need to copy?? Alot of my settings point to places that don't exist in this installation, and also there is information for programs that are not yet installed (many which will not be installed anytime soon). Thanks for the info!!

---

### Post by hyper_ch on 2007-04-03
hmmm, did you setup your ubuntu with /home as a seperate partition?

---

### Post by brennydoogles on 2007-04-03
> **hyper_ch said:**
> hmmm, did you setup your ubuntu with /home as a seperate partition?

Yes I did. Upon further inspection of my old home partition, i have been able to rescue most of the settings I need, I am only lacking my Evolution mail settings now.

---

### Post by Feba on 2007-04-03
I beleive firefox has an export bookmarks feature, although that's not what you want I suppose.

---

### Post by brennydoogles on 2007-04-03
> **Feba said:**
> I beleive firefox has an export bookmarks feature, although that's not what you want I suppose.

I was able to copy the bookmarks.html file from the previous install's /home/.firefox folder. It seems that I have ecerything I need now except Evolution.

---

### Post by kerry_s on 2007-04-03
copy the whole folder if you want exact same setup.

Example copy:
.firefox
.gaim
etc....

I always replace the new what_ever folder with my old one.

Example for firefox:

Delete the .firefox folder on the new install and put the .firefox folder from the old install.  You'll have your entire firefox just like the old one. Same with gaim and others.

---

