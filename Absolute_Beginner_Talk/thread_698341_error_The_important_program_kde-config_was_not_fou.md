---
title: "error: The important program kde-config was not found!"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by DaveGiant on 2008-02-16
I am trying to install 'beryl' on my new Ubuntu install. When I type in ./configure I get the following error.

> configure: error: The important program kde-config was not found!

Should this error come up? What is this kde-config and how do I install it?

---

### Post by kaiju on 2008-02-16
first things first: i don't know if it's normal or not for beryl to ask for kde-config
(to me it sounds somewhat fishy because you're saying that you have ubuntu, and kde apps are normally only found on kubuntu)

anyway, in case this is of any help:
for any required program, you can try to just type its name into a terminal (like gnome-terminal), and you will get some info about how to install it, e.g. typing kde-config gives:
The program 'kde-config' is currently not installed.  You can install it by typing:
sudo apt-get install kdelibs4c2a
bash: kde-config: command not found

other useful commands are 'apt-cache search' and 'apt-cache show'

---

