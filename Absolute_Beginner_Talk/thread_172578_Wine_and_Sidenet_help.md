---
title: "Wine and Sidenet help"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Henaro on 2006-05-08
Okay I hyave successfully installed Wine and Sidenet with IE 6.  But I have one problem.  How do I use it?  ](*,)

---

### Post by Nikusan on 2006-05-09
[QUOTE=Henaro]Okay I hyave successfully installed Wine and Sidenet with IE 6.  But I have one problem.  How do I use it?  ](*,)[/QUOTE]

Your windows programs will be installed in "/home/henaro/.wine/drive_c/Program Files/" or something similar. Navigate to this directory and run the program you want. Read [the wiki page]("https://wiki.ubuntu.com/Wine") for more info.

---

### Post by sitara on 2006-05-09
I have never managed to get IE working with Wine on Kubuntu. I have just upgraded to Dapper beta 2 in the hope that the problem might be solved, but still no joy.

I have tried Sidenet, IEs4Linux and Winetools. So far, Sidenet seems to get closer than anything else. IE6 is installed and when I start it the first time it downloads Mozilla ActiveX and installs it. Then a window flicks open and closed immediately. When I try to run IE6 from the terminal again, I get the following messages. Any ideas?

Keith

fixme:shdocvw:IEWinMain "" 1
fixme:shdocvw:iecs_QueryInterface unknown interface {00020400-0000-0000-c000-000000000046}
fixme:shdocvw:iecs_QueryInterface unknown interface {9c2cad80-3424-11cf-b670-00aa004cd6d8}
fixme:shdocvw:is_CanInPlaceActivate
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:shdocvw:is_OnUIActivate

---

### Post by Henaro on 2006-05-09
Okay well after following the instructions Nikusan has given me I have come across the same problem as sitara.  Please help me out.

Thanks,
Hen

---

