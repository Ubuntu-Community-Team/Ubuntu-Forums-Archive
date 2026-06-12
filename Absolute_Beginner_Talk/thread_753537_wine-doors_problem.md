---
title: "wine-doors problem"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by noorez on 2008-04-12
I used wine-doors to install IE6. However, when I go to start it, nothing happens. I executed the command in a terminal and here is what i got:

noorez@noorez-laptop:~$ env WINEPREFIX=/home/noorez/.wine/ wine "C:\Program Files\Internet Explorer\iexplore.exe"
err:module:import_dll Library shdocvw.dll (which is needed by L"c:\\windows\\system32\\iexplore.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\iexplore.exe" failed, status c0000135

i'm not sure how to fix these errors. Can someone help please ?

---

### Post by otrojake on 2008-04-12
I'm unfamiliar with wine-doors, so I can't give you any recommendations for that program.  But I've had good luck with IEs4Linux.  Check out their Ubuntu guide [here]("http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu").

---

### Post by puccaso on 2008-04-22
i have the same problem
im using wine-doors on hardy

iv dont a locate shdocvw.dll and its there.. so i dont know what the problem is?

---

### Post by mlalkaka on 2008-05-04
I'm having the same problem, but I don't think this is specific to Ubuntu. Have a look at [http://www.wine-doors.org/trac/ticket/723](http://www.wine-doors.org/trac/ticket/723)

---

