---
title: "Quick apt question"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by maxwas on 2006-08-31
Hello, 

How can i use apt to find out the software i have installed on my system?

Thx

---

### Post by %hMa@?b&lt;C on 2006-08-31
If you open up Synaptic then you can read it by doing the "status" button on the bottom left, and then installed on the left panel.
w00t 500 posts!

---

### Post by TFX360 on 2006-08-31
> **maxwas said:**
> Hello, 

How can i use apt to find out the software i have installed on my system?

Thx


```
aptitude
```


goto installed packages.

---

### Post by TFX360 on 2006-08-31
> **maxwas said:**
> Hello, 

How can i use apt to find out the software i have installed on my system?

Thx

Congrats dude :D

---

### Post by maxwas on 2006-08-31
I could not use synaptic because i am on ubuntu server with no desktop, sorry should have mentioned that ;) 

Thanks to TFX360 'aptitude' was exactly what i was looking for.

:KS

---

### Post by Anonii on 2006-08-31
Try 
*dpkg -l*

or *dpkg -l | grep <package name you want>*
to see if you have installed the package you are interested in.

:)

---

### Post by TFX360 on 2006-08-31
> **maxwas said:**
> I could not use synaptic because i am on ubuntu server with no desktop, sorry should have mentioned that ;) 

Thanks to TFX360 'aptitude' was exactly what i was looking for.

:KS

I assumed you did. Use aptitude to install stuff. Apt-get sometimes f*cks up dependancies.

And I mean like this:

Not

```
apt-get install samba
```

but 

```
aptitude install samba
```


PS: Your welcome!

---

### Post by Sharkee on 2006-09-04
I was getting the 102 error with samba and fixed it using:

[http://ubuntuforums.org/showthread.php?t=243191]("http://ubuntuforums.org/showthread.php?t=243191")

---

