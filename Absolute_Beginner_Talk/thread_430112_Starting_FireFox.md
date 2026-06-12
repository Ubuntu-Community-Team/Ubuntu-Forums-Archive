---
title: "Starting FireFox"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by iaow on 2007-05-01
Hi,

I recently installed Ubuntu 7.04 and tried running the Firefox browser to surf the internet. Unfortunately, it didn't start. The Firefox icon would appear on the taskbar on the bottom of the screen and closed.

For what it's worth, my internet connection is good. I was able to chat using Gaim.

Please help. Thanks. Janet.

---

### Post by taurus on 2007-05-01
Can you start it from a terminal to see what the error message is?

Applications -> Accessories -> Terminal
```
firefox
```

---

### Post by iaow on 2007-05-01
"Segmentation Fault (core dumped)"

I had this error the first time so I deleted all my partitions and rebooted the system using the LiveCD. Still have the same problem.

---

### Post by taurus on 2007-05-01
You mean you deleted and reinstalled Feisty, not deleted and ran from LiveCD!

Are you using 32bit or 64bit of Feisty?  Is firefox the only app that gives you that "Segmentation Fault (core dumped)" error message?

---

### Post by iaow on 2007-05-01
I used the 32-bit.

Other programs are fine. Only Firefox is giving me trouble. Are there any other browsers I can use? I just want to be able to surf the net. Any browser is fine with me.

---

### Post by bobplano on 2007-05-01
there are plenty of other browsers. iceweasel and epiphany are based on firefox and then there is the other mozilla browser, opera, and konquerer, not to mention lynx (text-based though)

---

### Post by taurus on 2007-05-01
You can check out swiftfox which is a little faster than firefox and of course, there is also opera.

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox)
[http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by iaow on 2007-05-01
I cannot use a browser so how am I going to download those files?

---

### Post by bobplano on 2007-05-01
apt-get, synaptic or add/remove works as long as you have an internet connection

---

### Post by iaow on 2007-05-01
Do I type the following command in the terminal?

sudo apt-get update && sudo apt-get install swiftfox

Thanks.

PS. Forgive me for the novice questionings. Janet.

---

