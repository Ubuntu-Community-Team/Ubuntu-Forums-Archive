---
title: "CD archiver on Ubuntu?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by pompiuses on 2006-07-17
To archive my cds on Windows I've used WhereIsIt.

That's an application that reads the content of a cd so you may search through it later to find stuff. Neat if you've got hundreds of cds (as I do).

Is there something similiar I can use on Ubuntu?

---

### Post by orb9220 on 2006-07-17
gwhere it's in synaptic

Removable media catalog manager.
GWhere allows to manage a database of your CDs and other removable media (hard disks, floppy drive, Zip drive, CD-ROM, etc...). With GWhere it's easy to browse your CDs or to make a quick search without needing to insert your CDs in the drive at each once. This program is written in C with GTK+ for GNU/Linux.

Hope this helps

---

### Post by orb9220 on 2006-07-17
Kcatalog for KDE but should run in gnome just fine also in synaptic

CD organizer for KDE
If you have many CD and tons of downloaded files, but you aren't able
to remember where you put a file when you need it, then Katalog may help
you. With this application you can scan a CD and store all the data about
each file in a tree structured catalog. You can add as many catalogs as
you like. Searching through the catalogs it's easy and fast. The folder to
search can be on your drive or on a removable media, such a CD, ZIP or
floppy. Katalog saves data in a XML file, compressed on the fly using gzip.

Homepage: [http://salvaste.altervista.org/](http://salvaste.altervista.org/)

---

### Post by Third Thoughts on 2006-07-17
> **pompiuses said:**
> To archive my cds on Windows I've used WhereIsIt.

That's an application that reads the content of a cd so you may search through it later to find stuff. Neat if you've got hundreds of cds (as I do).

Is there something similiar I can use on Ubuntu?

I don't know of any native Linux apps that do what you're talking about. You could try running WhereIsIt under wine, that's what I do with the one program  that there's no Linux replacement for (Firstclass). I managed to download and install WhereIsIt using wine, but I don't know if its fully functional because I didn't really bother playing around with it. If worst comes to worst you could always learn some shell scripting and hack together somethign that duplicates the basic functionality. Just create a folder called "Disk Archives" in your home folder. Then put in the disks you want to get a file listing for and do a ls -R, sending the output to a file in your folder. Then when you want to find a file just use grep on  all the files in your "Disk Archives" folder.

~Andrew S.

---

### Post by pompiuses on 2006-07-17
Ok, thanks for the input. I'll check those out :).

---

