---
title: "Make downloaded file executable"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-11-24
hi, i'm in the middle of installing Sun Java. i'm following the guide from [here](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java)  i'm up to  step#5 - Make the downloaded file executable.  i ran the command:
chmod +x jre-1_5_0_05-linux-i586.bin

it says "cannot access `jre-1_5_0_05-linux-i586.bin': No such file or directory.
 in the guide they use the last Java version jre-1_5_0_04 not jre-1_5_0_05

the file is on my desktop. what should the command be? thanks

---

### Post by aysiu on 2005-11-24
Try ```
cd Desktop
chmod +x jre-1_5_0_05-linux-i586.bin
```

---

### Post by Danielle on 2005-11-24
thanks for the help it worked. but now the very last command won't work:
 dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb
when i type it i get this message:
dpkg: requested operation requires superuser privilege

i tried putting sudo in front but it won't work :( do you know how to fix it? thanks

---

### Post by invalid on 2005-11-24
It should work with```
sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb
```

Cb

---

### Post by aysiu on 2005-11-24
[QUOTE=Danielle]
i tried putting sudo in front but it won't work[/QUOTE] "It won't work" isn't good enough. What happened? What was the error? Post the output.

---

### Post by Danielle on 2005-11-24
thanks, invalid and aysiu. it worked! i had alook at what i wrote first time around and i misspelled sudo, i wrote sudu :(

---

