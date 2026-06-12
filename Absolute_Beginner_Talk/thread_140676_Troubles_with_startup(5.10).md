---
title: "Troubles with startup(5.10)"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by webstuff on 2006-03-06
I've just installed my first linux dist. (Ubuntu ;o))
I did this i "Terminal"
sudo gedit /etc/X11/xorg.conf
And I add'ed "1280*1024"screensize to all screendeeps.
The i rebooted my computer and I got to the place where the modules are loaded, and the suddenly an "alert" box poppedup (in a sort of DOS "mood"?).
I said that some configurations weren't correkt (probally thos i just edited in Terminal).
After the messages I have to login with my administration user (still in the DOS look).
I get logged in, and the I'm am i "Terminal" but still in the damn DOS look, so i tried to type the same command as i did earlier, but then the message "Counld not open for displayin" appeard..

So if anyone can help me. PLEASE, be my guest\\:D/ 
But try to use no hard english words, cause I am really really bad at english ;) 

//Andreas

---

### Post by suRoot on 2006-03-06
Try 

```
sudo pico /etc/X11/xorg.conf
```

and change everything back to the way it was before.

gedit is a graphical app & will only work under XWindows.

For future reference, do this before making any changes:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
```

and then if you find it's broken after restarting

```
sudo cp /etc/X11/xorg.conf.orig /etc/X11/xorg.conf
```

restart & you're working again.

---

