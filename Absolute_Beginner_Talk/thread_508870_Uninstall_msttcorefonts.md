---
title: "Uninstall msttcorefonts"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Timmeh on 2007-07-24
How can I uninstall the fonts? They are not anti-aliased and still look bad in Firefox.

---

### Post by benx009 on 2007-07-24
i think the option to uninstall them should be available in synaptic (or adept if you are using kubuntu)

---

### Post by Timmeh on 2007-07-24
> **benx009 said:**
> i think the option to uninstall them should be available in synaptic (or adept if you are using kubuntu)
I searched for it in there, but it only brang up OpenOffice. o_O

---

### Post by RomeReactor on 2007-07-24
Hi. If they are still installed, try this from the terminal (Applications->Accessories->Terminal):
```
sudo apt-get remove msttcorefonts
```

---

### Post by Timmeh on 2007-07-24
> **RomeReactor said:**
> Hi. If they are still installed, try this from the terminal (Applications->Accessories->Terminal):
```
sudo apt-get remove msttcorefonts
```
It said it doesn't exist.

---

### Post by benx009 on 2007-07-24
then are you sure you installed them in the first place?  or, if so, what method did you use to install them?

---

### Post by Timmeh on 2007-07-24
I used this as a guide. [http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

---

### Post by benx009 on 2007-07-25
hmmm.... you should be seeing the option to uninstall msttcorefonts in your package manager....
maybe you misspelled the package's name:confused:

---

