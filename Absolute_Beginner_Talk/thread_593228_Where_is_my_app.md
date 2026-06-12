---
title: "Where is my app?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Tvanover on 2007-10-27
I have installed an application from a .deb package (adobe reader 8.1).  but it seems to not have registered.  It does not show up in my applications.  When I click on it's files it opens Evince Document reader.  The install does not throw any errors so I assume it worked.  The menu editor seems to be limited, and doesn't include the office or Network sub folders.  Am I missing something here?

I am using Xubuntu 7.04 (I think, what ever is the latest as of Oct 16)

---

### Post by taurus on 2007-10-27
I believe the name of that app is acroread.

```
whereis acroread
```

---

### Post by Tvanover on 2007-10-27
Well that gives me the app.  now how do I add it to my application menu and make it the default applications for PDF's?

---

### Post by taurus on 2007-10-27
Right click the PDF file and go to Properties.  In there, chance the file association from evince to acroread.

---

### Post by nrfool on 2007-10-27
At xubuntu, there is a use program: **Applications->Accessories->Appfinder**
start appfinder, type the name of the program you are looking for, search. You will get a result. If you right click on the search result and choose "more infor", you will see the command for that program. This will enable you to add shortcuts on the menu and front panel.

---

### Post by Tvanover on 2007-10-27
WOOT!  Great that worked fine, now any ideas on getting it into the application menu?

note. no joy on appfinder.  It shows everything I got using Add/Remove but nothing beyond that it seems.

---

### Post by zvacet on 2007-10-27
Main menu>on the left select where you want to put your app (accessories,graphic.office...) and on the right select>new item

1.command >usr/bin/acroread (I belive this is correct)
2.name
3.icons>usr/share/pixmaps

P.S. you will find main menu in **system>settings**

---

### Post by Tvanover on 2007-10-27
> **zvacet said:**
> Main menu>on the left select where you want to put your app (accessories,graphic.office...) and on the right select>new item

I am assuming that you mean right click on Applications and choose Edit menu.  In the Menu Editor I have :
```

Settings 
  Settings Manager	xfce-setting-show
  --seperator--
  --include--		system
  --seperator--
  about Xfce		xfce4-about
Quit			quit

```

as you can see I am lacking the options you list.

> 
1.command >usr/bin/acroread (I belive this is correct)
2.name
3.icons>usr/share/pixmaps

This works but it does not allow me to ad it to any sub folder but exists as a top level item.


> P.S. you will find main menu in **system>settings**
I think you are thinking of Ubuntu not Xubuntu.  As you can see my options are a bit more limited.

---

### Post by zvacet on 2007-10-27
I didn´t knew that you use Xubuntu.I never use it,so I´m not much of help to you.

---

### Post by nrfool on 2007-10-27
Interesting. I am using xubuntu too and my acrobat reader is also installed from downloaded packages from the official site. On my appfinder, acrobat reader shows up when you search "***reader***", but doesn't show when search "***acroba***t". It is also listed in the office categoray of appfinder.

---

### Post by taurus on 2007-10-27
Try **acroread** instead.

---

