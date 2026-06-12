---
title: "installed Ubuntu via text installer and..."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by crazydiver on 2007-06-15
Hello

  I just installed Ubuntu via text installer and after restarting I run Ubuntu.After booting Ubuntu A message on the bottom of my screen appears... To the best of recollection it read Kernel Alive and etc... thereafter my screen just goes blank. Got me puzzled. Any suggestions?

---

### Post by w4ett on 2007-06-15
What video card are you using?

---

### Post by overdrank on 2007-06-15
> **w4ett said:**
> What video card are you using?

If you can post the output of this command in terminal lspci  (terminal is under applications, accessories, terminal) That will help us help you!:KS

---

### Post by crazydiver on 2007-06-15
I am using Asus EN8500GT Silent  512mb  vid card


I just realized right now that my grammar was way bad!~ Corrected it! And thanks for understanding! mUst be really tired!~

---

### Post by crazydiver on 2007-06-15
overdrank,

  Sorry but I don't quite know where terminal lspci is at... I don't think I can access while I am booting...

---

### Post by overdrank on 2007-06-16
> **crazydiver said:**
> overdrank,

  Sorry but I don't quite know where terminal lspci is at... I don't think I can access while I am booting...

Ok sorry I will try to clarify: Ok we know which video card you are using. Asus EN8500GT (nvidia)
When you get to the blank screen, using the key pad hit alt,ctrl.F1 keys all at the same time this will enter the terminal. First enter your user name and password. Then enter the command *sudo dpkg-reconfigure -phigh xserer-xorg* this will configure your xorg to where you can boot into ubuntu. ( Hopefully) Then you can install the proper drivers using envy script. Good luck and hope this helps!:KS

---

### Post by crazydiver on 2007-06-19
Sorry for not replying soon, I was out on business! Thanks... eveything seems OK now... I really appreciate the support everyone!

Peace!

---

