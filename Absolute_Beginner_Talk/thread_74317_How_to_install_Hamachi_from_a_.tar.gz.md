---
title: "How to install Hamachi from a .tar.gz?"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by kane77 on 2005-10-11
How do I install program I've downloaded??? (for example hamachi)
I downloaded the hamachi...tar.gz when I open it I just see bunch of files how do I install it... (don't laugh at me I'm n00b :confused: ) What programs should I download For what version of Linux (when there isn't ubuntu? (Will programs for other distros work in Ubuntu??

---

### Post by hatatitla on 2005-10-11
Ubuntu uses debian packages, so try to find a *.deb file with program you wish. Then you can install the program by running this command in console:
```
dpkg -i name_of_file.deb
```

---

### Post by Ampersand on 2005-10-11
First, make sure it isn't available in the apt repositories. If you haven't done so, enable the universe and multiverse ([http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)), then search for it using Synaptic (in the System menu, under Administration).

If it's not there, and there isn't a .deb available from the site, you'll probably have to compile the program. 

Firstly, you'll have to install a compiler. To do this, open a terminal and run 

```
sudo apt-get install build-essential
```.

Afterwards, change directory to the folder created when you extracted the tar.gz ('cd hamachi' or whatever the folder is called) and run the following commands:

```

./configure
make
sudo make install

```

---

### Post by Gustav on 2005-10-12
to extract the tar.gz file do

tar xfvz thefile.tar.gz

---

### Post by patrick295767 on 2005-10-12
[QUOTE=Gustav]to extract the tar.gz file do

tar xfvz thefile.tar.gz[/QUOTE]

For newbies (like me too), mc 
can sometimes be useful to unpack files... 

Courage !!

(btw, nfo, [http://www.ubuntuforums.org/showthread.php?t=64557](http://www.ubuntuforums.org/showthread.php?t=64557) )

---

### Post by Wolki on 2005-10-12
You can also extract .tar.gz from nautilus, of course.

[QUOTE=Ampersand]
```

./configure
make
sudo make install

```[/QUOTE]

This is the basic way of installing things from source. You can install checkinstall ("sudo apt-get install checkinstall", or do it with synaptic) and then replace the last command ("sudo make install") with "sudo checkinstall". It will then create a package so that you have an easy way of uninstalling the software. Close synaptic, if you have it open, before doing that.

Also, you mught have to get special libraries required by the program you want to install. If that happens, tells us and we'll walk you through it.

---

### Post by Nasso on 2005-10-12
the best way to unpack archives it to install a program called unp. you can find it using synaptic.
Open up a terminal and type
unp file.tar.gz
or 
unp file.zip
or
unp file.rar
or 
unp *

or what ever file you want to unpack :) most of the times unp can figure out what typ of compression it is and then unpack it using the corrent program and flags.

peace out

---

### Post by karuptdata on 2005-10-12
If all else fails or you quit cant understand the mentioned procedures one thing you may want to try is Alien. in a terminal type sudo apt-get alien after alien has installed cd to directory where file resides for example cd home/user/desktop then type in this command sudo alien -d whateverfilename.tar.gz. Alien will then create a .deb file once that file is created type in dpkg -i whateverfilename.deb and it will install for you! Hope this helps! :)

---

### Post by ShagzModo on 2005-11-21
[QUOTE=kane77]How do I install program I've downloaded??? (for example hamachi)
I downloaded the hamachi...tar.gz when I open it I just see bunch of files how do I install it... (don't laugh at me I'm n00b :confused: ) What programs should I download For what version of Linux (when there isn't ubuntu? (Will programs for other distros work in Ubuntu??[/QUOTE]


question:
did you get Hamachi to work properly?
Please let me know how you got it to work, and if it funtions properly.
I am struggling to get thing working over here.

rgds.
ShagzModo

---

### Post by dspp on 2005-12-16
[QUOTE=ShagzModo]question:
did you get Hamachi to work properly?
Please let me know how you got it to work, and if it funtions properly.
I am struggling to get thing working over here.
[/QUOTE]

You ever get Hamachi running? Works fine here - listening to mp3s stored on a Windows box. Neat program.

---

### Post by mrdude1228 on 2005-12-18
I'm also a newbie at Ubuntu (and Linux in general), and I'm trying to install a tar.gz file. I've managed to get pretty far with a tutorial I found on Google ([http://video.google.com/videoplay?docid=5253052326994067125)](http://video.google.com/videoplay?docid=5253052326994067125)), and I've gotten everything to work so far, up until I get to where you're supposed use "./configure". Whenever I try to, I get the following response:

bash: ./configure: No such file or directory

I have the unzipped folder on my desktop, and I'm in the unzipped folder (my prompt is mrdude@ubuntu:~/Desktop/2Pong-0.6$). Is there something I'm missing?

Oh, and my Ubuntu computer isn't connected to the internet, if that matters.

---

### Post by Hypatia2 on 2005-12-19
I'm an Ubuntu newbie, but have been working with Unix for a looong time. I just came across Hamachi myself. When you download a file ening in '.tar.gz' or '.tgz', use the command:
'tar xvf Filename'. That extracts the file to a new directory (if the tar was built correctly). cd to that directory.
Look for a file called 'README' or 'INSTALL'. Read the instructions there.

---

### Post by mrdude1228 on 2005-12-19
The README says (at the bottom, past the details about the game itself):

The game is written in C, utilizing the SDL library. Use 'make' to compile it. The binary is distributed with the package. Use 'make install' to install it. It is installed to /usr/local/bin by default. This can be changed in the Makefile.

---

### Post by MicroChris on 2005-12-20
To install Hamachi:

-Download hamachi-0.9.9.9-7.tar.gz [(link)]("http://files.hamachi.cc/linux/hamachi-0.9.9.9-7.tar.gz")

-Extract the folder to your Desktop

```
cd home/$USER$/Desktop/hamachi-0.9.9.9-7
```

Then:

```
install -m 755 hamachi /usr/bin
```

```
ln -sf /usr/bin/hamachi /usr/bin/hamachi-init
```

```
install -s -m 700 tuncfg/tuncfg /sbin
```

After that, try running(root):

```
tuncfg
```

Then:

```
hamachi-init
```

Try some commands which are supplied in the README. I still have not figured out a way to actually access users, but I can install it.

-Chris

EDIT: I will post this as a HOWTO

---

### Post by shof2k on 2006-01-07
To add to MicroChris....

```
hamachi-start
``` will start the hamachi daemon

```
hamachi-login
``` will create your account and allocate your unique 5.* hamachi ip address.  Make a note of this for the future.

```
hamachi create <network name> 
``` will set up a new network. You will need a strong password here.

```
hamachi join/leave <network name> 
``` will connect/disconnect you to/from a network, so long as you know it's password.

```
hamachi list 
``` lists all the members attached to a network

The full command list is in the README document in the source :)

There is also a beta-level gui for hamachi at [http://forums.hamachi.cc/viewtopic.php?t=2488](http://forums.hamachi.cc/viewtopic.php?t=2488).  It still needs work but perhaps it could be developed further (in a similar way to smeg?)

Hope this helps,

---

