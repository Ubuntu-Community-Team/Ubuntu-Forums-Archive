---
title: "Setting Up Quake 1"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by yizuman on 2008-02-15
Looking through some posts and unable to find instructions on how to install Quake 1 and getting it to run.

I'm sure by now some quake players have already figured out how to get quake 1 to set up and run. So I am requesting a step by step instruction on what and where I can download files (any .deb files out there?) and how to get it running.

Any help is appreciated.

Thanks in advance,

---

### Post by Rhubarb on 2008-02-15
If you want to play Quake 1 in really nice OpenGL + good lighting effects.
Get the DarkPlaces Quake 1 engine here:
[http://icculus.org/twilight/darkplaces/download.html](http://icculus.org/twilight/darkplaces/download.html)

Download [http://icculus.org/twilight/darkplaces/files/darkplacesengine20071120.zip](http://icculus.org/twilight/darkplaces/files/darkplacesengine20071120.zip)
extract it somewhere in your home folder.
Rename the directory from darkplacesengine20071120 to something easy to remember like ~/games/quake

For nicer lighting effects on quake maps:
Download [http://icculus.org/twilight/darkplaces/files/darkplacesmod20071120.zip](http://icculus.org/twilight/darkplaces/files/darkplacesmod20071120.zip)
extract the contents to your ~/games/quake directory

Now in your ~/games/quake directory create a new directory, called id1
copy all your quake 1 pak files (from cd, or an existing installation) to ~/games/quake/id1

Open up a terminal, and type in:
```
cd ~/games/quake/
```

If you have a 32bit Ubuntu install:
```
./darkplaces-linux-686-glx
```

If you have a 64bit Ubuntu install:
```
darkplaces-linux-x86_64-glx
```

You may need extra libraries installed to play, if the game does not run, please post the output you get after executing the darkplaces binary and I'll help you out RE what libraries you need to download from the Ubuntu repositories.

---

### Post by finer recliner on 2008-02-15
well idk about quake 1, but for quake 3:

```
 sudo apt-get install openarena
```

---

### Post by vvlist on 2008-03-06
Hi, I'm running 7.10 64bit. I installed all the files from the links above, plus I added the pak files in ~/quake/ID1/.  But I get this error:
> /home/vvlist/quake/darkplaces-linux-686-glx: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory

after running the following command:
> /home/vvlist/quake/darkplaces-linux-686-glx

I tried the tenebrae port on this computer, and works but I'm really trying to find a port that will run on a much slower computer, my Eee Pc which runs a 32bit 7.10 install. Tenebrae ran at about 0.25 fps on the Eee. I have 3d acceleration running just fine on the Eee, and it runs open arena beautifully, but I miss Quake 1. Can you help a guy play one of his old favorites? I'm guessing I have to install a package or link a file to a path?

Edit: After reading [this]("http://ubuntuforums.org/showthread.php?t=610173&highlight=libXxf86dga&page=3") I issued a:
> apt-file search libXxf86dga.so.1

And it returned
> 
libxxf86dga1: usr/lib/libXxf86dga.so.1
libxxf86dga1: usr/lib/libXxf86dga.so.1
libxxf86dga1: usr/lib/libXxf86dga.so.1
libxxf86dga1: usr/lib/libXxf86dga.so.1.0.0
libxxf86dga1: usr/lib/libXxf86dga.so.1.0.0
libxxf86dga1: usr/lib/libXxf86dga.so.1.0.0
libxxf86dga1-dbg: usr/lib/debug/usr/lib/libXxf86dga.so.1.0.0
libxxf86dga1-dbg: usr/lib/debug/usr/lib/libXxf86dga.so.1.0.0
libxxf86dga1-dbg: usr/lib/debug/usr/lib/libXxf86dga.so.1.0.0

So the file does exist on my system, the problem is that DarkPlaces doesn't know where to look. I've looked through some of the files in the quake folder, and can't find where I would change that path. Any ideas?
Edit: Okay, I got it to work. I copied what I had on my 64bit desktop to my Eee. I tried to run it as is. I got an error saying the id1 folder could not be found. It was in the ~/quake/ folder. Then I moved it up one directory, so  the quake and the id1 folders were in the same directory and it worked. Hope that helps someone out. I think the error I had before on my other machine was due it being 64bit. Have fun playing Quake on Ubuntu!

---

