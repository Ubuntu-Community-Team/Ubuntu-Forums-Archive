---
title: "Trouble installing winrar"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by honsou on 2008-03-15
I'm having some problems with Winrar. I got ubuntu yesterday and know pretty much nothing about it. Anyway when I try to install winrar in the terminal I get

jamie@desktop:~$ sudo apt-get install rar 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jamie@desktop:~$ 

So could I get some help here?

---

### Post by dje on 2008-03-15
Just do what it says type the following into the terminal:
```
sudo dpkg --configure -a
```
and that should fix your problem

dje

---

### Post by jan quark on 2008-03-15
to install the the rar applications run in terminal
```

sudo apt-get install unrar-free
```

---

### Post by honsou on 2008-03-15
> **jan quark said:**
> to install the the rar applications run in terminal
```

sudo apt-get install unrar-free
```

that just comes up with the same problem and when I do put in sudo dpkg --configure -a it gives me a few messeges and then the computer just turns itself off

---

### Post by Bölvaður on 2008-03-15
1. open the terminal
2. Edit -> Current user
3. Title and Command
4. when command exits: Hold the terminal open

This should make sure you are able to copy and paste the "error code" into this thread.
It actually could be saying it has been installed already for all we know ^^

---

### Post by billgoldberg on 2008-03-15
Maybe something to know, there will be no mention of winrar or rar in your applications menu.

You'll just be able to extract them by right clicking or by using the standard archive manager.

---

### Post by honsou on 2008-03-15
> **Bölvaður said:**
> 1. open the terminal
2. Edit -> Current user
3. Title and Command
4. when command exits: Hold the terminal open

This should make sure you are able to copy and paste the "error code" into this thread.
It actually could be saying it has been installed already for all we know ^^

I have managed to get it working now thanks.

---

