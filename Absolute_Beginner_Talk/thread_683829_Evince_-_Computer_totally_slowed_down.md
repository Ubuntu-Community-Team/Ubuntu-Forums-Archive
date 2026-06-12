---
title: "Evince - Computer totally slowed down"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2008-01-31
Ok here is the deal. I am reading a book with evince. Now the bloody thing eats 95 MB of my operating memory and for some strange reason my computer behaves as if it were not 95 but 950 MB. I have 1 GB of memory an intel core duo processor (1.83 GHz) and 256 MB ATI x1400. What is going on with this application and would you suggest an alternative which requires less resources (or better yet how can I fix my current one?)

---

### Post by RomeReactor on 2008-01-31
Hi. Try running Evince from the terminal, see if it starts behaving the same way and post any output. As for other PDF readers, try XPDF or EpdfView; they're both available through Add/Remove/Synaptic. Or to install from the terminal:
```
sudo aptitude install xpdf
```
or:
```
sudo aptitude install epdfview
```

---

### Post by KOTAPAKA on 2008-01-31
Well I do not really know how to run it in the terminal. Please tell me where the terminal is located so I can browse and select it as the open-with application. Here is some more info - when I run evince with no file opened just the program it takes up to 3.8MB but if I open my book it goes to 95MB

---

### Post by sleepingdragon on 2008-01-31
I've had exactly the same problem. Evince slowed my computer down severely, even to the extent that the clock on the taskbar was jumpy, and I haven't seen it do that with complex 3D stuff on-screen. 

I'm not sure what is going on with Evince, I can't even get the computer to bring up a console so I can see my memory usage. For now, I've switched to xpdf and everything is fine again.

---

### Post by RomeReactor on 2008-01-31
> **KOTAPAKA said:**
> Well I do not really know how to run it in the terminal. Please tell me where the terminal is located so I can browse and select it as the open-with application. Here is some more info - when I run evince with no file opened just the program it takes up to 3.8MB but if I open my book it goes to 95MB

Sorry about that; the terminal is located in 'Applications->Accessories->Terminal'. Once you open it, write or paste:
```
evince
```
and press ENTER. Then open the book you were reading, and if any error messages are left in the terminal, please post them.

Just as a note, when I open a 213 page book book in evince, the memory usage is around 170 MB. So memory consumption *is* an issue with evince. However, my computer also has 1 GB of memory, and remains perfectly usable. So the problem might be either something to do with that particular book, or something related to evince in your system. Does this happen with other documents you open in Evince?

---

