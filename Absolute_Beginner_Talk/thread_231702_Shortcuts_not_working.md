---
title: "Shortcuts not working"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by GuitarHero on 2006-08-07
I use alacart to make shortcuts for programs that dont make them themselves for some reason but its not working.  I link them to the same file I normally double click to start the program but it does not work.

---

### Post by Anduu on 2006-08-07
I have had this happen sometimes as well.

Be aware that any app that is being launched using sudo needs to have the run in terminal box checked.

If all else fails here is a little something I do when this happens....create a script to launch your app and then link the Alacart entry to it.

---

### Post by GuitarHero on 2006-08-09
I've tried run in terminal.  How do I make the script, as in what do I save it as from gedit, extension wise.

---

### Post by Anduu on 2006-08-09
Just create a new file and name it whatever you like(ie myscript)...it does not need an extension as Linux recognizes it as a script by it's formatting.

Open it with gedit and make it look like so...

```
#!/bin/bash
/path/to/excecutable
```

Right click it and make its permissions executable.

Now put it whereever you like....I made a myscripts folder in my home folder.

Then link your menu entry to the script.

---

### Post by Anduu on 2006-08-09
Another thought...What version of Alacarte are you using?

---

### Post by GuitarHero on 2006-08-10
Whatever comes with Dapper, the script method works.  But its not seeing my icon for the program.  Theres a .png and a .xpm
I tried putting them in /usr/shae/pixmaps/

---

### Post by Anduu on 2006-08-10
Yeah the version from the repos is 0,8...try 0.9.A lot less buggy ;)

Here is a link [http://members.shaw.ca/anduu/ubuntufiles/alacarte_0.9-0ubuntu1~amaranth_all.deb](http://members.shaw.ca/anduu/ubuntufiles/alacarte_0.9-0ubuntu1~amaranth_all.deb)

Glad to hear the script works for you.

---

