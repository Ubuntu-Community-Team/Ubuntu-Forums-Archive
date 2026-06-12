---
title: "no minimize button in titlebar"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by DSdragondude on 2008-04-03
I recently rechanged the theme on my Ubuntu Gutsy Gibbon to find out that my minimize button is missing in all windows.

I used this to change it to look like a Mac :

[http://ubuntuforums.org/showthread.php?t=602540](http://ubuntuforums.org/showthread.php?t=602540)



I started to change back because I didn't like it, and suddenly this problem occured...


[http://i40.servimg.com/u/f40/11/50/38/77/screen11.jpg](http://i40.servimg.com/u/f40/11/50/38/77/screen11.jpg)




What can I do? This is a real pain ...

---

### Post by prismpirate on 2008-04-03
In terminal, type
```

gksudo gconf-editor

```

Navigate to /apps/metacity/general/

On the right pane, look for button_layout.

The text there should be:

```

menu:minimize,maximize,close

```

If not, change it. Tell me if it doesn't work

---

### Post by DSdragondude on 2008-04-03
It was the exact text you gave me and yet it hasn't fixed the problem 


(P.S. I tried that before I posted this thread, I forgot to say...)

---

### Post by prismpirate on 2008-04-03
I have no idea then, can't seem to figure out how the minimize button might have dissapeared. Anyone else knows the answer?

---

