---
title: "Help with Java"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by camz on 2007-03-23
After realising I can install Java from the Add/Remove Programs List, I attempted it, but the amount of progress I had made installing it manually made it impossible to install.

Here is what I did.

 How to install JRE v6.0

    * Read #General Notes
    * Read #How to add extra repositories 

    * Navigate to [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) 

Choose "Java Runtime Environment (JRE) 6" and click on "Download"
Accept License Agreement 
Download the "Linux self-extracting file"

    * Install the required tool : 

> sudo aptitude install java-common

    * Create the Ubuntu package : 

> fakeroot make-jpkg jre-6-linux-i586.bin

    * Install the resulting package : 

> sudo dpkg -i sun-j*.deb


    * Restart Mozilla Firefox 

I got as far as the fakeroot part until it messed up, could someone let me know whow to erase these settings so I can install JRE 5.0 from Add/Remove.

---

### Post by camz on 2007-03-23
plz help

---

### Post by camz on 2007-03-23
please

---

### Post by pirothezero on 2007-03-23
Have you tried using something like easyubuntu or automatix2?

---

### Post by camz on 2007-03-23
I have a new, smaller problem. I have managed to get into installing JRE in the Terminal, but I can't agree to the licence! It's a blue screen with an agreement on it how can I agree? What button? Oooo

---

### Post by camz on 2007-03-23
Woohoo I Did It. Nvm Now!

---

