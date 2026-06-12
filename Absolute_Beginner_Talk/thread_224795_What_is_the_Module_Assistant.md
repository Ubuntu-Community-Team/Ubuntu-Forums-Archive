---
title: "What is the Module Assistant?"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by TimJBart on 2006-07-28
I am installing the ATI drivers but I've hit a snag.  What is the module assistant.  I followed the command 

```
sudo apt-get install module-assistant build-essential
```

but I get the error message 

```
sudo: module-assistant: command not found

```

what does this mean and will it prevent me from installing the ATI drivers?  How do I get the module assistant?

thanks!

---

### Post by benuski on 2006-07-28
Why are you putting the module-assistant thing in their in the first place? if you're just trying to get build-essential, then leave out the module assistant, and just type "sudo apt-get install build-essential"

---

### Post by TimJBart on 2006-07-28
unfortunately for me I know very little about linux!  I am following the first set of instructions in this thread:  [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

It says to install the necessary tools:
> sudo apt-get update 
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

---

### Post by TimJBart on 2006-07-28
I have now got to a section that says I need to comile the kernel module, and the module assistant is obviously not there and so this bit is not working:

```
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod
```

---

### Post by benuski on 2006-07-28
Hmmm... maybe try doing "sudo apt-get install module-assistant" and then "sudo apt-get install build-essential".  That shouldn't be necessary, but maybe aptitude got a little confused.  


If this doesn't work, you may have to download the .deb file straight from debian [here]("http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fupdates%2Fmain%2Fm%2Fmodule-assistant%2Fmodule-assistant_0.9sarge1_all.deb&md5sum=a793ec02a1d6a0514c7239085403a1b7&arch=all&type=security").  Download the file to your desktop, right click on it, and then hit "install".  That should finally get it to work.

---

### Post by TimJBart on 2006-07-28
thanks, those terminal commands didnt work either, so i just got it straight from debian.  That got me through that stage of the ATI install, its still going!

What does the module assistant do?  will i ever use it again?

---

### Post by benuski on 2006-07-28
[Here]("http://packages.debian.org/stable/devel/module-assistant") is Debian's description of what module-assistant does.  I've been using linux (mainly ubuntu) since March and I haven't run across anything else that uses it.  But that doesn't mean too terribly much.

---

