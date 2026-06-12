---
title: "wine help"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by GonZo1323 on 2006-09-01
ok i installed wine the i installed aim in there
now how would i go about opening aim or wine???
i cant find it anywere

---

### Post by pyros on 2006-09-01
just type "wine /the/folder/where/aim/installed/aim.exe" (without the quotes) into a run prompt or terminal and press the enter key.

---

### Post by davmac on 2006-09-01
...and if that doesn't work you might need to open up a terminal window (application/accessories/terminal) and type "winecfg" and set the various options for how you want wine to behave.

Dave Mac

---

### Post by GonZo1323 on 2006-09-01
when i do that it just says cant find module and im sure were i installed it
wine c\program files\aim.exe

---

### Post by GonZo1323 on 2006-09-01
> **davmac said:**
> ...and if that doesn't work you might need to open up a terminal window (application/accessories/terminal) and type "winecfg" and set the various options for how you want wine to behave.

Dave Mac

tried that but it still wont oepn up aim

---

### Post by lynxus on 2006-09-01
Use GAIM rather than trying to wine aim.

---

### Post by hanzomon4 on 2006-09-01
Found this.

> **kripkenstein said:**
> To install aim in wine (that is, inside wine's fake windows C drive), just download the aim installer, and run it in wine. It should install ok (but not all software does).

It is then installed in the fake wine drive, under .wine in your home directory. Btw, you can navigate that drive conveniently (and run programs from it) using the wine file manager, run 'winefile'. Then on the top you can tell it to look in your "C" drive, this is the fake windows drive inside wine.

But only wine aim if gaim doesn't work.

---

### Post by Anonii on 2006-09-01
> **GonZo1323 said:**
> when i do that it just says cant find module and im sure were i installed it
wine c\program files\aim.exe
Ok, did you know that by typing half the name of a directory and then pressing the "Tab" button you will get the full name? Try it, and by using that trick get in this directory:

_cd ~/.wine/drive_c/Program Files/_
(Program Files, has a space and you will have to use Tab to access it.)

Find the AIM directory, by using the command:
_ls_
and get into it:
_cd <name_of_the_AIM_directory>_
Then use the ls command again to find the .exe that opens AIM:
_ls_
and use:
*wine <exe_filename>.exe*

If you didnt understand something, tell me what.
[COLOR="White"]
(Yes I know that you can access directories with spaces like this:
Program\ Files/. But learning how to use Tab, is better :] )[/COLOR]

---

### Post by GonZo1323 on 2006-09-01
this is way 2 much work to just get a couple files from one computer to the other, i tried setting up samba but idk my windows sn or password:x

---

