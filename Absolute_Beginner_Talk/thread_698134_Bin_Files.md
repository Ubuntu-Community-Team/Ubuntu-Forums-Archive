---
title: "Bin Files"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Ronnie on 2008-02-15
Hi all I just downloaded Google Earth. It downloaded to my desktop as a bin file.
How do I get it to install? I found some suggestions in this forum but have been unable to get it to to install. I have not been able to figure out how to navigate to my desktop in terminal. Any help would be greatly appreciated. I am running version 7.10 on a P4 2.53 with 896 megs memory on an Asus P4PE motherboard.

---

### Post by jfenwick on 2008-02-15
To navigate to desktop:

cd ~/Desktop

---

### Post by jfenwick on 2008-02-15
Then to install Google Earth try this:

```
chmod +x  G*.bin
./GoogleEarthLinx.bin
```

---

### Post by emarkd on 2008-02-15
It's in the Medibuntu repository, if you'd rather use the package manager to handle this.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by Ronnie on 2008-02-15
Excellent! thank you I got to the desktop and run chmod a+x GoogleEarthLinux.bin but nothing happened. I got that command from a Linux help site somewhere on the web but don't remember where. Is it right or wrong?

---

### Post by emarkd on 2008-02-15
Your command flagged the file as executable.  It won't really seem to do anything, but now you can run it using

```
./GoogleEarthLinux.bin
```

NOTE:  You're just typing the filename here, but you have to tell Linux which directory it's in before it'll run.  That's what the ./ part is about

---

### Post by Ronnie on 2008-02-15
Thank You! Jfenwick I got it installed when I saw your second post works just fine. I always seem to find the help I need here I hope someday i will be able to contribute something back.

---

### Post by Ronnie on 2008-02-15
Thanks very much for your help and explanition.
Is there a way to create a shortcut to click to start Google Earth or do I always have to open terminal and type the name?

---

### Post by Ronnie on 2008-02-15
Sorry for the stupid question the installer placed an icon on the desktop to start it from.

---

