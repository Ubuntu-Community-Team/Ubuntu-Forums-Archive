---
title: "ubuntu shows wrong graphics card and wrong soundcard driver"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by hempa on 2007-03-11
Hello i have some problems with my sound and with my graphics card. the soundcard problem that i have is that i have installed emu 10k1 but ubuntu still uses my old driver is there a script or a file somwhere that i can edit so that ubuntu starts to use emu10k1.

i also need to make ubuntu aware of that i am using a radeon X850 Xt graphics card because now it says that i am using a vesa card with a vesa driver how can i change this

---

### Post by Delvien on 2007-03-11
> **hempa said:**
> Hello i have some problems with my sound and with my graphics card. the soundcard problem that i have is that i have installed emu 10k1 but ubuntu still uses my old driver is there a script or a file somwhere that i can edit so that ubuntu starts to use emu10k1.

i also need to make ubuntu aware of that i am using a radeon X850 Xt graphics card because now it says that i am using a vesa card with a vesa driver how can i change this


check out an app called 'envy' it will install the correct driver for you

```
sudo aptitude install envy
```


Then

```
envy
```

---

