---
title: "Total Newbie: Trying to install Superkaramba from source files"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by lucakins on 2008-01-08
I am a total, super newbie so please excuse me if I'm a bit stupid.
So, I've been trying install Superkaramba on my os. I'm running Ubuntu 7.10.
Superkaramba is version 0.39, which I assume is the newest one I got from the the website. 
I extracted the files to a folder on my desktop and when I try to run the "./configure" in the terminal, I get what reads:
"Your Installation isn't able to compile simple C++ programs... If you're running a Linux distribution, you might be missing a package similar to libstdc++-dev."

But I've already installed libstdc++-6-4.1-dev.

I tried to run the command "sudo aptitude install libstdc++-6-4.1-dev" I get a message that reads "couldn't find a package whose name or description matched libstdc++-6-4.1-dev"

I don't really understand what's going on here but I would really, really appreciate any help. Thank you!

---

### Post by chips24 on 2008-01-08
type in the terminal

code:
> 
apt-get install build-essential

hope that works

---

### Post by lucakins on 2008-01-08
I tried it, but I get 
> E: Could not open lock file /var/ lib/dpkg/lock - open (13 Permission denied)
            E: Unable to lock the administration directory (/var/lib/dpkg), are you root?        

---

### Post by perlluver on 2008-01-08
> sudo apt-get install build-essential

Type sudo, before the above command.

Or just type in the terminal, > sudo apt-get install superkaramba

---

### Post by Sef on 2008-01-08
For installing anything, read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by lucakins on 2008-01-08
So far so good, thanks guys!
But I have another problem now that I believe is related to my graphics card.

> checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

After searching a bit, this apparently means I'm supposed to install "devel packages for KDE and Xorg" but I'm not sure where to find these (if possible.)

EDIT: Found them!

---

