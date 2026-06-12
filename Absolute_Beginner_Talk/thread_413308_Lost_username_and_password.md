---
title: "Lost username and password"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Win98Rocks on 2007-04-19
I just managed to install xubuntu on to an old compaq presario 1200 with 92 mb ram, it took two days and now I cant remember the username and password I entered.

I have tried to follow this [http://www.ubuntuforums.org/showthread.php?p=2162248#post2162248](http://www.ubuntuforums.org/showthread.php?p=2162248#post2162248) thread but doesnt really help.

I open the machine in recovery mode and get to where it says:
root@ubuntu:~# 

and now what?

I have forgotten the username and password I have to enter the the machine shows the login screen.

Do I really need a username and password?

---

### Post by amohanty on 2007-04-19
> I open the machine in recovery mode and get to where it says:
root@ubuntu:~# 

As it says there, you can look up you username from the /etc/passwd file

Typically the first user in ubuntu has an id of 1000 (just a no.) so to see that, at the prompt type:

**cat /etc/passwd | grep 1000**

you will get an output like:

**amohanty:x:1000:1000:A Mohanty,,,:/home/amohanty:/bin/bash**

the first word is your username. 

To change the password for the user at the same prompt type:
(in the case of my example the username is amohanty)

**passwd amohanty**

Follow the prompts and the njust reboot by typing:

**shutdown -r now**

HTH
AM

---

### Post by kvonb on 2007-04-19
To get a list of usernames on the system:

```
ls /home
```

To change the password of a user (in recovery mode):

```
passwd username
```

Then type:

```
exit
```

and it should reboot and you will be able to login with your new password :)

---

### Post by kvonb on 2007-04-19
hahahaha, isn't it amazing, there are several ways to skin each and every cat! :guitar:

---

### Post by Win98Rocks on 2007-04-19
ok, Ill give it a go and see what happens.

Do I really need a username and password to run xubuntu? My sun will get the laptop for online gaiming nothing else security is really not an issue. His 3 so he doesnt even have secrets to hide away yet :)

---

### Post by juantovarm on 2007-04-19
I personally don't use Xubuntu, just Kubuntu, but look for Login Window and then Security. Activate automatic login

---

### Post by amohanty on 2007-04-19
> Do I really need a username and password to run xubuntu? My sun will get the laptop for online gaiming nothing else security is really not an issue. His 3 so he doesnt even have secrets to hide away yet 

As long as your son is not the first user on the list. The first user you create is  a special user with sudo powers. So he may not do anything, but couple auto-login with sudo with wireless lan (hopefully you are using wpa or wpa2) and you could be opening a huge hole.

Its not him you need to worry about, its adults his mental age you need to be wary of :)

AM

---

### Post by Win98Rocks on 2007-04-19
> **amohanty said:**
> As it says there, you can look up you username from the /etc/passwd file

Typically the first user in ubuntu has an id of 1000 (just a no.) so to see that, at the prompt type:

**cat /etc/passwd | grep 1000**

you will get an output like:

**amohanty:x:1000:1000:A Mohanty,,,:/home/amohanty:/bin/bash**

the first word is your username. 

To change the password for the user at the same prompt type:
(in the case of my example the username is amohanty)

**passwd amohanty**

Follow the prompts and the njust reboot by typing:

**shutdown -r now**

HTH
AM

Strange, when I type in "cat /etc/passwd | grep 1000" it just returns root@ubuntu: ~# again

---

### Post by amohanty on 2007-04-20
> Strange, when I type in "cat /etc/passwd | grep 1000" it just returns root@ubuntu: ~# again

whow..thats a bit scary. Can you post the output of:

cat /etc/passwd | grep $(/bin/ls /home)

This is a variant of kvonb's solution. I just want to make sure that the user exists.

AM

---

### Post by Win98Rocks on 2007-04-20
Sure this is the output:

oem:x:299999:299999:OEM Configuration (temporary user),,,:/home/oem:/bin/bash

---

### Post by Win98Rocks on 2007-04-20
Looks like this post did the trick [http://ubuntuforums.org/showthread.php?t=273789](http://ubuntuforums.org/showthread.php?t=273789)

---

