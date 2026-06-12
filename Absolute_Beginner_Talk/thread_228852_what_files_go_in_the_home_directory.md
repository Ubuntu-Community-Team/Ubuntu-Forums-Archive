---
title: "what files go in the /home directory?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-03
Ok, as I draw closer to installing Ubuntu, I want to make sure I understand the /home directory properly (if I decided to put it on a separate partition). What types of things will go into this directory? I was thinking of making it a separate partition, for the normal suggested reasons, but only making it maybe 1GB. My understanding is that it stores application preferences and things that you'd want to save when reinstalling Ubuntu later. But will there be bigger files here? Is /home normally much bigger than 1GB?

Basically, I want to know what it *is* before I give it a partition of its own, which means allotting it space I can't change later (easily).

---

### Post by ironfistchamp on 2006-08-03
Personally I would make it bigger. Mine is 30Gb. Basically the home directory not only stores preferences and settings but it is like the My Documents folder on windows. You can store anything in there. Sometimes good for storing your own apps that you don't want to share or docs that are private.

Examples of things I have in mine.

Images
Music
A few apps
Videos
Documents
Settings
Gnome themes
Amsn themes

And pretty much anything else I have downloaded. 

Remember regular users (not root) can only write to their home directory. It is your space to do with what you want I guess.

Well that is my understanding

Hope this helps

Ironfistchamp

---

### Post by Metacarpal on 2006-08-03
/home will contain personal files for you and any other users you add to your system.  This is where you save your documents, pictures, music files, that sort of thing, as well as the configuration files for things like your desktop, mouse speed, internet bookmarks, email, etc, which change from one user to the next.

---

### Post by aysiu on 2006-08-03
**Windows**:
C:\
C:\Program Files
C:\Documents and Settings\username\My Documents
C:\Documents and Settings\username\Application Data

**Ubuntu**:
/
/usr/bin
/home/username
/home/username/.

Of course, it's a *bit* more complicated than that, but that gives you a general idea of the equivalencies.

---

### Post by ironfistchamp on 2006-08-03
Good call there aysiu I never thought of explaining it like that. :p It makes it alot clearer for me aswell.

---

### Post by mscman on 2006-08-03
> **ironfistchamp said:**
> 
Remember regular users (not root) can only write to their home directory. It is your space to do with what you want I guess.

This is only the *default* setup. You can modify your filesystem to any extent you like, such as creating a new "home" directory in the root filesystem and changing the ownership of the directory, although this practice isn't always recommended.

Back on topic, you may want to make the /home directory larger than 1Gb if you plan on having a lot of files. Like the above posts stated, your home directory isn't only for app/user settings, but also acts as your "My Documents" directory.

Just my two cents... :-D

***PLEASE READ***
I don't advocate setting up extra "home" directories in your filesystem until you get used to using Linux. This makes your filesystem more complicated and greatly increases your chances of seriously foobaring your system. (Messing with file permissions in general runs this risk)

---

### Post by ironfistchamp on 2006-08-03
Thanks for pointing that out mscman. Its prob not a good idea to make the whole filesystem RWX for everyone though :p It sounds like Windows to me.

---

### Post by cantormath on 2006-08-03
> **JohnJSal said:**
> Ok, as I draw closer to installing Ubuntu, I want to make sure I understand the /home directory properly (if I decided to put it on a separate partition). What types of things will go into this directory? I was thinking of making it a separate partition, for the normal suggested reasons, but only making it maybe 1GB. My understanding is that it stores application preferences and things that you'd want to save when reinstalling Ubuntu later. But will there be bigger files here? Is /home normally much bigger than 1GB?

Basically, I want to know what it *is* before I give it a partition of its own, which means allotting it space I can't change later (easily).

/home is alot like the "Documents and Settings" folder in windows, I think its alot cleaner.  There is a folder for each user of the machine in /home/, ie) in my home folder, there is a folder cantormath.

My /cantormath/ folder is like my documents.  My documents are in a folder called my documents, there is a My video folder, etc etc.  There is also the Desktop folder which leads to the user cantormath's desktop.  The only user whos home folder is not in /home/ is root.  

There are also many hidden folders in a users home folder, like .gnome/, which have to do with that users home settings. you can click on view and click show hidden folders to see them.

---

### Post by JohnJSal on 2006-08-03
Thanks guys. I think I get it a little better now. Seems like /home needs significant space. Even though I plan to use Ubuntu just to test it out, I don't want to short-change myself, so I guess I'll make it a decent size.

---

