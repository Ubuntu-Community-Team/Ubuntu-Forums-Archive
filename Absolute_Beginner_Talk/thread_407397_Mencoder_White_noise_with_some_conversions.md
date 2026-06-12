---
title: "Mencoder White noise with some conversions"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by apjone on 2007-04-12
When I use mencoder to encode some video files to avi to play on my portable media player i get white noise all the way through. This only happens on some files. here is the code is use

```

#!/bin/bash
mencoder  -noodml $1 -of avi -o $2 -ofps 24 -vf-add scale=224:176 -vf-add
\ expand=224:176:-1:-1:1 -srate 44100 -ovc xvid -xvidencopts
\ bitrate=550:max_bframes=0:quant_type=h263:me_quality=4 -oac 
\ lavc -lavcopts acodec=mp2:abitrate=128

```

Could this be down to drm withing the original file i am trying to convert? Any help would be useful

Thank you

---

### Post by bmaxd on 2008-01-04
Set the audio bitrate for the output file to the same as the original.

---

