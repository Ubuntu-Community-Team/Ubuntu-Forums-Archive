---
title: "What is Aptitude? [Resolved]"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by reabralop on 2007-01-20
What is Aptitude?
I first thought it was another name for terminal but now I am guessing that it is similar to terminal from what I've read.

How do I get it?
It isn't in the add/remove. I read in one of the threads that it is better that terminal in that it uninstalls more effectively. Is this true?

Thank you.

---

### Post by halitech on 2007-01-20
Aptitude is anotehr way of installing software. similiar to using apt-get in the terminal but does a little better job of tracking dependencies then apt-get.

should be able to go to the terminal and type

```

sudo apt-get install aptitude

```

then put in your password and you should have it. and it's not a terminal type application. it's an app you run from a terminal

---

### Post by JamieC on 2007-01-20
Terminal is the Linux command line, Aptitude is a package manager. The two are of no relation...

---

### Post by gruffy-06 on 2007-01-20
Aptitude is part of the base of any Debian-based distro. You shouldn't have to install it manually.:)

---

### Post by braddcadd on 2007-01-20
Aptitude is a better version of apt-get (it handles dependacies and complete removal better).  Apt-get and Aptitude will look on you sources list, download a package from the internet, and install it with very little hassle.  

Here is some vocabulary to help:

_Console:_ A command-line text based interface.  It allows the user to type in commands to interact with Linux.  Typing in commands is more flexible and powerful than using a window manager.

_X (window manager):_ A graphical way to interact with Linix.  It is user friendly and takes a lot of input through the mouse.  

_Terminal:_ A program that runs inside X, but allows the user to type in commands as if they were on the actual console.

---

### Post by halitech on 2007-01-20
I know apt is but I thought aptitude was an extra you can add but is not included

---

### Post by reabralop on 2007-01-20
> **gruffy-06 said:**
> Aptitude is part of the base of any Debian-based distro. You shouldn't have to install it manually.:)

If this is the case then how do I use it?

---

### Post by JamieC on 2007-01-20
Invoke aptitude with the appropriate parameters using terminal.

You many want to type "man aptitude" (documentation) or just "aptitude" (interface).

---

### Post by halitech on 2007-01-20
open a terminal and type 

```

sudo aptitude install (name of package)

```

it should ask for your password and away you go

---

### Post by reabralop on 2007-01-20
That's what I needed to know, thanks.

---

