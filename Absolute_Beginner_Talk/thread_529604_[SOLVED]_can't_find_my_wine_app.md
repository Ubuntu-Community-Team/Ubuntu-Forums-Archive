---
title: "[SOLVED] can't find my wine app"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-08-19
I've just successfully installed an application (dramatica) in wine; I know it was successful because on install it launched and I used it, saved my work and closed the app. However, now I come to launch the app again, to continue,  I can't seem to do so. I keep getting a 'can't find the app' error.

Using winecfg I can browse (in a pseudo Windows fashion) to the exe file, which is at 
c:\Program Files\Screenplay Systems\Dramatica Pro\Dramatica.exe
but I am unable to launch the file from a terminal. What is the correct terminal command to launch it? I've tried all the permutations I can think of, but I wonder if it's the spaces that are messing me up. The wine web site isn't very clear on this- or, isn't sufficiently clear for me at any rate.

 The other app I installed with wine put an entry in the Nautilus menu thing so for that one I just click on  Applicationa\Wine\Programs\Appname but dramatica didn't do anything quite so helpful.

---

### Post by Hobo Joe on 2007-08-19
Navigate directly to the file with Nautilus and try opening it that way.

Just incase you don't know, in Nautilus, CTRL + h will show hidden folders, and you go to .wine/drive_c and then on from there.

---

### Post by ginestre on 2007-08-19
> **Hobo Joe said:**
> Navigate directly to the file with Nautilus and try opening it that way.


Thanks- but I can find the file I just can't launch it. Trying like this gets a 
Cannot open /home/richard/.wine/drive_c/...s/Dramatica Pro/Dramatica.exe: No application suitable for automatic installation is available for handling this kind of file.
error, presumably because it isn't calling wine first

---

### Post by mysticmatrix on 2007-08-19
Open terminal and navigate to required directory by

```
cd '/home/richard/.wine/drive_c/Program Files/Dramatica Pro/'

```
Then type

```
wine Dramatica.exe
```

This should do the trick.

Alternatively you may try to right click the file and select Open with...

In the command line below, enter

```
wine
```

and click OK.

---

### Post by ginestre on 2007-08-19
Thanks, Mystic Matrix: that did the trick!

---

### Post by mysticmatrix on 2007-08-20
Anytime!!
And you can help us by marking this post solved so that other users may benefit from it.
To mark solved, click thread tools and mark as solved.

---

