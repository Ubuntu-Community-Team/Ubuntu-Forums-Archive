---
title: "changing default player setting in firefox from totem to realplayer"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2007-02-28
when i click some streaming link ,firefox launches totem movie player ,which is so hideous player that it can't play anything. so i installed realplayer for linux. now still firefox opens totem. how can i change firefox settings  so tht it launch realplayer rather than totem

---

### Post by Quillz on 2007-02-28
I think Firefox just uses whatever player is set as the system default. Thus, try changing Ubuntu's default from Totem to RealPlayer.

---

### Post by u04f061 on 2007-02-28
> **Quillz said:**
> I think Firefox just uses whatever player is set as the system default. Thus, try changing Ubuntu's default from Totem to RealPlayer.

how can i change ubuntu default player???

---

### Post by RichPicker on 2007-02-28
When you get that dialog box that asks "What should Firefox do with this file?" (or something close to those words), select "other", then go to usr/bin in the File System  and find the realplay file. (It is a link to the shell script) Select that file.

This is what I did, and it worked. 

Also you may need to do this from Fireftox: 
Select Tools > Add-ons. When you get the dialog box, click "Get Extensions" in the bottom right corner. Then from the Firefox Add-On page search for "MediaPlayerConnectivity" and follow the instructions to install that add-on. Restart.

---

### Post by xtoph on 2007-03-07
if you want the default player for double-clicking in ubuntu, you can change that.
find an example of the file type.  right-click on it->properties.
there is an "open with" tab for changing the player.

---

