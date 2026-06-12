---
title: "Need help running a new program"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by expo91 on 2008-03-15
I D/Led Citrix, then installed it. It did not put an Icon in the start menu so I'm trying to run it manually, I hit alt f2 and open a box but I can't find a file that I should type in the box that would start the program. Windows always gad an exe fire what should I be looking for in Linix? Also none of the files use citrix in their name so there again I'm so cinfussed!

---

### Post by unutbu on 2008-03-15
It might help to know a bit more about how you installed the program. 
Was it from a .deb file? Did you use get-apt or synaptic?

---

### Post by expo91 on 2008-03-15
I ran the program by right clicking on setupwfc, then a box opened and I selected run in terminal window, Below is what came up and I just answered the questions. There is a folder called ica client. 


Copyright 1996-2007 Citrix Systems, Inc. All rights reserved.

Citrix, Independent Computing Architecture (ICA), Program Neighborhood,
MetaFrame, and MetaFrame XP are registered trademarks and
Citrix Presentation Server, Citrix Access Suite, and SpeedScreen are
trademarks of Citrix Systems, Inc. in the United States and other countries.

Microsoft, MS, MS-DOS, Outlook, Windows, Windows NT, and BackOffice are
either registered trademarks or trademarks of Microsoft Corporation in
the United States and other countries.

All other Trade Names referred to are the Servicemark, Trademark,
or Registered Trademark of the respective manufacturers.

User install mode.

Select a setup option:

 1. Install Citrix Presentation Server Client 10.6
 2. Remove Citrix Presentation Server Client 10.6
 3. Quit Citrix Presentation Server Client 10.6 setup

Enter option number 1-3 [1]:

---

### Post by unutbu on 2008-03-15
Go to the gnome panel menu in the upper left corner. Click Applications>Internet. Do you see "Citrix Presentation Server Client"?

---

### Post by expo91 on 2008-03-15
No it isn't there

---

### Post by handydan918 on 2008-03-15
Failing that, try 
```
sudo updatedb
```

and then ```
locate ICAClient
```

(If installed as root, it should be in /usr/lib...but then you already know that, because you read the documentation before installing it, right?)

:)

---

### Post by unutbu on 2008-03-15
You could also try
```

/usr/lib/ICAClient/wfcmgr

``` 

if that doesn't work, and after you've run handydan's commands, you could also try
```
locate wfcmgr
```

---

