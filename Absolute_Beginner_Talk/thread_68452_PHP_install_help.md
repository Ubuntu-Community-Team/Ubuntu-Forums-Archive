---
title: "PHP install help"
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by jjtoymachine on 2005-09-23
Hi everyone, im new to Linux and im trying to setup all the things i need for my webserver i have followed the unofficial ubuntu guide closely but ive run into a problem.

i install apache with no problems

but when i type in: sudo apt-get install php4

i get a **E: couldn't find package php4 ** message


can you plz help?

JJ

---

### Post by SilentCacophony on 2005-09-23
You'll have to add the universe repository to get that. While there are some php packages in the main repository, most are in universe. See the [How to add extra repositories?](http://www.ubuntuguide.org/#extrarepositories) section of the unofficial guide for how to do that. That page has much more info than that, including some info for server setup.

Also, if you have the default ubuntu-desktop installed, you can use synaptic to browse the packages. If you're on just a server install, you might want to try the aptitude package manager, which lets you browse using a text ui.

---

