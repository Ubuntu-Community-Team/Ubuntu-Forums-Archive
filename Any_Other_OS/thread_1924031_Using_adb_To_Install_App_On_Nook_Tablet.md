---
title: "Using adb To Install App On Nook Tablet"
date: 2012-02-11
forum: Any Other OS
---

### Post by doppel.ganger on 2012-02-11
[FONT="Arial Black"][SIZE="4"][COLOR="Red"]ATTENTION ALL ANDROID DEVELOPERS:[/COLOR][/SIZE][/FONT]
I downloaded Android SDK for Linux and put the resulting folder in Documents. Then I opened 'android' and installed ALL the extra sdk's and features. I also downloaded the Amazon App Store app file (apk) from the Amazon website. I then opened a terminal and executed the following in an attempt to install Amazon App Store on an unrooted Nook Tablet running os version 1.4.1.
```
thomas@Thomas-Desktop:~$ cd ~/Documents/android-sdk-linux/platform-tools
thomas@Thomas-Desktop:~/Documents/android-sdk-linux/platform-tools$ ./adb install ~/Documents/Amazon-Appstore-release.apk
error: device not found
thomas@Thomas-Desktop:~/Documents/android-sdk-linux/platform-tools$
```
Why is it not seeing my Nook Tablet?

---

### Post by doppel.ganger on 2012-02-12
Why isn't seeing my nook tablet?

---

### Post by doppel.ganger on 2012-02-13
Hello? I fear i must *BUMP* this thread.

---

### Post by Bodsda on 2012-02-13
> **doppel.ganger said:**
> Hello? I fear i must *BUMP* this thread.

Please don't. This is an ubuntu related support forum for beginners, you would have better luck on an android development forum or in the programming talk sub forum on here.

Bodsda

---

### Post by drillerccg on 2012-03-03
you may not have sdk and adb setup correctly. Heer is what I have written on XDA
[http://forum.xda-developers.com/showpost.php?p=19446284&postcount=62](http://forum.xda-developers.com/showpost.php?p=19446284&postcount=62)

---

