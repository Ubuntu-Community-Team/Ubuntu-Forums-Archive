---
title: "Opening Programs with Wine"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by quinlo on 2008-04-03
I use wine as a windows emulator so I can use the microsoft office package. Is there anyway to choose the default program as excel to open files (such as document1.xls... an excel spreadsheet document).  When I try to choose the program to open it with it only gives me a list of linux apps not the apps I have through my WINE emulator....

---

### Post by Xiong Chiamiov on 2008-04-03
I'm not sure quite how gnome works, but if you can enter a command, do something like this:
```

env WINEPREFIX="/home/pearson/.wine" wine "C:\Program Files\Starcraft\Starcraft.exe"

```
obviously changing Starcraft to the path to MS Office.

BTW, is there any specific reason why you're using that instead of OpenOffice.org?

---

### Post by quinlo on 2008-04-03
I have a computer at work that uses windows and the microsoft suite and find it easier to just use the same program at home... I am not to familiar with open office... is it better in your opinion... does it have all of the same features as the micro office sweet?  Im pretty new to ubuntu.

I have actually tried that same code that you showed... it responded "could not add application to database."

---

### Post by Xiong Chiamiov on 2008-04-03
I personally like using OOo, though I haven't used Microsoft Office in ages.  As far as features, all I use it for is typing papers, but it does have quite a full feature set.

What about if you try a variation on
```

'/home/pearson/.wine/drive_c/CAVEDOG/TOTALA/totala.exe'

```

---

### Post by quinlo on 2008-04-03
I have a shortcut to microsoft word on my desktop ... a "launcher" if you will where the code is 

env WINEPREFIX="/home/adam/.wine" wine "C:\Program Files\Microsoft Office\OFFICE11\WINWORD.EXE" 

but entering that as the command to open yields the "could not add application to database."

I tried warping it to something like you had in your second post but to no avail...

Im not adept at this so perhaps I modified it incorrectly...

what is the exact code you would write?




p.s. I was planning on using micro office now to keep up with my job... but learn OOo on the side, I know they are compatible... I just need to learn how to wield the power of open source programs...

---

