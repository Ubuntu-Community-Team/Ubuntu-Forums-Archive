---
title: "So I've installed Ubuntu"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by theparoxysm on 2008-03-03
But I need help with two things.  Firstly it doesn't seem to recognise the wireless card built into this laptop, is there any way to correct this? I very sparingly need WiFi, maybe for an hour a month max, normally I use a hardline.

Also, anyone know where to find the JRE? I do programming in Java, and wanted to get a version for Linux that would work with Ubuntu, as well see if I could contribute to the Ubuntu Community.

---

### Post by aysiu on 2008-03-03
Please tell us what model wireless card you have.

---

### Post by wheredidrealitygo on 2008-03-03
If you don't know what kind of card you have, try going to a terminal (command line) and typing
```
lspci
```, and pasting the output here.

Then we can point you in the right direction :)

---

### Post by bren on 2008-03-03
1) wireless yes, you may need to install a driver.    Depending on your hardware this can be easy or tricky.   
2) type the following command into a terminal window and paste the results back here
> 
sudo lshw -C network
Then we know which hardware we are working with....
3) Java - i know nothing


bren

---

### Post by jcwmoore on 2008-03-03
Java:

go to System>Admin>Synaptic Package Manager

then go to Settings>Repositories

Make sure that all the Repositories are seleceted, then exit the window and click Reload

Then search for "Sun Java" and select the Sun Java JRE package to install

---

### Post by Jabz.biz on 2008-03-04
I have the same problem like theparoxysm. Wireless is not working... :(

@jcwmoore
The wireless has something to do with Java? But ok,...I`m n00b, I`m desperate...so I try. :) 

After clicking on Settings > Repositories I get this window with 5 Tabs...

1. Ubuntu Software
2. Third Party Software
3. Updates
4. Authentication
5. Statistics

Which Repositories need to be seleceted? In what Tab? ... I have no clue :) 
Thanks for your help.

---

### Post by jcwmoore on 2008-03-04
it should be the default tab... Ubuntu Software, if you have all of the options enabled, then you should be able to install java...

you really only need to be concerned with the Ubuntu Software tab...

---

### Post by nmartine on 2008-03-04
So, you go to filters and look at the origin?

---

### Post by Jabz.biz on 2008-03-04
Ok, got it. Nice... :) Thanks a billion.

---

### Post by bren on 2008-03-04
Jabz 

java has nothing to do with your wireless problem - they are entirely separate

the original poster had 2 questions in one post

jabz - if you want help with wireless you have to tell us your hardware - see any of posts #2-4 above

bren

---

### Post by stchman on 2008-03-04
> **theparoxysm said:**
> But I need help with two things.  Firstly it doesn't seem to recognise the wireless card built into this laptop, is there any way to correct this? I very sparingly need WiFi, maybe for an hour a month max, normally I use a hardline.

Also, anyone know where to find the JRE? I do programming in Java, and wanted to get a version for Linux that would work with Ubuntu, as well see if I could contribute to the Ubuntu Community.

Yes give us an lspci output so we can see what chipset your wireless card uses.

As far as java, use th following in a terminal to install the JRE and JDK.

```

sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```

---

