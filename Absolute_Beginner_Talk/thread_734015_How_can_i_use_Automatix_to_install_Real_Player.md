---
title: "How can i use Automatix to install Real Player?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by quddusaliquddus on 2008-03-24
Hi all :),
             I read somewhere on this forum that I can use Automatix to install Real Player easily. I've installed Autiomatix successfully but I dont know what to do next to install Real Player.

Any suggestions?

Thanks :D

Regards

Q

---

### Post by jan quark on 2008-03-24
**I would strongly encourage you to remove automatix from your system**

it is known to cause severe compatibility issues

you can install realplayer without it 
why install a applications which installs applications ?

download the player from here
[http://www.real.com/linux](http://www.real.com/linux)

make the file executable with

```
sudo chmod a+x /path/to/downloaded/file
```

and run the installer with
```
/path/to/installer.bin
```

---

### Post by quddusaliquddus on 2008-03-24
thanks for the info. How would i uninstall automatix? And also - the bin file is on my desktop - what wouldthe path to the desktop be?

Im sorry about all these questions - im not used to using the command line.

---

### Post by jan quark on 2008-03-24
wow now I am  little confused I posted again your answer into the other thread :)

how did you install automatix?

---

### Post by quddusaliquddus on 2008-03-24
I cant remember how i installed it sorry - all i can remember is that i used a deb file.

---

### Post by Ub1476 on 2008-03-24
Just move the file to your home directory and open the terminal.

To change directories, use the cd command.

```
cd Desktop
```

If you installed it via a .deb file, Synaptic should have picked it up. To uninstall with terminal write:

```
sudo apt-get remove automatix
#or
sudo apt-get remove automatix2
```

---

### Post by quddusaliquddus on 2008-03-24
ill stick to this thread for further discussion.

---

### Post by jan quark on 2008-03-24
try this code in terminal to remove automatix
```
sudo dpkg -r automatix
```

how is the real player installation going?

---

### Post by quddusaliquddus on 2008-03-24
Im typing:
```

sudo chmod a+x home/myusername/Desktop/RealPlayer11GOLD.exe

```

but it says:

```

chmod: cannot access `home/mysername/Desktop/RealPlayer11GOLD.exe': No such file or directory

```

---

### Post by quddusaliquddus on 2008-03-24
it doesnt uninstall automatix as it says that it is nt installed - BUT - I can run automatix from Application->System Tools->Automatix

---

### Post by quddusaliquddus on 2008-03-24
BTW - thanks for all the help youre providing. I may not have to install RealPlayer if I could find another media player that downloads youtube videos directly from the web browser. Thats the reason i want to install it.

---

### Post by jan quark on 2008-03-24
1. is your username really "myusername" ? when you go to places > home in which directory are you now?

2.perhaps you can search for automatix via the synaptic package manager. go to system > administration > synaptic package manger
and type automatix into the search field 
if you find something check the box next to the entry and select mark for complete removal and click on apply

---

### Post by jan quark on 2008-03-24
never used this before but will try this now
it seems a very cool method to download the videos from youtube

[http://www.go2linux.org/wget-to-download-youtube-videos](http://www.go2linux.org/wget-to-download-youtube-videos)

---

### Post by quddusaliquddus on 2008-03-24
lol. no my username isnt myusername. my username is 'rashid' which shows up when i goto places->home.

Whey! synaptic package manager.managed to remove it!

---

### Post by quddusaliquddus on 2008-03-24
its a bit long-winded and with having to do a lot of typing.

---

### Post by jan quark on 2008-03-24
yea and it does not work for me
giving me some weird error
> Resolving [www.youtube.com](www.youtube.com)... 208.65.153.253, 208.65.153.238, 208.65.153.251
Connecting to www.youtube.com|208.65.153.253|:80... connected.
HTTP request sent, awaiting response... 410 Gone
18:48:56 ERROR 410: Gone.

trying something other now
[https://addons.mozilla.org/en-US/firefox/addon/220](https://addons.mozilla.org/en-US/firefox/addon/220)

this firefox extension should download the youtube vids

---

### Post by jan quark on 2008-03-24
well then run
```

sudo chmod a+x home/rashid/Desktop/RealPlayer11GOLD.bin
```
and then
```

/home/rashid/Desktop/RealPlayer11GOLD.bin
```

and of course you need the bin file not the exe file
[http://www.real.com/linux](http://www.real.com/linux)

---

### Post by quddusaliquddus on 2008-03-24
ok. i installed flashgot but when i got to youtube to view a video it said i havnt got the flash plugin. so i followed the link and got my self a tar.gz version of the flash player. the tar.gz file contains the following files:

flashplayer-installer

and 

libflashplayer.so

How would i got about installing this plugin?

---

### Post by jan quark on 2008-03-24
see my small guide on this

[http://ubuntuhelp.piranho.de/tutorial3.html](http://ubuntuhelp.piranho.de/tutorial3.html)

---

### Post by jan quark on 2008-03-24
I hope you come along just fine

have to go offline now 

play some jazz...

---

### Post by quddusaliquddus on 2008-03-24
ive installed flash. Now im gonna experiment with flash got and see if its what im looking for. I'll post back again if i see it doesnt do wht i want to do and i want to install real player.

Thank You So much for All your help!

Regards

Q

---

