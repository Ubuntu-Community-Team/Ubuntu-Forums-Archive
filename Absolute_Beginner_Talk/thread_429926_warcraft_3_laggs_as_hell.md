---
title: "warcraft 3 laggs as hell"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by the_axiom on 2007-05-01
Hi, I've just installed wc3 and the expation + eurobattle in wine.
And it runs, but not smoothly at all. It's unplayable.
And the cause is probably not my hardware (dual core e6300 & 2gv pc6400)

Anyone got any idea how to fix this?

---

### Post by mejy on 2007-05-01
Can you post the version of wine and graphics card you're using please.

---

### Post by the_axiom on 2007-05-01
I have ati x1950xt.
I don't not where to check the wine version, but I assume the latest one since it wasn't a long time ago I installed it (1 week ago).

---

### Post by mejy on 2007-05-01
If you refreshed you'd see I've posted, and the fact that you're title is rude, uses incorrect grammar and isn't capitalised probably didn't help.
Edit:  In response to your updated post...
Type wine --version in the terminal to find your wine verrsion.
Have you installed the binary ATI drivers?
What does 'glxinfo | grep direct ' give?

---

### Post by the_axiom on 2007-05-01
Yes I saw, and re-edited the post.
Sorry if I dont live in America.

---

### Post by mejy on 2007-05-01
Check my revised post above ^^.  Things always seem to end up like this with retrospective editing...

---

### Post by the_axiom on 2007-05-01
I have 0.9.33-0ubuntu1 (wine).

Here's the result of typing your code:
> ~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

I do not know if I have binary ATI drivers, but I do think so since I got beryl up and running smoothly.

---

### Post by mejy on 2007-05-01
And there's your problem - if you're running beryl (therefore under XGL) with ATI's awfull Linux drivers you won't get 3D acceleration.  If you've used an up to date method to install XGL, you should be able to chose GNOME without XGL at the login screen.  Post a link to the tutorial you followed and I should be able to figure out what you need to do if this isn't enough info.  The only real solution is to get an nVidia card ;p, since they actually work on their linux drivers.

---

### Post by the_axiom on 2007-05-01
I could choose between "GNOME" and "GNOME with XGL" so I assume that "GNOME" is "GNOME without XGL".
 And I tried to start it that way, but sadly enough wc3 woudn't even start :(

---

### Post by mejy on 2007-05-01
type 'cat ' in the terminal, don't press enter, drag the shortcut into the terminal, then type ' | grep Exec'.  Run the command that gives and post the output.  Gnome without XGL is what you'll need to run it.

---

### Post by the_axiom on 2007-05-02
Exec=env WINEPREFIX="/home/usr/.wine" wine "C:\\Program Files\\Warcraft III\\w3l.exe"

---

### Post by the_axiom on 2007-05-02
bump

---

### Post by mejy on 2007-05-02
Run 'wine "C:\\Program Files\\Warcraft III\\w3l.exe"' from the terminal and post the output.  Then try running the whole output you received and see if they differ.  Post what you get back here.

---

### Post by the_axiom on 2007-05-03
I tried '**wine "C:\\Program Files\\Warcraft III\\w3l.exe"**' and '**Exec=env WINEPREFIX="/home/usr/.wine" wine "C:\\Program Files\\Warcraft III\\w3l.exe"**'.
Noone of them worked. The first code gives me an error: "Could not start War3.exe! Make sure the loader is in same dir"

---

### Post by mejy on 2007-05-03
> **the_axiom said:**
> I tried '**wine "C:\\Program Files\\Warcraft III\\w3l.exe"**' and '**Exec=env WINEPREFIX="/home/usr/.wine" wine "C:\\Program Files\\Warcraft III\\w3l.exe"**'.
Noone of them worked. The first code gives me an error: "Could not start War3.exe! Make sure the loader is in same dir"

OK... try running 'cd "~/.wine/drive_c/Program Files/Warcraft III/" && wine w3l.exe'.
Edit:  Also try 'env WINEPREFIX="/home/usr/.wine" wine "C:\\Program Files\\Warcraft III\\w3l.exe"'.  All without the outside quotation marks.

---

### Post by the_axiom on 2007-05-03
cd "~/.wine/drive_c/Program Files/Warcraft III/" && wine w3l.exe
> No such catalog (translated)
env WINEPREFIX="/home/usr/.wine" wine "C:\\Program Files\\Warcraft III\\w3l.exe"
> wine: the '/home/usr/.wine' directory specified in WINEPREFIX doesn't exist.
You may want to create it by running 'wineprefixcreate'.


---

### Post by mejy on 2007-05-03
That looks like the error, you may have more luck posting it at [http://appdb.winehq.org/appview.php?iVersionId=6482](http://appdb.winehq.org/appview.php?iVersionId=6482) .

---

