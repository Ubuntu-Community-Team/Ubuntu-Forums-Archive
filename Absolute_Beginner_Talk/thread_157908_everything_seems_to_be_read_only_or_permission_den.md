---
title: "everything seems to be read only or permission denied?"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Bhante Santi on 2006-04-10
I've been trying to get a wireless network card working, install more fonts and even just open some word documents, and I always have the same obstacle that everything seems to be read only, but I'm the only user and therefore an administrator account, what's going on?


Thanks, Bhante Santi.

---

### Post by frodon on 2006-04-10
In your ubuntu partition all the files need root access to be writable except for your home directory. So if you open a file without root access in your ubuntu partition it will be read only.
You should also read that : [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by tribaal on 2006-04-10
By the way, it is intendent to be like that to prevent people and viruses from destroying the system. 
You should just get used to this, and not login with root all the time :)

- trib'

---

### Post by Bhante Santi on 2006-04-10
[QUOTE=frodon]In your ubuntu partition all the files need root access to be writable except for your home directory. So if you open a file without root access in your ubuntu partition it will be read only.
You should also read that : [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]

Thankyou,

now I know how to edit the blacklist file to disable plasma54 and perhaps get the wireless card working, but when you say "except for your home directory" I find that even my word documents that I just copied over from my old computer are all read only and I have to save a copy to be able to edit them. They are in my home directory I think.

Thanks, Bhante Santi.

---

### Post by Perfect Storm on 2006-04-10
It's because the files you copied comes from the CD/DVD and therefore only read and executive. Just right click the file, go to properties and then the permissions tab and select write to Owner. 
You can select multiply files and do the same.

---

### Post by Bhante Santi on 2006-04-10
Next question, how do I run ndiswrapper.utils from the hard disk since I don't have direct access to the internet on the laptop I'm trying to install the wireless card on? It's seems to expect to connect to the internet is there a way to get around that?

Taa muchly.

---

### Post by 3G-Buntu on 2006-05-15
Thanks for the info!

---

