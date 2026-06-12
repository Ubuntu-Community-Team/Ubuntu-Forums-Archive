---
title: "Problem with javac installation"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by linuxneeewb on 2008-04-15
Dear all:

I tried to install javac by following some of the tutorials online. I got the right dependencies, and then I did the command
sudo apt-get install sun-java5-jdk 

For some reason my internet connection broke for a bit, and thus the installation of the package failed.

I tried doing both of the commands

sudo aptitude remove sun-java5-jdk
sudo apt-get remove sun-java5-jdk

But none of them work. I keep getting the response 
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


All I want to do is to simply have javac installed. I do not mind if I have to uninstall the package, and then re-install it. I would appreciate any and all help that you can give. Thanks.

:guitar:

---

### Post by thebigbluecan on 2008-04-15
Did you try installing Java through Synaptic Package Manager? Just make sure to turn on turn on the universe and multiverse repositories  :popcorn:  Thats How I got Java on my machine.

---

### Post by kpkeerthi on 2008-04-15
Just run that command as it says and then reinstall jdk
```
sudo dpkg --configure -a
```

---

### Post by linuxneeewb on 2008-04-15
Thanks a lot. You saved me so much time. Works perfectly now!!!

:lolflag:

---

