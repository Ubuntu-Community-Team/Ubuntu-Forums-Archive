---
title: "Tutorial update Help required."
date: 2009-05-17
forum: Art &amp; Design
---

### Post by AJB2K3 on 2009-05-17
I only have 8.10 lts (refuse to upgrade) and my font tutorial is out of date for above 8.10. Can someone help me by providing instruction for 9.XX *buntu's?

---

### Post by Fzang on 2009-05-17
How to install fonts for Jaunty?

Put fonts in 
```
/usr/share/fonts/"sort" 
```
where "sort" is a directory you can put fonts in to sort them. I don't think it actually matters where they're located in /fonts/ though..

After that refresh font cache with 
```
sudo fc-cache -f -v
``` 
or log out/in

Fonts need to be moved with root privileges in order to gain access to those directories

Is this what you wanted to know?

---

### Post by AJB2K3 on 2009-05-18
> **Fzang said:**
> How to install fonts for Jaunty?

Put fonts in 
```
/usr/share/fonts/"sort" 
```
where "sort" is a directory you can put fonts in to sort them. I don't think it actually matters where they're located in /fonts/ though..

After that refresh font cache with 
```
sudo fc-cache -f -v
``` 
or log out/in

Fonts need to be moved with root privileges in order to gain access to those directories

Is this what you wanted to know?

So the old home/user/.fonts no longer work?

---

### Post by Fzang on 2009-05-19
I'm not sure if it actually matters which directory you use. I've always used /usr/share/fonts/ though..

---

