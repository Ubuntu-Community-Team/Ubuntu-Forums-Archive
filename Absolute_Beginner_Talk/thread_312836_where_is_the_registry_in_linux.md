---
title: "where is the registry in linux?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by rajeev1204 on 2006-12-05
hi

i would like to know where is the registry in linux? is it called registry just as in windows or by some other name?

also what do we mean by symbolic links?

---

### Post by kerry_s on 2006-12-05
Funny, there is no registry.

A symbolic link is a link to another application/file/folder.

---

### Post by Shatrat on 2006-12-05
I dont even really know what a registry is. Can't be a good idea.
Symbolic links are like shortcuts, only useful.

---

### Post by RAOF on 2006-12-05
The closest thing to a "registry" for Gnome would be **gconf**.  You can access it by running "gconf-editor".  Or manually editing XML in ~/.gconf/*, but you probably don't want to do that :).

A symbolic link is, indeed, like a shortcut.  But it behaves in almost every way like the thing it's pointing to - for example, if a program tries to "read" from a symbolic link, it ends up reading from the file the link points to.

---

### Post by rajeev1204 on 2006-12-05
hi

thanks all u folks 
 
i have a million more questions ! i will keep posting

also could u give me some info or links where i can find out more about linux in general


regards

rajeev

---

### Post by MobyTurbo on 2006-12-05
Linux in general does not use a registry, you edit text files, or configure using the packaging tool. (dpkg-reconfigure allows you to re-answer questions apt-get and friends would give) 

There *is* a limited registry for GNOME applications, stored in XML (a text format) and editable with gconf-editor. However, that does not play the all-encompassing role it does in Windows, it's only for a few applications and for a few settings.

Symbolic links are links (creatable on the command line by ln -s) that allow one to give a program multiple names or put it in multiple places. (This is a lot more useful than one would think.) There is such a think as hard links, which people used prior to the invention of symbolic links in Unix in the '80s, but they are limited to one file-system and can't be used safely to link directories, so just about everyone prefers to use symbolic links. 

Windows has something like this, links to programs in different folders, like the mess known as "my documents", but these links, as you probably recall, produce a *lot* of disk thrashing when you use them and something's moved or been deleted. Instead of failing, it ends up trying to search the whole hard-drive for a file that looks right. "Those who don't learn from Unix are doomed to repeat it - badly."

I hope this has helped more than confused. You may wish to get a book on Unix that will help you learn some basic concepts. (Linux is a clone of Unix.)

---

### Post by housam on 2006-12-05
Try [this]("http://kernel.org") and [this]("http://www.die.net/doc/linux/man/man8/mount.8.html").

---

### Post by angkor on 2006-12-05
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

For (some more than others) useful linux commands.

---

### Post by rajeev1204 on 2006-12-05
thank u all

---

