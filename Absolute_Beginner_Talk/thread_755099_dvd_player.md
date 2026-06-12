---
title: "dvd player"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by jwalters on 2008-04-14
Since moving to Hardy Heron........neither VLC nor Movie Player will play or even read dvd. ........any help?

---

### Post by SlappyPappy on 2008-04-14
Do you upgrade or fresh install to Hardy?

---

### Post by pseudo-random on 2008-04-14
Have you installed the libCSS codecs for copy protected DVD's?

---

### Post by jwalters on 2008-04-14
I upgraded...........no  to install question.

---

### Post by jwalters on 2008-04-14
I recieved this message after loading everything I could find....could not play this media although a plug in is present to handle it.........??

---

### Post by stchman on 2008-04-14
> **jwalters said:**
> Since moving to Hardy Heron........neither VLC nor Movie Player will play or even read dvd. ........any help?

You need to install the appropriate CODECs.

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Once this is done you then need to then install the Medibuntu repos.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and look under Hardy.

After that install the libdvdcss2 package.

```
sudo apt-get install libdvdcss2
```

You will then be a DVD playing fiend encrypted or not.

---

### Post by jwalters on 2008-04-14
ok I have a picture, but no sound........the volums up everywhere I know to look ,but still no sound :(

Thanks for getting me this far.......

---

