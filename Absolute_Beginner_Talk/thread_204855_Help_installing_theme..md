---
title: "Help installing theme."
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by 5tudent on 2006-06-27
Hi,

I am a new comer to Linux. Yesterday I installed Ubuntu Dapper 6.06 on my laptop. 

I want a new theme (wall papers and such) for my laptop. Hence, I went to [www.Gnome-Look.org](www.Gnome-Look.org) and downloaded some GDM themes that I liked.

In ubuntu, when I try install theme, I get an error "invalid format". 

Should I not use GDM themes? 
What am I doing wrong? 

Please help. 

Thanks in advance.

---

### Post by nalmeth on 2006-06-27
extract the package to your desktop, and use this command to copy it to /usr/share/gdm/themes (this will need admin priviledges) replace gdmtheme with the name of the extracted folder.

cd ~/Desktop
sudo mv gdmtheme /usr/share/gdm/themes

When I've been forced to do this, it sometimes has meant that the theme didn't work. If the theme isn't right, GDM will revert you to your last one.

If you have similar problems installed gnome themes, copy or move the theme to /home/username/.themes

You *should* be able to install working themes directly in the theme manager for gnome or gdm.

---

### Post by johnc4510 on 2006-06-27
GDM's are login screen images. To install them in gnome:
System>Administration>Login Window
Click on add, and navigate to the download and open

---

### Post by 5tudent on 2006-06-29
Johnc4510 & Nalmeth:

Thanks for taking the time to reply to this newbie's question. 

John, I followed your directions and I was able to install the GDM themes.
Thank you.

---

### Post by InverseFlux on 2006-06-30
Excellent, appreciate the help this brought.  I was having issues getting themes to show up and this showed me the way.

::: grins :::

---

