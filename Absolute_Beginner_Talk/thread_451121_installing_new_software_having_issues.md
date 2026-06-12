---
title: "installing new software having issues"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by tawniteamo on 2007-05-22
whenever I try to install new software in the add or remove programs in Xubuntu, it keeps telling me to insert the Xubuntu cd (feisty) and I was wondering if I could somehow get rid of this

---

### Post by deadgobby on 2007-05-22
X uses very little resources to be as light as it can be on your system. I think you can go to synaptic and add CD should fix that. I can be wrong. Just ask my wife, she says I am wrong about 99% and I am right 100% of the time. 
Gobby

---

### Post by tawniteamo on 2007-05-22
what do you mean add cd? and it lets me install the software, just requires holding down enter lol while it downloads in the background

---

### Post by aysiu on 2007-05-22
Press Alt-F2 and type ```
gksudo synaptic
``` Then go to **Settings > Repositories** and uncheck the CD repository. Then click **Reload**

---

### Post by deadgobby on 2007-05-22
If you go into synaptic, go to EDIT>ADD CDROM when you want to install a package or unstall a a program. Or you can open up the Terminal and type oh lets say --v. So you type in the terminal 
type in --v

 GObby

---

### Post by deadgobby on 2007-05-22
Never mind she beat me too it
 aysiu's Avatar  	
aysiu

---

### Post by aysiu on 2007-05-22
> **deadgobby said:**
> If you go into synaptic, go to EDIT>ADD CDROM when you want to install a package or unstall a a program. > **deadgobby said:**
> I think you can go to synaptic and add CD should fix that. Gobby, I think you're missing that the OP does not want to add a CD-ROM: > **tawniteamo said:**
> it keeps telling me to insert the Xubuntu cd (feisty) and I was wondering if I could somehow **get rid of this**

---

