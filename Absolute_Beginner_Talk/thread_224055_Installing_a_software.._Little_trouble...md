---
title: "Installing a software.. Little trouble.."
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by yongblood on 2006-07-27
Hello! 

I am not an absolute beginner. I was using linux 3 years ago, and then quit because it was Red Hat, and it was crap. But now, I've decided to revisite my old friend Linux, and I decided to use Ubuntu! 

Now, I want to install a software, and I remember the procedure.

tar xvzf package.tar.gz 
cd package
./configure
make
make install

So, I went into Terminal, NONE of these operations work, Except for tar... The system says Unknown Command to configure, make and make install..

---

### Post by Dinerty on 2006-07-27
Install* "build-essential"*

---

### Post by taurus on 2006-07-27
You need to install build-essential first before you can build anything from source.  From a terminal, do

```

sudo apt-get install build-essential
tar xvzf package.tar.gz
cd package
./configure
make
sudo make install

```
By the way, what package do you have in mind because chances are there is one available in repo for you to install with apt-get/aptitude/synaptic...

```

sudo apt-get install <package>

```

---

### Post by yongblood on 2006-07-27
I checked, it's no package, it's only from the source. 

Thanks for the fast answer guys!

---

### Post by T700 on 2006-07-27
See the "how to install anything" link in my sig for detailed instructions on pretty much all the ways of installing.

Paul

---

### Post by taurus on 2006-07-27
> **yongblood said:**
> I checked, it's no package, it's only from the source. 

Thanks for the fast answer guys!
What package are you having in mind here?  Maybe you need to enable both universe & multiverse in /etc/apt/sources.list!!!

---

### Post by yongblood on 2006-07-27
It's some WEP hacker, I want to check if my wireless network is secure.

---

### Post by taurus on 2006-07-27
Then just follow my #3 post!

---

### Post by yongblood on 2006-07-27
It did not work

./configure doesnt work.

---

