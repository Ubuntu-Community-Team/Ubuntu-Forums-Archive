---
title: "Copy files and archive?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by iluminate on 2007-02-12
Hi all,

Hmm...strange this and I can not figure out the correct commands to archive what I want.
Maybe someone can give me useful hints?
Thing is that I want to create a "backup" of my content of /var/www/htdocs/CONTENT and then after the backup is created I want to delere all files and folders inside htdocs folder and replace it with new files.

So how do I do the backup?
I fist thought it was possible to mv and create a compressed archive of the content, but maybe its not?
So what method would you recommend?

I do not work with any gui, just terminal via SSH.

Cheers!

---

### Post by encompass on 2007-02-12
rsync does very well with backups... it has a variety of options, but I think you could look into it and ask questions from there...
man rsync for ALL the options.  Pretty long list.

---

### Post by iluminate on 2007-02-12
Thanks will check rsync! Think however I do not need rsync because I do not need to copy the files from Server to client, just a local backup to a different folder than /htdocs.
Will check it out thoug and do some reading!

Kittos!

---

### Post by highneko on 2007-02-12
This might work. Probably:
sudo tar -czf ~/htdocs.tgz /var/www/*
# [http://en.wikipedia.org/wiki/Tar_(file_format](http://en.wikipedia.org/wiki/Tar_(file_format))

---

### Post by encompass on 2007-02-12
I like rsync even for local transferes... it does a great job of preserving things... and if you make changes often... it makes the changes too without overwriting things it doen't need to.

---

