---
title: "Sources list help"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by dangerpl on 2007-04-18
Hi, I don't know much so it may sound stupid. I need to replace the text in the /etc/apt/sources.list by text in /etc/apt/sources.list_backup.

Thank you!

---

### Post by joeblow1102 on 2007-04-18
the advice i'm going to give will have you overwrite the sources.list text.  so i'm not sure if you need that or not, but to replace the file, you can go:

sudo mv /etc/apt/sources.list_backup /etc/apt/sources.list

---

### Post by ardchoille42 on 2007-04-18
Or you can backup your current sources.list first

```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak && sudo mv /etc/apt/sources.list_backup /etc/apt/sources.list

```

---

### Post by dangerpl on 2007-04-18
This is my actual problem. I recently tried installing some repositories for DVD authoring programs. Right now I'm getting this message from the Package Manager:

Error: Opening the cache(E:Malformed line 4 in source list /etc/apt/sources.list.d/edgy-universe.list(dist parse), E: The list of sources could not be read.)

---

### Post by STREETURCHINE on 2007-04-18
post the out put from 

    ```
cat /etc/apt/sources.list
```

 and post it here this should be easy to fix without overwriting everything

---

### Post by dangerpl on 2007-04-18
:( I don't know what I did wrong cuz now this file no longer exists! Help!

---

### Post by Ozitraveller on 2007-04-18
Do the backup files exist?

---

### Post by dangerpl on 2007-04-18
Yes, two files named sources.list.bak and sources.list.save... Are those the ones?

---

### Post by Ozitraveller on 2007-04-18
Just copy one of these file back to sources.list.

sudo cp /etc/apt/sources.list.bak  /etc/apt/sources.list

Then start over again.


If you open it with an edit 
sudo gedit /etc/apt/sources.list
then paste it in the thread.

:)

---

### Post by STREETURCHINE on 2007-04-18
if you are still using edgy  you can use the source.list i have posted
just put an # in front of the ones you dont want or erase them..

```
gksudo gedit /etc/apt/sources.list
```

and copy and paste

```

deb http://au.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy main restricted
deb http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

deb http://au.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy universe
deb http://au.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main universe

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu edgy-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
#AUTOMATIX REPOS END

#AUTOMATIX BLEEDER REPOS START

deb http://ubuntu.beryl-project.org edgy main
#AUTOMATIX BLEEDER REPOS END

###swiftfox###
deb http://getswiftfox.com/builds/debian unstable non-free
##swiftfox end###

#### picasa####
deb http://dl.google.com/linux/deb/ stable non-free
###picasa end####

```

---

### Post by dangerpl on 2007-04-18
Now, before I do this... These two files contain completely different text and I didn't create them. Unfortunately before I followed the first suggestion I didn't back these files up and for some reason they no longer exist.

---

### Post by dangerpl on 2007-04-18
Unfortunately, this doesn't solve the problem as I am still not able to perfom an update. The error is reffering to the file /etc/apt/sources.list.d/edgy-universe.list

---

### Post by Ozitraveller on 2007-04-18
Untick universe on the repo dialog.

---

### Post by dangerpl on 2007-04-18
Can you please clarify?

---

### Post by Ozitraveller on 2007-04-18
Sorry :)

There is a dialog in synaptic that you use to select the repositories, it's on the menu.
I think one of the items there is universe/multi-verse, also there is main, security...

Untick the universe option.

Check this out :

How to install ANYTHING in Ubuntu!
[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

Hope this helps.
:)

---

### Post by dangerpl on 2007-04-18
I can't seem to find it... I found repositories in the Package Manager however I can't find anything reffering to universe.

---

### Post by Sef on 2007-04-18
> Error: Opening the cache(E:Malformed line 4 in source list /etc/apt/sources.list.d/edgy-universe.list(dist parse), E: The list of sources could not be read.)

Try commenting out line 4 in your sources list.  To comment out a line, just put a # before the line.   When you comment out a line, the machine does not read that line.

---

### Post by Ozitraveller on 2007-04-18
The screen should look something like this

It's the first and third items you don't want ticked.

---

### Post by Perfect Storm on 2007-04-18
Have a look at : [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) to put a new sourcelist together with universe, multiverse and more.
replace the old one with it;
```
sudo nano /etc/apt/sources.list
```
save [ctrl]+[o} and exit [ctrl]+[x]

```
sudo aptitude update
```


Note, if you also add unofficial source in the list; you have to;
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys XXXXXXXXXXX
 gpg --export --armor XXXXXXXXX | sudo apt-key add -
```

Where XXXXXXXXX is the GPG Key

---

### Post by dangerpl on 2007-04-18
Thanks a lot everyone! That's all... For now... I'm sure I'll be back with more questions...

---

