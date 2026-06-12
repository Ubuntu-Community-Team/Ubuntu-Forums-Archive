---
title: "An Error has occured"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by {A}Poly on 2007-07-24
[IMG]http://img73.imageshack.us/img73/9936/error001wy9.png[/IMG]

this is what I get when i open Synaptic Package Monitor.. :mad:

this may have been caused because I was installing virtual box and it got stuck when it was almost done, so i rebooted and now I get that error message. :-?

anyone know how I can fix it?

---

### Post by Al3xK3aton on 2007-07-24
Your image is stretching the board really wide.

---

### Post by swoll1980 on 2007-07-24
go to terminal type " sudo dpkg --configure -a " without the quotes Were you using automatix by any chance? any time your pacage manager gets hung it borks up your dpkg and you have to run this command

---

### Post by Immolatus on 2007-07-24
It's basically telling you what to do.

In a terminal do:

sudo dpkg --configure -a

and press enter.
If this doesn't help do;

sudo apt-get -f

press enter and post the result if it's an error.

---

### Post by dreadlord_chris on 2007-07-24
yeah - you need to do what it says to do - open a terminal and enter:
```

sudo dpkg --configure -a

```

---

### Post by {A}Poly on 2007-07-25
now I get this:

[IMG]http://img477.imageshack.us/img477/7840/error002gh5.png[/IMG]

---

### Post by Immolatus on 2007-07-27
I had some trouble with this too. I would completely remove virtualbox from synaptic and do in a terminal:

sudo apt-get install -f

to clear it out. I'd just install it from the site download ( though I haven't tried this yet, I'm playing with qemu first).

---

