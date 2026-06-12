---
title: "adding programs to the command line"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by legit on 2005-10-21
hey all,
so i've been putting off posting this for a while because i thought i could figure it out, sadly i can't.  At any rate i have some basic installation questions.  I have downloded and untarred(sp?) several programs, all of which i have running.  thats all good and well i just don't understand how linux works specifically.  Once i download a tar.gz i unpack it and then install it but they all install to the current directory (usually my home folder) so where should i be installing them? Secondly how do i get them to be recognized by the command line? for example i installed eclipse and i want to type eclipse at the prompt and have it run how do i do this?  thirdly, how do i add programs to the "start"(sorry im not sure what to call it, i realize that this is a windows term) menu?
thanks for all the help i really appreciate it.
thanks,
- legit

---

### Post by gord on 2005-10-21
to get things running from the terminal you have to create a symbolic link to the program in /usr/bin, /usr/local/bin or one of the other runnable directory things(?). 
```

cd /usr/bin
sudo ln -s <path to file> 

``` 
should work fine i think... with <path to file> being /usr/home/firefox/firefox or whatever it is your installing :)

---

### Post by invalid on 2005-10-21
Many programs will do this for you automatically, with the "make install" command. However, not every single one has this option. Check the packages README for more information.

Cheers,
Cb

---

### Post by David Marrs on 2005-10-22
Generally speaking, files that are installed by the system (ie. via apt or dpkg) are installed to /usr/bin/ while files that you install manually should go to /usr/local/bin/. Programs installed here can be run directly from the terminal without the need to provide a full path.

---

