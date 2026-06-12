---
title: "Best way to key/alpha photos taken in green/blue screen in GIMP?"
date: 2011-07-30
forum: Art &amp; Design
---

### Post by OrangeVixen on 2011-07-30
What is the best way to key photos taken in a green screen or blue screen (key green or key blue) in GIMP?

I'm aware of the "Select by Color" tool, but I need a plugin or some one-pass tool/filter that I can use that will:

Alpha the background
Reduce spill/throwback green or blue
Adjust "noise" and transparency from spill/throwback

Something similar to Final Cut Pro's Motion 4 Primatte RT filter.

---

### Post by earlycj5 on 2011-07-31
Colors > Color to Alpha?

---

### Post by jasonrisenburg on 2011-08-01
[http://www.nebomusic.net/chromakey.html](http://www.nebomusic.net/chromakey.html)

---

### Post by jasonrisenburg on 2011-08-01
I wish there was like buttons in here.

---

### Post by prokoudine on 2011-08-02
Did you try [Foreground selection]("http://docs.gimp.org/en/gimp-tool-foreground-select.html") tool? In my experience it works very well on more or less solid backgrounds.

There is a GEGL operation for matting, but it doesn't have a nice UI yet, so I wouldn't recommend it to a GIMP newbie, especially when you need to process pictures with alacrity :)

---

