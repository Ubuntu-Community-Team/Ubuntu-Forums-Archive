---
title: "Double click to close windows"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by tatare99 on 2006-09-19
Dear all,

I'm quite new to Ubuntu (Dapper). Everything's fine :KS 

I'd just like to know, in Gnome, if it's possible to close a window by double clicking on the icon located at the top left corner of the window... yeah, well, just like in MS Windows actually :rolleyes: 
I'm not used to click on the "X"... do you know if there is a way to make this window's behavior possible, and if yes, how ?

Thanks a lot in advance for your answers ! :) 
Francois.

---

### Post by gborzi on 2006-09-19
Open the gconf-editor and select the /apps/metacity/general/button_layout entry. Its current value should be something like "menu:minimize,maximize,close" which means that on the left you have the menu button, and on the right the minimize,maximize,close buttons. Change this value to have the required button layout, e.g. on my system I use "close,maximize,minimize:menu". Please note that the close button works with a single click.

---

### Post by tatare99 on 2006-09-19
Thank you, gborzi, for your answer  ! :-)
I guess I understood your answer.
So actually, there is no solution for double clicking on the menu to close the window?

Anyway, thanks again for the answer !

---

