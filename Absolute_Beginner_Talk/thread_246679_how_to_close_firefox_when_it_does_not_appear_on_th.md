---
title: "how to close firefox when it does not appear on the screen"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2006-08-29
Hi,
I closed firefox in a awkward way and it disappered. when I click on the browser symbol at the top it gives the following error message:
"firefox is already running, but is not responding. To open a new window, you must first close the existing firefox process, or restart your system"

I run ps command in the terminal window but it did not list firefox process.
How could I stop the service from the terminal window.
Thanks alot.

---

### Post by PPAAUULL on 2006-08-29
Perhaps a "kill" command????

---

### Post by BlueStreak on 2006-08-29
try ps -e  

this will show all running processes whereas ps only shows processes running from within that terminal.

I think you know the rest but find the process id for fire fox and do kill xxxxx

---

### Post by Klaidas on 2006-08-29
```
killall firefox-bin
```

---

### Post by Toxicity999 on 2006-08-29
killall firefox-bin
if that doesn't work just restart, though... there's no reason it shouldn't work.

---

### Post by chuckyp on 2006-08-29
System > Administration > System Monitor 

That will bring up an app similiar to hitting ctrl+alt+del in windows.  You can see runing processes and kill them etc....

This would be a graphical way.  The other people mentioned using a kill comand this would be done through a terminal.

---

