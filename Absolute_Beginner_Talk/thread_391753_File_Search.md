---
title: "File Search"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by marty13 on 2007-03-23
Hi Guys,
in windows it is very easy to do a file search. How do i do a file search in Ubuntu 6.06??
second question, when i install ubuntu i used my name as a user. is "root" a defalt user and what would the defalt password be?
thanks.

---

### Post by milton1 on 2007-03-23
> **marty13 said:**
> Hi Guys,
in windows it is very easy to do a file search. How do i do a file search in Ubuntu 6.06??

There should be a "find files" option on the menu. Or, you can open a terminal and type 
```
locate <filename>
```

locate works very well and very fast, but it does need to be updated occasionally with
```
sudo slocate -u
```

> second question, when i install ubuntu i used my name as a user. is "root" a defalt user and what would the defalt password be?
thanks.

root is disabled by default in ubuntu. you can perform administrative tasks as your primary user by using the sudo command and your password.

---

### Post by tomxyz on 2007-03-23
If you are using gnome, under places (locations) you have 'search for files'

---

### Post by joethenoob on 2007-03-23
For the file search (GUI style), on the upper panel click Places>Search for Files....

For root access, you can open a terminal and type sudo (then whatever command) and you will be prompted for your password.

There is another way to get root access for a bit, but I don't know how safe it is. Maybe someone out there can tell us. In terminal, type sudo /bin/bash and enter your password when prompted. This way you don't have to keep typing sudo and your password if you need to run multiple commands as root. You will have close the terminal session to back out of root access. I'm told you can type exit to go back to normal user-level access, but I would rather close the session than take any chances.

---

### Post by tomxyz on 2007-03-23
If you don't want to type sudo in front of every command, type once sudo -i instead of just sudo. your $ sign should change in the # sign. You won't have to use sudo again until you close the terminal.

---

### Post by marty13 on 2007-03-23
WOW! i can not tell you how many times i looked at the dropdown menu "places" and never saw the file search option.
thanks guys!

P.S. is my face red!

---

### Post by doctapeppa on 2007-03-23
You also might want to check out a great program called Beagle. 

[http://www.ubuntugeek.com/install-beagle-search-tool-in-ubuntu-edgy.html#more-118](http://www.ubuntugeek.com/install-beagle-search-tool-in-ubuntu-edgy.html#more-118)

---

### Post by joethenoob on 2007-03-23
> **tomxyz said:**
> If you don't want to type sudo in front of every command, type once sudo -i instead of just sudo. your $ sign should change in the # sign. You won't have to use sudo again until you close the terminal.

Thanks! I like that option much better.

---

### Post by marty13 on 2007-03-23
installing vmware and it says it wants to use C compiler, but it can not find make.
did a search for make and i can not find it eather.
i thought the compiler was built in to linux?

---

