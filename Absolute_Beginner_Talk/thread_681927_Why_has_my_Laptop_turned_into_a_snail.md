---
title: "Why has my Laptop turned into a snail"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Batman77 on 2008-01-29
I have had gutsy on my HP laptop for a month and it has been running like a dream,,    left my laptop on at home. when I got home from work 2day,, it is frustratingly slow all of a sudden,  

I can't understand it, what could have slowed it down so much. I haven't installed any new applications,, besides the updates ,, could it be the latest gutsy update that has made it so slow?

Tried re-starting,, to no avail.. cpu monitor shows 99% use with just firefox open

---

### Post by emarkd on 2008-01-29
Go to the terminal and run

```
top
```

to see what's going it.

---

### Post by az on 2008-01-29
Is firefox using all the cpu cycles?

Run 
top

in a terminal to see the listing of running processes sorted by CPU use.

---

### Post by Batman77 on 2008-01-29
looks like GTK-Gnash is using up most of the resources ,, trying to copy and paste the terminal output but I cant, it keeps changing.. how do I grab a snapshot of the screen?

---

### Post by emarkd on 2008-01-29
That's the free version of flash that comes installed in Ubuntu by default.  Restarting Firefox may straighten it out for you, or you may have to uninstall gnash and install the real flash.

---

### Post by Batman77 on 2008-01-29
screenshot

---

### Post by emarkd on 2008-01-29
If you already closed Firefox and those gnash threads are still there, you can kill them from the command line by running 

```
pkill gtk-gnash
```

If the problem recurrs, you may want to remove gnash

```
sudo apt-get remove --purge gnash
```

Then, when you visit a website with flash content, it'll offer to install flash for you.

---

### Post by Batman77 on 2008-01-29
Thank you solved

---

### Post by emarkd on 2008-01-29
You're welcome.  You can mark this thread solved by clicking on Thread Tools... and the top.

---

