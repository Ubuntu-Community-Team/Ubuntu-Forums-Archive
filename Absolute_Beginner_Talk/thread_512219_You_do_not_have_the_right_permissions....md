---
title: "You do not have the right permissions..."
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by {A}Poly on 2007-07-28
When ever i try to extract something into a folder, for example I downloaded a new skin for XMMS and i tried extracting it into the appropriate folder: /usr/share/xmms/Skins. Whenever i try to do this i get this message:

Extraction not performed

You do not have the right permissions to extract archives in the folder "/usr/share/xmms/Skins"

How do i fix this?

---

### Post by machoo02 on 2007-07-28
try putting sudo in front of your extraction commands.```
sudo tar -xvzf xmms-skin.tar.gz /usr/share/xmms/Skins
```

---

### Post by {A}Poly on 2007-07-28
> **machoo02 said:**
> try putting sudo in front of your extraction commands.```
sudo tar -xvzf xmms-skin.tar.gz /usr/share/xmms/Skins
```

actually i just downloaded the skin off xmms.org, it opened in Archive Manager. from there i tried to extrack "sword.tar" to that location, and it said i didn't have the right permissions. I never touched terminal or put in any commands.

---

### Post by {A}Poly on 2007-07-28
so how do i get this skin to work?

---

### Post by bearyblue on 2007-07-29
you can't just extract the archive to /usr/share/. it belongs to root and you need to have root priveleges. you have to use sudo at the command line. or you can open archive manager as root. but command line is easier for me.

---

### Post by {A}Poly on 2007-07-29
> **bearyblue said:**
> you can't just extract the archive to /usr/share/. it belongs to root and you need to have root priveleges. you have to use sudo at the command line. or you can open archive manager as root. but command line is easier for me.

so what do i type into terminal?

---

### Post by Paul820 on 2007-07-29
You have an xmms folder in home. Open your home folder, press CTRL+h to unhide the files, look for the folder .xmms, inside that there is a folder called skins. Just put the unextracted file in there. XMMS will extract it for you.

---

