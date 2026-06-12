---
title: "Uninstalling Windows Apps"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by gabz8472 on 2007-08-10
I installed a couple of windows apps i thought might be useful for my clients, turns out they weren't. one has an uninstall command, the other doesn't. how do I remove them?

It would be so helpfull to learn this. thanks.

---

### Post by skymera on 2007-08-10
how did you install them?
wine?
crossover?

---

### Post by ukripper on 2007-08-10
If you are using Ubuntu then just go to terminal and type following command:

```
sudo apt-get remove APPNAME
```

just replace APPNAME with your app you want to remove.

If it is Windows OS then just click uninstall

---

### Post by skymera on 2007-08-10
he asaid windows apps.

so hes obviously using Wine of some sort..

---

### Post by ukripper on 2007-08-10
> **skymera said:**
> he asaid windows apps.

so hes obviously using Wine of some sort..

Windows could be X window - ( [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System) )and it is not obvious by his post what app he wants to remove and for which OS?

If it is wine then follow this link.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by El Lance-O on 2007-08-10
Well...it actually doesn't even sound like he used WINE, but more that he just tried to run a Windoze installer without WINE at all.

If that's the case, nothing happened and you can just delete the installer and whatever else you downloaded.

Oh and if you do want to run Windoze programs, then go to the link provided in the post above mine, and then once you have that installed and running, go [here]("http://appdb.winehq.org/") to get specific programs running.

---

### Post by gabz8472 on 2007-08-16
sorry, i guess i did forget to mention that i installed the apps using wine.

---

### Post by diatribe on 2007-08-16
/home/your_name/.wine is where the virtual windows dirve is stored, navigate there and remove them that way

---

### Post by gabz8472 on 2007-08-16
thanks. i got it done. you guys are a real gem, you know.

---

### Post by bogolisk on 2007-08-16
> **diatribe said:**
> /home/your_name/.wine is where the virtual windows dirve is stored, navigate there and remove them that way

Hmmmmmmmmmmm, I believe the prefered way to uninstall wine's windoze apps is:
```

uninstaller

```

it will show a list of windoze apps under wine. Select what you want to uninstall.

---

### Post by ukripper on 2007-08-17
Quoted from the guide link posted above - 

*[COLOR="Blue"]"Open up a terminal window and type "[COLOR="Red"]uninstaller[/COLOR]" - this will open up a program similar to Windows' "add/remove programs" control panel, allowing you to uninstall applications from a Wine installation. Running uninstall programs directly via Wine should also work normally. Alternatively, you could also simply delete the folder of the application. However, as when done in Windows, this method will be "unclean" and will not remove the program's configuration from the Wine registry like using an uninstaller will."[/COLOR]*

---

