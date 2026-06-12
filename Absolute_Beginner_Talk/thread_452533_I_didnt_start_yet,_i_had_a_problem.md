---
title: "I didnt start yet, i had a problem"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-05-23
hi, i am a fresh new user, actually i didnt become a user yet cuz i had a problem in the installation itself :-(
after booting i selected start or install ubuntu so after some commands running on the screen i had an error 
telling that i have a problem with X server, i selected ok to see more details where the error given was 
"no screen found" , but another note was written that "screens found but no suitable configuration found"
any idea ??

my laptop specs:
Dell Inspiron 6400
inetl Core 2  2.0 GHz
2 GB DDR2 memory
ATI Radeon Mobility X1400

---

### Post by southernman on 2007-05-23
If you'll read and follow the instructions based on this guide:

[Installing Ubuntu 7.04: ATI X**** Cards]("http://ubuntuforums.org/showthread.php?t=414194")

you should be good to go.

---

### Post by dstew on 2007-05-23
Are you having problems booting the Live CD? Sometimes the Live CD will not boot because of hardware issues. You can try different boot options by pressing F6 at the first screen. The Help menu there also can give you instructions on boot options. Try the options noapic, nolapic, and maybe nodma. I think the option vesa=force might also help.

If you can't get the live CD to boot that way, you can still install the same Ubuntu operating system using the Alternate Install CD. It is a simple text-based installer. The only disadvantage is that you don't get to try the Ubuntu desktop before you install. You can download the alternate CD .iso file from the [Download page]("http://www.ubuntu.com/getubuntu/download"), just click the box at the bottom. [Here]("http://users.bigpond.net.au/hermanzone/") is a page with directions.

---

### Post by akkad on 2007-05-24
:-) it really works, but i have one question here, while installation it didnt ask me to set root password, so later on  if i will be asked about the root password what shall i do???

one last thing how to enable 3d desktop ??

---

### Post by Bachstelze on 2007-05-24
No root password in Ubuntu :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

