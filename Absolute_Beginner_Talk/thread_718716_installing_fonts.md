---
title: "installing fonts"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Jabz.biz on 2008-03-08
Hi, 
I`m currently trying to install some more fonts. I looked through older threads of the forum but only founds some from 05-06. Seems a little to dangerous to trust them. 

I`m a complete noob to ubuntu, only using the UI. What i know so far is, that I can only install true type fonts (is that correct?!). The only question is, where can I put them? And how do I install them? Is it a copy/ paste job, like in windows?

Any hints, links,...are highly appreciated. 
Regards, Jab

---

### Post by jan quark on 2008-03-08
All fonts in Ubuntu are stored either in the directory

 /usr/share/fonts/   

 or in the directory

 /home/user/.fonts 

So all we have to do is to copy the font file into this directory. Type the following into the terminal

```
sudo cp -r font.ttf /usr/share/fonts/
```

---

### Post by st33med on 2008-03-08
Also, do this in the terminal to install these fonts if you want some (*gasp*) MS fonts:
```
sudo apt-get install msfonts-core
```

(I THINK it is msfonts-core, I cannot remember....)

---

### Post by Jabz.biz on 2008-03-08
thanks a billion for your help. 
Regards, Jab

---

### Post by steveneddy on 2008-03-08
> **st33med said:**
> Also, do this in the terminal to install these fonts if you want some (*gasp*) MS fonts:
```
sudo apt-get install msfonts-core
```

(I THINK it is msfonts-core, I cannot remember....)

```
suto apt-get install msttcorefonts
```

---

### Post by Tteddo on 2008-03-08
I also just copied all the fonts over from my windows partition to the aforementioned directories, they all seem to work fine.
For Wine you have to put them in your /home/username/.wine/drive_c/windows/fonts folder.

---

### Post by acidsolution on 2008-03-08
after copying fonts to /home/user/.fonts 
run this command on terminal
```
fc-cache -fv
```this should work for you

---

