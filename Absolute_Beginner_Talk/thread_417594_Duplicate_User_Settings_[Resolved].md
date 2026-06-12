---
title: "Duplicate User Settings? [Resolved]"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Hase on 2007-04-21
I have a user (me).  I have spent a great deal of time configuring e-mail clients, gnome/beryl and the like.  I now need to add another user (my wife).  I want her settings to be more similar to mine than to the default.  Merely copying the contents of my home directory (settings files, etc.) to her home directory and chowning them doesn't work.

Ideas?

---

### Post by Happy_Man on 2007-04-21
Merely copying the /home folder doesn't work (I had a nasty experience with this last night), so you need to wrap it all up as a .tar.gz file, and then unzip it for her. 

```
tar -pczf name.tar.gz /path/to/directory
```

---

### Post by ComplexNumber on 2007-04-21
> **Hase said:**
> I have a user (me).  I have spent a great deal of time configuring e-mail clients, gnome/beryl and the like.  I now need to add another user (my wife).  I want her settings to be more similar to mine than to the default.  Merely copying the contents of my home directory (settings files, etc.) to her home directory and chowning them doesn't work.

Ideas?
i assume that you will have root privilages and that its not necessary for your wife to have them. if you're the one who's going to be maintaining the system and installing programs, then your wife doesn't need root privilages.
in that case, its just a case of adding the new user. go main menu -> system -> administration -> users and groups. add your wifes name to the list of users AND groups. for example, if your wife's name is Clair, then add "Clair" to the list of users and then add "Clair" to the list of groups. also, make sure that user "Clair" is a member of group "Clair" and any other group that she needs to be a member of (i imagine that she needs to be a member of all groups that you are in except for admin).


btw when you create a new user, the home directory for that user together with all the directories (eg .gconf, .gnome2, etc) will automatically be created (remember the first time that you installed ubuntu and you had a home directory ready and waiting for you?).

btw2 the system defaults are mostly set in the /etc directory. but i thin i twould be easier to just add your wife as above and then manually change the settings so that they are similar to yours.

---

### Post by Hase on 2007-04-22
> **ComplexNumber said:**
> 
btw2 the system defaults are mostly set in the /etc directory. but i thin i twould be easier to just add your wife as above and then manually change the settings so that they are similar to yours.

I'm aware that many are in /etc (I'm a CL guy going back many years), but this is exactly what I want to avoid.  It's the Gnome/Beryl and other environment settings (which I have spent countless hours tweaking) that I am more concerned about.  

I'll have to try the tar.  Though doesn't the p option retain me as the owner of the files as they are uncompressed, shouldn't they be chowned to her user?

---

### Post by Happy_Man on 2007-04-22
Actually, in beryl you can export your settings to a file using the export button down in the lower left.

---

### Post by louieb on 2007-04-22
I believe that when you add a new user it copies the content of /etc/skel to the home directory of the new user. You might want to play with putting your . configuration files there and creating a test user just to see what it does as far as ownership and permissions  before adding your wife as user. But that may be more trouble than its worth unless you are adding more that one or two users.  
If it were me I'd probably just use tar. to backup and copy over the files. then use chown -R and change ownership. and be done with it.

---

### Post by chakkaradeep on 2007-04-22
Hope Ubuntu's Migration Assistant also includes this one day :) :KS

---

### Post by Hase on 2007-04-27
It turns out that "cp" and "chown" do work, what I was missing was that they don't copy/change dot files (which are most or all of the settings files).
First I created another user ( I prefer "adduser" over "useradd").
I then copied the normal files over:
```
sudo cp -rv /home/currentuser/* /home/newuser/
```
Than I copied the hidden files.  The first time I did this I issued the command without the "[a-zA-Z0-9]" and it also copied the ".." directory and I found myself in recursive hell.  To avoid copying the "..", I limited it:
```
sudo cp -rv /home/currentuser/.[a-zA-Z0-9]* /home/newuser/
```
Then chown the normal files:
```
sudo chown -Rv newuser:newusergroup /home/newuser/*
```
Then chown the hidden files.  This command is susceptible to the same ".." recursion problem and will change the ownership of the entire "home" directory if it isn't limited in the same way:
```
sudo chown -Rv newuser:newusergroup /home/newuser/.[a-zA-Z0-9]*
```
While messing up the ownerships in my home directory (see above), I accidentally reset the owner of the /home/newuser/ directory itself and had to fix it too (just avoid that mistake):
```
sudo chown newuser:newusergroup /home/newuser/
```

That did it.

---

