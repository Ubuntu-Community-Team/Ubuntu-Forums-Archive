---
title: "Hard drive light, go away!"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by tblehr on 2006-02-01
This is kinda weird, my hard drive light just stays on now since I installed Ubuntu.  Well, it stays on while i'm in Ubuntu, but goes off when I restart or go to windows....

I read another thread that talked about this too, but I never saw any solution.

Anybody know what might be causing this?

---

### Post by tblehr on 2006-02-05
Fixed it! :)

---

### Post by gerbman on 2006-02-05
[QUOTE=tblehr]Fixed it! :)[/QUOTE]

How?

---

### Post by tblehr on 2006-02-05
I have a IDE HDD and I have it converted to SATA.  So instead of having the light plugged into the motherboard, I plugged into the converter.  Bingo, it works! :)

---

### Post by nixclusive on 2006-02-05
[QUOTE=tblehr]I have a IDE HDD and I have it converted to SATA.  So instead of having the light plugged into the motherboard, I plugged into the converter.  Bingo, it works! :)[/QUOTE]
Sorry I had to post here :( But I have a serious problem now. I downloaded and installed a theme from gnome-look.org and got the error message when loading it:
There was an error loading the theme TuxZ12Ubuntu
Bad Stock label type

And when I click 'Ok' button I get a blue theme with a sunflower (?)
The loaded theme does not allow me to type a username and pass. Is there a way to fix this?

I'm using lynx text browser to post this message! Please mail replies to:
[email]nixclusive0@gmail.com[/email]

Ok I fixed it myself! Just edited the file /etc/gdm/gdm.conf and set:

Greeter=/usr/bin/gdmlogin

for the standard greeter...

---

