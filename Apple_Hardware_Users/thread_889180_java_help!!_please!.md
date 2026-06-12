---
title: "java help!! please!"
date: 2008-08-13
forum: Apple Hardware Users
---

### Post by CuteLuisa on 2008-08-13
Hey ubuntu world!!!

Hope everyone is doing good today! :)

Im having some trouble downloading java on my ubuntu laptop i tryed this code but it wont work what else can i try?



sudo apt-get install flashplugin-nonfree



i have no idea how to put that into code form so forgive me till i learn lol

---

### Post by niyonk on 2008-08-13
Hello, CuteLuisa :redface:

What that code/command does is install Adobe Flash plugin for your Firefox browser.

And what exactly do you mean by 'Code Form'??

see, [this link]("https://help.ubuntu.com/community/Java") for more info about Java

Cheers! :)

---

### Post by CuteLuisa on 2008-08-13
Ill check it out and what i mean is you know how when people but  a code command and its in a little box thing lol

Thanks
~CuteLuisa~

---

### Post by CuteLuisa on 2008-08-13
ow and i tryed that website and it did not work.
 plus i did not understand it that well lol (im not a dumb blond) im like real good on pc's but this computer is not only a mac but ubuntu i no nothing about both lol

~CuteLuisa~

---

### Post by niyonk on 2008-08-13
oh hehe, I ddnt realise this was a mac category :)

but, yeah the code u put up installs Adobe Flash, you know? for youtube videos.

The window you are talking about is probably a console window :)

You are using Ubuntu then, right?

---

### Post by CuteLuisa on 2008-08-13
Yah im on a mac laptop i just installed ubuntu like 3 days ago and i want flash i wanna watch youtube lol thats what i want to download wow i just made myself look real stupied i thought java and flash were the same thing :confused:


~CuteLuisa~

---

### Post by niyonk on 2008-08-13
Click 'Applications' on the top-left then 'Accessories' then you should find 'Terminal' 

Type in that command, enter your password and wait for it to finish ( < 10 seconds) :)

Welcome to the world of Linux :biggrin:

P.S Don't worry you ddnt know the diff between Java and Flash. Now you know, we are all learning. I am also still kind of new to this.

---

### Post by CuteLuisa on 2008-08-13
What code that one i put in my earlyer post? that onw wont work i got no idea what wrong :(

After i type that code in termial it says 


Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree

Help me Plz :(

---

### Post by niyonk on 2008-08-13
ok - :neutral:

what version of Ubuntu do you have?

try 'lsb_release -a' and tell me

or go to System->Administration->Synaptic Package Manager and search for flashplugin-nonfree

---

### Post by CuteLuisa on 2008-08-13
Description:    Ubuntu 6.06.1 LTS
Release:        6.06


LOL Thanks for helping me and not running away lol :D

~CuteLuisa~

---

### Post by niyonk on 2008-08-13
No Wonder! My system is Hardy Heron the latest, there are alot of differences.
Try and run these commands one after the other and it will install flash :)
Close firefox.

[download thi]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")s and save it in your home holder 

run the following commands:
- sudo -i
- tar zxvf install_flash_player_9_linux.tar.gz
- cd install_flash_player_9_linux/
- sudo ./flashplayer-installer
- exit


Good Luck let me know how it goes.

BTW, copy from here and paste in the Terminal using CTRL-SHIFT-V ;)

---

### Post by mkvnmtr on 2008-08-13
I think you probably have to enable the medibuntu repository to get that package. I don't remember how I did it but there will be a thread here that tells you how or someone will tell you. You know you can use a later version of Ubuntu right up to 8.04.?

---

### Post by niyonk on 2008-08-13
found something new

run 'sudo apt-get install -t dapper-backports flashplugin-nonfree'
the above will install the flash plugin without the long procedure

lol sorry for the long code :)


And next time it will be more advisable to install the latest distribution ;)

The very final solution would be 
- 'sudo gedit /etc/apt/sources.list'
- add 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main universe multiverse restricted' to the end of the text file(without quotes ofcourse) and save.
- run 'sudo apt-get update' to refresh the package repository
-you should now be able to run the code in your original post or the code at the beginning of this post

Good Luck!

---

### Post by CuteLuisa on 2008-08-13
I tryed that and it said error :( ugh man i dont know whats wrong. :( And i had no idea what to dowload my powerbook was dead so i instaled any ubuntu :(

---

### Post by niyonk on 2008-08-13
read my final solution in my previous thread.

I am getting frustrated too :(.

Take a deep breath, have a glass of milk :) and try my final solution.
It should definitely work.

Tell me for each step if you get an error. And this time make sure Synaptic package manager and firefox  are closed

---

### Post by CuteLuisa on 2008-08-13
The very final solution would be
- 'sudo gedit /etc/apt/sources.list'
- add 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main universe multiverse restricted' to the end of the text file(without quotes ofcourse) and save.
- run 'sudo apt-get update' to refresh the package repository
-you should now be able to run the code in your original post or the code at the beginning of this post

sorry but what do you mean by add 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main universe multiverse restricted'


SO Sorry but you you re frace that whole thing to noob talk? lol

---

### Post by CuteLuisa on 2008-08-13
this is what i got when i did what you said 

luisa@luisa-laptop:~$ sudo gedit /etc/apt/sources.list
Password:
luisa@luisa-laptop:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Fetched 4B in 1s (3B/s)
Reading package lists... Done
luisa@luisa-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree
luisa@luisa-laptop:~$

real long but that what i got

---

### Post by Oscar Pradilla on 2008-08-13
So easy...

1. Go to System>Administration>Software Sources
2. Third Party Software and select all
3. Updates: Select all the ubuntu updates
4. It will say to reload the repositories.  Click Yes and wait

Then
1. go to Applications 
2. Add and remove
3. Select SHOW>All the avilable applications
4. Search:  JAVA
5. Select Sun Java 6 Runtime
6. Apply
7. Restart

It's done

---

### Post by CuteLuisa on 2008-08-13
Go to System>Administration>Software Sources

I dont have sofware sources

---

### Post by Oscar Pradilla on 2008-08-14
everyone has !!

look closer.

unless your account is not administrator

---

### Post by Subetealabici on 2008-08-14
Hello 

 It's look like there is no java to see youtube videos under the PPC kernel, you can try with the gnash but as far as I now there are no java/youtube for PPC Kernel

---

### Post by starcannon on 2008-08-14
Get most of what you want with one command, flash, java, a bunch of codecs, etc...

```
sudo apt-get install ubuntu-restricted-extras
```

copy paste that in, or type it in, and you should have a bunch of goodies to make your internet life a bit more interesting.

GL and welcome to Ubuntu.

---

### Post by cyberdork33 on 2008-08-14
Everyone is giving your good information, if you weren't on a PowerPC machine... 

There is some information here:
[http://ubuntuforums.org/showthread.php?t=873484](http://ubuntuforums.org/showthread.php?t=873484)

and probably the most direct solution in in the PowerPC FAQ:
[https://wiki.ubuntu.com/PowerPCFAQ#Java](https://wiki.ubuntu.com/PowerPCFAQ#Java)

---

