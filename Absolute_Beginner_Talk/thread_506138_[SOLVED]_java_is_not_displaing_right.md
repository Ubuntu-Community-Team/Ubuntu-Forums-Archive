---
title: "[SOLVED] java is not displaing right"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-07-21
i just got my java to start working but its not working right. its not showing the whole screen when it displays

---

### Post by Daveth on 2007-07-21
which java version? 6? and did you install it with Synaptic?

---

### Post by trucker33377 on 2007-07-21
6 yes ive installed in synaptic now. its displaying but its flickering... also at java site says i need to update
	   Verifying Java Version

Oops! You don't have the recommended Java installed.
Your Java version is 1.4.2. Please click the button below to get the recommended Java for your computer.

---

### Post by RomeReactor on 2007-07-21
Hi. Close your browser and make sure you have the necessary packages installed; search for **sun java 6** in Synaptic and install **sun-java6-bin, sun-java6-fonts, sun-java6-jre** and **sun-java6-plugin**; or, to install from the terminal (Applications->Accessories->Terminal):
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```
Also, which browser are you using?

---

### Post by trucker33377 on 2007-07-21
im using firefox

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/java-gcj/jre/bin/java
 +        4    /usr/lib/j2se/1.4/bin/java
maybe this will help you help me

---

### Post by RomeReactor on 2007-07-21
That would be No. 2, **/usr/lib/jvm/java-6-sun/jre/bin/java**.

---

### Post by trucker33377 on 2007-07-21
yes it works but it flickers is there anything that can be done

---

### Post by crimesaucer on 2007-07-21
Hello, I'm glad you got java working from last night, I'm not sure about the "flickering" or the "not showing the whole screen" problems that you are having.


You might want to take a screenshot picture of your screen display problem and your flicker problem so you can get some help with that.

---

### Post by trucker33377 on 2007-07-21
well i think i got it all but the flickering but im not sure its even java related it seems to do it here as i type if you understand what in speaking of the line on the screen that shows your place

---

### Post by RomeReactor on 2007-07-21
The only thing I can think of that could be related to that could be a low refresh rate. What video card do you have? If it's Nvidia, try running running **nvidia-settings** from the terminal and increase the refresh rate.

---

### Post by trucker33377 on 2007-07-22
that sounds right i dont remember with i have off hand but its a few yrs old and has a 128 mb cash. its a cast off from my other computer that i upgraded

---

