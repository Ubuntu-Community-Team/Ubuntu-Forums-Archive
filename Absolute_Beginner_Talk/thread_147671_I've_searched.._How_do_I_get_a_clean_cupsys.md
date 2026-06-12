---
title: "I've searched.. How do I get a clean cupsys ?"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by Danny Boy on 2006-03-20
I was trying to make my XP laptop see the printer that's on my Ubuntu box, I followed a tutorial on the wiki. I messed up the cupsys file. Now when I try to open the printer dialouge it says "the cupsys server could  not be found". 

I'm thinking since I edited /etc/cups/cupsd.conf that if I just replace it with what was originally there it won't be a problem. 

Do anyone know where I can get an orignal file? Or maybe where I can copy the text from?

Thanks a lot, 

Dan

---

### Post by mlind on 2006-03-20
Have you tried removing the cups packages with apt-get using --purge switch and
then installing those back again.

use dpkg -l 'cups*' to see all cups packages. Ones marked with 'ii' are installed.

---

### Post by Danny Boy on 2006-03-20
I'm not quite sure what you mean. I got a listing with the dpkg command, I removed a couple, but the full file names aren't showing for the other ones so I cannot remove them.

---

### Post by mlind on 2006-03-20
I don't really know how to use dpkg queries, but you can find cups packages
using Synaptic or plain apt-cache search for example.

```

dpkg -l 'cups*' | awk '{print $2}' 

```

prints the package names only, add  'grep ii' to get only installed ones.

you have to remove packages using *sudo apt-get remove --purge package_name*

---

### Post by Danny Boy on 2006-03-20
Thank you very much I had like 7 packages listed. I got a little download happy when I seen all the free software. :D

I purged all of them and used apt-get install cupsys and now I can get to the printer "control panel"

Thanks again guys, :)

Dan

---

