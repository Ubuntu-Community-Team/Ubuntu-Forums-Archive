---
title: "Gamma Correction"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by 234234 on 2008-02-09
Hi.... to anyone who will be kind to help......


 I have monitor LG 1900 and ATI 9200...... and cannot correct the gamma, brightness and color...
    It is too bright.....
        I know this XGAMMA program but i don't know where to find it or even how to install it....
               Can you please give me assistance....
                    My eyes hurt....
                      I like UBUNTU, don't wanna go to Windows....
                 
                                        Thank YOu

---

### Post by randy78 on 2008-02-09
In a terminal, do:
xgamma -help

---

### Post by drtre on 2008-02-09
once i had this problem. as far as i know u should change the gamma each time you log into ubuntu. and the command is this, i guess: 
xgamma  -gamma <somthing between 0 to 10>
alternatives :
xgamma  -bgamma <somthing between 0 to 10>
xgamma  -ggamma <somthing between 0 to 10>
xgamma  -rgamma <somthing between 0 to 10>
 if you want to change the configuration permenantly you shold change the x11.conf file as root.

sorry if i've made any mistake cuz i'm not in front of my computer right now and i cant tell you for sure. but if you have further problems i can check it out later.

---

### Post by 234234 on 2008-02-09
there is this ATI Catalyst Center that i've found in forums that is to be installed...

and that could help.....

but don;t know how to install it

---

### Post by 234234 on 2008-02-09
i enter sh ./ati-driver-installer-8.28.8.run  to run the file but nothin happens

---

### Post by 234234 on 2008-02-09
nothing

i need the ubuntu cd to install the ATI catalyst,,,,,

i'm doooooooomed

---

### Post by 234234 on 2008-02-09
i did something 
started installing 
but this came up
......................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution

---

