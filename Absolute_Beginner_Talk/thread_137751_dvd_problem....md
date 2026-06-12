---
title: "dvd problem..."
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-02-28
I can't play any dvd's on totem player. I installed the multimedia codecs using automatix. Here is the error that i get when I try to play a dvd.

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

Does anyone know how to fix this.

---

### Post by taurus on 2006-02-28
Well, just install libdvdcss (and perhaps libdvdcss2) then!!!  Also, I find either xine or vls works much better with movies on DVDs...

---

### Post by grim918 on 2006-02-28
I thought that Automatix already installed the codecs. Where do I go to get the codecs that I need.

---

### Post by taurus on 2006-02-28
You can use either synpatic (use the Search to find the package) or from a terminal as

```

sudo apt-get install libdvdcss libdvdcss2

```

---

### Post by taurus on 2006-02-28
You can use either synpatic (use the Search to find the package) or from a terminal as

```

sudo apt-get install libdvdcss libdvdcss2

```

---

### Post by grim918 on 2006-02-28
ok thank you i got it working. The movies play a little slow though. Do you know of a way to make dvd movies play more smoothly. The sound plays good but the movie just looks choppy. Thankz again for  the help.

---

### Post by Coelocanth on 2006-02-28
You may need to enable DMA. [Go Here](https://wiki.ubuntu.com/DMA) to see about the procedure to do that.

---

