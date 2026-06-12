---
title: "Why can't I install any new programs?"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by jakelaptop on 2007-07-17
Every time I try to install a new program using synaptic or the terminal, I get error messages. 
In synaptic, it just flashes the progess bar for the install (once the download is done) and goes away, leaving the "x remain to install" at the bottom of synaptic. 
In terminal I get error messages (again, the downloads work just fine)
I forget precisely what the error message reads, but I can get that info for you if you need it. 

Thank you so much for your help.

---

### Post by Outrunner on 2007-07-17
Yes we need to know the error messages.

---

### Post by Al3xK3aton on 2007-07-17
These error messages are usually pretty descriptive, so if you read them then figuring out the solution shouldn't be a problem.

---

### Post by Koybe on 2007-07-17
You can try in a terminal :

```
sudo apt-get update
sudo apt-get upgrade
```

And then post the result here.

If there is broken or remaining package you can try :
```
sudo apt-get -f install
```

---

### Post by holiday34691 on 2007-07-17
I loaded Ubuntu 7.04 on the slave drive the other day and it worked very well until I filled up the hard drive.
Before I could delete some files to make room, the program wrote enough data to the drive that now I can't log in any more. When I try to log in I get an error message telling me it can't write to the log in file.

Anyone know how I can access the drive to delete files to make room? I didn't notice that Ubuntu needs 4 gb or more and the slave drive is only 3gb.

I'm running XP home. 

Could it be that the reason you can't install any new programs is that you've run out of disk space too?

---

### Post by jakelaptop on 2007-07-17
doubtful, because I can't get synaptic to let me REMOVE any programs either.

---

### Post by jakelaptop on 2007-07-17
jwertz@jwertz-laptop:~$ sudo apt-get install supertux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libopenal0a libphysfs-1.0-0 supertux-data
The following packages will be REMOVED:
  supertux-data-stable supertux-stable
The following NEW packages will be installed:
  libopenal0a libphysfs-1.0-0 supertux supertux-data
0 upgraded, 4 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/37.8MB of archives.
After unpacking 37.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)



that last bit is the error message. not sure if you need to read any of the stuff above it.

---

### Post by jakelaptop on 2007-07-17
any idea how I can get synaptic to give me an error message readout? It's probably going to be identical to that one in terminal, but it'd be nice to check.

---

### Post by Malibu Illusion on 2007-07-17
Try the commands Koybe posted several posts ago.

If they don't work, post what's in your /etc/apt/sources.list

---

### Post by jakelaptop on 2007-07-17
> **Koybe said:**
> You can try in a terminal :

```
sudo apt-get update
sudo apt-get upgrade
```

And then post the result here.

If there is broken or remaining package you can try :
```
sudo apt-get -f install
```




Here are the results: 


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

jwertz@jwertz-laptop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done

jwertz@jwertz-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Koybe on 2007-07-17
And then what if you retry supertux for now?

If it didn't work, you should check your source.list as Malibu Illusion told you. So post it here someone can help you.

I'm off for a while.

---

### Post by jakelaptop on 2007-07-17
same error code as before. 

dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by meierfra on 2007-07-17
Did you try the solution I posted in your other thread? It should work.

---

### Post by Malibu Illusion on 2007-07-17
Okay, try this:

```
sudo dselect update
```

Then try. =)

---

### Post by jakelaptop on 2007-07-17
Fixed! All better. I don't know how you wizards do this magic, but I sure am excited to begin the long road of learning. 
On a side note, this was really my first experience using web forums to learn how to do anything (other than be an obnoxcious ******* on fark) and I must say I am absolutely amazed by how helpful and nice you all are. Thanks for your time.

---

### Post by Malibu Illusion on 2007-07-17
No problem.

Take care.

---

