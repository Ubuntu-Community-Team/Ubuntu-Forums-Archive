---
title: "Installing Teamspeak2 CLIENT"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by goTUX! on 2006-12-26
Hi

Have tried installing TS2 client from [www.goteamspeak.com](www.goteamspeak.com)

I extract the tar.bz2 file and run the setup.sh script and i get icons in my home directory

After double clicking the Teamspeak link i always get this popping up saying its an executable text file. Clicking run works absolutely fine, but i dont understand why this happens. I would like it to just run without me having to go through that every time.

Sorry if im being thick, but dont really understand how to install from tar.bz2 files very well, the guides confuse me.

Thanks in advance

---

### Post by goTUX! on 2006-12-27
Nobody has any idea?

---

### Post by theoldgit on 2006-12-27
The way iI got round this [roblem was to create a launcher on the desktop. I use Gnome so the way I did it was to Right click on the desktop pick Create Launcher. Fill in the spaces amd away you go. To find the Command use Browse and select the the file u usualy use to launch TS.

If this wont work come back


hope this helps

---

### Post by goTUX! on 2006-12-27
Excellent, thanks!

Seems so easy but its always frustrating when you move to a new OS :D

Ok, next question...

Its installed in my home folder which means i can access it but nobody else. Still havent sussed out the filesystem properly, so where do i install it so that everybody can access it?

---

### Post by jvc26 on 2006-12-27
You could make a new directory:
```

sudo mkdir /apps

```
Then install the application to that folder, then change the permissions for that folder:
```

sudo chmod -R +rwx /apps

```
And that should allow anybody to access it from the computer - do you have several logins on the same computer I'm guessing?
Il

---

### Post by goTUX! on 2006-12-27
Is there not somewhere already?

I mean OpenOffice, Gaim etc are all available to all users. Where are they installed to.

"the other operating system" has a 'Program Files' folder which allows all users to run the programs.

There must be somewhere in linux or doesnt it work like that?

---

