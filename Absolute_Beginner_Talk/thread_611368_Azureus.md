---
title: "Azureus"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-11-12
I really don't get this. I think I just intalled Azureus. In a terminal I typed this:

sudo aptitude install azureus

I got the little blue frog in internet drop down menu, It starts to come up, acts like it wants me to set it up by asking for English, then it just goes away. What gives?

---

### Post by taurus on 2007-11-12
Do you have java (either Sun or Blackdown) on your machine?

Applications -> Accessories -> Terminal
```
java -version
```
Otherwise, try running it from a terminal to see what's wrong with it.

```
azureus
```

---

### Post by bgast1 on 2007-11-12
This is the output for Java

bob@bob-desktop:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
bob@bob-desktop:~$ 

I don't know how to run azureus from a terminal.

---

### Post by Maestro23 on 2007-11-12
> **bgast1 said:**
> This is the output for Java

bob@bob-desktop:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
bob@bob-desktop:~$ 

I don't know how to run azureus from a terminal.

Taurus told you. Open a terminal:

> azureus

---

### Post by bgast1 on 2007-11-12
This is the output when I try to run azureus from a terminal:

[PHP]bob@bob-desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E4350500214), pid=12161, tid=3084852112
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid12161.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
bob@bob-desktop:~$ 

[/PHP]

---

### Post by Casual Fan on 2007-11-12
applications>accessories>terminal
type azureus

or ALT-F2, select 'run in terminal' and type azureus in the textbox

---

### Post by bgast1 on 2007-11-12
By the way, the reason why I want to try Azureus is becase I want to see if I can download any faster. I am using Deluge and it is slow as molasses. I have a freaking torrent downloading at 3.1 KiB/s. That's ridiculous. Even with Comcast pulling their shenanigans, I would think I can do better than that. People are uploading faster than I am downloading.

I've done a little work since posting the above. I am certain that I have the right version of Java installed now. Even if I didn't before. I went to the Java site and ran their check to see if it was the right version and it came back Congratulations......etc.

Azuerus still doesn't run though.

---

