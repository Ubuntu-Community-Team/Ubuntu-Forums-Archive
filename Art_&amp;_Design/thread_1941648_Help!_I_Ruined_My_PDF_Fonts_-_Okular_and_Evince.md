---
title: "Help! I Ruined My PDF Fonts - Okular and Evince"
date: 2012-03-16
forum: Art &amp; Design
---

### Post by marseille on 2012-03-16
Hello...

I have no idea what I've done but my fonts were perfect before I decided to add more.

I ruined Okular and Evince but -- out of curiousity -- installed Pdfedit and noticed that Pdfedit is FINE :confused:

What have I done to my beautiful Okular:(

- - -

P.S. I already tried to going to `Appearances >> Fonts' but that didn't do anything. I've updated the font-cache... and now I'm stuck. Advice much obliged!

---

### Post by mraandtux on 2012-03-16
Try Konqueror? Foxit? xPDF?

---

### Post by marseille on 2012-03-16
Thank-you for being up on it mraandtux! That's why I love this forum! 

I think my panicking lit a fire under the *you know what* and I found the culprit... *after* freaking out (of course).

I may as well share since this was a pain that dragged out all week.

I got font happy over at Open Font Library [[http://openfontlibrary.org]](http://openfontlibrary.org]) and installed `Times Gothic', then completely forgot since I installed a ton of fonts for desktop publishing.

It didn't show up when I did this:

```

$ fc-list : file family | grep -i 'times.*new'
/usr/share/fonts/truetype/msttcorefonts/times.ttf: Times New Roman
/usr/share/fonts/truetype/msttcorefonts/timesbi.ttf: Times New Roman
/usr/share/fonts/truetype/msttcorefonts/timesbd.ttf: Times New Roman
/usr/share/fonts/truetype/msttcorefonts/timesi.ttf: Times New Roman
```

So then I went back to Okular to looked at what fonts were NOT embedded and sure enough, Times Gothic had somehow been chosen for Times. 

Sad to say, I removed it but don't want to. Can I just rename the ttf files?


PS... maybe I should have done this?

```
$ fc-list : file family | grep -i 'times.*'
```

I dunno but suggestions welcome.

---

