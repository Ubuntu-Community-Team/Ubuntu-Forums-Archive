---
title: "Running Shell Script at Boot Time"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by nyxynyx on 2007-01-01
Hello. May I know where do I insert some shell script code into so that the code will run at boot time? Its a simple script for replacing the xorg.conf with another one depending on whether my laptop will be using integrated graphics or dedicated. Thanks!

---

### Post by freebeer on 2007-01-01
I don't know if this is the best way, but have you tried:

adding it to start up programs in System > Preferences > Sessions.

---

### Post by nyxynyx on 2007-01-01
Thanks. But I think I need the script to run before X11. Will adding the script to sessions work this way?

---

### Post by MkfIbK7a on 2007-01-01
i know there is a way to do that but maybe its only in xubuntu its somewhere in the settings i will get back to you when i remember

---

### Post by freebeer on 2007-01-01
You're probably right about wanting to run it before x11 loads.  Or your script could make the change, then restart x, but that's a bit of an inelegant solution.  I'm not familiar with the details, but you might want to check out Runlevel and perhaps init.d.  Somewhere in there lies a solution, I think.

---

### Post by K.Mandla on 2007-01-02
I'm not on my machine right now so I'm not sure this will work ... or at least not 100 percent.

Open a file named "startscript" -- change it to whatever you want, but make sure you keep the name consistent through all this. :mrgreen:

```
sudo nano -w /etc/init.d/startscript
```
That uses nano, but you can use vim or gedit or mousepad or whatever. (The -w is no word wrap, which could interfere with longer commands.) Build your script.

```
#!/bin/sh
# your script goes here
```
Save it. Make it executable with

```
cd /etc/init.d
sudo chmod +x startscript
```

Now make a symbolic link in /etc/rcS.d so that it will run at boot up:

```
cd /etc/rcS.d 
sudo ln -s /etc/init.d/startscript S33startscript
```
Again, I haven't tried that and I'm at work so I can't test it, so use at your own risk. ;) If someone can improve on this, please jump in.

---

### Post by Thundercat on 2008-01-14
I'm trying to do something similar but mine will want to be run when logged in. I'm wanting a method to change my xorg between the single screen or dual screen versions I have and then restart x.
Can someone tell me how to restart x from within a shell script please?

Thanks :)

---

### Post by hyper_ch on 2008-01-14
Wouldn't it be better to just apply default values to startup instead of manually hardlinking it:

```

sudo update-rc.d /path/to/script.sh defaults

```

---

