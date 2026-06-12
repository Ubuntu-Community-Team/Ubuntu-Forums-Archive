---
title: "Launching an App?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-02-05
Hi,

I have finally managed to install VMware Workstation on my Ubuntu box and I am able to launch it from the terminal...

```

root@ubuntu64:/usr/bin# vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)

```

My problem is, I cannot launch the program from it's icon in **Applications>System Tools>VMware Workstation.**  If I click on it, it tries to start, but just doesn't get going.

Any help will be greatly appreciated.

---

### Post by darrenm on 2007-02-05
sudo apt-get remove libdbus-1-2

---

### Post by Norfolk 'n' Good on 2007-02-05
Thanks for your quick reply darrenm.

I tried your suggestion but it didn't work.  I was taking another look at the code, however, and was wondering... does the launch problem have something to do with the program not recognizing the .png file?  If so, How might I connect the two up?

---

### Post by darrenm on 2007-02-05
Hmmm, normally works for me.

Loads of suggestions here:
[http://64.233.183.104/search?q=cache:zaKEGoq6giQJ:www.vmware.com/community/thread.jspa%3FmessageID%3D566958%26tstart%3D0+vmware+libpng12.so.0&hl=en&ct=clnk&cd=1&gl=uk&client=firefox-a](http://64.233.183.104/search?q=cache:zaKEGoq6giQJ:www.vmware.com/community/thread.jspa%3FmessageID%3D566958%26tstart%3D0+vmware+libpng12.so.0&hl=en&ct=clnk&cd=1&gl=uk&client=firefox-a)

---

### Post by Rui Pais on 2007-02-05
it looks like some incompatible 32/64bits library checks...

read [this thread]("http://www.vmware.com/community/message.jspa?messageID=439407") on vmtn forum and see if suggestion on the third post counting from the end is of any help...

you could also try to ask on the [x84_64 forum]("http://ubuntuforums.org/forumdisplay.php?f=134") instead of the Absolute Beginner Talk where you get the attention of more specialized people on those kind of incompatibilities...

---

### Post by Norfolk 'n' Good on 2007-02-05
Thank you for all your help, in particular, Rui Pais.  Your suggested reading allowed me to solve my problem in minutes.  But now I have pulled all my hair out could you suggest a regrowth formula?:lolflag:

---

### Post by Rui Pais on 2007-02-05
No prob. [Formula in portuguese]("http://www.suneticsportugal.com/?gclid=CMKXv9uYl4oCFSQ8Xgody1tAkg")... but the images to for themselfs. ;)

Nice to know that it worked. It was a shot in the dark, a lucky guess (my main focus was point to a better forum but seems you wont need it after all. Good)

---

