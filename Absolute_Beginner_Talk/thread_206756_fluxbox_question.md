---
title: "fluxbox question"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by hikitsu4 on 2006-06-30
How do you remove the dockbar/panel in fluxbox and only keep the right click menu?

---

### Post by xtacocorex on 2006-06-30
Let me see if I hear you correctly, you want the right click menu to be on the screen at all times?

I don't think this can be done. I ran Fluxbox quite extensively before Dapper came out and I saw nothing in the config files that allowed this. 

Here is a link to editing the init file.
[http://fluxbox-wiki.org/index.php/Howto_edit_the_init_file](http://fluxbox-wiki.org/index.php/Howto_edit_the_init_file)

As always, I'm willing to be proven wrong in the pursuit of truth.

---

### Post by hikitsu4 on 2006-06-30
[quote=xtacocorex]Let me see if I hear you correctly, you want the right click menu to be on the screen at all times?

I don't think this can be done. I ran Fluxbox quite extensively before Dapper came out and I saw nothing in the config files that allowed this. 

As always, I'm willing to be proven wrong in the pursuit of truth.[/quote]
No i didnt mean that i just meant i want to remove the panel, i didnt say anything about the right click menu to be on all the time.

---

### Post by xtacocorex on 2006-06-30
From the link I edited to my post:
```

session.screen0.toolbar.visible: <boolean>
     The user can set whether they want to have a toolbar on screen at
     all.  Setting to 'false' removes the toolbar from the screen. This
     ultimately depends on whether or not the toolbar was compiled into
     the Fluxbox build. The default is that the toolbar will be visible.
     Default: true

```

Hope this helps.

---

### Post by hikitsu4 on 2006-06-30
[quote=xtacocorex]From the link I edited to my post:
```

session.screen0.toolbar.visible: <boolean>
     The user can set whether they want to have a toolbar on screen at
     all.  Setting to 'false' removes the toolbar from the screen. This
     ultimately depends on whether or not the toolbar was compiled into
     the Fluxbox build. The default is that the toolbar will be visible.
     Default: true

``` 
Hope this helps.[/quote]
yep it helped, thanks alot ;-)

---

### Post by xtacocorex on 2006-06-30
Glad that it worked. I might have to try that when I install Fluxbox on my laptop.

---

