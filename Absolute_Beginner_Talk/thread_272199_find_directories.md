---
title: "find directories?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by misfit815 on 2006-10-05
I'm a gnoob on Dapper Drake (and Linux in general).

While dealing with some other issues, I've needed to find where certain folders are located.  For instance, I have Apache HTTP Server 2 installed via apt-get, yet I don't know where it is (and no, it's not where the docs say it probably is).

So I'd like to find it.  The problem is that the Search utility built into the file browser doesn't seem to pick up on directory names, just files.  Retarded.  I've also flipped through the man pages for 'find' in the terminal window, and can't find (ha-ha) the right parameter there, either.

I'm even trying to 'find' a folder whose location I already know, just to get it to work - searched for 'src', which is in \usr.  No dice.  Found a bunch of files with 'src' in them, though!  Stoopid computer.

So, somebody, please... I've spent the better part of two decades understanding computers, and I can't find a directory... please help.

J

---

### Post by misfit815 on 2006-10-05
Ah...

find -name [expression]

Not intuitive.

---

### Post by CatKiller on 2006-10-05
If you want to know where things are installed that were installed through the repositories, you can find the package in Synaptic, click on Properties, and then the Files tab will tell you all of the files that were installed by that package.

---

### Post by po0f on 2006-10-05
misfit815,

The modules, etc, aren't installed at /usr/lib/apache2, the configuration files aren't in /etc/apache2, and the document root isn't in /var/www?  I believe these are the defaults.  But who knows, Debian/Ubuntu do things weird.

---

### Post by David_T on 2006-10-05
Just type "whereis apache"

...and the command "locate" is also good.  you could try 
"sudo updatedb" and then "locate apache".  locate (slocate) searches
an index of your files, rather than your filesystem so is faster.

---

