---
title: "[SOLVED] Can I install Windows fonts in Open Office?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by sdim on 2007-08-30
Hi,everyone.
Just wondering: Can I add fonts to Open Office,and especially fonts from Win XP (i.e.Times New Roman,etc.),since I've gathered a few over the years and are handy to me because of my job?
If yes,what's the way to do this?

Thank you.

---

### Post by schorsch on 2007-08-30
Have you already installed the package "msttcorefonts"`
```
sudo apt-get install msttcorefonts
```

---

### Post by sdim on 2007-08-30
Thanks for answering.
No.Never heard of it.
Does it provide Win fonts so that when I write a text in my Windows partition ,I am able to read it in my Ubuntu partition?

---

### Post by gn2 on 2007-08-30
If you search for "ttf fonts" in Synaptic Package Manager you will find lots of additional font sets you can install.

---

### Post by sdim on 2007-08-30
Thank you.
Installed the proposed package and indeed,there are some Win fonts in Open Office.Can we add more?

---

### Post by sdim on 2007-08-30
One more question: I have a file with lots of Win fonts (downloaded independently),which all have the extension _.ttf_.Can I install any of them in Open Office?

Thank you.

---

### Post by hyper_ch on 2007-08-30
You can install .ttf install...

just copy them as sudo to  /usr/share/fonts/truetype/   --> they should then be available.

---

### Post by schorsch on 2007-08-30
I never did it before but it should be possible by using "defoma" (Debian Font Manger) to add some fonts. You should read the man page for "defoma" to get more hints.

---

### Post by sdim on 2007-08-30
Thank you both.
To:hyper_ch-->you said copy them as sudo.How can this be done? I've no real experience in this.

---

