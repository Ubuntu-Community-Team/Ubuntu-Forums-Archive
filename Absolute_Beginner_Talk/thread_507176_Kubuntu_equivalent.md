---
title: "Kubuntu equivalent"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-22
I want to do this in Kubuntu: deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

what is the equivalent for the deb command?

---

### Post by cawill on 2007-07-22
[https://help.ubuntu.com/community/Repositories/Kubuntu](https://help.ubuntu.com/community/Repositories/Kubuntu)

Hope this helps, chris.

---

### Post by ukulele_ninja on 2007-07-22
When I run it in Kommand it says 'command not found'

---

### Post by mikewhatever on 2007-07-22
What do you run in Kommand?

---

### Post by ukulele_ninja on 2007-07-22
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

I ran that in the kommand window and it says command not found, i thought you had to change the first part for kubuntu?

---

### Post by sad_iq on 2007-07-22
Type ```
kdesu kate /etc/apt/sources.list
``` then add at the end of that file ```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
``` ...save...close it...then type in a konsole ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by cawill on 2007-07-22
I am guessing that your trying to add this repos so you can download beryl/compiz and other programs right?

In konsole
'kdesu kate /etc/apt/sources.list'

In kate at the bottom of the sources.list file add:
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

Save the file then in konsole again run:
'sudo apt-get update'

Or am I misunderstanding what your trying to do?

---

### Post by mikewhatever on 2007-07-22
> **ukulele_ninja said:**
> deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

I ran that in the kommand window and it says command not found, i thought you had to change the first part for kubuntu?

That's not a command. That is a repository to add to your sources list. You really should not copy anything you might think a command into the terminal and 'run' it.

---

