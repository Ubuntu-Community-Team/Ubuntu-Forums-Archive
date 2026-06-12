---
title: "Wheres my app? KDE not posting apps to menus"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by scwinn on 2007-03-21
Why do some programs appear in the KDE menu and others do not. I downloaded flightgear... but Iit isnt there. The same is tru for GNUS. How do I put them on the menu? Did I surpass the number of allowed menu entries or something?

Thanks

---

### Post by belikralj on 2007-03-21
I'm not sure how it is in KDE, but in gnome you can go to 'system -> preferences -> menu layout' and there you set which of the icons appear and which do not. I think it should be very similar in kde but maybie a kde user should tell you exactly how

---

### Post by scwinn on 2007-03-21
I do not know how to find an .exe in Linux. So I cannot help myself. Where are the apps anyway?

---

### Post by belikralj on 2007-03-22
Executables in linux don't have the extention .exe, I'm not certain what they use but I tink it is '.o'. As for where it saves them /bin is your basic shell commands folder and /usr/bin is the folder that contains almost all your programs. Some may also be in /sbin or your /usr/sbin so try looking for them there. For example I found a shortcut to firefox in my /usr/bin folder and it points to /usr/lib/firefox/firefox.

---

### Post by scxtt on 2007-03-22
extensions aren't required in linux, it's more of a carry over from other OS's that use them

.exe DOESN'T = executable, .exe makes people THINK "oh, it's an executable" ... an executable is any file that has the execute bit set, like -rw[COLOR="Red"]x[/COLOR]---r-- ... and of course is actually a binary file that can do something *execute*-like ...

and as far as menu items go, that really depends on who arranged the .deb file ... if they don't specify it, it's most likely not gonna happen ...

---

