---
title: "desktop background"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by clitmaster on 2007-08-13
hey I want to set it up so that my desktop background is periodically changed between images in my 'wallpapers' folder. 

Is this possible? how would I do this?

---

### Post by olejorgen on 2007-08-13
You could try **wallpaper-tray**.

.. or hack your own solution.
Here is a simple script that will change your wallpaper (in gnome):
```

#!/bin/bash

modes=" none wallpaper centered scaled stretched zoom "
mode="stretched"

if [ $2 ]; then
        if [ "${modes/[ ]$2[ ]/}" != "$modes" ]; then
                                mode=$2; 
        else
                echo "Invalid mode. ($modes)"
                exit;
        fi
fi
echo $1
gconftool -t string -s "/desktop/gnome/background/picture_options" "none"
gconftool -t string -s "/desktop/gnome/background/picture_filename" "$(realpath "$1")"
gconftool -t string -s "/desktop/gnome/background/picture_options" "$mode"

# Determines how the image set by wallpaper_filename is rendered. Possible values are "none", "wallpaper", "centered", "scaled", "stretched", "zoom".

```

---

### Post by clitmaster on 2007-08-13
oh awesome! wallpaper-tray will do the trick, thanx ;)

---

