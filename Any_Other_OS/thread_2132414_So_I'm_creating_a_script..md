---
title: "So I'm creating a script."
date: 2013-04-04
forum: Any Other OS
---

### Post by WarBringer on 2013-04-04
Goal: have a window pop up at log in question what directory I want to use for my wallpapers.
Programs being used: lxterminal and two scripts 
First script named (currently) test2.sh
```

echo "Do you wish to install this program?"
select dl in "Dragons" "Landscapes"; do
    case $dl in
        Dragons ) export wallpaperDir=/home/lance/dragons; break;;
        Landscapes ) export wallpaperDir=/home/lance/landscapes; break;;
    esac
done

```
second script named wallpaper.sh
```

#!/bin/bash

shopt -s nullglob
lxterminal -e "bash /home/lance/test2.sh"
cd $wallpaperDir

while true; do
    files=()
    for i in *.jpg *.png; do
        [[ -f $i ]] && files+=("$i")
    done
    range=${#files[@]}

    ((range)) && feh --bg-scale "${files[RANDOM % range]}"

    sleep 15m
done

```
Only issue so far is that the variable doesn't get set but I've yet to test it to where these scripts get excuted at boot time by using the autostart script in the openbox directory.

---

