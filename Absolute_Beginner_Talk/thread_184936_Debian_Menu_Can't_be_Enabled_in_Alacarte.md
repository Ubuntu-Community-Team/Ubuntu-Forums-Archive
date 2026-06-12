---
title: "Debian Menu Can't be Enabled in Alacarte"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-30
The title says it all:  when i try to enable the debian menu in alacarte, nothing happens; i just can't tick the box no matter how hard i try!  (and yes i do have the debian menu package installed--i just forgot what it was called)

---

### Post by Jagot on 2006-05-30
The package is called 'menu'.

Try ctrl-alt-del to reload GNOME and see if it comes up.

---

### Post by user1397 on 2006-05-30
[quote=Jagot]The package is called 'menu'.

Try ctrl-alt-del to reload GNOME and see if it comes up.[/quote]
i installed the menu package, but CTRL+ALT+DEL doesn't work!

---

### Post by user1397 on 2006-05-30
how can something so simple be so hard!!!!!!:(

---

### Post by catlett on 2006-05-30
If you already installed menu and debian didn't show up try adding this ```
sudo apt-get install menu-xdg 
```You may have to run update-menus after but it should show up next reboot regardless if it doesn't now.

---

### Post by user1397 on 2006-05-30
This is the output of my terminal:
```
$ sudo apt-get install menu-xdg menu
Password:
Reading package lists... Done
Building dependency tree... Done
menu-xdg is already the newest version.
menu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
``` and i did ```
update-menus
``` ```
killall gnome-panel
``` i logged out and in, i restarted, but still nothing!!!](*,)

---

### Post by catlett on 2006-05-30
Man this latest install of dapper is killing you! For the heck of it try installing it again and see what happens ```
sudo apt-get install menu
``` It has to work. I couldn't get it in my new dapper either until I found menu-xdg and that did it. Try menu again there is no way you shouldn't be getting it.

P.S. Aren't these Dapper versions supposed to be getting better as June 1st nears????

---

### Post by user1397 on 2006-05-30
[quote=catlett]Man this latest install of dapper is killing you! For the heck of it try installing it again and see what happens ```
sudo apt-get install menu
``` It has to work. I couldn't get it in my new dapper either until I found menu-xdg and that did it. Try menu again there is no way you shouldn't be getting it.

P.S. Aren't these Dapper versions supposed to be getting better as June 1st nears????[/quote]It just doesn't work!!!!!:(

---

### Post by NyTE on 2006-05-30
Ive done everything Erik has done,and I dont have the debian menu either.](*,)

---

### Post by user1397 on 2006-05-31
yep, still stumped with this one! * he starts slapping the desk while laughing * :mrgreen:

---

### Post by user1397 on 2006-06-01
for some reason, it works now.  all i can think of, is i turned off the computer at night, turned it on in the morning, and boom! there it was!

---

### Post by catlett on 2006-06-01
I'm glad you never leave a post hanging. I see it in my lists of posts and it baffles me why it didn't work. Diid you get any updates since? Probably not if your like me, I only got 1 update after the Dapper release. (a bit of an anticlimax, they could have at least given us a new splash page or background:( )

---

### Post by user1397 on 2006-06-01
wow, i can't believe i forgot a small detail...i installed the newest version of alacarte - 0.9 (instead of 0.8) then i rebooted and it worked!  (i don't know how i forgot this "little" important detail :mrgreen:)

---

