---
title: "How tp uninstall Kubuntu and KDE4"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by karthikophobia on 2008-02-13
Hi
I installed Kubuntu and KDE4 on my Gutsy. I hav hardly any space left on my drive so i need to uninstall them both. So plz help.

Thanq

---

### Post by HappyFeet on 2008-02-13
if you installed kubuntu and kde4 on top of gutsy gnome, make sure you are in the gnome desktop and just go to synaptic and search for kubuntu-desktop and kde4. then completely remove them.

---

### Post by karthikophobia on 2008-02-14
i tried uninstalling kubuntu-desktop but only a 455kb file got uninstalled

---

### Post by HappyFeet on 2008-02-14
uninstall any un-needed apps also.

and then do:
```
sudo apt-get autoclean
```
and
```
sudo apt-get autoremove
```

---

