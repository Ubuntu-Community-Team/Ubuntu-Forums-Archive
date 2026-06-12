---
title: "Opera 9.10 and multimedia plug-ins."
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2007-01-12
Hello, I just installed Opera (pretty fast browser) and I need to enable my multimedia plug-in support. Does anyone know how to do this?

---

### Post by crimesaucer on 2007-01-12
Anybody out there with Opera 9.10 and a working embedded media similar to the Firefox plug-ins or the extension for the media player connectivety.

---

### Post by crimesaucer on 2007-01-13
Just to help anyone with the same problem for Embedded media, this is what worked for me:

go to synaptic and install the mozilla plugger and mplayer.

I prefer xine and have it set for targeted media links, but for the actual embedded media, only mplayer works for me.

Then for java:

go to Opera's,

Preferences-->--Advanced-->--Content-->--Java Options 

and (for pc) make the path /usr/lib/j2re1.5-sun/lib/i386/

and then check validation.

also make sure you have everything that you want enabled in Tools-->--Quick Preferences.

---

### Post by geraner on 2007-01-15
If you have all this stuff running for Firefox 2.0 you can just add the directory under:

Preferences-->--Advanced-->--Content-->Plug-in Options...
And add there 
:/usr/lib/firefox/plugins

Close and restart your Opera and all the Multimedia stuff will work for Opera as well.

/Geraner

---

### Post by effo on 2007-02-01
> **crimesaucer said:**
> Just to help anyone with the same problem for Embedded media, this is what worked for me:

go to synaptic and install the mozilla plugger and mplayer.

I prefer xine and have it set for targeted media links, but for the actual embedded media, only mplayer works for me.

Once I figured out that the mozilla plugger is named mozplugger, this was VERY helpful, thanks for the tip! This was the magic trick:
```
$ sudo apt-get install mozplugger mplayer
```

---

### Post by crimesaucer on 2007-02-01
Sorry about that, I should of said mozplugger.

---

