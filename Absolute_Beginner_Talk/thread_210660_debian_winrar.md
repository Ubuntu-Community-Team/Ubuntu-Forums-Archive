---
title: "debian winrar"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2006-07-07
anyone know where i can get  debian version of winrar (winrar.deb)

---

### Post by someusernoob on 2006-07-07
Enable multiverse and universe in the repositories, update, and search for rar.

It's command line only. type rar --help in the terminal for the commands.

---

### Post by ovimunt on 2006-07-07
Hi,

You don't need a deb file to install Rar on linux. This is what you need to do instead: 

First of all make sure you have the ***build-essential*** package installed. You can install it like this:
> sudo aptitude update
sudo aptitude install build-essential

Download the linux version of Rar from here **[http://www.rarlab.com/rar/rarlinux-3.6.b6.tar.gz]("http://www.rarlab.com/rar/rarlinux-3.6.b6.tar.gz")**

You can do this in command line mode:
> sudo wget [http://www.rarlab.com/rar/rarlinux-3.6.b6.tar.gz](http://www.rarlab.com/rar/rarlinux-3.6.b6.tar.gz)
Now extract the file
> sudo tar zxvf rarlinux-3.6.b6.tar.gz

Install Rar:
> cd /rarlinux-3.6.b6/rar
sudo make
sudo make install

That's it, you're all set. Now you can either use Rar itself in command line mode or, in graphic mode, use Nautilus to extract your RAR archives just like any other archive.

---

### Post by FredB on 2006-07-07
It could be an answer. But using the unrar package from multiverse is lighter and it works too.

---

### Post by Stealth on 2006-07-07
I just "sudo apt-get install rar unrar" and then I can open em like any other archive. ^_^

---

### Post by ovimunt on 2006-07-07
Either way will work but what I'd like to point out is that it's good practice to use ***aptitude*** instead of ***apt-get***.

The reason for this is that if at a later time you want to remove any of the packages you've installed ***aptitude*** will also remove all dependencies, unless they're used by other packages, while ***apt-get*** won't be able to do this properly.

---

### Post by FredB on 2006-07-07
> **ovimunt said:**
> Either way will work but what I'd like to point out is that it's good practice to use ***aptitude*** instead of ***apt-get***.

The reason for this is that if at a later time you want to remove any of the packages you've installed ***aptitude*** will also remove all dependencies, unless they're used by other packages, while ***apt-get*** won't be able to do this properly.

Ok. Next time I will think about it ;)

Thanks for the tip !

---

