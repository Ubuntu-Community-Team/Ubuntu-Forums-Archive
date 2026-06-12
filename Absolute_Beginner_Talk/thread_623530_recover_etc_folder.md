---
title: "recover /etc folder"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-11-26
Hi,

I was using 7.04 ubuntu and I was backing up /etc folder regularly.

Today I started using 7.10 XUBUNTU.
and once I installed it I wanted to copy my old /etc to new /etc

I used cp command and as result, almost all the folders were omitted.

then I used cp -r command and then the OS crashed.

I wanted to restart it but it never restarted.

I am re-installing now but I am wondering what is the nicest way to copy old /etc folder on new one?

Thanks...

---

### Post by kpkeerthi on 2007-11-26
If you are not sure or if you are not comfortable with command line, you can always use nautilus to drag and drop the folder from the backed-up location to wherever you want.

Open two nautilus instances with 
```

ALT+F2

```
```

gksudo nautilus

``` 
```

gksudo nautilus

``` 

And drag and drop from/to wherever you want.

---

### Post by The Cog on 2007-11-26
Copying the entire /etc directory is probably not a good idea. It would be like copying the windows registry from ME to XW or XP to vista. I would expect it to break a great number of things. I can't even begin to know that would break or why, but I really don't think it's a good idea.

---

