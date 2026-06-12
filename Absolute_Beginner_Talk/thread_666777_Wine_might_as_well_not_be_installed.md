---
title: "Wine might as well not be installed"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by thedrizz on 2008-01-13
Darnit i hate wine

So everything i put in wine gives me basically the same thing. I reinstalled the damn thing.

Any command gives me something similar

And i apparantly cant post it because it counts as an image

i tried reinstalling, but the bloody thing is useless. Anything i try to do in wine under applications does not respond.

Anyone wanna help?

---

### Post by JoshuaRL on 2008-01-13
Did you configure it?  WINE runs as a compatibility layer, but it still needs you to set up the virtual side of the layer so it will run correctly.  Just go into Applications->WINE->Configure WINE.  And what programs are you trying to run?  They might not have support for them yet.

---

### Post by nikoPSK on 2008-01-13
what thing does it give you? 

Regards,
nikoPSK

---

### Post by thedrizz on 2008-01-13
yes, but as i mentioned the wine things under applications dont respond

I click on configure wine and nothing happens

---

### Post by nikoPSK on 2008-01-13
Is compiz disabled? That usually helps from my experience. :)

~/nikoPSK

---

### Post by thelatinist on 2008-01-13
Why did you post two threads on the same subject? This is not a place to vent, it's a place to get help with your problems.  The other thread at least has the error message.

---

### Post by thedrizz on 2008-01-13
Turning compiz off did nothing

I got frustrated and tried deleting it, but i dont know the command with sudo to erase it from the trash.

Reinstalled, nothing

---

### Post by thedrizz on 2008-01-13
> **thelatinist said:**
> Why did you post two threads on the same subject? This is not a place to vent, it's a place to get help with your problems.  The other thread at least has the error message.

er whoops, didnt see

---

### Post by JoshuaRL on 2008-01-13
```

sudo apt-get remove wine

```

I think, but I haven't done much with WINE from the terminal.

---

### Post by nikoPSK on 2008-01-13
> **JoshuaRL said:**
> ```

sudo apt-get remove wine

```I think, but I haven't done much with WINE from the terminal.

that uninstalls wine, does he want that? :confused:

---

### Post by JoshuaRL on 2008-01-13
> **thedrizz said:**
> Turning compiz off did nothing

I got frustrated and tried deleting it, but i dont know the command with sudo to erase it from the trash.

Reinstalled, nothing

I believe so.  Maybe?  If it doesn't work from the menu maybe a fresh install from their site is in order.

---

### Post by Xavieran on 2008-01-13
To try to run a .exe file from wine in the terminal just do ```
wine /path/to/your.exe
```
Sometimes the menu items for wine apps will not be responsive because:
A.You don't have enough RAM and proc power to run the wine binary layer (it is *very* hardware intensive to emulate an Operating System.
B.The apps may not have been installed correctly in the Wine folder...go to /home/your-username/.wine to see if they have been...
C.Sometimes apps just don't work under wine..:(

And yes to uninstall it would be sudo apt-get remove wine...

---

### Post by Sef on 2008-01-13
Locked. [Double Posting]("http://ubuntuforums.org/showthread.php?t=666778").

---

