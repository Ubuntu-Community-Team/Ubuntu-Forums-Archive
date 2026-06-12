---
title: "Where to find and how to install gimp-help"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by wink on 2007-05-27
Full-blown newbie (that's me) is trying his hand with Gimp. Unfortunately the Help files were not installed so now I need help locating and installing them.

Thanks for your help in advance.

---

### Post by Ek0nomik on 2007-05-27
```
dove@edelweiss:~$ sudo aptitude search gimp-help
Password:
v   gimp-help                       -                                           
p   gimp-help-common                - Data files for the GIMP documentation     
p   gimp-help-cs                    - Documentation for the GIMP (Czech)        
p   gimp-help-de                    - Documentation for the GIMP (German)       
p   gimp-help-en                    - Documentation for the GIMP (English)      
p   gimp-help-fr                    - Documentation for the GIMP (French)       
p   gimp-help-it                    - Documentation for the GIMP (Italian)      
p   gimp-help-nl                    - Documentation for the GIMP (Dutch)        
p   gimp-help-sv                    - Documentation for the GIMP (Swedish)      
p   gimp-help-zh-cn                 - Documentation for the GIMP (Chinese Simpli
p   gimp-helpbrowser                - Built-in Help Browser plugin for The GIMP
```

To install:

```
sudo aptitude install xxx
```

Where xxx is your package name.

---

### Post by wink on 2007-05-27
Thank you very much, exactly what I needed. 

 I guess it's easy to tell from my number of beans what a newbie I am.;)

---

