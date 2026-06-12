---
title: "Firefox from terminal"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-12
Okay - everyone knew this except me :) 
In Windows I would go directly to a website by using the Run menu and typing the URL - eg  [www.google.com](www.google.com)
With Linux (newbe here) I have been opening the browser - then changing the default url - a two step process.
The penny just dropped and I realized if I just go to the terminal and type 
[COLOR="Blue"]**firefox [www.google.com](www.google.com)**[/COLOR] - it loads the site right away.
Thought I'd pass on this shortcut for new users like myself.

---

### Post by aysiu on 2006-04-12
I didn't even know that could be done in Windows. Nice tricks.

---

### Post by kabus on 2006-04-12
If you put this function in your ~/.bashrc you can search straight from the command line with "google *searchterm*" :
```
google () {
firefox "http://www.google.com/search?q=$*"
}
```

---

### Post by pbaehr on 2006-04-12
That's a sweet little tip, kabus.

Just added that to my .bashrc.

Never would've thought of doing something like that unless you mentioned it.

Thanks!

---

### Post by mrchrisblau on 2006-04-12
That bashrc thing sounds cool. How do I get to it? What file do I edit?

---

### Post by 5-HT on 2006-04-12
[quote=mrchrisblau]That bashrc thing sounds cool. How do I get to it? What file do I edit?[/quote] 
It's a hidden file in your home directory (~/.bashrc).

You can see it if you enable hidden files to be shown in your file browser, or by just doing an 'ls -a' from the directory in a terminal.

To edit the file, just open it up with your favorite editor. 
A limited set of examples would be :
```
vi ~/.bashrc

OR

nano -w ~/.bashrc 

OR

gedit ~/.bashrc 
``` 

It's best to save a copy of the original prior to messing around with it, though there should be a default version in /etc/skel.

HTH

---

### Post by cliff0108 on 2006-04-12
I love it - google 'searchterm' from the terminal.
Works wonderfully !

---

