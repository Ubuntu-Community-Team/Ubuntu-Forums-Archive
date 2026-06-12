---
title: "[SOLVED] Adding audio info to conky"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-04-04
I want to add some lines to my .conkyrc file that would display some info about the song I'm listening to.

Like author - group - runtime

Can this be done?

Can this be done with exaile?

If not, with what audio players?

---

### Post by WorldTripping on 2008-04-04
I use RhythmBox, and conky displays this sort of info quite happily.

I'm not at my computer at the moment, but I think it goes something like this:
> ${color lightgrey}Now Playing: ${color} ${exec rhythmbox-client --print-playing}

There is an excellent thread in the cafe about conky

[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

---

### Post by aeiah on 2008-04-04
you can do this with exaile but i dont think its as simple as with amarok or rhythmbox. it has something to do with grabbing dbus information. ill have a look tonight if i remember, although you may find something with google

---

### Post by billgoldberg on 2008-04-04
> **aeiah said:**
> you can do this with exaile but i dont think its as simple as with amarok or rhythmbox. it has something to do with grabbing dbus information. ill have a look tonight if i remember, although you may find something with google

I'm looking but I can't find anything.

I tried the code from rythmbox and it didn't work with exaile.

Also the code is slightly wrong as it opens up rythmbox and if you close rythmbox it will open again by itself.

---

### Post by aeiah on 2008-04-04
nevermind, seems exaile has moved forward since when i tried messing with it (about a year ago)
```
${execi 10 exaile --get-title} 
${execi 10 exaile --get-artist}

```

there are probably others (maybe a progress bar). try scouring the exaile manual for other flag options

---

### Post by WorldTripping on 2008-04-04
hmmm

Try this instead.

> ${exec rhythmbox-client --print-playing --no-start}

Also, there is a list of all the variables you can use with conky:

[http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html")

---

### Post by billgoldberg on 2008-04-04
Thanks.

---

### Post by WorldTripping on 2008-04-04
Yay !

That's the first thread that I've helped to solve.

---

### Post by TheBigBakedBean on 2008-06-20
> **aeiah said:**
> nevermind, seems exaile has moved forward since when i tried messing with it (about a year ago)
```
${execi 10 exaile --get-title} 
${execi 10 exaile --get-artist}

```

there are probably others (maybe a progress bar). try scouring the exaile manual for other flag options

I wrote a script that uses the output from rhythmbox-client to make a progress bar in conky.  Feel free to use it:

[http://ubuntuforums.org/showpost.php?p=5223642&postcount=10](http://ubuntuforums.org/showpost.php?p=5223642&postcount=10)

---

