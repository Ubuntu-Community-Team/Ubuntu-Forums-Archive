---
title: "opera 9.02"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by new_foo on 2006-09-24
Have any of you tried to install or update to Opera 9.02?

I get an error when I try to.  Something about dependencies on a package that is not installed.

libqt3c102-mt

Is this mistake on opera's part?  I was reading it was replaced by 

libqt3-mt

and 9.01 used that one.

Thanks in advance

---

### Post by SunnyRabbiera on 2006-09-24
I encountered this before, but its alright as all you have to do is install the libqt3c102-mt or whatever else it is missing file via synaptic.
then give it another try

---

### Post by new_foo on 2006-09-25
Okay, I've been searching through the repositories, but I can't seem to find the package.  Could you give a little hint to where it might be?

Thanks

---

### Post by new_foo on 2006-09-25
UPDATE!!

Nevermind, I figured it out.

Thanks for the time.

---

### Post by rickympl on 2006-09-25
It would be appreciated by everyone that is encountering the same problem if you would explain what you figured out and how you got it working.

Just my 2 cents.

---

### Post by cotcot on 2006-09-25
It WAS a problem to install Opera 9 untill it became available on the commercial repository.

So add first :

> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

to your /etc/apt/sources.list;

than ;
```
sudo apt-get update
```

and then you can simply install opera 9 with 

```
sudo apt-get install opera
```

---

### Post by Kingsley on 2006-09-25
i just got mine to upgrade to 9.02. 

-download the opera 9.02 ubuntu package in tar.gz format (there's a checkbox to do so).
-unpack the tar.gz and go into opera 9.02 directory.
-type sudo ./install.sh and click yes to the next prompts

opera 9.02 should now be installed when your restart the browser.

---

### Post by new_foo on 2006-09-25
Oh, sorry about that.

And the solution was to download the correct package for your distribution.  I had the wrong package from the website.

Thanks

---

