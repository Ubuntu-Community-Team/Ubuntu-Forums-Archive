---
title: "Freemind file association"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Kamber on 2007-01-28
Hi.

I'm having some trouble getting ubuntu to automatically use freemind to open .mm files (since freemind saves its files in xml format with an .mm extention).

I've set freemind as the default application in Preferences->Open With, but even so, when I doubleclick a file I'm told that I can't open it because the filename indicates that it's a "troff MM input file", but the contents indicate that it's an xml file.

How do I get it to just open the file with Freemind?

---

### Post by TheWizzard on 2007-01-28
i had exactly the same problem. couldn't figure out how to get gnome recognise freemind files... in the end i switched to kde.

---

### Post by verevi on 2007-09-07
Here is how I got it to work:

Right-click on the .mm file.  Click on the "Open With" tab and choose ADD.  Then, click on use custom command and browse to the location of the freemind .sh file.  

Now, if you click on the file it will say its an executable.  If you click display, it will load the file in Freemind.

Now, make all freemind files not executable by typing:

```
chmod -R -x *.mm
```

Do this in the root directory of where you have mm files.

Hope this helps someone.

---

