---
title: "Where do I put my binaries?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Solarius on 2007-09-06
I'm a Linux desktop n00b... I'm great at the terminal and I've been using it for years, but day-to-day tasks are lost on me =)

So I downloaded a copy of Songbird, and it came as a .tar.gz file.  When I untar'd it, it created a folder with the binary and a bunch of setup files in it.  Great.  I run it, I like it, fantastic.

Now, I want to make it more prominent on my system.  I can add it to the Ubuntu menu, but where do the actual files go?  It looks like /usr/bin and such contain single binary files, but this has an entire folder of config files to go with it.  Right now, it's just sitting in my home dir, which feels wrong =)

Also, what's the difference between stuff like /usr/bin, /usr/local/bin, /usr/sbin, etc.?  I tried to google for some info but I didn't get great results.

---

### Post by jrusso2 on 2007-09-06
> **Solarius said:**
> I'm a Linux desktop n00b... I'm great at the terminal and I've been using it for years, but day-to-day tasks are lost on me =)

So I downloaded a copy of Songbird, and it came as a .tar.gz file.  When I untar'd it, it created a folder with the binary and a bunch of setup files in it.  Great.  I run it, I like it, fantastic.

Now, I want to make it more prominent on my system.  I can add it to the Ubuntu menu, but where do the actual files go?  It looks like /usr/bin and such contain single binary files, but this has an entire folder of config files to go with it.  Right now, it's just sitting in my home dir, which feels wrong =)

Also, what's the difference between stuff like /usr/bin, /usr/local/bin, /usr/sbin, etc.?  I tried to google for some info but I didn't get great results.

/usr/local/bin would work or even /opt

---

### Post by afonic on 2007-09-06
Sunbird comes precompiled right?

Just copy the whole directory to /opt and then create a menu item though System -> Preferences -> Main Menu.

---

### Post by eentonig on 2007-09-06
With the risk of stating the obvious....

What is songbird and isn't it (or an alternative) available in the repo's?

---

### Post by alienexplorers on 2007-09-06
I store my binaries in /opt or /usr/local/bin.  Either will work.

---

### Post by afonic on 2007-09-06
> **eentonig said:**
> With the risk of stating the obvious....

What is songbird and isn't it (or an alternative) available in the repo's?

[http://www.songbirdnest.com/](http://www.songbirdnest.com/)

Its not in the repos yet as only an Alpha is out. And I don't think there is something similar to it to use as an alternative.

---

### Post by mali2297 on 2007-09-06
I would move the whole folder to */opt*, make root owner of all the files and add a symbolic link in */usr/bin* to the binary. 

It would be a pity to leave */opt* empty. :-)

---

