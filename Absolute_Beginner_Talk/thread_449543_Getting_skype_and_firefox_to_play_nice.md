---
title: "Getting skype and firefox to play nice?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Old Pink on 2007-05-20
Hi there,

When clicking a link like **[this]("skype:matt.hoy?chat")**, you should be prompted to talk to me via Skype (try it, I'm usually available, drop me a line) 

Instead I get this error:
[IMG]http://img171.imageshack.us/img171/8573/screenshotalerteu7.png[/IMG]

To fix this, you should follow the instructions here: [http://share.skype.com/sites/linux/2006/08/making_skype_links_work.html](http://share.skype.com/sites/linux/2006/08/making_skype_links_work.html)

BUT, the instructions don't work! I think it's because /usr/local/bin/skype-action-handler doesn't exist. But when I run ```
locate skype
``` I don't find any alternative.

Thanks for any help
Matt [img]http://mystatus.skype.com/smallicon/matt.hoy[/img]

---

### Post by Ghostlove on 2007-05-20
Instead of locate, try whereis?

---

### Post by Klargodut on 2007-05-20
I run these lines in a terminal (my skype was installed to /usr/bin):

```

/usr/bin/gconftool-2 -s -t string /desktop/gnome/url-handlers/skype/command '/usr/bin/skype-action-handler &#8220;%s&#8221;'
/usr/bin/gconftool-2 -s -t bool /desktop/gnome/url-handlers/skype/enabled true

```

and it worked like a charm after restarting firefox.

---

### Post by Old Pink on 2007-05-20
Now I get a blank firefox window, a new skype running and this error, twice:
[img]http://img174.imageshack.us/img174/7004/screenshotcriticalskypeil6.png[/img]

Wouldn't say it was much of a better situation. Thanks for the help so far.

Whereis gives the following:
skype: /usr/bin/skype /usr/X11R6/bin/skype /usr/bin/X11/skype /usr/share/skype
skype-action-handler: /usr/bin/skype-action-handler /usr/X11R6/bin/skype-action-handler /usr/bin/X11/skype-action-handler

---

### Post by Old Pink on 2007-05-20
> **Klargodut said:**
> I run these lines in a terminal (my skype was installed to /usr/bin):

```

/usr/bin/gconftool-2 -s -t string /desktop/gnome/url-handlers/skype/command '/usr/bin/skype-action-handler “%s”’ 
/usr/bin/gconftool-2 -s -t bool /desktop/gnome/url-handlers/skype/enabled true

```and it worked like a charm after restarting firefox.

How do I **undo** the effects of these commands?

---

### Post by Old Pink on 2007-05-20
> **Old Pink said:**
> Now I get a blank firefox window, a new skype running and this error, twice:
[IMG]http://img174.imageshack.us/img174/7004/screenshotcriticalskypeil6.png[/IMG]

Wouldn't say it was much of a better situation. Thanks for the help so far.


OK, so all works well when Skype isn't running already.

When Skype is already running, I get the error(s) above.

When it isn't, Skype opens, logs in and does what the link requires.

How do I solve the "already running" problem? As I like to have skype open constantly

---

### Post by Klargodut on 2007-05-20
To undo:

```

gconftool-2 --recursive-unset /desktop/gnome/url-handlers/skype

```

---

### Post by Old Pink on 2007-05-20
> **Klargodut said:**
> ```

gconftool-2 --recursive-unset /desktop/gnome/url-handlers/skype

```Thanks, now it's working with just the about:config modifications.

But the links still only work when Skype isn't already running. Fancy coming on Skype and helping me realtime? I guess it's just trial and error...

---

### Post by Klargodut on 2007-05-20
Strange, for me your link works both when skype is running and when it isn't... 

The about:config modifications won't work however, and I have to use the 2 gconftool lines, so I guess it's all trial and error as you say...

---

