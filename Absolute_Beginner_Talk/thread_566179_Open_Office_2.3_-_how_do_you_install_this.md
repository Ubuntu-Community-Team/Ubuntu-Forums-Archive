---
title: "Open Office 2.3 - how do you install this?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-03
There is a new Open Office 2.3 at [www.OpenOffice.org](www.OpenOffice.org).  It looked like the closest distribution was the "debian" version.  I downloaded it and extracted the files.  There were a large number of *.deb files.  How do you install this into Ubuntu Feisty Fawn?

Thanks

Carl

---

### Post by philinux on 2007-10-03
To save you any hassle wait till 18th Oct.

Upgrade to gutsy and voila 2.3 available in repo

---

### Post by cwmoser on 2007-10-03
Are Ubuntu releases generally problem free installations?  Or should we wait a few weeks for the problems to be identified and solved?

Thanks

Carl

---

### Post by por100pre1 on 2007-10-03
Can you list the *.deb files here? By the way, in my humble opinion, you should stick with the version from the repositories. In OOo usage stability is paramount.

---

### Post by philinux on 2007-10-03
From what I've read, do a google search for gutsy gibbon, it's the best yet.

---

### Post by Martje_001 on 2007-10-03
Upgrade to Gutsy:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-manager -d (or if it's official out: sudo update-manager --dist-upgrade)
```

---

### Post by Paul820 on 2007-10-03
> **Martje_001 said:**
> Upgrade to Gutsy:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-manager -d (or if it's official out: sudo update-manager --dist-upgrade)
```

Before you do that you had better back up your sytem, it might break it.

---

### Post by stchman on 2007-10-03
> **cwmoser said:**
> There is a new Open Office 2.3 at [www.OpenOffice.org](www.OpenOffice.org).  It looked like the closest distribution was the "debian" version.  I downloaded it and extracted the files.  There were a large number of *.deb files.  How do you install this into Ubuntu Feisty Fawn?

Thanks

Carl

To install .deb files cd to the folder that contains all the .deb files ant type th following:

```
sudo dpkg -i *.deb
```

There might be a debian menus in another folder, install that as well.

---

### Post by Kynan on 2007-10-09
Thanks man, i'm using mint so it will be a while till i can get new openoffice so this helps :)

---

