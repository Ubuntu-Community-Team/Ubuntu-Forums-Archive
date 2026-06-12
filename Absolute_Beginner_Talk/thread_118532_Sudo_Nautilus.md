---
title: "Sudo Nautilus"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by Edho on 2006-01-17
Had to manual copy plugins in a folder ...opera/plugins
According the giving instructions it's only possible with the sudo in terminal...
(a lot of textwriting)

I thougt...  let's try it with the filebrowser.
So first in terminal , Sudo Nautilus...
Then i can copy to the normaly closed folder with the mouse.


I did'nt realise that until now.
Maybe a tip for other beginners.


Edho

---

### Post by 23meg on 2006-01-17
You can also hit alt+f2 and type ```
gksudo nautilus
```

---

### Post by Gustav on 2006-01-17
If you use that a lot it's a good idea to create a launger that runs 'gksudo nautilus'.

I did that but I rarely use it since i like the terminal better.

---

### Post by 23meg on 2006-01-17
You may also find [this trick]("http://www.ubuntuforums.org/showthread.php?t=24008") useful.

---

### Post by Edho on 2006-01-17
Wow !
23 meg
It works fine !  (only with the loop-thing.)

Thanks.

---

### Post by 23meg on 2006-01-17
What's the loop-thing?

---

### Post by Edho on 2006-01-17
The for-do in the script....

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gnome-sudo "gnome-open $uri" &
done

---

### Post by 23meg on 2006-01-17
Oh right; I thought you were referring to the icon method.

---

### Post by hen3rz on 2006-01-17
> You may also find this trick useful.
Sweet tutorial. This is alot easier then the right click menu. Thank you.

---

