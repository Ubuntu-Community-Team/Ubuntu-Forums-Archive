---
title: "help with installing a new theme"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2006-11-07
I downloaded a new theme from gnome-look.org and followed the instructions in the readme file, however it does not tell me what to do once you make install.  I'm sorry, I am fairly new to ubuntu and still get confused when trying new things out.  Does anyone know what I should do from here?

---

### Post by autocrosser on 2006-11-07
Well--if it's just a metacity theme (for Gnome), you just goto Menu>System>Preferences>Theme and tic the tab <Install Theme> This will open a file directory that you can nav to your new theme--then install--You do not need to do a make-sudo make install with most themes--The theme manager will do it for you.

---

### Post by jordanmthomas on 2006-11-07
If you're having to make it, then it is not a theme, but a theme engine.
That said, you'll need to find a theme for that particular engine.
For example, there is the Murrine engine with themes called Murrinaxxxx, which you can just drop onto the theme manager

---

### Post by familyjules74123 on 2006-11-07
Well, I tried that and it told me I had to compile the theme.  So I did the make install commands.  Again, I am new to ubuntu and I could have just been doing something that wasn't even necessary.

---

### Post by jordanmthomas on 2006-11-07
Which theme are you trying to install, exactly?

---

### Post by familyjules74123 on 2006-11-07
You were right, it was a theme engine, are there guides on what to do for theme engines, or is it simple and easy to figure out?

---

### Post by jordanmthomas on 2006-11-07
Chances are, there will be a link to a .deb that is already compiled for Ubuntu.

Compiling GTK engines really isn't that difficult, but you will need the gtk-dev, build-essential (something similar to that, at least) and maybe some more packages to compile.  

Compiling is simple, but not so easy to figure out at first.  I don't know of a guide specific to gtk themes, but there are plenty around to help you compile stuff.

Once you get the dependencies installed, it's usually just
```
./configure
make
sudo make install
```

---

### Post by jordanmthomas on 2006-11-07
I'd also like to say that I don't actually use Ubuntu any more, so I am not sure of the exact package names you'll need.  Sorry.  :(

---

### Post by familyjules74123 on 2006-11-07
hmm, thank you.  I'm not currently on ubuntu, so I will do some researching and try it next time I am on ubuntu.  I will post back here if I run into problems.

---

