---
title: "Installin JRE with firefox"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-02-04
Hi

I'm not sure if this is the right place to post but I am trying to follow the instructions to install JRE in firefox.

It says:

	   Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   

Well, I go to the terminal and type 'su'. Sure enough it asks for a password. I then type the password I used when setting up ubuntu and it goes like this:

john@john-desktop:~$ su
Password:
su: Authentication failure
Sorry.

Any clues?

Thanks

---

### Post by annda on 2007-02-04
ubuntu doesn't use su by default because the root account isn't enabled (so no root password). use sudo instead (with your user password).

---

### Post by BarfBag on 2007-02-04
> sudo su

Try that.

---

### Post by ubername on 2007-02-04
> **BarfBag said:**
> Try that.

Thanks so much for all your help. I feel very dumb having to ask all these questions, but you are helping a lot. 

I tried the 'sudo su' command and it seemed to work, but then I couldn't follow any of the other instructions from the java website about how to install the JRE. For example it says

change to the directory in which you want to install. Type:
cd <directory path name>
For example, to install the software in the /usr/java/ directory, Type:
cd /usr/java/

Well I have no idea which directory I want to / should install the software in. I tried the 'CD' command above and it said 

root@john-desktop:/home/john# cd /usr/java/
bash: cd: /usr/java/: No such file or directory
root@john-desktop:/home/john#


Can someone give me a dummy's guide  to installing the java JRE in firefox 2.0.0.2 running in ubuntu 6.06?

(I'm not even sure it isn't installed, but when I click on the 'verify installation' button at 

[http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1)

I get a 'click here to download plugin' message)

Thanks for your patience.

---

### Post by annda on 2007-02-04
i highly recommend getting automatix2 to do the dirty job for you.

here's more info:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by ubername on 2007-02-12
> **annda said:**
> i highly recommend getting automatix2 to do the dirty job for you.

here's more info:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

And that was that! Thanks very much, all done now. Automatix helped with loads of other things too. (currently working on MySQL but will post questions when I know better what I am doing)

---

