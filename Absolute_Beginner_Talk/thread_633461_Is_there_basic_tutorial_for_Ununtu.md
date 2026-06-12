---
title: "Is there basic tutorial for Ununtu"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by latestgood on 2007-12-06
Hello,

I just started linux and I'm having problem following other peoples step because I have no basic skill. Is there a website that teaches basics of ubuntu? 

For example, when a guide tells me to:

STEP 3: COMPILE PROGRAM

Now we'll complile the Ndiswrapper program. In a terminal, go to the directory where you extracted ndiswrapper and execute the following:

Code:

cd YOUR-NDISWRAPPER-DIRECTORY
sudo make uninstall



I don't know how to figure out my directory... What is the default directory? Also, when there are two lines in the code, do I copy and paste each line at a time or just copy everything and paste it to the terminal?



Thank you

---

### Post by philinux on 2007-12-06
How to install anything

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by Vadi on 2007-12-06
Oh dear! Compiling programs isn't for newbie. Why do you need to compile ndiswrapper anyway? You can easily get a pre-compiled version, just copy/paste this in the terminal:

```
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```

That said, check out Ubuntu Screencasts ([click]("http://screencasts.ubuntu.com/")). Those guys make videos. Also, just google "Ubuntu Tutorials" - you'll get a ton of them.

That said - when copy/pasting in the terminal, you can actually do both. If you do the latter, the terminal will automatically execute each command after the last one is done. But, I don't recommend this - because if the last command fails for some reason, it'll still go on - so doing it line-by-line is better.

---

### Post by latestgood on 2007-12-06
Wow, I realized how strong this community is with helping other people.

Thank you

---

