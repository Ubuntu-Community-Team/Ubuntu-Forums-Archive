---
title: "Print the package list"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by brentoboy on 2005-10-16
how can I print a list of all  the packages on my system?  - just the installed ones

would it be possible to print the list, complete with descriptions of each package?

certainly there is an apt-get ... list.... | more > mylist.txt /... -5dt zwp 
command line option for something like this.

who knows the jargon and can help me out?

---

### Post by Kyral on 2005-10-16
sudo dpkg --get-selections > packages.txt

Should do it. It just prints out the package list and "installed" though

---

### Post by brentoboy on 2005-10-17
that's the command line wizardry I was talking about.

Thanks!

---

