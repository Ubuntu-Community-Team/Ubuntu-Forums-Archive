---
title: "burning cd failure: Sony dru-510a"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Ba66e77 on 2007-01-02
I'm getting failures/coasters from my attempts to burn cds with a Sony DRU-510a.  From Nautilus, I get coasters but no errors if I burn data or audio disks.  If I try to burn disks from an image file, it does nothing.  Just sits there.  Reading from both dvds and cds works fine, though.

I found another post with similar problems ([http://ubuntuforums.org/archive/index.php/t-260641.html](http://ubuntuforums.org/archive/index.php/t-260641.html)) but it has no reply.  Anyone have an idea of what to try?

I'm running Edgy (I know, not recommended for newbies, but I didn't find that until after I installed).  Is there any reason to think things would work better if I switch to Drake?

---

### Post by taurus on 2007-01-02
Besides using nautilus to do your burning, have you at least tried other apps like gnomebaker, xcdroast, k3b, graveman, etc.?

---

### Post by Ba66e77 on 2007-01-02
I've tried xcdroast, but got a "you must be logged in as super user and configure the program " type message.  I'm embarrassed to say, but I didn't know how to do that, so I left it alone.  
I'll try some of the other programs you mentioned when I get back to my home machine this evening.

---

### Post by taurus on 2007-01-02
Do you belong to group cdrom?

Applications -> Accessories -> Terminal
```
groups
```
Otherwise, run it from a terminal with the gksudo.

```
gksudo xcdroast
```

---

