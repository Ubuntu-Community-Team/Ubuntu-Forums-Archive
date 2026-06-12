---
title: "[SOLVED] can't install Amarok 1.4.9.1"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by gedzilla on 2008-04-16
i'm having trouble installing Amarok 1.4.9.1 (trying to get the cover manager working!)
anyone have an idiots guide for my 'brother' *ahem*?!

---

### Post by jbruwer on 2008-04-16
Hey

Are you referring to the cover manager included with amarok, so you have it installed or is the problem getting it installed in the first place ?

JB

---

### Post by stchman on 2008-04-16
> **gedzilla said:**
> i'm having trouble installing Amarok 1.4.9.1 (trying to get the cover manager working!)
anyone have an idiots guide for my 'brother' *ahem*?!

Amarok is in the repos.

```
sudo apt-get install amarok
```

---

### Post by gedzilla on 2008-04-16
i've installed version 1.4.7 and have been using it for a while, except the the cover manager stopped working a couple of weeks ago (something to do with changed permissions with Amazon?). The kind folks from Amarok have just released a new version (1.4.9.1) to resolve this, before releasing version 2.... or something like that... only problem being i'm a bit of a dullard and can't get it to download. :confused:

---

### Post by gedzilla on 2008-04-16
[QUOTE=stchman;4730076]Amarok is in the repos.

not the new version, i'm afraid...

---

### Post by jbruwer on 2008-04-16
You will have to install it from source then.

you can download it [_here_]("http://amarok.kde.org/wiki/Download:Source") and the installation instructions are there aswell

---

### Post by stchman on 2008-04-16
> **gedzilla said:**
> [QUOTE=stchman;4730076]Amarok is in the repos.

not the new version, i'm afraid...

Then you are going to have to build it from source.

---

### Post by gedzilla on 2008-04-16
tried it this morning - no joy (and was late for work as a result - whoops). I think i'm having trouble extracting the 'tarball'... I try again and let you know the results...

---

### Post by gedzilla on 2008-04-16
When i enter:

tar xjf amarok-1.4.9.1.tar.bz2

in the terminal i get;

tar: amarok-1.4.9.1.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by Oldsoldier2003 on 2008-04-16
> **jbruwer said:**
> You will have to install it from source then.

you can download it [_here_]("http://amarok.kde.org/wiki/Download:Source") and the installation instructions are there aswell

Amarok 1.4.9.1 is included with Hardy. Why not wait a few days, or just upgrade now and beat the rush?

---

### Post by jbruwer on 2008-04-16
This may be a stupid question but, is the tarball in the location you are running the terminal command from ?. That would indicate the "Cannot open: No such file or directory"

---

### Post by gedzilla on 2008-04-16
i'm sure that's not a stupid question at all - it's just that you're asking a complete moron... maybe i'll just upgrade to to Hardy... never was very patient!

---

### Post by jbruwer on 2008-04-16
:)

if you open the terminal it displays the location in front of the cursor for instance:

```
username@machine_name:~$ 
```

the tarball should be in that location in order for the tar command to find the file. So when u open up a terminal type

```
ls
```

it will display the files currently in that location. If the tarball is not listed your in the wrong location. Let me know what it says

---

### Post by stchman on 2008-04-16
> **gedzilla said:**
> When i enter:

tar xjf amarok-1.4.9.1.tar.bz2

in the terminal i get;

tar: amarok-1.4.9.1.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Open a terminal and change to the folder the tarball is in and try:

```
tar -xvjpf ./amarok-1.4.9.1.tar.bz2
```

That should unpack the archive assuming you have write priveliges in that folder.

---

### Post by gedzilla on 2008-04-17
well... i've managed to extract the tarball to my home directory - just can't figure out how to install it now... god, i'm such a noob...

---

### Post by stchman on 2008-04-17
> **gedzilla said:**
> well... i've managed to extract the tarball to my home directory - just can't figure out how to install it now... god, i'm such a noob...

There should be a 

./configure in the folder you extracted.

Refer to the install instructions.

[http://amarok.kde.org/wiki/Download:Source](http://amarok.kde.org/wiki/Download:Source)

---

### Post by gedzilla on 2008-04-25
Yay!! upgraded to hardy yesterday and installed amarok from synaptic - it all works beautifully now...:guitar:

---

### Post by davexnet on 2008-04-26
What about Ubuntu 7.10 ?  I already have 1.4.7 installed.
How do I upgrade to the new version?

Uninstall the old one first?

---

