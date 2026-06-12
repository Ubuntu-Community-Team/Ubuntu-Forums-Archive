---
title: "[SOLVED] Problem Installing tar.gz"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Stall on 2007-09-30
Hello. I am having a difficulty installing tar.gz files. As suggested in a tutorial, I cd to the extracted folder, and then type in ./configure. After that, I believe one is suppose to type in make. However, when I type in make, I get the message "make: *** No targets specified and no makefile found.  Stop."

What am I doing wrong?

---

### Post by ddrichardson on 2007-09-30
There isn't a makefile by the sound of it. What files are in there?

---

### Post by brettg on 2007-09-30
Ensure that you are following the instructions for the particular package you are installing and don't rely on a generic howto. Look for a README file for specific installation instructions.

You also need to ensure you have gcc and some other dev packages installed. Depending on what you are installing, you may also need other libraries as well. Kernel headers may also be required. Again, check the README for details.

I usually check google to see if someone else has pre-packaged whatever it is I'm trying to install. I'm getting lazy in my old age and find that managing a system that is fully packaged is easier than a hybrid of both. YMMV of course.

---

### Post by aysiu on 2007-09-30
What's the name of the program?

---

### Post by Stall on 2007-09-30
Flash.

---

### Post by ddrichardson on 2007-09-30
Try [here ]("https://help.ubuntu.com/community/RestrictedFormats/Flash")first.

---

### Post by Stall on 2007-09-30
> **ddrichardson said:**
> Try [here ]("https://help.ubuntu.com/community/RestrictedFormats/Flash")first.
The quide to updating repositories is for 6.10 and 6.04. I am running 7.04.

---

### Post by carloslosgrande on 2007-09-30
[FONT="Comic Sans MS"]I'm probably missing something, but have you looked at 'add/remove' ? Thats where I got it from.[/FONT]

---

### Post by aysiu on 2007-09-30
Try one of these methods:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Stall on 2007-09-30
> **aysiu said:**
> Try one of these methods:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

That got it, thank you.

Also thank you all for the other bits and pieces of advice I got for installing tar.gz files in the future.

Thank you again.

---

