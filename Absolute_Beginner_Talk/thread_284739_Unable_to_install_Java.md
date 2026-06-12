---
title: "Unable to install Java"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by geo_bio on 2006-10-26
I am trying to install Java for firefox. It seems that firefox knows that I am missing java, but is unable to install it for me (although it does install flash). 

So I did the manual install. First, I have two problems
I followed these instructions, except...[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

I am unable to type in the command "su" - typing that it and using my login password ends up with 

> su: Authentication error.
Sorry.

And yes it is the right password.

Next, I am unable to install to the directory /usr/java. First, /java does not exist yet. However, I attempt to copy using

sudo cp ~/Desktop/java /usr/

but it ends up telling me that it omitted ~/Desktop/java.... not really a great result.

Can anyone tell me know to have full root powers? Please! I try to change the password for "root" to something different than my current one. and then I try to log in, but it says that I cant from the login screen.

Any help with Java in ubuntu?

Thanks

---

### Post by pay on 2006-10-26
Ubuntu is different to other distros because it doesn't use a root account like the others. The sudo command is used instead. To get root access you can do "sudo <my command>" or i think its "sudo -i" or "sudo su" but I may be wrong. You can't copy java into a directory that doesn't exist. To make a direcoty as root it's "sudo mkdir <my directory>"

---

### Post by Malakia on 2006-10-27
Go to [www.ubuntuguide.org](www.ubuntuguide.org) and follow the directions on their to install java and it evens shows you how to update it too.

---

### Post by PriceChild on 2006-10-27
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) for more information on how sudo works.

[http://wiki.ubuntu.com/Java](http://wiki.ubuntu.com/Java) for instructions on how to install java
or... just type this:
```
sudo apt-get install sun-java5-bin sun-java5-plugin
sudo update-java-alternatives -s java-1.5.0-sun
```

---

