---
title: "Floppy Formatter stopped working"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by PhilJ on 2006-01-10
Hi all,                        PROBLEM SOLVED
    last night it was working and I formatted some floppies. Today it doesnt. All I get is a message .
CANNOT INITIALISE DEVICE
Unable to open any device formatting cannot continue

I can format from a terminal with  fdformat /dev/fd0
and the floppy is present if fstab and I can mount it and umount it but nothing doing with floppy formatter. 

Anyone any ideas, Ive looked thru the forum but cant seem to find an answer ?

thanks

philj

---

### Post by L Campbell on 2006-01-10
[QUOTE=PhilJ]Hi all,
    last night it was working and I formatted some floppies. Today it doesnt. All I get is a message .
CANNOT INITIALISE DEVICE
Unable to open any device formatting cannot continue

I can format from a terminal with  fdformat /dev/fd0
and the floppy is present if fstab and I can mount it and umount it but nothing doing with floppy formatter. 

Anyone any ideas, Ive looked thru the forum but cant seem to find an answer ?

thanks

philj[/QUOTE]

Have you tried a different floppy, or tried the current one in another computer?

Good luck.

---

### Post by PhilJ on 2006-01-11
Hi,
yes have tried a swap  and its OK.
 Also tried about half a dozen floppies from a new box and can format them all from the terminal

philj

---

### Post by PhilJ on 2006-01-11
OK found it,

sudo gedit /etc/groups

add 'hal' (without quotes) to floppy

save

sudo gedit /etc/modules

add 'floppy' (without quotes)  to end of list

save

this adds floppy to list of modules to be loaded at startup
reboot and floppy formatter should work again

philj

---

### Post by az on 2006-01-11
I had to install pmount from backports yesterday, on an older machine because of a bug which caused this.

I could not browse a floppy either (Wrong URI message or something)

Now it works!

---

