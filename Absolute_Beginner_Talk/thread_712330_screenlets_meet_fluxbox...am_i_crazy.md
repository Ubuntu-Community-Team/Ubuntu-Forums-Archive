---
title: "screenlets meet fluxbox...am i crazy?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by il-luzhin on 2008-03-01
I'm hoping it might be possible to use screenlets with fluxbox and though I've seen many suggestions that say it's possible, I have as of yet had zero success on my own.  

Can anyone point me toward a tutorial?

Thanks

---

### Post by PeterJS on 2008-03-01
Does fluxbox play nice with compiz or other composite managers? I know IceWm doesn't ( :(), Screenlets need a composite manger for them to work properly.

---

### Post by spupy on 2008-03-01
I think i was able to run gDesklets once, but i didn't like them. Other than that, i see two options:
1. Use xcompmgr. If PeterJS is right and screenlets need composite, xcompmgr is a simple composite manager that plays nice with fluxbox.
2. Find some apps for the fluxbox dock (called the slit). You can find them here: [http://www.dockapps.org/]("http://www.dockapps.org/")

---

### Post by il-luzhin on 2008-03-02
thanks.  Xcompmgr didn't work out of the box but I'll look into it a little closer when I get a chance

---

### Post by spupy on 2008-03-02
> **il-luzhin said:**
> thanks.  Xcompmgr didn't work out of the box but I'll look into it a little closer when I get a chance

Yeah, it's not polished. Hard to configure (only via the command line). I use this command:
```
xcompmgr -c -t -3 -l-10 -r7 -o .5 &
```

---

### Post by rjmdomingo2003 on 2008-03-02
You can try adesklets. I've tried one from gnome-look.org: [http://gnome-look.org/content/show.php/CircleMeter+adesklet?content=69600](http://gnome-look.org/content/show.php/CircleMeter+adesklet?content=69600)

Am not sure 'bout the others.

---

