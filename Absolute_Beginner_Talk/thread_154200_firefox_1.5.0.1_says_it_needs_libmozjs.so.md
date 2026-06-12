---
title: "firefox 1.5.0.1 says it needs libmozjs.so"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by buckykat on 2006-04-02
i have searched the posts, and found directions to install firefox 1.5.0.1 . they don't work for me on ubuntu 5.10. the terminal looks like this:
buckykat@buckykat:~$ cd ~/Desktop
buckykat@buckykat:~/Desktop$ sudo /home/buckykat/Desktop/firefox-bin
/home/buckykat/Desktop/firefox-bin: error while loading shared libraries: libmoz js.so: cannot open shared object file: No such file or directory
buckykat@buckykat:~/Desktop$ sudo apt-get install libmozjs
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libmozjs
buckykat@buckykat:~/Desktop$ sudo apt-get install libmozjs.so
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libmozjs.so
buckykat@buckykat:~/Desktop$
help please!

---

### Post by aysiu on 2006-04-02
[QUOTE=buckykat]
buckykat@buckykat:~/Desktop$ sudo /home/buckykat/Desktop/firefox-bin[/QUOTE] What instructions told you to do this?

Try this instead:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Haegin on 2006-04-27
I have now got this problem (or a similar one) and no matter how I install firefox it still has problems. Whenever I run firefox I get told it needs libmozjs.so when I can quite clearly see it on the system using locate.

Any ideas?

---

### Post by joshrobinson on 2006-04-27
[QUOTE=Human Prototype]I have now got this problem (or a similar one) and no matter how I install firefox it still has problems. Whenever I run firefox I get told it needs libmozjs.so when I can quite clearly see it on the system using locate.

Any ideas?[/QUOTE]

i have that file located in my /usr/lib/firefox directory
you want me to upload the file for you to see if you can put it in there?

---

### Post by joshrobinson on 2006-04-27
[QUOTE=joshrobinson]i have that file located in my /usr/lib/firefox directory
you want me to upload the file for you to see if you can put it in there?[/QUOTE]

[http://www.ground-impact.com/libmozjs.so]("http://www.ground-impact.com/libmozjs.so")

right click save to disk.. just clicking it wont work probibly

---

