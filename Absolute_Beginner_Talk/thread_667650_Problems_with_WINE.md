---
title: "Problems with WINE"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by NeoEIRE on 2008-01-14
hi
i cant get any of my games to work on ubuntu 7.04 like:-
battlefield1942 +mods like desert combat
battlefield2
ROME-total war
Sim city 4 rush hour
or any other PC windows games...

plus i have been told WINE should run VeonTV player so i can watch online tv-series and movies from there site:-

[http://www.veoh.com/videos/v2875812AnGw5yYA](http://www.veoh.com/videos/v2875812AnGw5yYA)

but it freezes at about 80% everytime...

can any1 help with this, as far as i know WINE is upto date and working as it has worked with casino software and other small programs

thanks

neoeire:confused:

---

### Post by nikoPSK on 2008-01-14
Well, first, make sure you have compiz disabled. Two, bf1942 (which is a great game) runs fine in wine for me, maybe set some things in 
```

winecfg
```

Best,
nikoPSK

---

### Post by NeoEIRE on 2008-01-14
hi
i ran the command in terminal and this is what i get:

neoeire@neoeire-desktop:~$ winecfg
fixme:ntoskrnl:KeInitializeSpinLock 0x4677a4
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\HbTools\\HBTV\\HBTV.exe" failed with error 1813
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\HbTools\\HBTV\\HBTV.exe" failed with error 1813
fixme:shdocvw:PersistStreamInit_InitNew (0x1aa750)
fixme:shdocvw:WebBrowser_QueryInterface (0x1aa750)->({3af24292-0c96-11ce-a0cf-00aa00600ab8} 0x1aa250) interface not supported
fixme:shdocvw:OleObject_Advise (0x1aa750)->(0x1aa224, 0x1aa27c)
fixme:shdocvw:ViewObject_SetAdvise (0x1aa750)->(1 00000000 0x1aa224)
fixme:shdocvw:ViewObject_Draw (0x1aa750)->(1 -1 (nil) (nil) (nil) 0x30c 0x1aa294 0x1aa294 (nil) 00000000)
fixme:shdocvw:WebBrowser_QueryInterface (0x1aa750)->({fc4801a3-2ba9-11cf-a229-00aa003d7352} 0x7e4c05f4) interface not supported


i looked everywhere on the control panal that appears and saw nothing like compiz to disable or even check if its enabled

is this right?

---

### Post by nikoPSK on 2008-01-14
> **NeoEIRE said:**
> hi
i ran the command in terminal and this is what i get:

neoeire@neoeire-desktop:~$ winecfg
fixme:ntoskrnl:KeInitializeSpinLock 0x4677a4
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\HbTools\\HBTV\\HBTV.exe" failed with error 1813
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\HbTools\\HBTV\\HBTV.exe" failed with error 1813
fixme:shdocvw:PersistStreamInit_InitNew (0x1aa750)
fixme:shdocvw:WebBrowser_QueryInterface (0x1aa750)->({3af24292-0c96-11ce-a0cf-00aa00600ab8} 0x1aa250) interface not supported
fixme:shdocvw:OleObject_Advise (0x1aa750)->(0x1aa224, 0x1aa27c)
fixme:shdocvw:ViewObject_SetAdvise (0x1aa750)->(1 00000000 0x1aa224)
fixme:shdocvw:ViewObject_Draw (0x1aa750)->(1 -1 (nil) (nil) (nil) 0x30c 0x1aa294 0x1aa294 (nil) 00000000)
fixme:shdocvw:WebBrowser_QueryInterface (0x1aa750)->({fc4801a3-2ba9-11cf-a229-00aa003d7352} 0x7e4c05f4) interface not supported


i looked everywhere on the control panal that appears and saw nothing like compiz to disable or even check if its enabled

is this right?

well, there are issues. To see if compiz is on, goto System->Preferences->Appearance then the desktop effects tab.

Best,
nikoPSK

---

### Post by moebob24 on 2008-01-14
I think running the command
 
```
metacity --replace
```

will disable compiz if you have it installed...but I am not sure if it truly disables it or just switched window managers.

---

### Post by nikoPSK on 2008-01-14
> **moebob24 said:**
> I think running the command
 
```
metacity --replace
```will disable compiz if you have it installed...but I am not sure if it truly disables it or just switched window managers.

Ah, thanks. In the desktop effects tab it should say Disabled or something. I picture of a wand with a red circle over it.

---

### Post by NeoEIRE on 2008-01-14
hi
this is what i get with the metacity --replace command:


neoeire@neoeire-desktop:~$ metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


plus the directions u gave to desktop effects were not exact, but my desktop effects are disabled
and i am running ubuntu 7.04 if that makes a difference?

still no sign of anything called compiz

thanks 4 the quick reply
neoeire

---

### Post by nikoPSK on 2008-01-14
> **NeoEIRE said:**
> hi
this is what i get with the metacity --replace command:


neoeire@neoeire-desktop:~$ metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


plus the directions u gave to desktop effects were not exact, but my desktop effects are disabled
and i am running ubuntu 7.04 if that makes a difference?

still no sign of anything called compiz

thanks 4 the quick reply
neoeire

well, no need for the metacity command. Your compiz is off.... :shock:

---

### Post by NeoEIRE on 2008-01-15
has any1 got any other suggestions to this problem?

---

