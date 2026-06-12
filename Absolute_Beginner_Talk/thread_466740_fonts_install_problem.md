---
title: "fonts install problem"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-06-07
For viewing certain sites they recommend those respective fonts to be installed.

For one such site with **tamil **font requirement , i copied the font file (xxx.ttf) into **fonts:///** folder as *root* but its not copying that and also not displaying the text correctly in the webpage. i tried changing the encoding styles but still its not coming....



This is very easy in windows as we copy the *.ttf file to c:/winnt/fonts dir and then it works perfectly. here its difficult to understand.

pls help me installing fonts to view such sites....

---

### Post by mcduck on 2007-06-07
If you want to only install the font for one user, put it into ~/.fonts directory.

For all users, the correct place is /usr/share/fonts. You need root privileges to copy anything there, so open 2 Nautilus browsers as root by running 'gksudo nautilus' to get one open and then go to File/Open New Window to open the other one. This is because both the window where you copy, and window where you are copying from, need to run as root.

You may need to log out and back again before your new fonts are visible to all programs.

---

### Post by NeoLithium on 2007-06-07
You don't have to reboot your comptuer after installing, you can refresh the font cache with this command in terminal:
```
sudo fc-cache -f -v
```
On a side note, I'd recommend putting them in the /usr/share for system wide, but that's just me ;)

---

### Post by sankarv on 2007-06-07
hi, i copied the font(ttf file ) to my ~/.fonts dir. but still the problem exists. the webpage is not displayed properly. i tried setting different encodings in the view menu of mozilla. that does nt help. i also restarted the system and once again it was showing junk characters in the webpage.

---

### Post by Najand on 2007-06-07
Use the command NeoLithium said, then go to FireFox Preferences and select contents tab. Then change your  default font ther to the one you installed. If it doesn't work, there are still ways to solve your problem.

---

