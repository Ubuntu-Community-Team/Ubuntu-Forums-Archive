---
title: "menu.lst timeout load sequence?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-07-31
i've begun tweaking the menu.lst file, but everyone says you can "change the timeout to 10 seconds or 3 seconds" I understand that is the timeout to select a boot option before the default loads,...but how do you select a boot option?  

also in menu.lst, 
what does changing "default" from 0 to 1 do?

thanks.

---

### Post by johntkucz on 2007-07-31
also, how do I know for sure if my windows xp internal drive is ntfs (I assumed it is)?

---

### Post by Burgerbreath on 2007-07-31
I assume that your first question has to do with selecting the default boot option right? To do this count down the "titles" in your menu.lst starting from 0 until you reach the desired boot. Then use that number and set "default" from 0 to whatever number you got. 

Default should do what you are asking for as stated above^. 

Hope this helps.

---

