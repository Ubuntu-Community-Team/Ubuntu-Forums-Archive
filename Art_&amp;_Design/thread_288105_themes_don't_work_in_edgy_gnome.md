---
title: "themes don't work in edgy gnome?"
date: 2006-10-29
forum: Art &amp; Design
---

### Post by Master Ar2ro on 2006-10-29
I have updated to edgy just recently, and now only the Human theme seems to work. I had a few extra themes installed, and downloaded a couple more.
Now, when I change to any of those themes (few of them were working 100% on dapper) only metacity theme gets applied. The GTK theme is removed, and only colors get applied, no images are used as if there were missing. No files are missing, the themes that used to work (for example VistaBut) fail to work now, one I downloaded today (Neutronium) fails as well.
Those themes are from gnome-look.org. Can anyone help?

---

### Post by Ubnuut on 2006-10-30
Exactly the same problem here. I would also like to get a solution for this problem. All my GTK themes that work well in Dapper don't work well in edgy.

---

### Post by anodizer on 2006-10-30
```
sudo apt-get install gtk2-engines-pixbuf
```

:wink:

---

### Post by Master Ar2ro on 2006-10-30
It's already installed. So that's not it. Any other ideas? ;)

---

### Post by anodizer on 2006-10-30
That's weird. You should try to install gtk-engines-pixmap too.

---

### Post by Master Ar2ro on 2006-10-30
There's no gtk-engines-pixmap in edgy's repositories. That might be the cause, but since it's not available there's no way to fix the problem :|

//EDIT:
Ok, so I downloaded that package from packages.ubuntu.com (version 0.12-8), but that still doesn't fix the problem. At least not without a reboot. I'll check that soon.
//EDIT2:
Nothing changed after I installed that package. :???: Perhaps you have some more ideas?

---

### Post by anodizer on 2006-10-30
> **Master Ar2ro said:**
> Perhaps you have some more ideas?

Are you sure your themes don't need any exotic engine like Murrine or Candido/Rezlooks to work? I can't imagine anything else, you should contact one of the theme creators, probably he'll know what the problem is.

---

### Post by kyoushu on 2006-10-30
All pixmaps themes don't work out of the box for some reason.  In synaptic if you install gtk2-engines-pixbuf it will be fixed.  Worked for me. And yeah, check if you're using a theme that uses an engine you don't have.

---

### Post by Master Ar2ro on 2006-10-31
> **anodizer said:**
> Are you sure your themes don't need any exotic engine like Murrine or Candido/Rezlooks to work? I can't imagine anything else, you should contact one of the theme creators, probably he'll know what the problem is.

Yes, I'm sure they don't need any of those engines, as both state:
```
  engine "pixmap"
  {
```
I can try contacting the theme creators, but as I said earlier, at least one of those themes worked under dapper, so the problem lies most probably in edgy.

[QUOTE=kyoushu]In synaptic if you install gtk2-engines-pixbuf it will be fixed. Worked for me.[/QUOTE]
But the problem is that I already have that engine installed and still nothing works.

Thanks for trying anyway, guess I'll be left with only the standard theme for a while...

---

### Post by Master Ar2ro on 2006-10-31
Ok, I managed to get it to work. I completely removed gtk2-engines-pixbuf and gtk-engines-pixmap and them reinstalled them, though I still don't know why it didn't work earlier, since the versions installed are the same...

Thanks for your help ;)

---

### Post by jasonxh on 2006-11-30
Unfortunately I'm not that lucky ... It still does not work now ](*,) 
If anyone knows what might be the cause, please give me a hint ...

---

### Post by jasonxh on 2006-12-01
Well, never mind. I somehow get it right, although I've no idea what I did ...

---

### Post by bratsever on 2006-12-01
I have the same problem in Edgy. :( and I cant find decision of this problem

---

### Post by Camden on 2006-12-06
I wonder why gtk2-engines-pixbuf isn't installed by default.  It seems a kind of critical to having operational themes.  Just pondering why.

---

### Post by strabes on 2006-12-08
run gnome-settings-daemon and then try to set custom gtk/icon/cursor themes

---

