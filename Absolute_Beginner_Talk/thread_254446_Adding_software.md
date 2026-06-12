---
title: "Adding software"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by rbrines on 2006-09-10
When I use the Add/Remove applications everytime it tells me that "The List Of Applications Is Out Of Date" this is not really a proablem it just gets anoying it's only started doing it recently. Anyone know why?

---

### Post by jordanmthomas on 2006-09-10
Go to System --> Accessories --> Terminal
Type this
```

sudo apt-get update
```
this will update your list of software and you shouldn't have any more complaints (for a while anyway)

---

### Post by rbrines on 2006-09-10
I tryed that and it still says it out of date?

---

### Post by jordanmthomas on 2006-09-10
You got me.  I don't actually use the Add / Remove Applications program so I don't know about any peculiarities it has

Anyone else got an idea?

---

### Post by CatKiller on 2006-09-10
> **rbrines said:**
> When I use the Add/Remove applications everytime it tells me that "The List Of Applications Is Out Of Date" this is not really a proablem it just gets anoying it's only started doing it recently. Anyone know why?

So what happens if you click on the Reload button?

---

### Post by rbrines on 2006-09-10
It update it self but the next time i go to use it, it say it out of date agian

---

### Post by CatKiller on 2006-09-10
> **rbrines said:**
> It update it self but the next time i go to use it, it say it out of date agian

How long is it between times that you run the application? I think that all of the apt-get based programs are set up to check every now and then for newer versions of the programs you have installed. I think it might default to every week, or so. It's probably configurable, if you wanted to set it longer, although I haven't felt the need to, so I couldn't tell you exactly where the option is.

---

