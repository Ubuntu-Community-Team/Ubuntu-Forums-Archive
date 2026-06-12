---
title: "Update Manager Down again, and I don´t know why!"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by ela04cz on 2007-07-15
My update manager is down after I tried to install Automatix2, and I still haven´t figured out what is wrong with the etc/apt/sources.list fine. 

This is the out put of sudo apt-get -f install 
E: Type &#8216;¨deb&#8217; is not known on line 47 in source list /etc/apt/sources.list
E: The list of sources could not be read.

I used cat /etc/apt/sources.list to see the file, it includes a faulty line at the end read ¨deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main¨ (including the quotation marks, so definitely wrong)

However, when I gksudo nano /etc/sources.list trying to edit it, the file looks all right! Without that faulty line at the end! I guess probably I edited it before not using the nano but open the sources.list.save file from root and delete the line, but the system doesn´t know this change yet. Can someone help me with this please?

The last line is the faulty one I reckon, but I cannot see it from nautilus root or gksudo nano /etc/apt/sources.list

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
¨deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main¨

Many thanks to anyone who looks through this.

---

### Post by ela04cz on 2007-07-15
My update manager is down after I tried to install Automatix2, and I still haven´t figured out what is wrong with the etc/apt/sources.list fine.

This is the out put of sudo apt-get -f install
E: Type ‘¨deb’ is not known on line 47 in source list /etc/apt/sources.list
E: The list of sources could not be read.

I used cat /etc/apt/sources.list to see the file, it includes a faulty line at the end read ¨deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main¨ (including the quotation marks, so definitely wrong)

However, when I gksudo nano /etc/sources.list trying to edit it, the file looks all right! Without that faulty line at the end! I guess probably I edited it before not using the nano but open the sources.list.save file from root and delete the line, but the system doesn´t know this change yet. Can someone help me with this please?

The last line is the faulty one I reckon, but I cannot see it from nautilus root or gksudo nano /etc/apt/sources.list

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
¨deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main¨

Many thanks to anyone who looks through this.
__________________

---

### Post by mcduck on 2007-07-15
You have some extra characters on the last line:
```
¨deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main¨
```
should be:
```
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
```

Also, you said you used "gksudo nano /etc/sources.list" to edit the file. That won't work, as the file is in /etc/apt/sources.list..

---

### Post by rax_m on 2007-07-15
You could try a different editor like gedit, maybe that will show up the characters.

Otherwise, copy all of the lines that are correct into a new file, save as a different name. Then rename the existing sources and mv then rename the new one to sources.list. 

But convoluted but I can't think of any reason why it shouldn't work. 

Rax

---

