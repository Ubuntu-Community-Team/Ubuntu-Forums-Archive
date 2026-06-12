---
title: "I installed some programs:"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Sonastylol on 2008-02-01
((Now - im still a newb))   Including the Avant Window Navigator..

I see that I can make some launchers ( shortcuts ) and I would like to do this... problem is, I dont know what directory all "MY PROGRAMS" are in...

So, can someone please inform me where my firefox is? And where my Trillion or AIM would be once installed? Etc... so I can finish this :)

---

### Post by barrack on 2008-02-01
Usually, most programs are in /usr/bin/ but the programs you mentioned can be launched by  just typing the name of the program as the command.

With AWN, what I find easiest is find the launcher in the menu editor (System>Preferences>Main Menu) and copy and paste the information into the AWN Launcher.

I'm not sure about AIM or Trillian, but a very good equivalent is either Gaim or Pidgin, preinstalled and found under Applications>Internet.

Hope that helps.

---

### Post by erfahren on 2008-02-01
you don't necessarily need to input the full path to the executable file in order to launch it - you just need the command - like:
```

firefox

```
many (or most) programs have their excutables in /usr/bin - and it will be checked (along with the other common paths) for the excutable.

If you are using Ubuntu (gnome) you can just right-click on a menu item and have it added to the panel.

you can also right-click on the Menu and select "Edit menu" and in the menu editor you can find the menu item and right-click on it to see the Properties (including the command to launch it) - also change icon, etc.

---

### Post by PeterJS on 2008-02-01
Here's the wiki page that covers where everything is stored:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)

---

