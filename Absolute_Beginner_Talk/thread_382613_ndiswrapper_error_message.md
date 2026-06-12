---
title: "ndiswrapper error message"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Griffiss on 2007-03-12
Hi, when i type ```
ndiswrapper -v
```

I get this error message:

```
utils Error: no version specified!
```

might this have something to do with my wireless not working?

---

### Post by cyberdork33 on 2007-03-12
I believe you need to install the ndiswrapper-utils package from apt before you can use ndiswrapper.

---

### Post by Griffiss on 2007-03-12
I've installed ndiswrapper-utils-1.8. It was on the ubuntu cd. I don't have an internet connection from the computer that I have ubuntu on so I can't download a more recent version - actually I have a dual boot on it with windows xp which can connect, so if I can download it ondo the windows partition and then shlep it over to ubuntu then it might work... but I don't know how to do that..

---

### Post by Bachstelze on 2007-03-12
Then, whenever istructions tel you tu use the *ndiswrapper* vommand, use *ndiswrapper -1.8* instead. For example

```
ndiswrapper-1.8 -v
```

---

### Post by Griffiss on 2007-03-12
Hi HymnToLife

I tried that - I removed ndiswrapper using synaptic and reinstalled using ```
sudo apt-get install ndiswrapper-utils-1.8
```
then reinstalled the driver, consistently using ndiswrapper-1.8, but the same error message came up when i typed ```
ndiswrapper-1.8 -v
```

---

