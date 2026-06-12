---
title: "VCD (Kinda Off-Topic)"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Malodorous on 2006-01-15
How do I make a VCD in Linux?

---

### Post by kabus on 2006-01-15
If you don't mind using the command line you could do it like this :

First install vcdimager and cdrdao
```

sudo apt-get install vcdimager cdrdao
```

Then turn your mpg file into an vcd image

```
vcdimager yourmovie.mpg
```

And finally burn the resulting image

```
cdrdao write --device /dev/hdd videocd.cue
```

(replace /dev/hdd with your cd writer)

---

