---
title: "Live CD: blank screen in Asus Laptop"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by beagle on 2006-01-03
I prefer to test with Live CD, before installing Ubuntu.  Therefore, I downloaded 'Ubuntu-5.10-Live.iso' and burnt a CD.  Made sure the the CD is good by testing it in my desktop.
When I try to boot my Laptop with Ubuntu-live-CD, it seems to unpack and setup the file systems; but in the end, I get a blank screen. :( 
Next, I booted the Laptop with Knopix-4.0.2-live CD and it worked fine.
Thanks in advance for any tips to get the Ubuntu-live to work.

The following is my hardware info:
Asus M6B00N
Intel Centrino M, 1.7Ghz
512Mb RAM
Video: ATI9200

---

### Post by daller on 2006-01-03
Use this as a boot argument:

```
linux vga=771
```

Does that work?

---

### Post by beagle on 2006-01-03
[QUOTE=daller]Use this as a boot argument:

```
linux vga=771
```

Does that work?[/QUOTE]

Tried 'linux vga=771' and 'vga=771'
Both arguments gave the following error:
"Could not find kernel image: linux".

---

### Post by daller on 2006-01-03
[QUOTE=beagle]Tried 'linux vga=771' and 'vga=771'
Both arguments gave the following error:
"Could not find kernel image: linux".[/QUOTE]

Maybe it's:

```
live vga=771
```

...haven't used a livecd!

---

### Post by beagle on 2006-01-03
[QUOTE=daller]Maybe it's:

```
live vga=771
```

...haven't used a livecd![/QUOTE]

That's it. :D 

Thanks a lot.

---

