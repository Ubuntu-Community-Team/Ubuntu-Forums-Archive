---
title: "cant Access Debian Menu From Application Menu"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by jbowman86 on 2007-04-13
Hi Guys. Im trying to access the debian menu as a package i have just installed is not in the application menu. I also do not know the package name to type into a terminal.       
I unintsalled and reinstalled debian menu but it still wont show in applications menu. alacarte menu editor shows debian menu in the apps menu but i am unable to 'tick' it to make it show in the actual menu itself. Please help as im starting to get a bit frustrated. CHEERS

---

### Post by jrib on 2007-04-13
> **jbowman86 said:**
> Hi Guys. Im trying to access the debian menu as a package i have just installed is not in the application menu. I also do not know the package name to type into a terminal.       
I unintsalled and reinstalled debian menu but it still wont show in applications menu. alacarte menu editor shows debian menu in the apps menu but i am unable to 'tick' it to make it show in the actual menu itself. Please help as im starting to get a bit frustrated. CHEERS

Have you checked permissions and ownership of ~/.local and everything under it?

---

### Post by jbowman86 on 2007-04-13
how do u do that?

---

### Post by jrib on 2007-04-13
```
find ~ ! -user $USER -exec ls -ld '{}' \;
```

should list anything in your HOME that is not owned by your user.

For permissions, you can check permissions on a file with:
```
ls -ld ~/.local
``` for example, but it is more likely that the ownership is fubared rather than the permissions.

---

### Post by Skidpad on 2007-04-13
Did you install the both the menu and menu-xdg packages?  You need both for it to work.  You also need to update your menus when done.  

Since you've presumably installed only the Debian menu package, try this code I used to fix the same problem when I installed it:

sudo aptitude install menu menu-xdg
sudo update-menus

---

### Post by jbowman86 on 2007-04-16
Hi. Although those two commands sorted out my debian menu problem. a friend also decided to switch  from xp to ubuntu 6.06 for desktop aswell. When the first line was entered into terminal it downloaded and installed the menu package but the second line  returns the following error. 

~$ sudo update-menus
sudo: update-menus: command not found

Any help would be great, thanks guys.

---

### Post by zvacet on 2007-04-16
```
sudo aptitude update
```

---

