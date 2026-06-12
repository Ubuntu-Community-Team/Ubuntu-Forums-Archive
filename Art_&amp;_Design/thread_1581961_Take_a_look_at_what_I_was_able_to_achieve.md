---
title: "Take a look at what I was able to achieve"
date: 2010-09-25
forum: Art &amp; Design
---

### Post by rswoods on 2010-09-25
I wanted to save vertical screen space on my netbook so I installed a few programs and stumbled on something cool.

I'm using the "Equinox light" theme, which is pretty attractive with the global menus and smooth window border transitions:
[http://ompldr.org/vNW4zdg/windowed.png](http://ompldr.org/vNW4zdg/windowed.png)

but this surprised me, when maximus is disabling titlebars for maximized windows the toolbar and panel are seamless and it looks great:
[http://ompldr.org/vNW4zdQ/maximized.png](http://ompldr.org/vNW4zdQ/maximized.png)

what do you think?  pretty cool right?

---

### Post by nitrogensixteen on 2010-09-25
looks cool, too bad the only browser that offers good script blocking and fine cookie control doesn't work with global menus...

---

### Post by cjmabry25 on 2010-09-25
That is awesome. And that theme is beautiful haha. Definitely gonna use that.

---

### Post by saket3143 on 2010-09-28
How did u do that can u elaborate on the procedure

---

### Post by chrisw92 on 2010-09-30
man, that looks brilliant. I'm not keen on the close/max/min buttons but I love the screenshot when its maximized.

---

### Post by Lucradia on 2010-10-01
> **saket3143 said:**
> How did u do that can u elaborate on the procedure

install maximus and whatnot.

[http://en.wikipedia.org/wiki/Ubuntu_Netbook_Edition#Component_packages](http://en.wikipedia.org/wiki/Ubuntu_Netbook_Edition#Component_packages)

---

### Post by tripmix on 2010-10-05
I once made an image that when displayed in a web browser made hole so I could see right trough to my desktop, and that was before transparency was a part of kde. Never managed to reproduce it. And once I got a image stuck in the root window that remained after I formated the disk. Just saying, amazing what can happen when you're messing around :D

---

### Post by Lucradia on 2010-10-05
btw, I don't really like maximus, as we need a way to exclude certain apps from maximus (IE: Pidgin buddy list, conversation in pidgin, empathy buddy list, and empathy convos, etc.)

It's not real fun to have maximus force-maximize a window that's already small.

---

### Post by ixifx on 2010-10-07
> **Lucradia said:**
> btw, I don't really like maximus, as we need a way to exclude certain apps from maximus (IE: Pidgin buddy list, conversation in pidgin, empathy buddy list, and empathy convos, etc.)

It's not real fun to have maximus force-maximize a window that's already small.

you can use gconf editor to change the way maximus behaves.  it will be under /apps/maximus after installed.  you should see "binding" "exclude class" "no maximize" and "undecorate"

---

### Post by Lucradia on 2010-10-08
> **ixifx said:**
> you can use gconf editor to change the way maximus behaves.  it will be under /apps/maximus after installed.  you should see "binding" "exclude class" "no maximize" and "undecorate"

buddy list for both pidgin and empathy and their convos are all "normal windows," defining under "class" or "type" wouldn't work. Think "title" instead, or the name of the binary.

---

### Post by Crafty Kisses on 2010-10-08
Solid work, thanks for sharing.

---

### Post by kernst on 2011-01-26
> **saket3143 said:**
> How did u do that can u elaborate on the procedure

How to get the [global menu]("http://code.google.com/p/gnome2-globalmenu/") and a whole lot more:
[LIST]
[*][http://www.webupd8.org/2009/11/ubuntu-netbook-remix-optimization-guide.html](http://www.webupd8.org/2009/11/ubuntu-netbook-remix-optimization-guide.html)
[*][http://www.webupd8.org/2010/06/how-to-get-most-out-of-ubuntu-netbook.html](http://www.webupd8.org/2010/06/how-to-get-most-out-of-ubuntu-netbook.html) (an updated version with more recent packages and slightly different methods)
[/LIST]

---

### Post by kernst on 2011-01-26
> **Lucradia said:**
> btw, I don't really like maximus, as we need a way to exclude certain apps from maximus (IE: Pidgin buddy list, conversation in pidgin, empathy buddy list, and empathy convos, etc.)

It's not real fun to have maximus force-maximize a window that's already small.

See this thread: [http://ubuntuforums.org/showthread.php?t=1483946](http://ubuntuforums.org/showthread.php?t=1483946)

Maximus has a gconf key which can be used to add window classes (e.g., as returned by [FONT="Courier New"]xprop[/FONT]) to its exclusion list. The forum thread above contains a script which can be used to automate this and bind it to a hotkey.

The script works really well, and makes using Maximus full-time actually tolerable.

---

### Post by Lucradia on 2011-01-28
> **kernst said:**
> See this thread: [http://ubuntuforums.org/showthread.php?t=1483946](http://ubuntuforums.org/showthread.php?t=1483946)

Maximus has a gconf key which can be used to add window classes (e.g., as returned by [FONT="Courier New"]xprop[/FONT]) to its exclusion list. The forum thread above contains a script which can be used to automate this and bind it to a hotkey.

The script works really well, and makes using Maximus full-time actually tolerable.

As I said before, Pidgin and the stuff I mentioned are considered "Normal window" to class, and therefore, setting "class" and "type" would not work.

---

### Post by Copper Bezel on 2011-01-28
Forgive my ignorance - I've never used Maximus, because I've felt that 10" is plenty for a normal desktop environment and I don't use static horizontal panels - but can't this be handled through Window Rules? That is, set Maximized for type=Normal & !name=pidgin, or some such? I mean, I don't know whether the ordinary maximize function is all Maximus needs, but I've just set up my system to not let me restore any window but Nautilus with the above syntax, and it's working fine.

---

### Post by Lucradia on 2011-01-29
> **Copper Bezel said:**
> Forgive my ignorance - I've never used Maximus, because I've felt that 10" is plenty for a normal desktop environment and I don't use static horizontal panels - but can't this be handled through Window Rules? That is, set Maximized for type=Normal & !name=pidgin, or some such? I mean, I don't know whether the ordinary maximize function is all Maximus needs, but I've just set up my system to not let me restore any window but Nautilus with the above syntax, and it's working fine.

Maximus doesn't follow window rules as per normal. name doesn't work. Plus, the name, if I recall, for pidgin is "Buddy List" or something (Yes, with a space.)

it would be better if we could exclude binaries, etc.

---

### Post by Copper Bezel on 2011-01-30
I didn't mean window rules in Maximus, I meant the Compiz plugin "Window Rules," which you could use to force everything that isn't Pidgin or a dialog to maximize. But you're saying that just maximizing a window won't force Maximus to work with it? Too bad.

Incidentally, "Buddy List" is the window *title* for Pidgin, but the *name* value is actually "Pidgin" (with a capital, so I was wrong, too.) In compiz (and most applications,) the space wouldn't be a problem anyway, because you could just put the term in quotation marks ... but none of that actually helps here. Bleh.

---

### Post by xtremethegreat1 on 2011-02-12
Awesome!

---

