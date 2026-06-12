---
title: "[SOLVED] How do I start xserver with -scanpci option?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-04-09
In researching a problem I am having, I went directly to the xorg documentation.  It mentions there that to really determine the busid of my video card I need to start the server with the -scanpci option.  Since this is general xorg documentation and not Ubuntu-specific, can someone tell me how to do this in Ubuntu?  I tried startx -scanpci but that doesn't work -> it thinks it's an option for xterm and blows out.

Thanks!  :)

---

### Post by kebes on 2008-04-18
> **anewguy said:**
> to really determine the busid of my video card I need to start the server with the -scanpci option.

There are three ways to determine the video card busID (see also some info [here]("http://en.wikibooks.org/wiki/MythTV/Installing#Configure_TV-out")):
```

Xorg -scanpci
```
or
```

sudo scanpci
```
or
```

lscpi

```

Using lspci, for instance, look through the output and find the listing for your graphics card (which will of course depend on the make and model). The numbers at the start of that line give you (in hexadecimal format), the BUS ID, then the card number, then the function number.

I don't know exactly what you need the numbers for, but you can then convert them into the format you need.

Hope that helps.

---

