---
title: "CheckGmail"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-01-14
Hi,

I have installed CheckGmail from synaptics.  I also installed the crypt-simple set so that my password is encrypted.  Everything works great.

I have set up checkgmail under system-preferences-sesssions-startup programs to start on startup.

When I type "checkgmail" into terminal, the program opens in the system tray, but as soon as I close terminal the program closes.  Why is this happening?

---

### Post by mykalreborn on 2007-01-14
because that's just the way it works. i dunno if you can bypass that.
instead you can make a launcher.
right-click on the desktop and choose create launcher. give it whatever name you please and in the command section type "checkgmail".
and you can also put an icon for the launcher

---

### Post by capitalistpiglet on 2007-01-14
if you want to run this program from the command line then type ```
checkgmail &
```

---

### Post by brandoncolorado on 2007-01-14
> **mykalreborn said:**
> because that's just the way it works. i dunno if you can bypass that.
instead you can make a launcher.
right-click on the desktop and choose create launcher. give it whatever name you please and in the command section type "checkgmail".
and you can also put an icon for the launcher

Is is possible to make it stay open though?  I guess I don't see how this is useful if you have to leave the terminal open all the time.  I would like a notifier that works like the gmail notifier in Windows so you can be doing other things and it tells you when you have email.

---

### Post by mykalreborn on 2007-01-14
> Is is possible to make it stay open though? I guess I don't see how this is useful if you have to leave the terminal open all the time. I would like a notifier that works like the gmail notifier in Windows so you can be doing other things and it tells you when you have email.
 you can install automatix and install gmailchecker from there. it'll work like a charm. reply if you need help on installing it. and say what ubuntu you have, 6.06 or 6.10

---

### Post by rfruth on 2007-01-14
I use the Google toolbar, makes checking gmail easy :) 

[http://www.google.com/tools/firefox/toolbar/FT3/intl/en/](http://www.google.com/tools/firefox/toolbar/FT3/intl/en/)

---

### Post by brandoncolorado on 2007-01-14
> **mykalreborn said:**
> you can install automatix and install gmailchecker from there. it'll work like a charm. reply if you need help on installing it. and say what ubuntu you have, 6.06 or 6.10


Thanks, I have installed Automatix and am in the process of installing tons of stuff found in it.  Great piece of software.  Does Automatix automatically update with the rest of Ubuntu?

---

### Post by mykalreborn on 2007-01-15
> Does Automatix automatically update with the rest of Ubuntu?
if you installed it properly, added the repository list, yes. but it's not going to put other programs or anything like that in the list, if that's what you're thinking

---

### Post by jordanmthomas on 2007-01-15
You could also launch it by pressing Alt + F2 and typing
```
checkgmail
```

---

### Post by macogw on 2007-01-15
nohup checkgmail &

it'll say it's appending output to nohup, then you can hit the X and it'll keep running

---

### Post by orb9220 on 2007-01-15
Or like me just add it to startup programs in session manger. So it will startup automatic to sys tray.

No fuss.

---

### Post by clantoncs on 2007-01-15
orb9220 is spot on.  Add it to your startup programs through your top menu bar (at least for gnome):

system-> preferences-> sessions-> 
then add it under the startup programs tab with 'checkgmail' (as you know).  

I'm sure this is reply is redundant, but I think the ubuntuguide website should really add a howto on checkgmail.  That startup tab can be a bit hidden for us newbies, remember!

---

### Post by brandoncolorado on 2007-01-15
Thanks everyone.  Resolved.  The Automatix installation made it work perfectly.  Thanks.

---

