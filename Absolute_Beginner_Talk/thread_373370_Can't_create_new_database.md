---
title: "Can't create new database"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by David Floyd on 2007-03-01
I've sucessfully installed Dapper about 4 weeks ago and been experimenting since.

I now want to transfer my Databases from my XP machine (which are Access databases) to MySQL on my Linux box.

So I have installed Apache/PHP/MySQL using Synaptic.

Then I followed instructions on this thread [http://ubuntuforums.org/showthread.php?t=275451](http://ubuntuforums.org/showthread.php?t=275451) (Maybe that was the wrong thing to do :( )

Now I'm in a muddle:confused: .  I have two items in my menus 'MySQL Administrator' and 'MySQL Query Browser' and the only way I seem to log on to these is by using the defaults set by PureFTPd in the above thread. I don't like that - I prefer to set my own way of logging in.

Secondly I cannot seem to create a new database. I've tried using the GUI 'MySQL Query Browser' and the terminal, and I get the same error, i.e. 1044 Access denied for user 'ftp'@'127.0.0.1' to database 'bath_wells' (ie the database I tried to create).

Where have I gone wrong?
Help, please!

David

---

### Post by userundefine on 2007-03-01
Use phpmyadmin.  Easiest for navigating mysql IMO.  Very simple.

---

### Post by ktusyn on 2007-03-01
try doing it without ftp cuz you might be having trouble with root privledges.

---

