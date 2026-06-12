---
title: "need some quick help with wine : )"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by h-town on 2008-03-30
I installed Traktor studio (which i've read works great in wine) and there is this advice from winehq

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5144](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5144)

> After installation, copy the following files to the installation directory from your Windows installation or from dlldump.com:
- wmasf.dll
- wmvcore.dll
- drmclien.dll
- wmidx.dll 

Where's the installation directory? is that in "Browse C Drive" ?

---

### Post by robalcorn on 2008-03-30
I think if you go to your home folder and go to view click on  show hidden files than go to wine/drive_c/program files/ you will see the installed directory and than copy the requested dl's there.

---

### Post by sancho panza on 2008-03-30
I think it refers to the installation directory in .wine/drive_c which should be in the users home folder. Thats the folder acting as the C drive for wine windows programs.
(Note that the wine dir is a hidden directory.)
Let us know if that works,

---

### Post by h-town on 2008-03-30
i pasted the files into:

/home/harrison/.wine/drive_c/Program Files/Native Instruments/Traktor DJ Studio 3

When I double click the exe nothing happens. but I also seem to have another tracktor directory in my home file

I authorized  the regestration tool file.. so everything should be working. all my other exe files open up no problem, so it's not a problem with wine. maybe I should make a post at the winehq appdb?

---

### Post by sancho panza on 2008-03-30
Does right clicking the exe and selecting 'open with >wine' help?

---

### Post by h-town on 2008-03-30
no difference. 

but I just noticed that at winehq they tested 0.9.52 wine with traktor studio 3 and I have 0.9.58- could that be it?

---

### Post by h-town on 2008-03-30
also i'd like to point out i'm using hardy heron..

---

### Post by h-town on 2008-03-30
I have an idea for installing it properly.. maybe I have to manually open up the regestration tool while the installer is open, because it freezes after I install the program which may mean it's waiting for me to complete registration so that the traktor.exe will now execute. However, I need to uninstall the program and reinstall to test my theory. When I try to uninstall I get an error message asking for... ......

oh wait, now I have a new problem. When I click on "Uninstall wine program" the thing doesn't load anymore. Man, I love what ubuntu is about but it really gives me a headache sometimes. 






I give up.. how can I manually uninstall all the traktor files???

---

### Post by h-town on 2008-03-30
i have a great idea.. i'm just going to format my hard drive (which isn't going to be hard since i've backuped everything about a month ago), downgrade from vista to xp with ubuntu as well. I'll use xp for reason, photoshop, traktor and ubuntu will stay open source all the way.. no more headaches, no more wine.

---

### Post by sancho panza on 2008-03-31
Before u format, try uninstalling wine and then remove the .wine dir in your home folder. That should remove all traktor files. Then reinstall wine and try to install traktor keeping all that you now learnt in mind.

---

