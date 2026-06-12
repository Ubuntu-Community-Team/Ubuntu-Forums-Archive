---
title: "Mplayer error message?"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-11
I get this error messege every time I open mplayer.

[ws] Sorry, your system does not support the XShape extension

And then it has some black boxes. How can I fix this?

---

### Post by Case_f on 2006-04-15
Check your Xorg.conf file if you have the following in section Module:

```
Load "extmod" 
    SubSection  "extmod" 
      Option    "omit xfree86-dga"
    EndSubSection

```

If not, add that and restart X. Your problem should be solved.

---

### Post by stylius on 2007-11-12
Same problem here, I added those lines in the Modules section, but still the samo error.

Any idea?

---

