---
title: "Eternal Lands Install"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by That Guy X on 2006-10-19
Hi, Im trying to install an mmorpg game called Eternal Lands but i cant figure it out:confused: These are the directions

To play on Linux:
Download the zip file, and unzip it.
cd to the directory where you installed it.
chmod to 775 and execute el.x86.linux.bin
edit el.ini and change datadir to where you unzip everything
Also, the zip file has no base directory, so you should unzip it in a new directory you create.
To play under FreeBSD, download the Linux version, download the code from the CVS, and use the freebsd make file.

lol im a noob and i have no idea what half that stuff means](*,)  Its real annoying having to switch to win-doze to play, can someone please give me some simplified instructions on what i have to do?

Thanks in advance,
                  Steve

---

### Post by Sef on 2006-10-19
Read '[How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu'.

---

### Post by maaronB on 2006-10-19
Most of the commands are fairly simple.
I am going to go install it on my machine and will give step by step what I am doing.

First thing is this:
*Also, the zip file has no base directory, so you should unzip it in a new directory you create.*
*Download the zip file, and unzip it.*
What they are saying is we need to create a new folder to put this in.
I am going to put mine in on my Desktop and call it Eternal.
So I downloaded the file.
Created a folder called Eternal.
Put the .zip that I downloaded in Eternal.
Double clicked it.
Hit Extract.
Extracted into the Eternal Folder that I had just made.

---

### Post by Lord Illidan on 2006-10-19
No, don't do that.

The preferred way of installing EL is to create a new directory under /usr/local/games/el

so.

launch a terminal, and type : ```
sudo mkdir /usr/local/games/el
```

then copy the extracted EL folder to that location.

then run ```
sudo chmod -R 777 /usr/local/games/el/*
```

EL is a nice game, man. Don't give up because you are a newbie, I once was too. We all were.

---

### Post by maaronB on 2006-10-19
ignore this do what post above stated.

---

### Post by That Guy X on 2006-10-19
ok, I did what Lord Illidan said and then what? No installer launched or anything :-k

---

### Post by That Guy X on 2006-10-19
Im useing Kubuntu, if that makes any difference?

---

### Post by maaronB on 2006-10-19
It shouldn't.  
It should now be installed on your system.  You won't see an installer, because you have basically set everything up manually.  

Just to see if everything worked cd to the folder that you created. 
and run
./el-132.x86.linux.bin

---

### Post by That Guy X on 2006-10-19
I got this =(

./el-132.x86.linux.bin: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

---

### Post by maaronB on 2006-10-19
Open Synaptic and install libopenal

You will probably have to do this a few times to get all the dependencies installed.

---

### Post by That Guy X on 2006-10-19
I still got the same error.](*,)  When I went to synaptic this came up 
libopenal0 idk if that makes a diff or not?

---

### Post by maaronB on 2006-10-19
did you install libopenal0?

---

### Post by That Guy X on 2006-10-19
yeah

---

### Post by maaronB on 2006-10-19
Ok, I have two versions available.  libopenal0 and libopenal0a.  Installed on mine is libopenal0a.  So to test I uninstalled it.  Then tried running the game.  I recieved the same error that you get.  So I installed libopenal0 and everything worked.  Then I uninstalled it and installed libopenal0a.  Everything worked.  Since there is also a libopenal-dev I installed it (it automatically installed libopenal0a) and everything worked.  

So any current version of libopenal should work.

---

### Post by maaronB on 2006-10-19
Are you sure it is giving you the exact same error. 
As in.
./el-132.x86.linux.bin: error while loading shared libraries: _**libopenal.so.0**_: cannot open shared object file: No such file or directory.  

And not a new different dependency error.

---

### Post by That Guy X on 2006-10-19
yeah its the same on all of them.

---

### Post by Dual Cortex on 2006-10-19
must... resist... urge.. to.... instal... an MMORPG!!!!

---

### Post by Mr_bleu on 2007-07-15
djr@djr-laptop:~$ cd /home/djr/el_install
djr@djr-laptop:~/el_install$ ./el.x86.linux.bin
I/O warning : failed to load external entity "/usr/local/games/el//actor_defs/actor_defs.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/strings/channels.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/strings/channels.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/books/races/human.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/books/races/human.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/books/races/dwarf.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/books/races/dwarf.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/books/races/elf.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/books/races/elf.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/books/races/gnome.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/books/races/gnome.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/books/races/orchan.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/books/races/orchan.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/books/races/draegoni.xml"
I/O warning : failed to load external entity "/usr/local/games/el//languages/en/books/races/draegoni.xml"
I/O warning : failed to load external entity "/usr/local/games/el//knowledge.xml"
I/O warning : failed to load external entity "/usr/local/games/el//knowledge.xml"
CampfireEffect (0xbea6ab8) created.
LampEffect (0xbea7728) created.
LampEffect (0xbea7ac8) created.
LampEffect (0xbea7e80) created.
FountainEffect (0xbea82a0) created.
CandleEffect (0xbea83a0) created.
CandleEffect (0xbea8458) created.
el.x86.linux.bin: model.cpp:50: CalModel::CalModel(CalCoreModel*): Assertion `pCoreModel' failed.
Aborted (core dumped)
Anyone Else?  I've installed libopenal (and some more to be sure).

---

### Post by Mr_bleu on 2007-07-15
It works.  I put el in /usr/local/games/el/ and followed the directions posted on page one:
 Re: Eternal Lands Install
No, don't do that.

The preferred way of installing EL is to create a new directory under /usr/local/games/el

so.

launch a terminal, and type :
Code:

sudo mkdir /usr/local/games/el

then copy the extracted EL folder to that location.

then run
Code:

sudo chmod -R 777 /usr/local/games/el/*

You have to download the music files and create a music folder then unzip to that folder.

---

### Post by Skneepa on 2008-01-20
Hi people...! 

I tried installing EL using a terminal, following your directions, however I cannot copy the exctracted folder to the one I created in usr/local/games/el, the system notifies me that since i'm not the owner i can't copy anything to that folder. When I was asked for my password I provided though...

Any suggestions?

I'm currently running Ubuntu Ultimate 1.6 (Ubuntu 7.10)...

Thanks in advance! :)

---

### Post by nsimeone2000 on 2008-02-23
Once you have made the folder in that directory, in order to copy or do anything to it (unless you are logged in under root) you have to use the following command:

sudo chmod -R 777 /usr/local/games/el/

The 777 there is kinda like web design permissions, it allows you to read/write/execute.


My problem is when I try to run the game I keep getting this error need to install libcal3d12, but I cannot find for my version of ubuntu in synaptics.

I cannot use wine because of my stupid AMD chipset, guess hope is lost for me to run this game, it looked promising, oh well.

---

