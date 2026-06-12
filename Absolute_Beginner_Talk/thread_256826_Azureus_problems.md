---
title: "Azureus problems"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-13
hello im using azuresus but it will work for 5 minutes then it closes and then a popup window come up and when i press "hide" it just wont go away and all my downloads stops :( please help

---

### Post by skymt on 2006-09-13
There are two workarounds for the pop-up not closing. One involves upgrading to the latest Azureus development version. This can create problems, so we'll go with the other one. Believe it or not, if you open the About window (Help > About Azureus), you can close the pop-up. :rolleyes: What a fix, huh?

I can't help you with your downloads stopping unless you tell me what the pop-up says.

---

### Post by Zaid on 2006-09-13
Same thing happens to me.

---

### Post by haxer on 2006-09-13
Azureus did not shutdown tidily. Check /home/oem/.asureus/logs/save for diagnostic log files and consider reporting them to Azureus team if this is the result of an application error .Also check the Wiki (see the help menu)for `Azureus Disappears` 

What the hell is the program talking about?

---

### Post by haxer on 2006-09-13
Yeah that helped to close the window but Azureus is still ****** up :(

---

### Post by haxer on 2006-09-13
please help :(

---

### Post by skymt on 2006-09-13
Are you using Sun Java?

To find out, run "update-alternatives --display java" and post the output.

---

### Post by haxer on 2006-09-13
oem@haxer:~$ update-alternatives --display java
java - status is auto.
 link currently points to /usr/lib/jvm/java-gcj/jre/bin/java
/usr/bin/gij-wrapper-4.1 - priority 41
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.1.1.gz
/usr/lib/jvm/java-gcj/jre/bin/java - priority 1041
 slave java.1.gz: /usr/lib/jvm/java-gcj/man/man1/java.1.gz
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java - priority 53
 slave java.1.gz: /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/man/man1/java.1.gz
/usr/bin/java-sablevm - priority 350
 slave java.1.gz: /usr/share/man/man1/java-sablevm.1.gz
Current `best' version is /usr/lib/jvm/java-gcj/jre/bin/java.
oem@haxer:~$


Thats what i got ... and do you know how to update so i can get frostwire working?

---

### Post by skymt on 2006-09-13
Okay, easy. Run this command:```
sudo update-alternatives --config java
```Choose /usr/lib/jvm/java-1.5.0-sun/jre/bin/java from the list. That should make Frostwire work also.

---

### Post by haxer on 2006-09-13
Thanks that really helped me hehe.. your the best omg one little thing solved the whole thing damn i love this forum and linux :)

---

### Post by antonius1 on 2007-06-14
This is what I got when I typed in "update-alternatives --display java": 
java - status is manual.
 link currently points to /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java - priority 53
 slave java.1.gz: /usr/lib/jvm/java-1.5.0-sun/jre/man/man1/java.1.gz
/usr/bin/gij-wrapper-4.1 - priority 41
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.1.1.gz
Current `best' version is /usr/lib/jvm/java-1.5.0-sun/jre/bin/java.

I am running fiesty 7.04 and I think there might something wrong with my display drivers or my actual video card b/c I had trouble with playing videos, displaying certain graphics, and screen refreshing when i was running windows now it seems the problem has followed me to ubuntu.  I love the desktop effects and wobbling windows.  I am such an ubuntu newbie please help.

---

