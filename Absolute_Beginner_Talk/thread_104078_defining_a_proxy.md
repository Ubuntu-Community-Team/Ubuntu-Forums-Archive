---
title: "defining a proxy"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2005-12-15
When i try to use atp it never goes further than 

```
0% [Connecting to security.ubuntu.com (82.211.81.138)]

```

I am in my university network, i think i have to define the proxy somewhere. Can somebody help me?

Thz

---

### Post by NotJustANewbie on 2005-12-15
I think its "apt", not atp...
Anyway, what are you trying to do?
You must first do:
```
sudo apt-get update
```
before you can install anything new via apt

---

### Post by pedrotuga on 2005-12-15
yep.. i misstyped... apt i ment.

But the same problem hapen when i do 
```
sudo apt-get update
```

I heard i have to define a proxy to my shell or something...
i defined a proxy in firefox in order to be able to browse the web... i think it should be the same, my university proxy. But how do i define a proxy for the shell?

---

### Post by kaamos on 2005-12-15
If I remember correctly, gnome has global proxy options. Somewhere in the menus.. Can't check because I use xfce now. Also what you could try in the terminal before running apt:
```
export http_proxy=http://the_proxy_here:port_number/
```
Not too sure about that though.. Hope this helps!

---

### Post by pedrotuga on 2005-12-16
Yep, it helped, because it works :cool: 

Now that i can use apt i am kind of satisfyed but... i have to type the export comand everytime i want to use apt... is there any file i can place that comand so i dont ned to run it all the time?

thx

---

### Post by bscbrit on 2005-12-16
/etc/rc.d/rc.local" is a script that runs on each boot.  If you add the line to this file it will be set each time you start the computer.  You will have to be 'root' to edit this file.

---

### Post by pedrotuga on 2005-12-16
lets see... there are the folders:

rc0.d
rc1.d
rc2.d
rc3.d
rc4.d
rc5.d
rc6.d
rcS.d

but no rd.d :(

---

### Post by Mustard on 2005-12-16
Down the bottom of this page are the instructions for setting up a proxy in terminal....

[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)

Remember to close the terminal and reopen it before testing.

---

### Post by pedrotuga on 2005-12-16
Working ;)

---

