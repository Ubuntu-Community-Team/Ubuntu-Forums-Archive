---
title: "Compiz Fusion Won't Start! Need help!"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by eoghanmurray on 2007-07-19
**I have installed Compiz Fusion on my installation of Feisty, and have Fusion Icon installed, but I can't launch Compiz - it simply defaults back to Metacity!**
Is there any way around this? I use an ***ATi X600*** graphics card with restricted drivers activated.

Thanks in advance for help:)

---

### Post by corevette on 2007-07-19
A couple of suggestions:
-Try running Compiz Fusion from the terminal and paste the output, or you can look in the output to find the error
-Try asking in [Ubuntu Forums :: Desktop Effects & Customization]("http://ubuntuforums.org/forumdisplay.php?f=223")

---

### Post by zerobinary on 2007-07-19
can't use restircted driver with it 
disable restricteddriver or don't use compiz 
without restricted driver perforance will be down

---

### Post by misfitpierce on 2007-07-19
> **zerobinary said:**
> can't use restircted driver with it 
disable restricteddriver or don't use compiz 
without restricted driver perforance will be down


Untrue I run an ATI card with restricted drivers... Ive made an XGL session which you may need to do if you have not already... Also you need to add something to xorg file under Devices...

    Option        "AddARGBVisuals" "True"
        Option       "AddARGBGLXVisuals" "True"

---

