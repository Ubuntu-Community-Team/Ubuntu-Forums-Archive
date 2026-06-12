---
title: "Firefox 2 Java Problems"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by think13 on 2006-11-01
Well, I recently manually downloaded Firefox 2.0 (I am still running 6.06, upgrading looked way too problematic).  Now I cannot get Java to run on Firefox 2.0.  Java worked fine on firefox 1

I went to a page that had information about Java and Ubuntu, and installed the package sun-java5-plugin.  I also have sun-jre1.5, sun-java-bin, and sun-java-jre packages installed.

Another interesting development is that somehow I cannot find how to run firefox1, though I did not remove that package.  Running firefox in the console gets me firefox 2.0.

Help?

---

### Post by raqball on 2006-11-01
FF2 would have overwritten all your ff files... So in theory ff does not exist anymore.

---

### Post by bihe on 2006-11-01
The ubuntu firefox package searches for plugins in 

/usr/lib/mozilla-firefox/plugins/
/usr/lib/mozilla/plugins
~/.mozilla/firefox/plugins/

I'm not sure wheter the firefox install from mozilla looks in the ubuntu
dirs. One solution would be, to copy your plugins from the /usr/lib/... 
directories to your local plugin direcotory in your home folder. 

Visit the following link to find out more: [http://plugindoc.mozdev.org/linux.html]("http://plugindoc.mozdev.org/linux.html")

---

