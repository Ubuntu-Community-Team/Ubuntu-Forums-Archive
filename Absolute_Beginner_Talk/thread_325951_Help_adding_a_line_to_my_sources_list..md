---
title: "Help adding a line to my sources list."
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Ambertone on 2006-12-26
Hi all, I need to add a new line to my sources list and have no idea how to do this? The line is:

deb [http://nightlies.videolan.org/build/dapper-i386](http://nightlies.videolan.org/build/dapper-i386) /

Cheers

Rod

---

### Post by 23meg on 2006-12-26
Hit Alt + F2, or open a terminal, paste this```
gksudo gedit /etc/apt/sources.list
```and hit enter. 
Enter your user password, add the line to the bottom of the line, save the file.

---

### Post by Ambertone on 2006-12-26
Hi there, thanks for that, I got and "authentication failed" typing in your fist line in the console but the editor opened anyway.  I added the source to the list (there was nothing in it) and hit save and closed.

Next is how to access the source to install libdvdcss?

Cheers

Rod

---

### Post by 23meg on 2006-12-26
If there was nothing in it you probably misspelled something. Just paste the line exactly as it is in my post.

---

### Post by Ambertone on 2006-12-26
Yes, that did it. I think i missed the "apt" part. I cut and pasted the sources line in and saved with no problem. How do I access the source to install libdvdcss?

Appreciate your help.

Cheers

Rod

---

### Post by halitech on 2006-12-26
after you have the repo added, still in the terminal type 

```

sudo apt-get update
sudo apt-get install libdvdcss

```

---

### Post by scrooge_74 on 2006-12-26
sudo apt-get update
sudo apt-get install libdvdcss

is that the name of the package it should do it

---

### Post by Engnome on 2006-12-26
> **Ambertone said:**
> Yes, that did it. I think i missed the "apt" part. I cut and pasted the sources line in and saved with no problem. How do I access the source to install libdvdcss?

Appreciate your help.

Cheers

Rod

The source? You don't want the source if you want to install something. Unless you want to try and compile it yourself. I'm guessing you added this repository to install libdvdcss? If it's in the repository you can:

```

sudo apt-get update
sudo apt-get install libdvdcss

```

---

### Post by 23meg on 2006-12-26
The package name may also be *libdvdcss2*.

---

### Post by Ambertone on 2006-12-26
Hi all, I got into the repository but get a message about it being unavailable but is referred to by another package. This might mean that the package is missing, obsolete etc.

The information I'm trying to work from is here is anyone want to help me with this challenge. :) 

[http://nightlies.videolan.org/](http://nightlies.videolan.org/)

Cheers

Rod
Melbourne, Australia.

---

### Post by 23meg on 2006-12-26
For an alternative way of installing libdvdcss, see this:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Ambertone on 2006-12-26
Is it possible to do a search for similar named packages from within the terminal or from the URL of the repository?

Cheers

Rod

---

### Post by Ambertone on 2006-12-26
23Meg, that did it, thank you so much for your help. It's funny that you just expect that you can play a DVD on any player considering you either paid to hire or buy the DVD but it's not the case.

Cheers

Rod

---

### Post by Ambertone on 2006-12-26
Hi all, 

Just one other question, I've notice that the new repository now appears in: System> Administration> Software sources. I notice there is an "add" button and was wondering if there is a reason to add through a terminal and not under software sources?

Cheers

Rod

---

