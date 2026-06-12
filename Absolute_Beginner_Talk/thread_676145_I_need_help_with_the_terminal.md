---
title: "I need help with the terminal"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Emmazing on 2008-01-23
I am a new user and I am trying to install stuff using the terminal. I have found instructions online for what I want to install, but when I type in the 'sudo' commands I always get a message saying that it is not a recognized command. Either that or it says "E: couldn't find package". I have tried to do a few things using the terminal but it seems as though everything I try doesn't work. Is there a setting that i need to enable before I can use the terminal or am I just missing something?

---

### Post by emarkd on 2008-01-23
Sounds like you're trying to installing things from apt.  The command should go like this:

```
sudo apt-get install whatever

```
but the whatever has to be the exact name of the package.  You can also search the repository from the commandline if you don't know the exact name.

1.  Update your local copy:

```
sudo apt-get update
```

2.  Search for your package:

```
sudo apt-cache search whatever
```

After you find it, you can install it using the first code above

PS.  You can do all of this graphically by clicking on Administration > Synaptic Package Manager

---

### Post by jeffus_il on 2008-01-23
post a command that doesn't work with the error as well.

---

### Post by kellemes on 2008-01-23
> **Emmazing said:**
> I am a new user and I am trying to install stuff using the terminal. I have found instructions online for what I want to install, but when I type in the 'sudo' commands I always get a message saying that it is not a recognized command. Either that or it says "E: couldn't find package". I have tried to do a few things using the terminal but it seems as though everything I try doesn't work. Is there a setting that i need to enable before I can use the terminal or am I just missing something?


You're missing something I'm sure.. ;-)
Can you explain what you're trying to do.. what do you want to install, and using what instructions?
Surely we can help.

---

### Post by mali2297 on 2008-01-23
Give us an example of a command that doesn't work for you.

All packages that you can install with apt-get are also accessible from Synaptic.

---

### Post by ronmarley1 on 2008-01-23
Additionally, this site is great for learning the terminal.
Cheers!
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by Emmazing on 2008-01-24
Thanks for the help! for some reason I was putting a y in the apt-get (like this, apt-get-y). I don't know where that came from or why i thought I needed it. But if I use the way that was posted here it works. :)

---

