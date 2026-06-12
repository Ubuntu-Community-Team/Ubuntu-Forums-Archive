---
title: "IMPORTANT- what the heck happened to firefox and pidgin?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Smatt454 on 2008-02-25
Hello all. this ones serious

********PLEASE NOTE I AM RUNNING KUBUNTU 7.10, NOT UBUNTU*********

firefox and pidgin (my instant messaging service) too a crap. like literally i was running both, they died and wont re open.

of course i restarted. kdm wouldnt start. i fixed that and everythings fine exept firefox and pidgin wont start. i tried reinstalling firefox but it's no go. here's the error message i get when i run firefox from a terminal 
> /usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl

pidgin gets a similar error.  

i dont know it this is related,  but KNetwork manager shows the little unplugged symbol and when i right click it it says it's not running. I'm using wifi atm and i have an Ethernet card installed but not in use.  My Teacher (an avid Linux user) says that it's because one of my network interfaces is unplugged (that doesnt make sense to me, especially since it always showed that it was plugged in before when i was using my wifi)

EDIT: 
FUN FACT-  I am using Konqueror as my web browser atm

---

### Post by luisito on 2008-02-25
Both Firefox and Pidgin are GTK+ based. If you're running KDE probably all the other programs you use are not. Can you run any GTK+ based application?

I wouldn't know how to solve the problem anyway. How did this happen?

---

### Post by Smatt454 on 2008-02-25
i dont think i can

and it just...stopped working. like spontaneous

---

### Post by crf on 2008-02-26
As a test, try renaming /usr/local/lib

---

### Post by Smatt454 on 2008-02-28
hmmm, i dont seem to have any of my libgdk-x11 libraries...how do i get them back??

---

