---
title: "Install Java"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by CoCoKnots on 2008-04-14
I have been trying to download & run Java (jre-6u5-linux-i586-rpm) with Ubuntu. 
I make it thru the Lic Agreement, but when I try to run it, I receive an 
error "Could Not Open jre-6u5-linux-i586.rpm" Archive Type Not supported. I've 
been working on this all week-end. Do you have any idea what I could be doing 
incorrectly ? 
I have followed instructions on pages 235 &236 of Linux for Dummies to add Java. 
Number 16 states to "Double Click the j2re RPM file" The RPM is installed for 
you. You now have Java support".
There is no file called 'j2re RPM' on my computer. Is this an error ? Please 
Help... Thanks, Cal

---

### Post by perlluver on 2008-04-14
There is a much easier way to get Java in Ubuntu.  Look in synaptic for Sun Java, RPM, doesn't really work in Ubuntu.  You would need a .deb or the .bin self installing java package from Sun.com.

---

### Post by kwacka on 2008-04-14
deleted

---

### Post by perlluver on 2008-04-14
Also you can open up a terminal and type ```
sudo apt-get install ubuntu-restricted-extras
``` and that will bring Java with it.

---

### Post by Seisen on 2008-04-14
The correct way to install Java is enable the multiverse repository in your source list and then ```
sudo apt-get update
sudo apt-get install sun-java6-bin, sun-java6-jre sun-java6-plugin
```

---

### Post by CoCoKnots on 2008-04-14
Thanks Perlluver, Whei I tried that... This is a new error I received.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
cocoknots@cocoknots-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

Any idea what I need to do now ?
Thanks,
Cal

---

### Post by CoCoKnots on 2008-04-14
Thanks Seisen,

I received the same dpkg configure -a error I just posted.

Cal

---

### Post by forrestcupp on 2008-04-14
You need to put **sudo** before the dpkg --configure command.  That output is one of the dumb mistakes that needs to be corrected.

Also, to enable the multiverse repository, go to System->Administration->Software Sources, and in the Ubuntu Software tab, just make sure all of the boxes are checked.  You need that for java.

Edit:
But thank you for actually trying what the output says to do.  You wouldn't believe how many people don't pay attention.

---

### Post by RedRat on 2008-04-14
> **Seisen said:**
> The correct way to install Java is enable the multiverse repository in your source list and then ```
sudo apt-get update
sudo apt-get install sun-java6-bin, sun-java6-jre sun-java6-plugin
```

Tried this but got an error message:
Couldn't find package sun-java6-bin

Does this mean that the bin is no longer in the repo??

---

### Post by RedRat on 2008-04-14
OK solved that problem. You had a comma after the sun-java6-bin. Took that out and it went through ok.

---

### Post by friartuck on 2008-04-14
Yups forrestcupp  tolld me the same I posted the same kind of message and he helped me out.

---

