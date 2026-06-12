---
title: "HOWTO: An HDR-like effect w/ ImageMagick"
date: 2008-03-08
forum: Art &amp; Design
---

### Post by timbounceback on 2008-03-08
I wrote a script recently that takes an existing image and adds an effect to make it look like an HDR photo (via a Gaussian blur). It requires ImageMagick. I would post a before and after, except the image I used was from Flickr and I don't remember the license. Anyway, copy and paste the following into mkhdr.sh:```
convert -gaussian $1 $2 - | composite -compose overlay $2 - $3
```Now run ```
./mkhdr.sh [gaussian blur radius] [input file] [outputfile]
```I found that a number around 2-3 works well for the Gaussian blur radius. You can also do this in GIMP, but I prefer the command-line :). Oh, and I was originally going to put this into the tutorials section, but it didn't seem on-topic enough, so I posted it here instead. Please move if neccesary.
Enjoy!

---

### Post by delmore on 2010-04-29
Awesome! I didn't notice much difference in the amount of blur I added. In fact, browsing through the tests I just ran in feh, there is no discernible difference between '-gaussian 2' and '-gaussian 50'

Perhaps this could be tweaked? Maybe I'm doing it wrong.

Either way, it looks great regardless of the blur amount... Been using it on grainy black and white photos and still looks great

---

