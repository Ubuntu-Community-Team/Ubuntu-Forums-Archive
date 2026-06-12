---
title: "Love Ubuntu, wanna make a video."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-06-14
I've got all the Compiz eye candy working smoothly and Ubuntu looks like Windows circa 2015.  

How do I record my desktop in action?  Preferably with live sound coming from Rhythmbox (not added later).

Any ideas?

---

### Post by Crafty Kisses on 2007-06-14
You can run this command to install "RecordMyDesktop"
```
sudo apt-get install recordmydesktop
```

---

### Post by aberadam on 2007-06-14
Thanks.  

Amazing, there's a program just for it...

---

### Post by aberadam on 2007-06-14
OK, I did that and it installed.  How do I use it?

---

### Post by aberadam on 2007-06-14
It's ok, got the graphic frontend from add/remove. 

Thanks.

---

### Post by Crafty Kisses on 2007-06-14
> **aberadam said:**
> It's ok, got the graphic frontend from add/remove. 

Thanks.

I apologize for the late response, you open up terminal and type:
```
recordmydesktop
```

Then if you want to stop recording:
```
Ctrl+C
```

Hope this helps. :)

---

### Post by Crafty Kisses on 2007-06-14
> **aberadam said:**
> I've got all the Compiz eye candy working smoothly and Ubuntu looks like Windows circa 2015.  

How do I record my desktop in action?  Preferably with live sound coming from Rhythmbox (not added later).

Any ideas?

For the sound you probably want to install the package called "kmix" that's just me:
```
sudo apt-get install kmix
```

When you install kmix, you select the "Mix" option then play your audio file, then you should hear it in your video.

---

