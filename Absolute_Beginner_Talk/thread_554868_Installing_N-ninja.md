---
title: "Installing N-ninja"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by xangelo on 2007-09-19
I've always liked the game N-ninja released by [Metanet ]("http://www.harveycartel.org/metanet/downloads.html") and I found out that they had a linux release. The game is a flash game. 

I am unsure of how exactly to go about installing it as it didn't come in a .deb file and was instead a .tar.gz file. I tried 

sudo make install

Which failed and threw back: make: *** No rule to make target `install'.  Stop.

If anyone could help, it would be greatly appreciated, thanks, 
Angelo

---

### Post by Maestro23 on 2007-09-19
> **xangelo said:**
> I've always liked the game N-ninja released by [Metanet ]("http://www.harveycartel.org/metanet/downloads.html") and I found out that they had a linux release. The game is a flash game. 

I am unsure of how exactly to go about installing it as it didn't come in a .deb file and was instead a .tar.gz file. I tried 

sudo make install

Which failed and threw back: make: *** No rule to make target `install'.  Stop.

If anyone could help, it would be greatly appreciated, thanks, 
Angelo

Compiling programs from Source: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Handling_.22.tar.gz.22_.28Tar.2FGZip.29_Archives](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Handling_.22.tar.gz.22_.28Tar.2FGZip.29_Archives)

*You may have to install additional software if the game runs into any dependency issues.  It should come with a README or Config file contianing what it is needed.

Good luck.

---

### Post by mysticmatrix on 2007-09-19
This file is a binary file, much like an .exe on Windows. 
Ok, extract the files from the compressed archive by right clicking it and choosing extract here.
Open the extracted folrder. You'll find a file called n_v14. Right click on it and under permissions tab, make it executable, if it isn't already.
Now open terminal and navigate to required directory. If you don't know how to do that, this should help you. [https://help.ubuntu.com/7.04/basic-commands/C/ar01s03.html](https://help.ubuntu.com/7.04/basic-commands/C/ar01s03.html)
Basically you'll have to use

```
cd /home/<username>/<where ever your file is>
```

Then use this command

```
nice -n 20 ./n_v14
```

Other way would be to directly double click n_v14 file. This might also work.

PS: This is binary/non-free software. Please read README.txt supplied with such softwares. They usually mention how to run required app.(Atleast this one did)

---

### Post by fuzymonkey on 2008-03-13
I think this thread might be a little old, but I found that running the windows .exe of N Ninja in Wine works better than the linux download for some reson...

---

