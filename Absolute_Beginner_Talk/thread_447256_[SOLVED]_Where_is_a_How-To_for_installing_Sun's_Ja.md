---
title: "[SOLVED] Where is a How-To for installing Sun's Java"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-05-17
I am trying to figure out how to install Sun JAVA on the Feisty Fawn.

I looked here:

[http://ubuntuforums.org/showthread.php?t=402663&highlight=feisty+installing+java](http://ubuntuforums.org/showthread.php?t=402663&highlight=feisty+installing+java)

and here:

[http://ubuntuforums.org/showthread.php?t=434964&highlight=feisty+installing+java](http://ubuntuforums.org/showthread.php?t=434964&highlight=feisty+installing+java)

but the two posts seem to have conflicting info.

Will apt-get (or better aptitude) install java? I thought there was more to it than running the Synaptic Update Manager. Is it configuring the Java once it's installed that's the "high learning curve".

Please somebody throw me a fastball and I'll it it out of the park.

---

### Post by bobplano on 2007-05-17
it looks like the second thread has the commands you need. i don't really recall configuring java, but then again i used automatix.

---

### Post by Michaelt74 on 2007-05-17
Applications>Add/Remove, On the top right hand window, click on 'Show: All available applications'
Search for Sun Java and select which one you want to install.

Good luck!

---

### Post by Seisen on 2007-05-17
You can either use synaptic to install Java or you apt-get or aptitude. The difference between apt-get and aptitude is that aptitude install the files that are associated that the file you are installing. To install in Synaptic do a search for sun-java6-jre

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by Prometheus.172214 on 2007-05-17
It should be easier for you to do this via the Add / Remove or via Synaptics Package Manager. I have seen the direct installation options for various Sun JAVA related packages and addins there.

---

