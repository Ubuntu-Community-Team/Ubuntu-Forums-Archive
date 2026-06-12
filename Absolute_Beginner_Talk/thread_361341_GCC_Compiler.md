---
title: "GCC Compiler"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by 42Wired on 2007-02-14
I just installed Dapper two days ago, and have no Linux knowledge whatsoever. I downloaded a driver for my printer, which apparently needs to be compiled in a C compiler.

I downloaded gcc-4.1.2.tar.bz2 from [here]("http://gcc.gnu.org/mirrors.html") (St. Louis mirror site), and now I have all these files I don't know what to do with.

I read the README and FAQ files, but they assume that I have basic knowledge of my OS.

After much Googling, I turned here. Can someone who knows what they're doing please help me?

---

### Post by taurus on 2007-02-14
```
sudo aptitude update
sudo aptitude install build-essential
```
That would install gcc and a bunch of other files that you need to build something from source.

---

### Post by maxamillion on 2007-02-14
```
sudo aptitude install build-essentials
```

that command in the Terminal will (probably) install everything you need to compile.

[http://packages.ubuntu.com](http://packages.ubuntu.com) <---check there before downloading things, 90% of the time if there is a program/compiler/etc that you need for linux, its in the repositories. (thanks to the hard work of the debian/ubuntu team(s))

EDIT: Taurus beat me to it :P

---

### Post by taurus on 2007-02-14
> **maxamillion said:**
> ```
sudo aptitude install build-essentials
```


By the way, it's **build-essential** with no s at the end.

---

### Post by maxamillion on 2007-02-14
> **taurus said:**
> By the way, it's **build-essential** with no s at the end.

ah ... so it is ... :( my bad.

---

### Post by TheApe on 2007-02-14
I have a point about it.
If it's "essential" why doesn't it come with system by default?

I know that we should manage software with APT, but not all of them are in the repositories.

---

### Post by Perfect Storm on 2007-02-14
I does come by default (on the CD), but not install by default.

---

### Post by TheApe on 2007-02-14
>  I does come by default (on the CD), but not install by default.

Sorry. I meant to say that, why doesn't comes installed by default.
Well, off topic... :)

---

### Post by Perfect Storm on 2007-02-14
Well, newbies shouldn't have to compile their own stuff in Ubuntu but rely on the apt or other easy to get. It's very few newbies that need/require to compile their own stuff, most can be found if you enable univrse/multiverse in your sourcelist, other than that it's possible to find .deb or private sourcelist on the web (but not recommendable if you don't trust the source). For each time Ubuntu gets released (newer version), more and more software and libs can be found in the apt. So it's actually very very few things you can't find there. And if you need to compile you can get the tools very easely.

No reason to bloat the distro more than needed ;)

---

### Post by 42Wired on 2007-02-14
Thanks to both of you.

To use GCC, do I just type the commands into the console, or do I need to start up GCC somehow first?


Code:

sudo aptitude update
sudo aptitude install build-essential

Also, what does the above code mean? Is it specific to what I just did, or do these commands have other uses (though install and update are pretty self-explanatory)?

---

### Post by Perfect Storm on 2007-02-14
sudo = superuser do (when you want to mess with root)
aptitude = is an installer application like apt-get
update and install tells aptitude what to do in this case update updates the sourcelist and install build-essential to install yes build-essential

---

### Post by bodhi.zazen on 2007-02-14
What are you trying to install ?

FYI the Ubuntu repositories are quite large and you may just need to enable a few repositories.

For further information on installing see here:

[http://ubuntuforums.org/showthread.php?t=298818](http://ubuntuforums.org/showthread.php?t=298818)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by 42Wired on 2007-02-14
> **bodhi.zazen said:**
> What are you trying to install ?

FYI the Ubuntu repositories are quite large and you may just need to enable a few repositories.

For further information on installing see here:

[http://ubuntuforums.org/showthread.php?t=298818](http://ubuntuforums.org/showthread.php?t=298818)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)


I'm trying to install drivers for my Canon Pixma MP500, and now trying to update Firefox to v2.0.0.1.

The printer is more important at this point, though.

Thanks for the URLs, too.

---

### Post by bodhi.zazen on 2007-02-14
Not sure about the printer, again check the Ubuntu repos :P

For Firefox : [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by Unlockitall on 2007-02-14
i want to learn python, so would this give me the programs needed, also when i did this it said it would use up over 30 gigs, and i dont really have that kind of space, so is there a partial form of this installer just for python?

---

### Post by 42Wired on 2007-02-14
> **bodhi.zazen said:**
> Not sure about the printer, again check the Ubuntu repos :P

For Firefox : [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

The code works fine as far as I can tell, but I can't see all the choices when it prompts me to choose a localization. Is there any way to pause the output of the program, scroll past the top of the screen, save that output to a file, etc.?

---

### Post by 42Wired on 2007-02-14
OK, I found it in Google (choice 8 for en-US).

But I would still like to know for future reference. Thank you everyone for all your help.

---

### Post by bodhi.zazen on 2007-02-14
You can re-direct the output of a command to a file by re directing it, like this :

command > file_name

You can then look at the output with any editor or less :

less file_name

HTH

---

### Post by edgy_pranay on 2007-03-31
hi peeps
im new to ubuntu.i need gcc compiler for my work.i hav typed d following 2 lines nd it downloaded some files

it downloaded files related to gcc

sudo aptitude update
sudo aptitude install build-essential

but how do i install d compiler

---

### Post by windofkeltia on 2007-04-18
Once you've done the installation, as guided by all the replies above, you should see where gcc is by typing:

# which gcc

If you see nothing, get root and go look for it, but it should be on /usr/bin/gcc and so you should modify your PATH environment variable to include /usr/bin. Do this thus:

# echo $PATH

If you don't see /usr/bin already there, then add it:

# PATH=$PATH:/usr/bin

At this point, your configure, make, etc. will find gcc and use it. If you have trouble beyond this point, then you probably need some tutorial sort of help and there isn't the bandwidth to give that to you within this forum unless you can ask specific questions.

Good luck.

---

