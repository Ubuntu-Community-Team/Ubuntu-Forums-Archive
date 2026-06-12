---
title: "Transfering Files Into Root"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by victor9098 on 2007-07-21
Hello All,

Have just finished my install and have gotten all 170MB worth of updates.

I copied files from my old OS and intended to "drag & drop" them into the appropriate folders in Ubuntu (My Thunderbird & Firefox settings) but I am not allowed since I am not root!? 

Is there anyway I can gain permission, even for a short period of time? 

Thank you!

---

### Post by pyros on 2007-07-21
> **victor9098 said:**
> Hello All,

Have just finished my install and have gotten all 170MB worth of updates.

I copied files from my old OS and intended to "drag & drop" them into the appropriate folders in Ubuntu (My Thunderbird & Firefox settings) but I am not allowed since I am not root!? 

Is there anyway I can gain permission, even for a short period of time? 

Thank you!

You can use the sudo and gksudo commands for this, for example running "gksudo nautilus" will open up a file manager window with root permissions.

---

### Post by sancho panza on 2007-07-21
If I remember correctly, all your personal settings are stored in the dot (.) files which are hidden by default in your personal home folder. If you dont like using the terminal, u can view these folders by enabling hidden files in your nautilus folder browser. You should find ur firefox and other program settings folder for which you'll have the write permissions by default.
If you are new to linux, I would not advise that you use the sudo command to overwrite the firefox and other folders not in your home folder. The dependencies might get messed up, the older programs may not work in the new OS.

---

### Post by victor9098 on 2007-07-21
Thank you...will give those suggestions a try! :)

---

### Post by meierfra on 2007-07-21
Where are your  trying  to put the setting files? They  belong inside   your home folder, and you don't need permisssion to drop files into your home folder.


Edit: Oops, seems somebody  already pointed this out.

---

### Post by pyros on 2007-07-21
> **sancho panza said:**
> If I remember correctly, all your personal settings are stored in the dot (.) files which are hidden by default in your personal home folder. If you dont like using the terminal, u can view these folders by enabling hidden files in your nautilus folder browser. You should find ur firefox and other program settings folder for which you'll have the write permissions by default.
If you are new to linux, I would not advise that you use the sudo command to overwrite the firefox and other folders not in your home folder. The dependencies might get messed up, the older programs may not work in the new OS.
Good catch there sancho, I was just assuming that the files were given root permissions when the old os volume was mounted.

---

### Post by Nythain on 2007-07-21
maybe they aren transfering home settings files... i have a list of backed up /etc/ config files, and some /usr/bin/ scripts i wrote that i have to put back in place when i reformat... either way, back to the question at hand.

if doing it in terminal, use sudo like this:
sudo cp /path/to/file.whatever /path/to/where/file/goes.whatever

if you want to do it graphically, as mentioned above:
gksudo nautilus
should do the trick

---

