---
title: "[SOLVED] Can't open themes???"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Phiber_tek on 2007-12-05
I just downloaded a few themes from here [http://themes.beryl-project.org/](http://themes.beryl-project.org/) and am running beryl and compiz fusion right now, the themes saved to my desktop and are 2 gzip archives and one "emerald theme"...when I double click the icon as if to unpack it, it tells me the following error message:  "Could not open "black" archive type not supported" I'm not sure what to do, do I need another program to unarchive it? Nevermid the emerald theme one I found that all you do is go to Emerald Theme Manager and click on import then find it and double click it; but for the other two how do I go about unpacking those?

---

### Post by Hospadar on 2007-12-05
do you have emerald installed? "sudo apt-get install emerald"

Then go System->Preferences->Emerald Theme Manager and use the "import" button.

if the themes don't render immediately after you select them in emerald, in a terminal type "nohup emerald --replace"

---

### Post by Phiber_tek on 2007-12-05
I did that with the theme that was .emerald but I have three that are a gzip archive and I need to figure out how to extract those...

---

### Post by Hospadar on 2007-12-05
ohh, could you post a link to where you downloaded the themes (the specific themes in question)

Also, what version of ubuntu are you using?

---

### Post by weezalxc on 2007-12-05
What does the 'nohup' in the command "nohup emerald --replace" do?

---

### Post by CatKiller on 2007-12-05
> **weezalxc said:**
> What does the 'nohup' in the command "nohup emerald --replace" do?

From **man nohup**:

> DESCRIPTION
       Run COMMAND, ignoring hangup signals.


It means that the program keeps running, even if you close the terminal that launched it.

---

### Post by CatKiller on 2007-12-05
They are all .emeralds, aren't they? Have you called them the wrong thing by mistake? Perhaps you could rename them to black.emerald instead of black.tar.gz, for example, and see if that helped?

---

### Post by Phiber_tek on 2007-12-05
I'll try that I cant do anything right now as I'm at school (posting and checking from my iPod) but I get out   at 2:15 so I'll post back at 2:20 in about an hour and 15 minutes...

---

### Post by DragonKore on 2007-12-05
You can also try importing them directly from within the Emerald Theme Manager.

---

### Post by weezalxc on 2007-12-05
> **CatKiller said:**
> From **man nohup**:



It means that the program keeps running, even if you close the terminal that launched it.

Ahhh...that is quite useful!  Thanks! :)

---

### Post by asmiller-ke6seh on 2007-12-05
> **Phiber_tek said:**
> I did that with the theme that was .emerald but I have three that are a gzip archive and I need to figure out how to extract those...

You import the .gz directly, without extraction, into the Compiz Theme manager.

---

### Post by Phiber_tek on 2007-12-05
Alright I just renamed it to .emerald and it all worked...So thanks again everyone...

---

### Post by CatKiller on 2007-12-06
Don't forget to mark the thread as "Solved".

---

