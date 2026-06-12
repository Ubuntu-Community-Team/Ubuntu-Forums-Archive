---
title: "ffmpeg screencasting issue - please read"
date: 2012-09-26
forum: Any Other OS
---

### Post by nikonian on 2012-09-26
Hello my good friends :-)

I have been using this script for AGES on Ubuntu, but suddenly, now I am using Linux Mint 13, it throws an error. Here is the script:

```


#!/bin/bash

ffmpeg -f alsa -ac 1 -ab 192k -i pulse -acodec pcm_s16le -f x11grab -r 15 -s 1280x1024 -i :0.$1 -r 15 -s 1280x1024 -sameq -aspect 5:4 -vcodec libx264 -vpre lossless_ultrafast -threads 0 $2.mkv

```

Here is the error message I see, when I run './screencast 0 output' :

```

Unrecognized option 'preset'
/usr/share/avconv/libx264-lossless_ultrafast.avpreset: Invalid option or argument: 'preset=ultrafast', parsed as 'preset' = 'ultrafast'

```

Does anyone know what the issue I am seeing, is? 

Thank you! :)

---

### Post by oldos2er on 2012-09-26
Moved to Other OS/Distro Talk.

---

### Post by nikonian on 2012-09-26
Fixed it!

Modified script :-)

```


#!/bin/bash

ffmpeg -f alsa -ac 1 -ab 192k -i pulse -acodec pcm_s16le -f x11grab -r 15 -s 1280x1024 -i :0.$1 -r 15 -s 1280x1024 -sameq -aspect 5:4 -vcodec libx264 -preset:v ultrafast -threads 0 $2.mkv


```

---

