---
title: "Browser seems non responsive while opening"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by enduser on 2007-12-10
when i double click my firefox icon nothing happens.

If i continue to click i get an error message saying only one instance may be open at a time.

If i just wait the browser eventually does open. 

Why does it take so long for the browser to respond? Shouldn't the shell load first and then all the add ons and other less important stuff?

I know the time is semi comparable to other operating systems but still it feels a lot slower. Maybe its just the lack of an animated cursor. (which my thunderbird has)

how do i apply that animated cursor to my firefox opening? (soi will at least know if the computer registered my clicks)

BONUS COOKIE: anyone know how long we should expect to wait before celtx ports to synaptic or add programs. Following the directions i still couldn't make it work.

---

### Post by jken146 on 2007-12-11
I haven't got a clue why Firefox does this (it does it to me at uni on Fedora 7 but not at home on Ubuntu).  I just use Epiphany instead.

---

### Post by flamelab on 2007-12-11
Remove it completely (purge-uninstall it ) and then install it from the beginning .
Before that , check the command```
 firefox -safe-mode
```to check if there is a weird plugin that causes the problem .

---

### Post by Tom Mann on 2007-12-11
I've had that problem, run this command in the terminal (make sure there are no visible windows open)

```
killall firefox
```

(also, note the lack of the sudo command)

then click the firefox icon and it should give you the "Restore Session" dialog box.

(PS - I'm not at my Ubuntu desktop at the moment, could someone do a ps -a | grep firefox and confirm I've got the killall parameter right?)

---

