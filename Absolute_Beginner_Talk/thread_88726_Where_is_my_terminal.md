---
title: "Where is my terminal?"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-11-10
I just upgraded to breezy and now when i press the right mouse button, I don't seen an option for terminal which I used to have with hoary.  Can this be fixed?

---

### Post by Sutekh on 2005-11-10
You need to install this either by using the command line

```

sudo apt-get install **nautilus-open-terminal**

```

or simply search for it in Synaptic

---

### Post by rjwood on 2005-11-10
there is also one in application>accessories

---

### Post by nrwilk on 2005-11-11
[QUOTE=rjwood]there is also one in application>accessories[/QUOTE]
or, to get a more traditional one:
<ctrl><alt><any F-key between F1 and F6 inclusive>

To get back to your X11 graphical interface, hit <ctrl><alt><F7>

If you're on a PPC machine (Apple) it will be <ctrl><command><F1 through F7>

I love using the terminal this way.  It makes me feel like I'm somehow more connected to our ancient ancestors.  Cave hackers, Homo-Geekus. hehe

---

### Post by earobinson on 2005-11-11
other than personal preference is there any reason to use the terminal this way?

---

### Post by nrwilk on 2005-11-11
[QUOTE=earobinson]other than personal preference is there any reason to use the terminal this way?[/QUOTE]

If you're doing something that requires shutting down the X window system, such as installing proprietary nvidia drivers.  Uncommon situations such as that...

---

### Post by earobinson on 2005-11-11
thanks :)

oh ya to the OP you can always click system->preferences->keyboard shortcuts (or type gnome-keybinding-properties in the terminal) and bind open a terminal to a key

---

