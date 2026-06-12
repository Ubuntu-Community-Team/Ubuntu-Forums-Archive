---
title: "Installing Firefox extensions"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by Lonestar on 2006-06-21
I am a new Ubuntu 6.06 user and successfully installed it on my laptop.  However I have a question, I cannot figure out how to install some of the Firefox extensions that I use to use.  I figured out that I needed to run Firefox with the SUDO command to download the extensions.  They downloaded but when I closed Firefox and reopened they were gone.  When I ran Firefox again with SUDO they were there again...:confused: 

I am sure that I am skipping a step or overlooking something...it has been a long day.  

Can someone please help me to understand the correct steps to use when adding extensions, themes, etc. to Firefox?

Thanks,

---

### Post by rai4shu2 on 2006-06-21
All you need to do is run Firefox as normal and either download the xpi file or open the file from your hard drive into Firefox (using the File/Open File... selection in the menu). Then quit and restart Firefox.

---

### Post by aysiu on 2006-06-21
Running Firefox with *sudo* is probably what got you into trouble in the first place. Paste these commands in ```
mv ~/.mozilla ~/.mozilla.backup
firefox
``` Then try to install an extension. If you ever have to run Firefox as root again (which you generally shouldn't) use ```
gksudo firefox
``` **Don't use *sudo* to launch Firefox**.

---

### Post by Lonestar on 2006-06-21
Thanks Aysiu! It works now.  I think what got me confused was at first I did just launched Firefox and tried to install a couple of extensions, but they would partially download and never finish.  I know now not to use *sudo* to launch Firefox.

So I can learn...do you know what was going on before that would cause the extensions to partially download?   Also, is there anything I need to "cleanup" when I did it the wrong way?

Once I used cut-n-paste the code in that you provided everything worked fine .

Thanks,

---

### Post by Brunellus on 2006-06-21
[QUOTE=aysiu]Running Firefox with *sudo* is probably what got you into trouble in the first place. Paste these commands in ```
mv ~/.mozilla ~/.mozilla.backup
firefox
``` Then try to install an extension. If you ever have to run Firefox as root again (which you generally shouldn't) use ```
gksudo firefox
``` **Don't use *sudo* to launch Firefox**.[/QUOTE]
funny.  I've never needed to be root to install any extensions.

---

### Post by aysiu on 2006-06-22
[QUOTE=Brunellus]funny.  I've never needed to be root to install any extensions.[/QUOTE]
Nor have I.

---

