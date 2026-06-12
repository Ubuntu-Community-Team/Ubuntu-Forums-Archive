---
title: "plug-in download"
date: 2005-05-29
forum: Absolute Beginner Talk
---

### Post by benevolent on 2005-05-29
Can i download plug-ins for the mp3player & for the movie player from a non ubuntu system and installing them afterwards???i have a problem with my modem...and if so, how can i install them...

thx-again-dmitris

---

### Post by SGC on 2005-05-29
Search and download the programs that you like from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) or any site that offers a debian packages and then use the following command to install them:
dpkg -i PACKAGE_NAME.deb

---

### Post by The Na Kun on 2005-05-29
[QUOTE=benevolent]Can i download plug-ins for the mp3player & for the movie player from a non ubuntu system and installing them afterwards???i have a problem with my modem...and if so, how can i install them...

thx-again-dmitris[/QUOTE]
 Yeah, you can download the files from another OS then write them to a cd or floppy then throw it in and take the files out on to the ubuntu system then install them (I do this since I can't use aol on linux).  There is usually a README file, just...Read it and it will tell you how to install, but with most you just extract it and do this-
cd [insert path to file's directory]
./configure
make

Well, from what I know and I just set up ubuntu yesterday, so might not be totally correct..  If it is a .deb then you do like-
dpkg -i [insert path to the file..thing]

But really, there isn't alot I can do since I don't have internet and can't set up a modem...

---

### Post by jobezone on 2005-05-29
You forgot one last step when compiling a program from source. The way to install the app system-wide (so that all users can run it):

```

tar zxvf <name-of-compressed-file.gz>
cd <directory-where-files-where-placed> 
./configure
make
make install

```

If you don't run "make install", you can still run the program, because it was compiled when you ran "make". The executable file to run will either be in the root directory, or inside a subdirectory called "bin". To execute this executable file, which will run the program you just compile, you do:
> 
./<name of executable>


It is a lot easier to install applications which come in .deb packages format:
> 
dpkg -i package.deb


But watch out though, because manually installing .deb packages like this, won't automatically download from the net it's dependencies! This won't break your system:) , you just might not be able to install the debian package (that's what .deb files are called) because it needs another packages to be already installed in your system.

So, any missing dependency it spells out, you get from packages.ubuntu.com, and install these packages first.

If you add a conection to the net, you could use either Synaptic (Package Manager), or the apt-get comand line tool, to do all of this automatically. For example, to install Mplayer in a pentium II, you could do in a command line:
> 
sudo apt-get install mplayer-686


and it would download the mplayer package, all of it's dependencies, and install them all!

Checkout [http://www.ubuntuguide.org](http://www.ubuntuguide.org) for a sort of "cookbook" for Ubuntu.

---

### Post by benevolent on 2005-05-31
thankyou! and do you know any website where i can download the ubuntu plugins from a windows (oust from here) system?

---

### Post by poofyhairguy on 2005-05-31
[QUOTE=benevolent]thankyou! and do you know any website where i can download the ubuntu plugins from a windows (oust from here) system?[/QUOTE]

[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

---

### Post by jobezone on 2005-05-31
[QUOTE=benevolent]thankyou! and do you know any website where i can download the ubuntu plugins from a windows (oust from here) system?[/QUOTE]
 You can get any package in any ubuntu Release from packages.ubuntu.com , and extra packages from the Backports repository at [http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php) .

If you mean plugins as in multimedia codecs, like mp3, wmv, etc. these are the instructions needed as told in [www.ubuntuguide.org](www.ubuntuguide.org) :
```

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install w32codecs
gst-register-0.8

```
Take note that instead of "sudo apt-get install gstreamer0.8-plugins" you will have to run "sudo dpkg -i <name of package.deb>" , and gst-register-0.8 is a command you'll have to run at the end, so that gstreamer registers the new codecs.

You probably also will want another videoplayer, and it's a package called "xine" or "xine-ui" that you should get.

---

### Post by poofyhairguy on 2005-05-31
[QUOTE=jobezone]
You probably also will want another videoplayer, and it's a package called "xine" or "xine-ui" that you should get.[/QUOTE]

I think that its better to advise Gxine -the xine for gnome.

---

