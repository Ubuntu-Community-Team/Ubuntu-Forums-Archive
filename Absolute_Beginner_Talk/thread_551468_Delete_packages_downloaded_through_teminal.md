---
title: "Delete packages downloaded through teminal"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-09-15
Hi. I have a problem installing compiz with another repo and I think that it maybe is because it's using the earlier downloaded packages for the other repo to install. So where do I find and delete these packages ?

---

### Post by shad0w_walker on 2007-09-15
Open a terminal and run this command

```
sudo apt-get clean
```

This will remove ALL the packages you downloaded to your machine (Only the package files, not the actual programs will be removed)

If you want to remove just the files you downloaded for Compiz then run this command

```
gksu nautilus /var/cache/apt/archives
```

This should open up nautilus (File browser) to the folder containing the local packages. 

All these commands will run the programs as ROOT so be careful not to just go around and delete any thing your unsure about.

---

### Post by PriceChild on 2007-09-15
If using a root nautilus like that then please close the terminal as **soon as you're finished**.

---

