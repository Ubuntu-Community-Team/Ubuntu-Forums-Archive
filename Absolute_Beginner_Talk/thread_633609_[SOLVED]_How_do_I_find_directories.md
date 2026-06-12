---
title: "[SOLVED] How do I find directories?"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Phiber_tek on 2007-12-06
I recently downloaded Flash Player from adobe and it saved to the desktop, I double clicked install and it asked if I wanted to view, run, cancel, or run in terminal; I chose run in terminal, it goes in, asks you a few questions, etc. but then it asks for your firefox directory and lists a few i search them in the search thing in the top right but find nothing, what is the 'typical' firefox directory? Any help is appreciated, thanks.

---

### Post by taurus on 2007-12-06
There's an easier way to install it.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by Phiber_tek on 2007-12-06
> **taurus said:**
> There's an easier way to install it.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

lol alright thanks, I figured out that it wasn't asking me for the directory it was telling me, but I went in to check that directory, I still cant find the .mozilla folder but that's alright, just as long as it worked.

btw, how do you know what it's called in terminal like I'm 'new' to this all but I'm getting the hang of it but I still don't get like how you know to type in 'flashplugin-nonfree' like I would just try 'flashplayer' but instead you have that longer code, how do you know what that code is?

---

### Post by taurus on 2007-12-06
If you are not sure the exact name of it, try System -> Administration -> Synaptic Package Manager -> Search.  Then, just type **flash** and it will show you the name of the program.  You can install it by putting a check mark next to it.

---

### Post by Phiber_tek on 2007-12-06
> **taurus said:**
> If you are not sure the exact name of it, try System -> Administration -> Synaptic Package Manager -> Search.  Then, just type **flash** and it will show you the name of the program.  You can install it by putting a check mark next to it.

Oh, I see awesome, thanks!

---

