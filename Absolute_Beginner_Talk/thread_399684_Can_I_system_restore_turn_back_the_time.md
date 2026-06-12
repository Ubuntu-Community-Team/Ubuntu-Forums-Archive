---
title: "Can I system restore? turn back the time?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by numerical on 2007-04-02
****
Is there a feature similiar to systme restore (like in windows) in edgy ubuntu 6.10? after installing many network programs in an attempt to connect to my wireless router,I  guess there was a conflict so i uninstalled the other network programs but still my default networking app doesnt open .Ever since I made these changes my system is very unstable (keep getting bug error when i try to open networking. (hence i cant connect to the internet to fix the problem) Is system restore an option or should i reinstall ubuntu over a newly formatted partition?

Thanks everyone!

---

### Post by land0 on 2007-04-02
Try using synaptic to reinstall the default app. When you removed the other network apps did you select completely remove?

---

### Post by numerical on 2007-04-03
thanks for you response,I cannot remove most off the wlan /network progs in synaptic it says "unable to remove you must fix "broken " files first._What is the default app called anyway? Plus i cannot connect to the internet so how would i reinstall them ?

any advice on the best course of action?

---

### Post by floke on 2007-04-03
Is there nothing in synaptic you can click to 'repair' broken packages?

---

### Post by mikewhatever on 2007-04-03
There seems to be no system restore function in Ubuntu. You can try fixing the broken packages in synaptic: Edit>Fix Broken Packages.
Also, how did you install the programs without Internet connection? Generally it's a good idea to vaguely know what you're doing. If, for example, you network card is not recognized, no program would help you connect.

---

### Post by numerical on 2007-04-03
I installed everything with a DSL line plugged in . However that doesnt work anymore.I did not completey remove anything(just remove).And i tried to Fix broken packages but it cannot find any when i search both ways in synaptic.

---

### Post by IsaacJ on 2007-04-03
I think some sort of system restore function would be a fantastic idea for Ubuntu--either that, or some other alternative that allows to make changes without too much worry.  I imagine a true system restore would be a pain for someone to write/develop, but it would help Ubuntu and Linux in general compete with MS.

The Fix Broken Packages feature has worked for me so far, though I'm also pretty new to Linux.  Sometimes I am able to reinstall features without a network connection if I didn't completely uninstall, sometimes I'm not.  (Not sure why)  *I have found that you must uninstall conflicting features before installing or reinstalling others.*

I had to uninstall WICD before reinstalling the NM-Applet, for instance.  You might need to try something like that.  I would try fixing the package, then uninstalling it and reinstalling the one you want.

IsaacJ

---

### Post by IsaacJ on 2007-04-03
Oops, you were writing as I was writing.  My bad.  :) 

IsaacJ

---

### Post by numerical on 2007-04-03
I totally agree with you .Either a system restore function would be great or a function that could undo changes made in Terminals .I ended up reinstalling ubuntu today  . (didnt lose any valuble data -just upset becasue i spent so much time installing various games +education+ internet programs .however i glad to have a fresh copy running and after i figure out how to ndiswrapp my windows drivers i should be up and running .

thanks everyoen for you advice.

---

### Post by shoq on 2007-04-15
So what is the alternative to a restore function?
Just copy the entire file system as backup? 
I am new to Linux. Are there really simple backups that could make such a snapshut nearly one click easy, so that it could be done before any major install?

---

### Post by Mujaheiden on 2007-04-15
Yeah, i just restored my moms XP computer and then realised I miss something like that in Ubuntu (just reinstalled alst week :-(

---

### Post by Fascination on 2007-04-15
This should help you out:

[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

There are alternatives, but that is one of the easiest (at least, thanks to that guide!). :)

---

### Post by Quillz on 2007-04-15
I also agree that a System Restore of sorts could be a boon to Ubuntu (and Linux in general.)

---

