---
title: "Reading Beginning Ubuntu Linux- Why are symbolic links created when using init.d"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by ghoran on 2007-12-12
Hello everyone,
This is my first post in this forum.
A little background.
I am a computer programmer that codes on a UNIX server and a Linux web server.
My desktop is Windows XP.
At home I have two machines. One on XP (AMD 2200 w/256 Meg) and one on Simply Mepis 3.3 (AMD 1.1 Ghz w/ 256 Meg)
My children want me to upgrade both computers to Ubuntu as the Simply Mepis machine never crashes or slows down :) 

I code on the UNIX server is C++ and I understand Makefiles and imake. I have also done some shell scripting and user Perl to read sybase and output excel. <- Some background.

My question is this:
In reading, "Beginning UBUNTU Linux: From Novice to Professional Copyright 2006" from the library I am coming across something that I have been confused about.

I believe that /etc/init.d is run at startup. Right? Can someone explain that?

When setting up things to run at startup we edit a file and then create a symbolic link to that file.

For example, at one point (Chapter 8 page 88) he talks about setting up WPA support. This requires a package installation and configuration (No problem).

My confusion is (remember I am just reading the book and need yet to install) is why do we create a sctipt in /etc/init.d directory and then need to create a symbolic link to that to /etc/rc2.d.
For example:
sudo ln -s /etc/init.d/wpasupplicant /etc/rc2.d/S40wpa

Why do we not point a startup script to /etc/init.d?
What runs at startup?

Thanks
Gary

---

### Post by ByteJuggler on 2007-12-12
The actual startup scripts are stored in init.d, however, there are multiple possible "runlevels" possible on Linux.  Each runlevel can have its own set of services started or not started.  So, to facilitate that, each runlevel is represented by its own folder, for example "runlevel 2" is represented by folder rc2.d.   Now, because you don't want to duplicate the startup scripts into each runlevel folder (would mean you'd have to e.g. fix a bug 5 times in one script if you have a copy of the same startup script in five runlevel folders), you instead simply link the file in init.d to the relevant runlevel folder.  Then if you fix/change the script in init.d, it in effect automatically applies to all runlevels where that startup script is linked to.  Also, notice the naming convention is "SXX" where XX is a number in the rcX.d folders, this is to allow an ordering to be imposed on the order the services start in based on the filenames of the startup scripts.  So if you want to make a script start sooner you can just rename the link and reduce it's "S" value, and be done with it.  

Hope that clarifies it.

---

### Post by ghoran on 2007-12-12
ByteJuggler,

YOU ROCK!
I cannot believe how quickly you responded. If my email was not open I would have not checked until tomorrow.
The explanation is perfect!
Thanks so much.

Thanks
Gary

---

