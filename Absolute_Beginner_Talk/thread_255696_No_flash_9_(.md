---
title: "No flash 9 :("
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Imma Krout on 2006-09-11
Is there NO way to play flash 9 media such as the stuff on myspace in ubuntu? :-\"

---

### Post by jordanmthomas on 2006-09-11
You can run Firefox in Wine and then install Flash 9.
Here is a decent looking guide.  
I looked through the steps and it seems right.

[http://www.howtoforge.com/ubuntu_flash_player9](http://www.howtoforge.com/ubuntu_flash_player9)

---

### Post by Najand on 2006-09-11
Does it work when you install "flashplugin-nonfree" from "multiverse" repository?

---

### Post by jordanmthomas on 2006-09-11
It shouldn't.  Myspace uses Flash 9, and we Linux users only get Flash 7.

---

### Post by Najand on 2006-09-11
Oh, I see... I don't know much about Flash Player and Adobe who has bought the macromedia company, alot. I am so sorry.

---

### Post by jordanmthomas on 2006-09-11
That's nothing to be sorry over.

---

### Post by Imma Krout on 2006-09-11
Works!

Thanks so much. :)

---

### Post by H3HI on 2006-09-11
Open the file ~/.mozilla/firefox/pluginreg.dat ( or ~/.mozilla/pluginreg.dat )
change
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$

;)

---

### Post by jordanmthomas on 2006-09-11
Holy crap!  That actually works (at least for the one flash 9 video I tried)!

Thanks a bunch H3HI

---

### Post by motstudios on 2006-10-22
i tried this little trick and still cant view the vids on myspace :(

---

### Post by jordanmthomas on 2006-10-22
Well, now you can just install flash 9
```
wget http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz
tar xvzf FP9_plugin_beta_101806.tar.gz
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/ 
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/firefox/plugins/
```
restart firefox and bingo!

---

### Post by kerry_s on 2006-10-22
Grab the flash 9 beta, it works pretty good.

---

### Post by Drakkor on 2006-10-22
:)

---

### Post by flosoft on 2006-10-28
Great :) It worked like a charm :)

---

### Post by dillbertdabomb on 2006-10-28
go and get the flash 9 so file and put it in your firefox plugins folder!
works for me (kitten cannon here I come...)

---

