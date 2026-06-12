---
title: "[SOLVED] java 6 wont work"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-07-20
Well im sure it work just not for me. it shows being installed but when i go to linux survival the plug in wont work

---

### Post by crimesaucer on 2007-07-20
If you are on Firefox, type "about:plugins" in the address bar with out the quotes.

See if it says java6 plugin in the list.

---

### Post by crimesaucer on 2007-07-20
Also try this in Terminal:

```
 sudo update-alternatives --config java
```


...it will give you a list to configure your java, it will look like this:

```

blah@blah-blah:~$  sudo update-alternatives --config java
Password:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.0
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/bin/gij-wrapper-4.1
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.
blah@blah-blah:~$ 


```


...just follow directions and chose your /usr/lib/jvm/java-6-sun/jre/bin/java (which was number 2 for me)

---

### Post by trucker33377 on 2007-07-20
its not on plugins

---

### Post by crimesaucer on 2007-07-20
How about your " sudo update-alternatives --config java", is it configured correctly to java6?

---

### Post by trucker33377 on 2007-07-20
1    /usr/bin/gij-wrapper-4.1
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java
i think so

---

### Post by crimesaucer on 2007-07-20
Yes, you have it configured.

Check your Firefox plugins folder: /usr/lib/firefox/plugins

Let me know if you have a libjavaplugin.so

---

### Post by crimesaucer on 2007-07-20
You could try reinstalling it with this command in Terminal:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```


Also make sure you have all the repositories you need: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)



....then check again to make sure your java is configured correctly, also restart Firefox again to see if the plugin went to the correct place which is: /usr/lib/firefox/plugins

then it should show in the about:plugins

(I didn't mean to have a smiley, that was supposed to be "about : plugins")

---

### Post by trucker33377 on 2007-07-21
ok i did that it now comes up but its not right most of the page is missing . i checked the folder its in there. so is this one it has a box with an X in it  if that means anything /usr/lib/firefox/plugins/libflashplayer.so

---

### Post by mig5 on 2007-07-21
> **trucker33377 said:**
> ok i did that it now comes up but its not right most of the page is missing . i checked the folder its in there. so is this one it has a box with an X in it  if that means anything /usr/lib/firefox/plugins/libflashplayer.so

Have you checked /usr/lib/firefox/plugins for libjavaplugin.so ?  Where did you install java from originally, from the repos or following the guide on Sun's website?

---

### Post by trucker33377 on 2007-07-22
ive got it working now how do i mark it solved

---

