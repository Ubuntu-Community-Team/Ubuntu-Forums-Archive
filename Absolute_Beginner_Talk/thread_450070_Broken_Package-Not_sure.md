---
title: "Broken Package-Not sure"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by clemkonan on 2007-05-20
\
 I was installing Java Run Time V6.0 with Mozilla Plugin when I got stuck on a box asking for an ok.

I cannot continue I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
clemkonan@clemkonan-desktop:~$ 

Not sure what is implied by "manually run" I entered this into terminal and used my password but it did not help.

Can I get some simple 1,2,3, directions?

Thanks

---

### Post by blackened on 2007-05-21
Ok first a couple of questions: what do you mean by "...got stuck on a box asking for an ok"?

The java runtimes require you to agree to the eula in order to use them, so you should have just been able to agree and have the installation continue.

What was the output of sudo dpkg --configure -a? Did you try to reinstall the runtimes after you did this? Because if you didn't agree to the eula, then the installation halted itself.

---

### Post by clemkonan on 2007-05-21
It was the end user licensing agreement. I was trying to click "OK" without success then Firefox presented a dialog box that was also unresponsive. I tried to run the run time  statement again in terminal thats when I got the meassage I posted. So what I am trying to say is that responding to the licensing agreement resulted in my "yes" response not being applied.

I tried to load another programme , Google Earth and again I got the same message.

Trying to type the output message into terminal did not work looks like  I am missing part of the statement.

I am going to go back and try again

---

### Post by clemkonan on 2007-05-21
clemkonan@clemkonan-desktop:~$ sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
clemkonan@clemkonan-desktop:~$

---

### Post by clemkonan on 2007-05-21
How do I manually run this statement?

---

### Post by blackened on 2007-05-22
What does
```
sudo dpkg --configure -a
```
give you?

Try running that first, then try installing something from the repos, something without a eula.

What's happened is that dpkg is complaining because of your unfinished install and won't allow you to install anything else until you get it sorted out.

---

### Post by VoidBoy on 2007-05-22
> **clemkonan said:**
> clemkonan@clemkonan-desktop:~$ sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
clemkonan@clemkonan-desktop:~$

This is what you should do:
1.   Applications-accesories-terminal,........... once the terminal is open type:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

2.   The terminal will be downloading the contents. After that, you just follow (by hitting ENTER) the instructions until it says something like: "do you agree with the terms".......you just type "yes"(without quotation marks of course) and hit enter

3.   If the screen delays, just wait a bit..........if it doesn't load, type "yes" again. After that, more "installing" will be followed and you will be finish with the instalation ;)

---

