---
title: "Removing Wine"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-08-07
Okay, so I installed Wine, and it was working good for a while, but now Wine wont work, not only that but the whole machine is having oddities. How do I remove Wine and EVERYTHING that has to do with Wine.

---

### Post by Ek0nomik on 2007-08-07
```
sudo apt-get remove wine
```

```
cd ~/
rm -r .wine
```

This will uninstall the wine software, and remove any files in the .wine folder, where programs you installed via wine are stored.

You may want to remove some menu entries too, which can be done by going to Preferences/Main Menu

---

### Post by Cheese Roller on 2007-08-07
Didn't work. Wine is still in the Applications Menu.

---

### Post by Bofur on 2007-08-07
You can delete it by going into edit menu, find the icons, right click and delete.

---

### Post by stchman on 2007-08-07
> **Cheese Roller said:**
> Okay, so I installed Wine, and it was working good for a while, but now Wine wont work, not only that but the whole machine is having oddities. How do I remove Wine and EVERYTHING that has to do with Wine.

If you installed wine via apt-get use the following:

```

sudo apt-get autoremove wine

```

This will remove dependencies as well.

---

### Post by Cheese Roller on 2007-08-09
Okay, Wine programs are still there.

I have typed in every code given to me so far.

Is there a way to seriously remove all of it or what?

---

