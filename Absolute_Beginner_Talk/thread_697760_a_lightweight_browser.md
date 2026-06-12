---
title: "a lightweight browser?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by syms on 2008-02-15
can someone reccomend lightweight web browser? ive tried firefox, iceweasel, swiftfox, swiftweasel, opera, epiphany, midori, konqueror web browsers. all these browsers feels slow exept midori, but it is buggy as hell, it crashes every two minutes and the scrolling is not smooth. im searching for somethink like internet explorer. my pc is still amd duron 900 mhz, 312 ram, 80 gb 7200 rpm samsung hdd, nv riva tnt2 model 64 video.

---

### Post by DJiNN on 2008-02-15
What OS are you running? (X/K/Ubuntu etc - or something else?) I've downloaded & compiled the latest version of Kazehakase (Version 0.5.2 i think) and installed on antiX (Mepis based) and that works great..... much better than the version in the Ubuntu repos (Version 4.something i think).

If you're using Ubuntu (With Gnome) on a machine of that spec, you may find that if you install something like antiX or TinyMe, you'll get a much better response for the software that you're using..... Opera works really well in TinyMe and the version of Iceweasel that comes with antiX also works well. 

Are you running plugins with Firefox at all? That always seems to slow it down somewhat i have found....... :)

---

### Post by Dr Small on 2008-02-15
+1 for Kazehakase

---

### Post by syms on 2008-02-15
in right of my account info there is writed that im using xubuntu 7.10 gutsy gibbon and no, im not using any firefox plugins. thanks i will try antiX and kazehakase :)

---

### Post by syms on 2008-02-15
thank you two, kazehakase works faster than all of them :-D:-D:-D

---

### Post by billgoldberg on 2008-02-15
[All linux browsers.]("http://www.itp.uni-hannover.de/~kreutzm/en/lin_browser.html")

Firefox 3 b3 is pretty lightweigth (haha).

---

### Post by DJiNN on 2008-02-15
> **syms said:**
> thank you two, kazehakase works faster than all of them :-D:-D:-D

Excellent.... that's good to hear. Have fun! :D

---

### Post by DJiNN on 2008-02-15
> **billgoldberg said:**
> [All linux browsers.]("http://www.itp.uni-hannover.de/%7Ekreutzm/en/lin_browser.html")

Firefox 3 b3 is pretty lightweigth (haha).

Thanks for the link, although the page seems to have moved [here]("http://www.helgefjell.de/browser.php") and even that's about a year out of date now. :) Shame too, because there were some interesting browsers mentioned. 

As for Firefox 3b3, i've actually found it to be quite good, which wasn't what i was expecting at all. A pleasant surprise. :D

---

### Post by t0p on 2008-02-15
The lightest browser I know of for Ubuntu is **w3m**.  It comes installed by default - just open a terminal and give the command
```
w3m
```
**Warning:** It's very likely *too* lightweight for the OP - he said he wanted something like Internet Explorer(!!), and w3m ain't *nothing* like IE - but someone might like it.

Incidentally, the OP said he wanted a lightweight browser, then said he wanted IE.  Anyone else think that's odd?  I mean, IE is the absolute *antithesis* of "lightweight"...

---

### Post by bbqsandwich on 2008-02-15
Don't forget about ELinks!
```

sudo apt-get install elinks
```

Also, I found this line of the w3m options choices amusing:

> -debug           DO NOT USE

---

### Post by 1875 on 2008-02-15
you could always use lynx.:)

---

### Post by toobuntu on 2008-02-28
There's also a build of K-Meleon that is meant for running under WINE.

K-Meleon is lightning fast and based on the same gecko rendering engine used by Firefox, but without all the bloat.  It uses the system's window decorations instead of providing its own.

I tried it because I just didn't like the Kazehakase interface, but I do not use it in Ubuntu because of unresolved printing issues - which you may not have.

K-Meleon unofficial builds web page:
[http://kmeleon.sourceforge.net/wiki/UKmeleon]("http://kmeleon.sourceforge.net/wiki/UKmeleon")

This is the version I installed and tested:
[http://rs251l32.rapidshare.com/files/73306368/353733/K-Meleon-NX-18111.zip]("http://rs251l32.rapidshare.com/files/73306368/353733/K-Meleon-NX-18111.zip")

---

### Post by Oldsoldier2003 on 2008-02-28
> **1875 said:**
> you could always use lynx.:)
+1 

:) lynx is my favorite ultralightwieght champion of webbrowsing,back from my starting forrays into linux.. slackware without X

---

### Post by chris4585 on 2008-02-28
links2 is awesome

links2 -g 

try that in a terminal and that is awesome i think its the best lightweight internet browser out there 8)

---

### Post by olejorgen on 2008-02-28
I'd say it's not so much browsers that's heavy, mor like it's webpages that's crappy.

---

### Post by harold4 on 2008-02-28
Dillo

---

### Post by yotam on 2008-05-10
> **Dr Small said:**
> +1 for Kazehakase

On Xubuntu-8.04(beta), it comes up nice and fast.
But when I try to go to its 'Preferences' I get:


```
(kazehakase:13178): Gtk-CRITICAL **: gtk_tree_store_get_value: assertion `VALID_ITER (iter, tree_store)' failed

(kazehakase:13178): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.3/gobject/gtype.c:3368: type id `0' is invalid

(kazehakase:13178): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced
Segmentation fault (core dumped)

```

---

