---
title: "[SOLVED] the upper bars in my windos desappear"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by shayvasa on 2008-02-20
i installed compiz fusion and in the howto it said to when i finish put in the terminal compiz -replace and when i did that the bars that has the x to close the windows and to minimize etc. has desappeared form all my windows...what can i do??

---

### Post by jan quark on 2008-02-20
install this application:

```
sudo apt-get install compizconfig-settings-manager
```

and try to enable the window decoration through it

once installed this app can be found in 

system > preferences

---

### Post by shayvasa on 2008-02-20
i cant find the window decoration option

---

### Post by glennric on 2008-02-20
> **shayvasa said:**
> i cant find the window decoration option

Go to System->Preferences->Appearance and look under the Visual Effects tab.

---

### Post by mivo on 2008-02-20
Which Ubuntu version are you using? You said you installed Compiz-Fusion, but in 7.10/Gutsy it's already pre-installed and you only need to turn it on in System->Preferences->Appearance, as Glennric said. Just checking here in case something got messed up and you somehow manually installed Compiz-Fusion by following a How-To for an older version.

---

### Post by shayvasa on 2008-02-20
i have 7.10 all i did was installing the compiz manager (ccsm) but then it sayed to do compiz -replace and then everything got messed up

---

### Post by spiderbatdad on 2008-02-20
You should have emerald theme manager under your system preferences. Select or import and select an emerald theme. I believe compiz setttings manager also allows you to select a windows theme manger...chose emerald. You may want to look into compiztray-icon. It makes it easy to manage compiz settings.[http://forum.compiz-fusion.org/showthread.php?t=3988](http://forum.compiz-fusion.org/showthread.php?t=3988)

---

### Post by shayvasa on 2008-02-20
spider can u explain better plz? i tried downloading a emerald theme and it didnt work.

---

### Post by spiderbatdad on 2008-02-20
From the emerald themes manager, go to the repos tab and fetch a theme...then back to the themes tab to select a theme. This seems redundant. Compiz should have windows management. You may need to enable the windows decorator in the compizconfig-settings-manager...called Advanced Desktop Effect Settings under system preferences. I stopped using compiz, so I can't be a lot of help. I only wanted to suggest the compiztray-icon, as I liked it when I did use compiz.

---

### Post by Funky91 on 2008-02-20
you may need to install emerald theme manager. It was not already installed on my standerd 7.10 instalation. It is easy to do tho you should be able to find it through synaptic.

---

### Post by mivo on 2008-02-20
Hold on with installing more things for the moment. :) If you haven't already, it may be a good time to reboot your system. Actually, restarting X should suffice: Just press ctrl+alt+backspace, or log out and back in. Does this fix the window bar problems?

In the Compiz settings manager, also make sure you have the relevant options turned on (under Windows Management -- particularly Extra WM Actions, Move Window, Place Windows).

---

### Post by spiderbatdad on 2008-02-20
ok go to the emerald theme manager repositories tab and hit the fetch gpl'd themes. Then go to the edit themes tab. You'll only see one, but there is a drop down arrow to reveal the others.

---

### Post by shayvasa on 2008-02-20
lol i did ctrl alt backspace and it worked...thanx :D

---

### Post by mivo on 2008-02-20
I'm glad. :) It's a very Windows-like method of fixing problems, and I cringe every time, but sometimes it actually does resolve troubles!

---

