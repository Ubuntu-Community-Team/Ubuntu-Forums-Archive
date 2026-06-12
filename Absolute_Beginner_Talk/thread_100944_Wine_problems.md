---
title: "Wine problems"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by cjm5229 on 2005-12-08
I'm having a problem using wine. I tried to install a windows program, and got a fatal error in the install shield. now I have the install shield in notification toolbar and It won't go away. I tried closing it and rebooted the computer and it is still there. How can I kill it. Also where can I find instructions or a how to on using wine. I would like to be able to run my windows money program. I seem to be getting everything else dialed in quite nicely with a lot of help in the forums. Just about ready to remove my Windows XP partition, and I am ready to remove my linspire partition. Ubuntu Is Great!
Thanx, Carl

---

### Post by justin_p on 2005-12-08
I have had the same problem everytime I have tried to install something with wine.  [http://www.winehq.com/site/documentation](http://www.winehq.com/site/documentation) can give some good tutorials on setting it up.  Like I said, I have never had any luck.  What program are you trying to run?  Is there no Linux alternative?  I have been windows free at home for 3 years.

---

### Post by ltmon on 2005-12-08
[http://winehq.org](http://winehq.org) has an applications database which you can search for your particular software and find out if anyone else has had any success with it.

L.

---

### Post by YokoZar on 2005-12-08
To kill Wine you have several options.  The easiest is to open a terminal and type *wineserver -k*.  If that doesn't work, another option is to *killall -9 wine-preloader*.

---

### Post by cjm5229 on 2005-12-08
Thanx for the help. That killed the window. I will study that wine guide for awhile before I try it again. The main program I want to install is Microsoft Money, Just because I don't want to have to try to transfer all the info in it to something else. I really think I could live without just about everything else about Windows. :) If I could export the info to something like MyMoney I wouldn't even need that. I really appreciate the speed with which a problem can be solved in Ubuntu Forums, A few other Linux Forums I tried, it seemed like no one really wanted to help a noob. Hey, we all gotta start somewhere, It seems like this is the place to start. 
Carl

---

### Post by ltmon on 2005-12-08
[http://appdb.winehq.org/appview.php?versionId=2728](http://appdb.winehq.org/appview.php?versionId=2728)

There's a nice howto on any little adjustments you need to make to get MS Money 2004 to work.

L.

---

