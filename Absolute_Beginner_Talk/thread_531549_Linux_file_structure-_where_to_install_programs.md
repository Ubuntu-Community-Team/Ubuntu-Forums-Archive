---
title: "Linux file structure- where to install programs?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by kolibri on 2007-08-21
I am setting up Ubuntu on two computers, one of which I will be the only user for about 5 years, the other will have two or three users.  Where do i install programs that might be used by several users?  For example,  on my single user system I just installed Matlab- the install instructions said to install it under /usr/local/  (It took me an hour to realize I had to modify the ./install command with sudo ./install.)  It worked, but why did i put it there?  Other programs installed by synaptic went into /HOME/myusername/.  Why did they go there?

On my other (multiuser computer), if I want to install programs to be used by several users, where would I put them?  (and why?)

TIA

---

### Post by ddrichardson on 2007-08-21
It doesn't really matter, just down to convention. Traditionally non-system programs/libraries and documentation are installed to /usr/local in some distros.

Some distros use /opt - as long as the user's path includes these folders it's all good.

---

### Post by kolibri on 2007-08-21
[QUOTE=

Some distros use /opt - as long as the user's path includes these folders it's all good.[/QUOTE]

OK, I found /opt on my linux file system map, but what do you mean by the 'user's path'? (absolute beginner, remember :) )

---

### Post by PetruM on 2007-08-21
If it goes in **/usr/local/** it will be usable by all users, I think. Your home directory usually contains settings of those programs (I personally never found a program installed by Synaptic over there). :)

---

### Post by ddrichardson on 2007-08-21
Wether or not users can use files depends on wether or not the path variable includes that folder. Path is stored in .bashrc amongst other places and tells the system where executables are stored. Thats what appending "./" does - tells the term to run it from the current folder and not  search elsewhere.

---

### Post by Chaotic Thought on 2007-08-21
Definitely /usr/local. The reason for this is that the package manager will add/remove things from the /usr tree, so if you put stuff there as well, your packages might get overwritten. For example, I compiled a custom version of Window Maker (which is also in the Ubuntu repositories, and is also installed on my system), and the version in /usr/local takes precedence over the /usr version.

---

