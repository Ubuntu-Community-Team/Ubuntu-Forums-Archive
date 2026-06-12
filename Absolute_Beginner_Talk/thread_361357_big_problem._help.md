---
title: "big problem. help"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-14
Okay, i've wanted to install a language pack and installed one (i had the automatic login option on) . then nothing changed and i thought that a restart is required to change the language.
i restarted, it said it was loading window manager, nautilus..and then it booted into ubuntu desktop, i could see the icons and only white bars where the taskbars are,and then it restarted to the login , i entered my name and password and it logged into the desktop and then again, and again.finally it stopped restarting and booted into the normal desktop with the taskbars loaded.
i went into the login manager and checked out the automated login and checked a "secure login" or something like that , i thought it may fix the problem. i reverted to english as default(even though no language change was made,apparently), then i restarted. an error appeared that said:


The greeter application appears to be crashing. Attempting to use another one.



then the GNOME desktop manager came up and i logged in with the same result, ubuntu restarts into the login window..
the only way i could start something in ubuntu was to open only the terminal which i used to open firefox and go to the forums.


HELP ME.

---

### Post by panti19 on 2007-02-14
now i booted, but it said


[I've detected a panel already running, and will now exit.]

and now i can use ubuntu, but i don't have the taskbars.:confused: :confused:

---

### Post by panti19 on 2007-02-14
help me. 
i can't use ubuntu like this..
with a little luck , i boot into the OS but with no taskbars...
:confused:

---

### Post by meborc on 2007-02-14
try booting into rescue mode... then from terminal try to 
```
sudo apt-get remove THELANGUAGEPACKYOUINSTALLED
```
and make sure you have the english one...

then restart your box and boot to normal mode

i'm not sure it will help, but there is not much to lose :)

---

### Post by panti19 on 2007-02-14
i removed the pack when i got to boot the second time..
also, what is the command to open terminal?
i can't find it anywhere..
because now i am in normal ubuntu but without the taskbars, so i can't acces the menus

---

### Post by vijayanand_sodadasi on 2007-02-14
> **panti19 said:**
> i removed the pack when i got to boot the second time..
also, what is the command to open terminal?
i can't find it anywhere..
because now i am in normal ubuntu but without the taskbars, so i can't acces the menus

Try this to open a terminal
Alt + F2  and then enter gnome-terminal
(F2 is the function key F2)

---

### Post by panti19 on 2007-02-14
ok.. now i can't even boot in the normal ubuntu without the taskbars.. (not because of the command.. i just did a restart) the thing is it restarts just after the sound finishes playing or even before
i can't even boot in  failsafe gnome
only failsafe terminal.

---

