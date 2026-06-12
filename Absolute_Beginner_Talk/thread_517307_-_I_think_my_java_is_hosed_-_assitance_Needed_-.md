---
title: "- I think my java is hosed - assitance Needed -"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by KevinD_Atl on 2007-08-04
[FONT="Tahoma"][SIZE="3"]My Azurues was going slow as could be and then would stop.  Upon some investigation I found that you need the Java 1.5, and Ubuntu installs 1.4 by default. So I needed to update to this version. I've tried everything and tried to install the updates using many methods.  Here's what I get when I do the java -version 

root@Ubu:/home/kevind# java -version
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found
root@Ubu:/home/kevind# 

If I do the javac -version , i then get it states it installed 1.6.  However, my Azurues doesn't even load at this point.  Can I remove all of these and start from scratch?


[/SIZE][/FONT]

---

### Post by nitro_n2o on 2007-08-04
read this: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) and install the Sun java

---

### Post by TrashmanL on 2007-08-04
I looked up Sun Java 6 in the multiverse and installed it. Installation seemed to go OK, but when I ran Firefox, sites requiring java still said I had none. I tried Sun Java 6 first, but in the end I had to install the Blackdown Java 1.4 before the Java plugin worked and I could get Java in my browser.

Is there something I might have done wrong? I installed Sun Java 6 right from Add/Remove program, I figured that would be the fool proof way of doing it.

---

### Post by TrashmanL on 2007-08-04
Update: Though I couldn't get Sun Java 6.0 to work (I installed both the Console and WebStart), when I installed the Sun Java 5.0 Plugin and Runtime they worked fine in my browsers. Personally, I would like to have the most up to date version, but 5 is definitely better than 4. 

I'm just an Ubuntu/Linux n00b, but I did manage to get 5.0 to work so I may be of some help. I've got Fiesty Fawn (7.04). What version of Ubuntu are you using? 

Is there some reason you're trying to install Java from the command line? I've found the Gnome Add/Remove Applications GUI that was included to be very powerful and helpful. You don't have to manually edit any files to change configurations, You just have to select Show: "All available applications" and the multiverse is enabled. Alternately, these options are spelled out when I click on Preferences. Then just search for Java in the search bar, and all the available Java versions are shown and install with a click. Much easier than using apt-get for n00bs like me.

---

### Post by TrashmanL on 2007-08-15
Another update, incase anyone cares. I haven't done anything new, but I checked my java version using about: java and it said I was using Java 6. When I activated the console while using Java, it also said I was using Java 6. Oddly, when I only installed Java 6, the plugin didn't work, but when I installed the Java 5 plugin on top of Java 6, not only is Java working, but running Java 6. I don't know why, but it worked for me.

---

