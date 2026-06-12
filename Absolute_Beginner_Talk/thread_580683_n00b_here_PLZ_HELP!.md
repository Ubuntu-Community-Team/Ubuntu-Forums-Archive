---
title: "n00b here PLZ HELP!"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by XxSRMxX on 2007-10-19
Compiz worked perfectly fine when i had Feisty now that I upgraded to Gusty I can not get anything to work. Im so confused. I've tried uninstalling and installing several times but nothing works. I really would like to have my cube back lol this is what it says when i put compiz in the terminal...

 ```
stacey@stacey-laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
```

---

### Post by DSn0wMan on 2007-10-19
I have been busy cleaning up my compiz-fusion as well. I had something newer than is actually avaiable in gutsy. The trick for me was to un-install all compiz stuff run  ```
sudo apt-get clean
``` to get rid of the local copies wich aptitude will happily install until you get rid of it because they are newer than what is in the repos.

Hope that helps.

---

### Post by XxSRMxX on 2007-10-19
I'll try this thanks for the reply!

---

### Post by XxSRMxX on 2007-10-19
well that didnt work. still getting the same results....man what is going on

---

### Post by conehead77 on 2007-10-19
Did you try this link: [http://forlong.blogage.de/](http://forlong.blogage.de/)

Compiz isnt working with the ATI propriatary driver i think. But read the blog, it explains everything very good.

---

### Post by tboutcher on 2007-10-19
they blacklisted any car that doesn't work 110% of the time. You can remove the list and it should work just fine.
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

---

