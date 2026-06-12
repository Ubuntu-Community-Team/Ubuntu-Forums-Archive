---
title: "Linux filing system?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2006-07-10
I was travelling through my folders and had a thought, is Linux really that organized? I'm looking around and I don't really know. In Windows you have your documents, program files, etc. In Linux what is the equivalent of Program Files? My drive is filling up and I don't know what I'm doing. For example my /proc folder is taking up 896.1MB and inside it, is loads of folders with numbers for names so, what exactly is /proc? 

Then /usr what about in here? It's taking up 1.8GB so I excpect this is like Program Files right? What about /var?

I know Linux filing system in Linux is different I'm just trying to understand it so I know what I'm installing too much of so my drive doesn't fill up to quickly. So could someone shed some light these folders and what they are for?

---

### Post by jd65pl on 2006-07-10
Hi, I wondered the same and found [this]("http://www.ubuntuforums.org/showthread.php?t=17841&highlight=essential+programs") thread useful, I don't know if its what you are looking for tho.

Thanks

---

### Post by Brunellus on 2006-07-10
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

in general:

"programs" are installed in any number of places.  Ubuntu's packages tend to put them in /usr .  they can also be in /opt

/var is where logs are kept;  there are scripts that rotate & purge logs every so often, and you can change those.

note that there are things in the filesystem that aren't really "files" per se--like the whole /proc directory-- but *nix treats everything like a file.

Incidentally:  they're really *directories,* not *folders*.  That's always irritated me;  a "folder" is a graphical representation of a directory in a filestructure.  But then, I guess I grew up on MS-DOS, and still have that mentality.

---

