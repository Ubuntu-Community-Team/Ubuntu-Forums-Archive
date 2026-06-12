---
title: "[SOLVED] oops lost my taskbar thingy"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by nothingspecial on 2008-02-20
The great thing about ubuntu is that you can mess with it to your heart`s content. Unfortunately when you`re a complete novice like me you can mess it up with no idea how to fix it.
 I ran sudo apt-get install kubuntu desktop but it didn`t work properly, I didn`t get an option to boot into kde. No major problem, I like gnome so I sudo apt-get removed it. In the process, however, I lost my taskbar ie the one that has a little box to click on to restore your window when you minimize it. 
 Also the other taskbar with applications, places etc on it is all messed up, everything is in the wrong place. And when I restart it says I`m loading Kubuntu even though I`ve removed it (thats no problem, it`s just wrong).
 Can anyone help me fix this? I`ve lost my deleted items folder button and I have to restart everything I minimize which is annoying. 
  I won`t be looking at this thread for a few hours as, after spending alot of time trying to fix it, I have to sleep, but please try to help.
Thankyou in advance.:):KS

---

### Post by TuxImpersonator on 2008-02-20
I can't really help with the removing kubuntu properly but if you right click on your top task bar and choose "New Panel" then right click the new bottom panel and choose "Add to Panel" then click and drag "Window list" (in the second section) into your bottom task bar you'll get your window list back. (I can tell you this method works as I had to use it this morning!)

As for your top bar do you mean they're in the wrong order or there's something missing?

---

### Post by AMegapode on 2008-02-20
This should enable you to get the "Ubuntu" splash screen back.

```

sudo update-alternatives --config usplash-artwork.so
sudo update-initramfs -u

```

---

### Post by nothingspecial on 2008-02-20
Thats fixed it.

---

