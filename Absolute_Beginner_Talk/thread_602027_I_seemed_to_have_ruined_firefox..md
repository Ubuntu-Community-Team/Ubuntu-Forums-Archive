---
title: "I seemed to have ruined firefox."
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Lui2692 on 2007-11-03
Well onto round three of questioning. Im slowly getting the hang of ubuntu, however it seems every time i try to enable something new i disable something else. Today i was experimenting with opening the compiz config panel and it locked up my computer. Then upon restarting it am unable to open any videos online and not even load  certian websites ---> vidiac.com. Any help would be great appreciated still confused as to how to manually set firefox plugins as well. Thank you all very much great community!.

---

### Post by k33bz on 2007-11-03
Did you by any chance try to reinstall Java?

---

### Post by alienexplorers on 2007-11-03
Your main plugins are Java and Flash.  You can go to:
> [https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)
to get flash player plugin.

For Java type:
> sudo apt-get install sun-java6-jdk
Then set up a symbolic link to the plugin in your firefox plugin folder.

The main java plugin will be found at:
> ls -n usr/lib/jvm/JAVA_VERSION/jre/plugin/i386/ns7/libjavaplugin_oji.so

---

### Post by Lui2692 on 2007-11-03
dont quite understand symbolic link. What is it and how do i make one. Thank you
EDIT: Also i am unable to hit ok in the Java install.

---

### Post by Dr Small on 2007-11-03
Symbolic Link is nothing more than, what is termed on Windows as a "shortcut".

---

### Post by Lui2692 on 2007-11-03
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
EDIT: for the java Plugin

---

### Post by Dr Small on 2007-11-03
```
sudo dpkg --configure -a
```

---

### Post by Sef on 2007-11-03
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

The command is ```
 sudo 'dpkg --configure -a
```.   (The op may know that, but another poster may not.)

---

### Post by Lui2692 on 2007-11-03
ahh ok ran it 
lui2692@lui2692-laptop:~```
$ sudo dpkg --configure -a
Setting up java-common (0.26ubuntu1) ...

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

what exactly does that mean? and do i need to do something more?

---

### Post by jhenager on 2007-11-03
How do I create a symbolic link?
In Terminal, type:

ln -s [TARGET DIRECTORY OR FILE] ./[SHORTCUT]

For example:

ln -s /usr/local/apache/logs ./logs

This points a symbolic link "./logs" to "/usr/local/apache/logs"

Everything you ever wanted to know about symbolic links and how to remove them, too!
[http://www.google.com/search?hl=en&q=create+symbolic+link&btnG=Google+Search](http://www.google.com/search?hl=en&q=create+symbolic+link&btnG=Google+Search)

---

### Post by jhenager on 2007-11-03
Found this answer:
This is normal and to do with triggers, if a package requires ldconfig to be run after installing a library then the trigger cause the command to be run only once at the end of installation rather than after every library is installed. ldconfig creates the necessary links and cache to shared libraries.
here:
[https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/15849](https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/15849)

---

