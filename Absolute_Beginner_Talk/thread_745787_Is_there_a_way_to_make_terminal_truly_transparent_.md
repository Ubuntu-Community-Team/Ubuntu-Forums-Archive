---
title: "Is there a way to make terminal truly transparent without copmiz?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2008-04-04
Does anyone know?
Thank you.

---

### Post by Inxsible on 2008-04-04
yes you can edit the profile of the Terminal by going to Edit>>Current Profile. On the Effects tabs you can set the transparency.

---

### Post by wormser on 2008-04-04
Terminal> Edit> Current Profile> Effects Tab and select Transparent background.  You can also create multiple profiles under Edit> Profiles.

---

### Post by systemintheglitch on 2008-04-05
No i really want it "TRULY" transparent meaning that you can see the windows behind it.. Without compiz or "desktop effects" set.

---

### Post by joshrobinson on 2008-04-05
yup
check this tutorial

[http://www.ubuntugeek.com/how-to-create-a-transparent-terminal-session-as-your-desktop-background.html]("http://www.ubuntugeek.com/how-to-create-a-transparent-terminal-session-as-your-desktop-background.html")

---

### Post by jordanmthomas on 2008-04-05
> **joshrobinson said:**
> yup
check this tutorial

[http://www.ubuntugeek.com/how-to-create-a-transparent-terminal-session-as-your-desktop-background.html]("http://www.ubuntugeek.com/how-to-create-a-transparent-terminal-session-as-your-desktop-background.html")

That's still not truly transparent per se.

To get a truly transparent terminal you will need a compositing manager of some sort (compiz, etc)
If you can't / don't want to run compiz, others that should work to give true transparency:
[LIST]
[*]kwin has a compositor
[*]xfwm4 has a composite manager
[*]xcompmgr can be used with any window manager
[/LIST]

---

### Post by joshrobinson on 2008-04-05
> **jordanmthomas said:**
> That's still not truly transparent per se.


to me, if you can see through it, its transparent

---

### Post by jordanmthomas on 2008-04-05
> **joshrobinson said:**
> to me, if you can see through it, its transparent

There is a difference in transparent and truly transparent though.
Old transparency just copies the wallpaper and uses it as a background.
True transparency shows whatever is behind the window.

The first screenshot here is true transparency, and the second is not.  See the difference?

---

### Post by joshrobinson on 2008-04-05
> **jordanmthomas said:**
> There is a difference in transparent and truly transparent though.
Old transparency just copies the wallpaper and uses it as a background.
True transparency shows whatever is behind the window.

The first screenshot here is true transparency, and the second is not.  See the difference?

yeah i see the difference, and know the difference, i guess i missed the part where the op wanted "true transparency"

i *assumed* the OP wanted something like mine (you know what they say about assuming things)
screenshot below

mines done with compiz though

---

### Post by nutz on 2008-04-05
> **Inxsible said:**
> yes you can edit the profile of the Terminal by going to Edit>>Current Profile. On the Effects tabs you can set the transparency.

+1, but requires compiz

---

### Post by systemintheglitch on 2008-04-05
I don't get it.. I heard that gnome 2.22 had it's own compositor?! I'm on the latest ubuntu beta which has gnome 2.22.. Why is this not a feature. This is like the most obvious thing ever to include! :)

---

### Post by jordanmthomas on 2008-04-05
> **systemintheglitch said:**
> I don't get it.. I heard that gnome 2.22 had it's own compositor?! I'm on the latest ubuntu beta which has gnome 2.22.. Why is this not a feature. This is like the most obvious thing ever to include! :)

Metacity (gnome's default window manager) DOES act as a compositor, but if I recall correctly, Ubuntu doesn't enable it when they  compile it.  You can try to turn it on but it might not work:
```
gconf-editor /apps/metacity/general
```
and turn the checkbox for "compositing_manager" on

Like I said, it probably won't do anything (it didn't on Edgy, which is the last Ubuntu I used at all)

EDIT
I just turned it on on my Arch install and metacity does indeed work as a compositor.  It's not as fast as compiz, but true transparency does work.

---

### Post by systemintheglitch on 2008-04-05
WOW!!

The alt tab is wayyy better with the default metacity compositer enabled!!!

Now, i can't figure out how to get true transparency in the terminal though(actually just open a new window :) ).. And also how to get rid of the "thumbnails" in the new alt_tab, which will make it faster... 

Any help?

---

### Post by systemintheglitch on 2008-04-05
Also, it's kind of buggy when loading when loading windows, and pop ups, it kinda flashes garbage before showing the actual window.. Maybe this is due to my gfx card?

Any tips on trying to make it lesss buggy?

---

### Post by Joeb454 on 2008-04-05
No it does it with mine too :) Though so did Compiz-Fusion, so I figured I'd just live with it :)

Also the gconf-editor method is what I used, because I realised I only really used Compiz for a truly transparent terminal ;)

---

### Post by systemintheglitch on 2008-04-05
Yah but I still want two things really bad:

1.I want less buggy window loading (no garbage before it shows the actual window-probably just my problem)

2. And no thumbnail previews on alt+tab

---

