---
title: "FireFox problem"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by MikeyRibbs on 2007-03-13
Ok, I downloaded allpeers the other day and everything was going smoothly until firefox crashed. I had mulitple tabs open at the time. It was no biggie happens all the time. I clicked to load and it wouldn't load. I tried restarting and logging out and back in. I've uninstalled and reinstalled. I tried booting from terminal and I get this. "
michael@michael-desktop:~$ firefox
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
                 AllPeers initiated successfully
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
Segmentation fault (core dumped)
michael@michael-desktop:~$ 
"
Can anyone tell me how to fix this. I am not fond of any other browser and I really need allpeers.

---

### Post by bruenig on 2007-03-13
Perhaps you should remove the all peers extension at least right now to see if firefox will start without it.

They are located in ~/.mozilla/firefox/*.default/extensions/

Tip if you don't want to wade through all of those cryptic directories to try to figure out which is which, you can generally cd into the extension directory and use find to help you along.
```
cd  ~/.mozilla/firefox/*.default/extensions/
find . -name *.jar 
```
That will generally (not on all extensions) tell you what the directory is for that extension and then just delete that directory and the extension is uninstalled.

---

### Post by MikeyRibbs on 2007-03-13
Wow! That worked perfectly, I guess I'll just try and reinstall allpeers and if that doesn't work I'll just have to figure something out. Thanks again!

---

