---
title: "Ndiswrapper can't find internet drivers...."
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Swimmerboy196 on 2007-11-24
Well, you think that it'd be easy to connect to the internet....

I just put Ubuntu on a slave drive on one of my computers. I had to manually install the driver for my wireless internet card. So I posted a question about what to do - I installed ndiswrapper, found my driver cd, and pasted my drivers into my home directory. I go to install the drivers in Terminal (using "sudo ndiswrapper -i MYDRIVER"), and the output says that ndiswrapper can't find the files to install. 

Where should my drivers be pasted? Have I done everything necessary before trying to install? I have a feeling the answer is pretty simple, but I'm quite a noob.....Any help you can give is greatly appreciated - not really a point in an open source OS without internet access....

---

### Post by corevette on 2007-11-24
not much help, but you could ask on the official ndiswrapper forums: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/)

---

### Post by mouseboyx on 2007-11-24
you should paste your driver in your home directory so...

/home/yourname
or ~ will take you to it

and you know when you paste it MYDRIVER is replaced by the name of the driver which is a .inf file.

---

