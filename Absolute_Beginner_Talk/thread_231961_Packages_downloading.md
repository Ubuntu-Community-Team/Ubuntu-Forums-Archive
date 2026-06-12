---
title: "Packages downloading"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by sankarv on 2006-08-08
In packages.ubuntu.com


for many cases each package is listing out lot of dependencies which inturn has lot of depencies which goes on. It is dfficult to download all for installing offline.


Is there any single package file which holds all the dependencies inside so that its easy for offline installation.

---

### Post by arjun.shankar on 2006-08-08
Use 'Synaptic Package Manager'

You can launch it with:
**sudo synaptic** in the terminal

OR

Go to this menu entry (from the GNOME panel):
**System-> Administration -> Synaptic Package Manager**

You can also use apt-get:

Do this to learn more:
**man apt-get**

usually, you type something like this to install or remove some package:

**apt-get install *<package-name>***

**apt-get remove *<package-name>***

---

### Post by asfx on 2006-08-08
That wont work if you're offline..
I'm having a similar problem..

---

### Post by arjun.shankar on 2006-08-08
Oops! Sorry, didn't notice the offline part. Let me see...

By the way, what sort of platform will you be downloading these packages on?

---

### Post by asfx on 2006-08-08
Windows XP, dare I say it, but its the only PC I have available with a Internet connection. Is that what you meant? Or did you want to know if its i386? 

Sorry bit of a noob. :)

---

### Post by sankarv on 2006-08-08
I normally will download in net cafes and then install in my home PC. It would be better to have single package which is convenient. Thats why i asked so...

---

### Post by arjun.shankar on 2006-08-08
Well, as far as I know, there is no way to get all the dependencies in one package.
If you can get hold of a cafe running ubuntu, or even some other form of linux, then maybe a small script will do your job.
And hey, I'm a newbie too!

---

