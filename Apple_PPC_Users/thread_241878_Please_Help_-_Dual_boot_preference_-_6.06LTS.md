---
title: "Please Help - Dual boot preference - 6.06LTS"
date: 2006-08-22
forum: Apple PPC Users
---

### Post by jez999ukdg on 2006-08-22
Hi everyone,
Im a newbie just getting into Linux, so far its been great! Really liking Ubuntu, only thing is, is that im now stuck... 

Basically i want to keep osx as primary boot, and at the moment if left alone it goes to ubuntu.  I promise you all that i have searched for the last 4 hours everywhere (it seems) to find an answer, but none seem to help me.  

I found that i need to edit /boot/grub/menu.lst but when i look for this it doesnt exist... - i have a boot directory but there's no further directories within...  :( am i doing something fundamentally wrong, for example is it because its hidden?  i have a very basic knowledge of linux. i do understand superuser stuff, (i think) but can anyone help out?

Also does anyone know if there are any issues with KDE working on a mac?

( i have a G4 PPC running Tiger )

Thankyou, and sorry if this is really basic, - didnt want to ask but im really stuck ...

---

### Post by jez999ukdg on 2006-08-23
Ok

Im sorry for all those checking this post, but i will offer the solution i found.

It seems that my Ubuntu (6.06) uses yaboot as a boot option thingy. what i had to do was:

1) goto /etc/yaboot.conf and edit it.
2) added the line- defaultos=macosx
3) save it and exit
4) then in terminal run - ybin -v

after rebooting it now works in the way i wanted... hope that helps somebody out there, as initially i couldn't find any solution... this took me a good 5hours or so of searching the net!!! oh well....

---

### Post by stmiller on 2006-08-23
Add these lines to your yaboot.conf for more booting options:

enablecdboot
enableofboot
enablenetboot

---

### Post by jez999ukdg on 2006-08-23
Hi stmiller

what do these other options do...?

cd boot - boot from cd - ok
of boot - ???
net boot - i'm guessing network boot?

cheers.

---

