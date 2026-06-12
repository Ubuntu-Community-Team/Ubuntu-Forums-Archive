---
title: "problem with apt-get"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Nefarious on 2007-06-19
every time I try installing something I get a a message that is like this

Media change:Please insert disk labeled ubuntu server ect...

something like that. so I insert the disk hit enter and the message comes back up every time. doesn't mater what it is..

also when I first installed the ubuntu server 7.04 I chose to install LAMP which needless to say didn't install. 

I've already guessed that I have a bad disk would anyone agree with me?

---

### Post by dbbolton on 2007-06-19
> **Nefarious said:**
> every time I try installing something I get a a message that is like this

Media change:Please insert disk labeled ubuntu server ect...

something like that. so I insert the disk hit enter and the message comes back up every time. doesn't mater what it is..

also when I first installed the ubuntu server 7.04 I chose to install LAMP which needless to say didn't install. 

I've already guessed that I have a bad disk would anyone agree with me?
go to System > Administration > Software Sources, and uncheck the CD sources

---

### Post by Nefarious on 2007-06-19
how exactly do I do that on the command line as I don't have an x windows system because Im using server edition.

---

### Post by PaulFr on 2007-06-19
Change directory to /etc/apt and run **grep cdrom sources.list | grep -v '^#'** to get the uncommented cdrom references which apt-get is using. Then you will need to comment out each such line by editing (**sudo vim sources.list**) and inserting a # character at the beginning of each of the cdrom line(s) identified above. When you are done editing, again run the command given above to see if you have commented it properly.

I am not sure whether cdrom entries are also present in the files in /etc/apt/sources.d directory (for me, there are no cdrom references in those files). You may need to check. Hope this helps.

---

### Post by Nefarious on 2007-06-19
Thank you I highly appreciate it.. I will go and try this now ^-^

---

### Post by RedSquirrel on 2007-06-19
The lines with "cdrom:" are near the top of the file. 

If I remember correctly, there is only one line that needs to be commented and /etc/apt/sources.list is the only file you have to edit so that apt-get will stop asking you to insert the CD.

You might also prefer nano to vim:

```
sudo nano -wB /etc/apt/sources.list
```I'm not sure why LAMP didn't install; it worked fine for me. Did you check the CD before you installed?

---

### Post by Seisen on 2007-06-19
You are correct Red Squirrel.

---

