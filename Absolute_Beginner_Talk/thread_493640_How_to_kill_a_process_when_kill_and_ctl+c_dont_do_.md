---
title: "How to kill a process when kill and ctl+c dont do the trick???"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-07-05
so i was runnin zsnes... and it locked up, no big, save states are great.

i try to close the window, but it wont close... no problem i think, a simple pidof zsnes and sudo kill pid should do the trick. nope... killed the rom that was locked up but the process (using the same pid, 4881) still running.

ok, ill try the good ol control+c in the terminal thats running it to interupt and cancel it... still no luck... now i affectively have a black window almost the size of my desktop that just wont go away... it will minize and shade, but it just wont close or die

im sure a reboot would fix this problem, but i was wondering if anyone had any other ideas or options up thier sleeve

---

### Post by Adramelech on 2007-07-05
kill -9 pidofprogram

---

### Post by Nythain on 2007-07-06
ok, so that did the trick... whats teh -9 do extra anyways... and you'd think id know this info being a fan of monzy and his song kill dash nine

---

### Post by deadlikeoscar on 2007-07-06
Type "man kill" in the terminal if you want the long answer.;)

---

### Post by Adramelech on 2007-07-06
-9 tells what signal is going to be send to the process.

signal number 9 is KILL, the default signal is 15 TERM that fails to close process sometimes.

For more information:

man kill

---

### Post by Nythain on 2007-07-06
thanks for the actuall answer... reading man pages is sometimes more complicated than doing a tune up on a lincoln navigator

---

### Post by Old Pink on 2007-07-06
If you're looking to quickly get rid of a frozen window without finding the pid, and opening terminal...

[LIST=1]
[*]Hold Alt and tap F2
[*]Type **xkill** in the box at the top of the new dialog
[*]Hit return/enter
[*]Watch as your cursor becomes a skull and cross bones
[*]Click whatever it is that's annoying you. ;)[/LIST]

---

