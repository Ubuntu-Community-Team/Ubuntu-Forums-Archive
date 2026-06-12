---
title: "problems installing ia-32 libs"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by voidoid on 2007-05-13
Right I'm running Feisty on an AMD64 machine, and anytime I try to install ia32-libs I get the following error message ```
 sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs

```

How do I let my machine know where this library is? 

Thanks

---

### Post by josesanders on 2007-05-14
I posted a more detailed solution on your other thread, but just to clarify, when you use the 'apt-get install' command, you are retrieving the installation package from a remote server, not from your local system.  If you download the file manually (it will have a .deb extension), I think you can just double click on it.  Also, you could run the command:

$ gdebi filename.deb

---

### Post by voidoid on 2007-05-17
sorry, only just got back to this one! it gives me an error that says 'wrong architecture 'AMD64'' which is odd, given that I am definitely running an AMD64 processor, on a motherboard that matches!

---

