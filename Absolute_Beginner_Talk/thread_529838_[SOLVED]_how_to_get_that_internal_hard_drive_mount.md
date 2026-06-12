---
title: "[SOLVED] how to get that internal hard drive mounted on every boot"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-08-19
for a long time now i have been trying to get my 80 gig NTFS /hdc drive mounted on boot up. i have read thread after thread on how to do CLI (command line interface) commands to make it work.

Nothing has worked.


Till this morning.

Out of sheer frustration and last ditch hope i went to "applications" and scrolled to "add remove"

click on "show all available apps"

now search and find a program called "storage device manager"
now install it.
after it is installed, to find it go to "system -> administration"
find storage device manager and open it.
now pick the hdd you want to be auto mounted on the left side.
on the right side the hdd will probably be unmounted like mine was. click on the button that says "mount" then click on default.

Thats it!

Restart your pc and everytime you restart it is going to be there, no mucking round, no jumping thru hoops, no cli , IT JUST WORKS!

Hope this helps a few others who are in the same boat as me.

---

### Post by carloslosgrande on 2007-08-19
[FONT="Comic Sans MS"]Hey Stinger, that works great! thanks man.[/FONT]

---

### Post by stinger30au on 2007-08-20
glad to help out. this little "quirk" has had me going for ages. hopefully others will find it and use it as well

---

### Post by rspaulding on 2007-09-03
I am trying to use this method but I can't do anything with the HD's that I want to mount, all the options are grayed out:

[IMG]http://img65.imageshack.us/img65/8977/screenshotstoragedeviceaf8.png[/IMG]

:confused:

---

### Post by carloslosgrande on 2007-09-03
Hi, I'm a little confused that your drives are showing without partitions? Other than your IDE drive.
When I select, say, sdb1 a message tells me that it isn't configured, it'll ask me if I want to configure it. Then you can do whatever.

---

### Post by rspaulding on 2007-09-04
anyone know what my problem might be?:confused:

---

### Post by carloslosgrande on 2007-09-04
[FONT="Comic Sans MS"]This is a solved thread, I think you'll have more success if you post your own thread.
It seems like your IDE drives are fine but your SATA drives/flash? are not configured?
But one thing I'm not, is an expert.[/FONT]

---

