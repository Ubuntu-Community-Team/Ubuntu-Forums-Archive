---
title: "java is driving me crazy"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by vi3tboitim on 2006-09-18
im trying to install java and this is wut comes up. can only help?

Could not open the file /home/tinguyen/Desktop/u…k-1_5_0_08-linux-i586.bin.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.



HELP!!!

signed,
Tim

---

### Post by ignorance on 2006-09-18
Gedit can't open that file as it says 
Please check that you are not trying to open a binary file.
and you're file is a binary file 
follow this one(don't know if it will work)

```
Copy the bin-file to you're home folder
cd home
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jdk-1_5_0_08.linux-i586.bin
sudo dpkg -i sun-j2sdk1.5_1.5.0+update08_i386.deb
sudo update-alternatives --config java
```

---

### Post by bulldog on 2006-09-18
In synaptic is java available as far as I now,search for jre.

Otherwise you could use Automatix to install it for you and you can choose for a lot more handy applications.

I put the link in a moment

Take a look here and you'll be suprised.

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

---

### Post by vi3tboitim on 2006-09-18
well it says the file is a "binary" but like i got it straight from the java web

---

### Post by ignorance on 2006-09-18
As far i can see there is no option to install jre or jdk with synaptic.

---

### Post by bulldog on 2006-09-18
> **ignorance said:**
> As far i can see there is no option to install jre or jdk with synaptic.

Maybe you should take a look at your sources.list and see if you have the repository's enabled?

Uncomment Multiverse and Universe and all the rest {can be done in synaptic too}

But I advice you to take a look at Automatix because it can do a lot more for you.

---

### Post by vi3tboitim on 2006-09-18
let see i just installed automatix how do i use it? im pretty new to linux =p

---

### Post by bulldog on 2006-09-18
Read the tutorial!

But if you have installed it type automatix in your terminal and follow the steps on screen.

---

### Post by ignorance on 2006-09-18
Yes, all my repository's are enabled and no i don't want to use Automatix.

---

### Post by bulldog on 2006-09-18
> **ignorance said:**
> Yes, all my repository's are enabled and no i don't want to use Automatix.

That's your choice,I don't care.

It's pretty simple but if you want to do it the hard way,be my guest.

---

### Post by vi3tboitim on 2006-09-18
YES! I GOT IT
thanks alot man

---

