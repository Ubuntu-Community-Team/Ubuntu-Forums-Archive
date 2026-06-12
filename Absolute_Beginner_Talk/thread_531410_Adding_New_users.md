---
title: "Adding New users"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-08-21
I created two new users on my machine. I did not give them the rights to administer the system (its an option on one of the tabs while creating the user)

They currently belong to different groups like user1:user1 and user2:user2.

1) Now I want to give them access to all the movies, music and pictures folders that I have in one of my drives. How do I do this? Should I create a new group and make both of them (and me) the members of that group and give rights to that group ?

2) Since I did not give them administration rights, they do not have links to the synaptic package manager and Applications-->Add/Remove. I also tried installing thru the command line and it kept saying "Sorry, Try again" even tho the password I entered was correct. How do I allow them to have installation rights, so that they can install games/music players etc (preferably) without giving them the root password and without giving them admin rights. Is this possible?

---

### Post by Ek0nomik on 2007-08-21
Regarding Number 1...

Couldn't you just make your two new users members of **your** group?  Since you are the user who created those folders and files, you could just make them part of your group.

Number 2...

I'm not sure how you could allow them to install software.  The purpose of having the root password is so that nothing can be installed without that root password.  You could probably create separate directories that aren't owned by root in which they could install to, but that would start to create a mess of work for you I imagine.

---

### Post by bodhi.zazen on 2007-08-21
You can manage the shared files/directory via permissions.

You can either chmod 777 or 
chown root.users <directory>
chmod 770 <directory>

& make the new users members of the group uses

For add-remove programs you will need to edit sudoers. This is the advantage of sudo over su

Again, make a group, say install, and give the group access vis sudoers to say apt-get or aptitude

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

See the examples near the end of that page ...

---

### Post by WebSiteGuru on 2007-08-21
> **Inxsible said:**
> 1) Now I want to give them access to all the movies, music and pictures folders that I have in one of my drives. How do I do this? Should I create a new group and make both of them (and me) the members of that group and give rights to that group ?

Yes, create a group (IE: mydata) and give user1 and user2 read/write access to that group. Your username should already have the right to the folder, since you are the owner creator to the folder.

> **Inxsible said:**
> 
2) Since I did not give them administration rights, they do not have links to the synaptic package manager and Applications-->Add/Remove. I also tried installing thru the command line and it kept saying "Sorry, Try again" even tho the password I entered was correct. How do I allow them to have installation rights, so that they can install games/music players etc (preferably) without giving them the root password and without giving them admin rights. Is this possible?

I would like to know that too. :D :guitar:

---

### Post by Ek0nomik on 2007-08-21
> **bodhi.zazen said:**
> You can manage the shared files/directory via permissions.

You can either chmod 777 or 
chown root.users <directory>
chmod 770 <directory>

& make the new users members of the group uses

For add-remove programs you will need to edit sudoers. This is the advantage of sudo over su

Again, make a group, say install, and give the group access vis sudoers to say apt-get or aptitude

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

See the examples near the end of that page ...

Doing 777 would simply make all the music, movies, and pictures readable and writeable by **all** users, correct?

So it wouldn't just be creating rights for those three users, rather *everyone*.

---

### Post by Inxsible on 2007-08-21
> **Ek0nomik said:**
> Regarding Number 1...

Couldn't you just make your two new users members of **your** group?  Since you are the user who created those folders and files, you could just make them part of your group.
But that would give them all permissions of my group which I don't want. I would much rather create a separate group specific to this purpose.

---

### Post by funrider on 2007-08-21
1. put all the movie and music files in a shared drive/directory and grant the respective right on the top level

2. i dun think you can do that. only user in admin group are sudoer (correct me if i am wrong).

---

### Post by Inxsible on 2007-08-21
2 Rephrased !!

2) The users user1 and user2 are probably not gonna use the command line to install stuff (but it wont hurt to have it since I can then use the CLI when logged in as them) 

They also probably don't need the Synaptic Package Manager, since they wouldn't know what package to look for.

They do, however, need the Applications --> Add/Remove to be seen so that they can install a few things here and there.

This is the only condition my gf would start using Ubuntu :( since she wants it to be "as easy" as Windows :mad:

And the reason behind me NOT wanting to give admin rights to those users is that I am trying to idiot-proof the system for them, so they can't delete/move some important files

---

### Post by schorsch on 2007-08-21
> **funrider said:**
> 
2. i dun think you can do that. only user in admin group are sudoer (correct me if i am wrong).
Just as bodhi says: Add both users to a new group (let's call it install) and add
```
%install ALL=(root) PASSWD: /usr/bin/apt-get, /usr/bin/dpkg, /usr/bin/aptitude, /usr/bin/synaptic
```
You can also add the following line in /etc/suders in section "cmnd alias specification":
```
Cmnd_Alias    INSTALLATION = /usr/bin/apt-get, /usr/bin/dpkg, /usr/bin/aptitude, /usr/sbin/synaptic 
```. When you did this, the first mentioned code can be changed to 
```
%install ALL=(root) PASSWD: INSTALLATION
```
So you have just to edit the cmnd-aliases ...

---

