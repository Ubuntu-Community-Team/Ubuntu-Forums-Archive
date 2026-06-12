---
title: "how can I uninstall wrong repos"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-02-02
I just installed a bunch of repositories for  7.10 & I have 7.04.
I used apt-get install ubuntu-restricted-extras & it got locked up at java
Now I can't install Gstreamer to play wmv files in totem which was the whole purpose of installing the repos in the first place.
Will an uninstall command help?
I'm a little nervous now.

---

### Post by Paqman on 2008-02-02
When you say "it got locked up at Java" what exactly happened? If you used apt-get in a terminal window it should have spat out some dialogue about the error.

---

### Post by spiderbatdad on 2008-02-02
the repos are listed in /etc/apt/sources.list  if you open that file with a text editor you can manually delete the gutsy repos. Then run sudo apt-get update

---

### Post by spiderbatdad on 2008-02-02
though you need to have su permissions with the text editor so:```
gksu gedit /etc/apt/sources.list
``` and save when done.

---

### Post by garyed on 2008-02-02
I used apt-get install ubuntu-restricted-extras & everything stopped at the java screen where it asks you to accept the agreement. The java screen completely covered the terminal & I finally close out both screens after  15 or so minutes.

I'll try the other solutions
Its about 2 am now & I'm going to sleep on this till the morning.

Thanks for all the help,

---

### Post by dcstar on 2008-02-02
> **garyed said:**
> I used apt-get install ubuntu-restricted-extras & everything stopped at the java screen where it asks you to accept the agreement. The java screen completely covered the terminal & I finally close out both screens after  15 or so minutes.

I'll try the other solutions
Its about 2 am now & I'm going to sleep on this till the morning.

Thanks for all the help,
```
sudo dpkg-reconfigure debconf
```

You must actually answer the Java licence question, otherwise you will remain in the loop of a partially installed package.

Once you remove the wrong repositories, you must then "Downgrade" all incorrectly installed packages to the correct version for your install (use Synaptic to do this).

The "Backports" repository will contain any newer packages available to run on your system, this is the **ONLY** source of packages from newer versions that is guaranteed to work on your version.

---

### Post by garyed on 2008-02-02
> **dcstar said:**
> ```
sudo dpkg-reconfigure debconf
```

You must actually answer the Java licence question, otherwise you will remain in the loop of a partially installed package.


That was the problem, the install stopped right at that point &  left me no way to answer the license question. 
Thanks for the help, I'll try that other stuff too.

---

### Post by garyed on 2008-02-02
Okay, now in Synaptic I get the message I have a broken package & the search shows  Java...I
It gives me an option to reinstall but I think it would be better to uninstall but I don't know how or 
if that would be the best thin to do. I'm a little nervous trying to install it.
Any ideas

---

### Post by jan quark on 2008-02-02
try this to fix broken packages
```

sudo apt-get -f install
```

run in terminal

---

### Post by garyed on 2008-02-02
> **jan quark said:**
> try this to fix broken packages
```

sudo apt-get -f install
```

run in terminal

That did the trick.
All is well, thanks a lot.

---

