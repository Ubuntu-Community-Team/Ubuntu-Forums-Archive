---
title: "Urgent help ...please ...!!!"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by mourad on 2006-06-29
I have just download Xubuntu, and after going through the manual, and trying to get some programs installed ... I right clicked over the "Application" tab and chose "Edit Menu", and after that NO window pop up and I click over the "Application" tab it DOES NOT OPEN, and Now it's name changed to "XFEC menu" after I rebooted, and still I click over it and nothing opened, and I can't access anything now ....

Anybody can help how to restore the Application tab ?!?!?!?!

THanks ...
P.S ; reboot in recovery mood , I tried and it didn't get me inside the Xubuntu, I used "failesafe" and I didn't know what to type ....:confused: :mad: :confused: :mad:

---

### Post by Kilz on 2006-06-29
[QUOTE=mourad]I have just download Xubuntu, and after going through the manual, and trying to get some programs installed ... I right clicked over the "Application" tab and chose "Edit Menu", and after that NO window pop up and I click over the "Application" tab it DOES NOT OPEN, and Now it's name changed to "XFEC menu" after I rebooted, and still I click over it and nothing opened, and I can't access anything now ....

Anybody can help how to restore the Application tab ?!?!?!?!

THanks ...
P.S ; reboot in recovery mood , I tried and it didn't get me inside the Xubuntu, I used "failesafe" and I didn't know what to type ....:confused: :mad: :confused: :mad:[/QUOTE]

Its a known issue, [and in the release notes is a fix.]("https://wiki.ubuntu.com/XubuntuDapperReleaseNotes#head-b38e122d8c9dc3a3a68b3b1704231a9e90ca7361") Im sure a lot of people will be glad when they fix this flaw.

---

### Post by mourad on 2006-06-29
[QUOTE=Kilz]Its a known issue, [and in the release notes is a fix.]("https://wiki.ubuntu.com/XubuntuDapperReleaseNotes#head-b38e122d8c9dc3a3a68b3b1704231a9e90ca7361") Im sure a lot of people will be glad when they fix this flaw.[/QUOTE]

thanks I opened the link, but it does NOT say how to remove it or where to find the  ~/.config/xfce4/desktop/menu.xml  to remove it.....

---

### Post by mcduck on 2006-06-29
[QUOTE=mourad]thanks I opened the link, but it does NOT say how to remove it or where to find the  ~/.config/xfce4/desktop/menu.xml  to remove it.....[/QUOTE]
well, it's in ~/.config/xfce4/desktop, so it _does_ say where the file is..

To remove it, you can either open a terminal and run 'rm ~/.config/xfce4/desktop/menu.xml' or browse to ~/.config/xfce4/desktop with any file manager and remove the menu.xml file (~ is your home directory, and all files/dirs with a dot first in their name are hidden files, so you need to set your file manager to show hidden files before you can see the .config directory inside your home dir)

---

