---
title: "Not starting Ubuntu"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by exod40 on 2006-04-15
When i logged in. There is an orange screen with nothing else there. Last time when i have working Ubuntu, I tried to install one program for Bulgarian letters.

---

### Post by mostwanted on 2006-04-15
When you're in the boot menu select the recover mode. Then issue these commands

```

mkdir /home/insertYourUserName/oldsettings
mv /home/insertYourUserName/.* /home/insertYourUserName/oldsettings
```

This will move all the hidden files in your home folder to a folder called oldsettings, also in your home folder. Remember to swap insertYourUserName for your actual username.

The hidden files are typically configuration files, so if you've screwed something up, moving them all into another folder resets your user to the default settings. You can then log in normally (hopefully) and copy the folders and files back that do not hinder your login.

---

