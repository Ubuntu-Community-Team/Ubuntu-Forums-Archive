---
title: "How to install Window applications"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by faust3x on 2008-01-16
I installed wine through the terminal, now I wanna install IMVU from imvu.com

a friend told me with wine installed I could install window applications easy.

---

### Post by kestrel1 on 2008-01-16
You only need to double click on the EXE as you would in Windows.

---

### Post by eolson on 2008-01-16
I think your friend may have been a little overly optimistic.   Somethings work under Wine and others don't.

---

### Post by kestrel1 on 2008-01-16
Yes, unfortunatly not everything will work. It is worth trying though.

---

### Post by faust3x on 2008-01-16
it says cannot open the file No Application suitable for automatic installation is available for handling this kind of file.

Is there something I am missing?

---

### Post by FuturePilot on 2008-01-16
Did you run 
```
winecfg
```
yet?
You need to run that once so that Wine gets configured

---

### Post by faust3x on 2008-01-16
how do I configure the wine so it will run window applications?

---

### Post by FuturePilot on 2008-01-16
> **faust3x said:**
> how do I configure the wine so it will run window applications?

Run the command I posted above. You shouldn't have to change any of the settings in that configuration panel. You just need to run it so it will create your .wine directory which is where all your Windows apps will be installed to.

---

### Post by faust3x on 2008-01-16
I did, but when I save the application to the desktop the IMVU still won't open, how do I get it to open?

---

### Post by FuturePilot on 2008-01-16
> **faust3x said:**
> I did, but when I save the application to the desktop the IMVU still won't open, how do I get it to open?

If you right click on it you should get an option to open it with Wine. If not right click on it and to to Properties. Go to the Open With tab and click Add. At the bottom there should be one for Wine. Select that and make it default by clicking the bubble next to it.

---

### Post by faust3x on 2008-01-16
wine isn't on the list :(

---

### Post by FuturePilot on 2008-01-16
Hmmm. Try using the Custom Command thing at the bottom and type in 
```
wine
```

---

### Post by faust3x on 2008-01-16
the program works, but it's super slow and it doesn't even look right....

It keeps crashing

---

### Post by FuturePilot on 2008-01-16
That's one of the things with Wine. Not everything will work correctly or even work at all. It's very hit or miss with Wine.

---

### Post by faust3x on 2008-01-16
is there anything that would make it run right?

---

