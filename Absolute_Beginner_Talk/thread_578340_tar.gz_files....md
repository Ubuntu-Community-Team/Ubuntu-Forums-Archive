---
title: "tar.gz files..."
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Officer Dibble on 2007-10-17
There  was a thread discussing this recently and I lost it completely because the flow of these forums move so rapidly! :)

Maybe those discussion headers on the home screen should have a reference to the forum from which the question was from, but that's another discussion.

I know I have 100+ beans and I should probably know by now, and I am really embarrassed at not knowing how to do this yet, but I really truthfully can't work out how to install a file with the extension 'tar.gz'... it's really irritating me that I can't find anything on this.

Basically, I've downloaded Seamonkey as I am not 100% happy with Firefox in Ubuntu and have heard that Seamonkey is better... but it has downloaded with that dang tar.gz stuff at the end of it... I though I was doing pretty well at avoiding all that stuff too... well it's finally come to the crunch and I have to do it.

Please help, how do I install a tar.gz file? :oops:

---

### Post by rjmdomingo2003 on 2007-10-17
[FONT="Trebuchet MS"][/FONT]Here: [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by hyper_ch on 2007-10-17
before you can compile the program, you need to get the tools for compilation:

```

sudo apt-get install build-essential

```

---

### Post by logos34 on 2007-10-17
The exact instructions are here:

[http://www.mozilla.org/projects/seamonkey/releases/seamonkey1.1.4/installation.html#linux_install](http://www.mozilla.org/projects/seamonkey/releases/seamonkey1.1.4/installation.html#linux_install)

If you downloaded the **Full Installer (14 MB)** use this:
--> Installation with the SeaMonkey Installer 

Or 
     
**tar.gz format (15 MB)**:
--> Manual Installation With the tar.gz Archive

---

### Post by FredB on 2007-10-17
> **Officer Dibble said:**
> There  was a thread discussing this recently and I lost it completely because the flow of these forums move so rapidly! :)

Maybe those discussion headers on the home screen should have a reference to the forum from which the question was from, but that's another discussion.

I know I have 100+ beans and I should probably know by now, and I am really embarrassed at not knowing how to do this yet, but I really truthfully can't work out how to install a file with the extension 'tar.gz'... it's really irritating me that I can't find anything on this.

Basically, I've downloaded Seamonkey as I am not 100% happy with Firefox in Ubuntu and have heard that Seamonkey is better... but it has downloaded with that dang tar.gz stuff at the end of it... I though I was doing pretty well at avoiding all that stuff too... well it's finally come to the crunch and I have to do it.

Please help, how do I install a tar.gz file? :oops:


I think there is a SeaMonkey version available from repositories.

At least, on gutsy, it is IceApe, the "trademark" free version.

You can grab IceApe 1.1.1 on getdeb.net :

[http://www.getdeb.net/app.php?name=Iceape](http://www.getdeb.net/app.php?name=Iceape)

To unpack a tar.gz file ? In nautilus, right-click on it, then extract.

In a console : tar xvfz name-of-file.tar.gz

---

### Post by FredB on 2007-10-17
> **hyper_ch said:**
> before you can compile the program, you need to get the tools for compilation:

```

sudo apt-get install build-essential

```

I don't think the original poster grabbed the source code. Because it means : having a development environment, and it is not really easy for beginners to setup.

---

### Post by hyper_ch on 2007-10-17
I dunno what he fetched... a .tar.gz is most often the source ;) and also poser #2 referred to compiling.

---

### Post by FredB on 2007-10-17
> **hyper_ch said:**
> I dunno what he fetched... a .tar.gz is most often the source ;) and also poser #2 referred to compiling.

The code I grabbed from cvs.mozilla.org is under a tar.bz2.

And you can find binaries in a tar.gz format. So... :-\"

---

### Post by hyper_ch on 2007-10-17
that's what I expressed with "most often" ;)

---

### Post by Officer Dibble on 2007-10-17
I was told that Seamonkey is better than Firefox in Ubuntu, so I went to their website and downloaded it...

[http://www.mozilla.org/projects/seamonkey/releases/](http://www.mozilla.org/projects/seamonkey/releases/)

Was there an easier way of doing this? :confused:

---

### Post by FredB on 2007-10-17
No. Until you install Gutsy and IceApe - same code but different branding.

Better ? Same rendering engine. More complete, that's sure !

---

### Post by jayaramk on 2007-10-17
firstly install the essentials required...

sudo apt-get install build-essential


and then extract the tar.gz file and navigate to that location.......
then type 

./configure
make
sudo make install

and thats it the downlaoded source code will be complied and installed!!!

---

### Post by FredB on 2007-10-17
> **jayaramk said:**
> firstly install the essentials required...

sudo apt-get install build-essential

and then extract the tar.gz file and navigate to that location.......
then type 

./configure
make
sudo make install

and thats it the downlaoded source code will be complied and installed!!!

And it WON'T work. You need a config file named .mozconfig, some dependancies - like gtk2.0-dev, liborbit-dev for example.

For your Information, I build my own firefox / thunderbird / seamonkey since beginning of 2002...

---

### Post by Orbital75 on 2007-10-17
Hey guys I'm a newbie with a pretty good size post count as well and from direct
experience not all .tar.gz or .tar.bz are source you have to compile. 
A lot of them you just have to uncompress by right clicking and choosing extract
and then installing them with either the debian package installer ( if it's a Deb file )
or just choosing them with the Theme manager ( If it's a Theme ).
Some files are even .sh files and you just run them by command line.

If you could just post what you downloaded and someone will help you out.
We just don't know what you downloaded.  :)

By the way, you may be talking about my post..... Here is the thread 
[http://ubuntuforums.org/showthread.php?t=577149](http://ubuntuforums.org/showthread.php?t=577149)

---

### Post by ayenack on 2007-10-17
Check out [getdeb's]("http://www.getdeb.net/browse.php") website Iceape is on there as a .deb file should be able just to download it double click it and it'll install. You'll have to register then click on Categories Internet & Network.

Good luck. ayenack.

[http://www.getdeb.net/browse.php](http://www.getdeb.net/browse.php)

---

