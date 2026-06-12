---
title: "Graphics Card Problem"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by tdashroy on 2008-01-24
Hello, I just recently got ubuntu and am wondering if there is a way for me to change my Graphics drivers.  I try to go to System>Administration>Screen and Graphics and change it to what I think it should be, but when I go back to it, it just has it as "vesa - Generic VESA-compliant video cards".  I found my graphics card with the command "lspci",

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

this does mean i have an Intel 965 doesn't it?

Help would be much appreciated.  Thanks :)

---

### Post by smacattack on 2008-01-24
Is there something wrong with it?  I mean is compiz or something not working or what exactly?

I'm just asking because as far as I know my graphics cards isn't recognized/installed properly but everything works haha, so no complaints from me...

---

### Post by amd-64 on 2008-01-24
May be the i965 driver is not installed. You can install it as follows

sudo apt-get install xserver-xorg-video-intel

---

### Post by tdashroy on 2008-01-24
It says it is installed correctly and the most up-to-date, and it seems to be working fine, but I did just try compiz and it says

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

now i have no idea what that means, so help would be again be greatly appreciated: Thanks :)

---

