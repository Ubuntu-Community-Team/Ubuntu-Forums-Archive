---
title: "Nikotine-Plus and azureus ports?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by chrilos on 2007-06-14
Hi I have just installed the file-sharing program nicotine-plus but I have been unable to find any songs from singer Dimitris Kokotas. can somebody help?Hehe just playing. Anyway how can I figure out which ports to use for nikotine and azureus. Thanks!

---

### Post by kingpico on 2007-06-14
i had the same problem, but with vas vas vas . What i did : apt-get open port vas 

so i guess it will be the same for u : apt-get open port kokotas 

did that help u?

---

### Post by chrilos on 2007-06-14
Thanks that was really helpful. However you need to download the Xristodoulopoulos dependency.

in the terminal type apt-get install xristodoulopoulos.tar

Don't forget to type sudo at the beginning.

Hope this helps!

---

### Post by kingpico on 2007-06-14
u mean the byzantine libraries?

---

### Post by chrilos on 2007-06-14
Exactly. However, if you are using feisty you will have to configure the klarino application. 

Try: sudo update-alternatives --config klarino
        choose byzantine-makis

This should do the trick and Kokotas will appear in the search.  But, you should still remove the problem that creates the bug this means typing in the terminal: 

rm .kiamos/afonos*

Glad I could help!

---

### Post by asymmetric on 2007-07-06
Lolzor

---

