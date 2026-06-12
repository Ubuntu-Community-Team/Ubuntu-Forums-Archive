---
title: "libiw-dev package not found"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by rubykj on 2007-03-07
hello
I am trying to set up my wireless internet. It seems that I need network manager to do so. I tried to install it and while compiling I got an error wireless-tools>= 29pre9 not installed or not functional. Looking at other forums it seems that the fix to this was to install libiw-dev.
 I can't seem to do so, package not found. I just installed edgy yesterday and I am a beginner.
Can you please help me? I need some step by step troubleshooting
thanks a bunch

---

### Post by Perfect Storm on 2007-03-07
How's your sourcelist looks like?
```
cat /etc/apt/sources.list
```

Or look at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to find it.

---

### Post by annda on 2007-03-07
wireless-tools 28 is in the repositories - are you sure you need to compile v29?

---

### Post by rubykj on 2007-03-07
thanks 
AI for responding
I typed in that code, what am I looking for?

---

### Post by rubykj on 2007-03-07
annda
I'm really a new beginner. Is there another way you could phrase your question?

---

### Post by Perfect Storm on 2007-03-07
You're looking for if the **deb-src** is uncomment, but if you don't have any internet connection on you ubuntu system it's a bit useless then. If you have the option to use wire until the wireless is setup it can be a plus.

Other than that you can go to the link I gave you and find the packages you're missing, burn them down or use an usb stick to transfer them to your ubuntu.

---

### Post by rubykj on 2007-03-07
I plugged the DSL straight into the laptop and no connection.
I need network manager to connect regardless right?

---

### Post by rubykj on 2007-03-07
which deb-src needs to be uncommented?

---

### Post by rubykj on 2007-03-07
the deb-src [http://security.ubunu.com/ubuntu](http://security.ubunu.com/ubuntu) edgy-security universe line is commented as well as all the deb-src lines under the heading of add software from the 'backports' repository and the 'universe' repository

What do I need to do to connect to the internet if I plug in the wire directly?

---

### Post by holy*cow on 2007-03-10
hey I am have a similar problem. I am trying to set up wireless internet and am trying to install network manager. I am running Ubuntu 6.10. When I try to configure i receive the message
 configure: error: wireless-tools >=28pre9 not installed or not functional.
i have downloaded and installed libiw-dev and i still receive this message. 
please help i am new to Ubuntu and Linux

---

