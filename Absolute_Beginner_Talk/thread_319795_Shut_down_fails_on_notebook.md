---
title: "Shut down fails on notebook"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Erunno on 2006-12-16
Hi all,

I'll come right to the point if nobody minds the lack of courtesy ;)

I'm running Ubuntu 6.10 on a Toshiba Satelllite notebook ( I don't know which one, it was a gift and the documentation was lost but it's over 3 years old by now). Whenever I try to shut down the notebook from the gnome menu I can see the Ubuntu logo and the progress bar for a couple of seconds. The progress bar freezes midway, the logo disappears along with the bar and all that is left is a black screen with an underscore in the top left corner. As the notebook is unresponsive after that I have to power it down manually.

This behavious is pretty annoying as Ubuntu has to restore the journal each time and I doubt that this is good for my personal data in the long run.

So, my apologies if the problem has been reported already but I couldn't find a topic which matches my problem exactly.

Does anybody have any experiences with dealing with this problem ?

Cheers,
Erunno

---

### Post by xyz on 2006-12-16
Just a thought, what happens when you run:
```
shutdown -h now
```

---

### Post by xyz on 2006-12-16
Just found this:

```
sudo gedit /etc/modules
```
ADD:
> apm power_off=1
AND:
```
sudo gedit  /etc/lilo.conf
```
ADD:
> append="acpi=off apm=power_off"
by **<=Kross=>** on ubuntuforums.

---

### Post by Erunno on 2006-12-16
It worked ! :) 

Thank you very much.

---

