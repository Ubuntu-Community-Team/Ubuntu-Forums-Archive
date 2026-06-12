---
title: "Where are all the programs?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-01
Sometimes I will go into the Synaptic Pkg Mgr and search for a program that I do not think I have installed, because I cannot find it in the Applications menu.  But when I find the program in Synaptic, it tells me it is already installed.  Currently, I am trying to use VMWare.  And Synaptic says that it is installed, but I don't see it anywhere in the Applications or Systems menu (the START menu?? what does Linux call this?)

I have had this problem before, sometimes I want to run an app that Synaptic says it already installed, but isn't showing in the "start" menu.  Where can I find these apps?

---

### Post by oilchangeguy on 2007-04-01
go to applications, accessories, alacarte menu editor. from there you should be able to add items.

---

### Post by johnc4510 on 2007-04-01
Oilchangeguy is correct, althought some 3rd party apps. still won't be there. You can however add them to the menu. When you have ala carte open, look on the right hand side and you will see a button called:
+ New Item

You can use this to add a new app to any of the sub menus.

---

### Post by pmueller on 2007-04-01
For some reason in my version of edgy Ubuntu, I do not have alacarte in the menu.  If this is the case try Applications, Accessories, Terminal and type in alacarte at the command prompt.

Paul in NH

---

### Post by russell.h on 2007-04-01
Or (at least in Feisty, not sure about others) you can right click on the Applications menu, and it gives you an option to edit it.

---

### Post by johnc4510 on 2007-04-01
You can also just right click on any portion of the drop down menu and select:  Edit Menu

This launches ala carte

---

### Post by kc5hwb on 2007-04-01
There is no button on the right side.  From the File Menu, I see
+ New Entry  (is this it?)

And I still don't see VMware in any of these menus, though I did find some other things that I was looking for.

---

### Post by Maestro23 on 2007-04-01
In termial:

> whereis filename

Should give you the path to the bin file. Can try "locate" as well.

---

### Post by johnc4510 on 2007-04-01
Yes, that would be it. Then follow Maestro23's instructions to locate the correct path to the bin file.

---

### Post by zvacet on 2007-04-01
You can not see your apps forfew reasons:they don´t have GUI or Icon is not automaticly added to programs.if you want to know where they are it is probably in usr/bin.You can use this comand to find apps
```
whereis program_name ls
```
And, yes it is new item.To add app click on new item and you will see launcher.Make it like this:
1.name = app name
2.command = usr/bin/app_name
3.icon = usr/share/pixmaps

---

### Post by kc5hwb on 2007-04-01
Found it, added it, but when I click on the new link from the Apps menu, it tells me "permission denied"

---

### Post by iClouseau88 on 2007-04-01
I got more or less the same problem as you do.  Despite the fact Synaptic Pkg Mgr indicates that "a la carte" **is** already installed, I cannot find it anywhere. I followed all the other threads in this post, still no go.  I wonder if others are missing the point, since the majority of them seem to be giving advice about editing the Applications menu to add/edit a program item.

:confused:

---

### Post by Maestro23 on 2007-04-01
> **iClouseau88 said:**
> I got more or less the same problem as you do.  Despite the fact Synaptic Pkg Mgr indicates that "a la carte" **is** already installed, I cannot find it anywhere. I followed all the other threads in this post, still no go.  I wonder if others are missing the point, since the majority of them seem to be giving advice about editing the Applications menu to add/edit a program item.

:confused:

In terminal type:

> alacarte

What pops up?

---

### Post by iClouseau88 on 2007-04-01
What pops up is the so-called Main Menu. Below it are the three panels with menu items or choices.  The first and second panes are almost identical.

Is this what you call "a la carte"?  I always believe alacarte is the title of a menuing program that allows user to add/edit/remove menu items with similar structure to Add/Remove Programs and Device Manager in Windows XP.  Perhaps I am mistaken.

---

### Post by kc5hwb on 2007-04-01
What about my permissions denied error?  I can't seem to get VMware to run

---

### Post by johnc4510 on 2007-04-01
The bin file probably needs to be made executable. In a terminal type this:

gksudo nautilus

A file window will open which will give you root permissions. Navigated to the bin file in question and right click on it. Then choose permissions and see if the box toward the bottom that says make file executable is checked. If not check it and close the root window and try menu launch again.

---

### Post by kc5hwb on 2007-04-01
> **johnc4510 said:**
> The bin file probably needs to be made executable. In a terminal type this:

gksudo nautilus

A file window will open which will give you root permissions. Navigated to the bin file in question and right click on it. Then choose permissions and see if the box toward the bottom that says make file executable is checked. If not check it and close the root window and try menu launch again.


Well, I did that and now when I click on it from the Applications Menu, nothing happens.

I went into the File Browser and double-clicked on the vmware.4.gz file itself and it just opens another file menu window.  It doesn't seem to want to execute.

---

### Post by johnc4510 on 2007-04-01
Not sure I can help you any further, maybe someone else can though.

Sorry and Good Luck

---

### Post by kc5hwb on 2007-04-02
I can't find the VNC client and I can't find the VMware player.  I am not sure that I installed VMware correctly since it isn't listed in Synpatic, but I installed VNC thru Synaptic and I still can't find it.

---

### Post by kc5hwb on 2007-04-14
My Ala Carte Menu Editor is gone and Synaptic shows that Partimage is installed, but I can't find it anywhere in the menu.

---

