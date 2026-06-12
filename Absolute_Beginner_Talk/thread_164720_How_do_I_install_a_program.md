---
title: "How do I install a program?"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Tanchistu on 2006-04-23
How do I install a program that is not in the list of Automatix? Can I install .rpm packages? For example I want to install this program [http://www.beryllium.net/~remco/linabx/](http://www.beryllium.net/~remco/linabx/) what are the steps that I have to follow?

---

### Post by derjames on 2006-04-23
to install RPM packages use the ALIEN command to convert the file to .deb... then use dpkg as usual...

cheers

---

### Post by mostwanted on 2006-04-23
[QUOTE=derjames]to install RPM packages use the ALIEN command to convert the file to .deb... then use dpkg as usual...

cheers[/QUOTE]

Why make it two-step?

you can install with alien.

```
alien -i /path/to/package.rpm
```

But normally when you install software in Ubuntu you do so from the Ubuntu repositories. Open System &#8594; Administration &#8594; Synaptic.

---

### Post by user1397 on 2006-04-23
A .rpm file is the type of packaging system that redhat and fedora linux use. You could use the rpm package maybe, but you would need to install alien from synaptic and some other stuff. Ubuntu/Debian users can use .deb, .tar, and a couple others i think. 
So instead of the rpm file, download [linabx-1.99.6.tar.gz]("http://beryllium.net/%7Eremco/linabx/linabx-1.99.6.tar.gz").  First extract it to somewhere, (i'll use the desktop for the example).  Then open a terminal Applications->Accesories->Terminal, and type in ```
cd Desktop/[linabx-1.99.6.tar.gz]("http://beryllium.net/%7Eremco/linabx/linabx-1.99.6.tar.gz")
```
Then ```
./configure
```
If you get an error try ```
sudo ./configure
```
Then ```
make
```
Then ```
sudo make install
```
That should do it.
[]("http://beryllium.net/%7Eremco/linabx/linabx-1.99.6.tar.gz")

---

### Post by dermotti on 2006-04-23
or type **gksudo synaptic**

---

### Post by Tanchistu on 2006-04-23
The program that I want to install is not in Synaptic, and I have to choose from     *   linabx-1.99.6.tar.gz and * linabx-1.99.6-1.i386.rpm.

Alien dosen't work, I searched for it in synaptic and didn't found it.

---

### Post by Tanchistu on 2006-04-23
[QUOTE=erik1397]A .rpm file is the type of packaging system that redhat and fedora linux use. You could use the rpm package maybe, but you would need to install alien from synaptic and some other stuff. Ubuntu/Debian users can use .deb, .tar, and a couple others i think. 
So instead of the rpm file, download [linabx-1.99.6.tar.gz]("http://beryllium.net/%7Eremco/linabx/linabx-1.99.6.tar.gz").  First extract it to somewhere, (i'll use the desktop for the example).  Then open a terminal Applications->Accesories->Terminal, and type in [/QUOTE]

after ./configure I get this:

configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

---

### Post by kh4nh on 2006-04-23
[QUOTE=Tanchistu]The program that I want to install is not in Synaptic, and I have to choose from     *   linabx-1.99.6.tar.gz and * linabx-1.99.6-1.i386.rpm.
[/QUOTE]

Choose and download linabx-199.6.tar.gz

Open Terminal and type these commands in with the order as they appear: 
           0- sudo apt-get install build-essential
           1- cd Desktop
           2- tar xzvf linabx-199.6.tar.gz
           3- cd linabx-199.6
           4- ./configure
           5- make
           6- make install
           7- make clean

Good luck

---

### Post by mostwanted on 2006-04-23
[QUOTE=kh4nh]Choose and download linabx-199.6.tar.gz

Open Terminal and type these commands in with the order as they appear: 
           0- sudo apt-get install build-essential
           1- cd Desktop
           2- tar xzvf linabx-199.6.tar.gz
           3- cd linabx-199.6
           4- ./configure
           5- make
           6- make install
           7- make clean

Good luck[/QUOTE]

Step 6 should be *sudo make install* and step 5 can usually be skipped as compilation happens automatically for the install target in any well-written makefile.

Also note that sometimes there's no script called configure, so if it complains there's no configure script, just skip that step. Configure is normally used to construct a custom makefile based on your system specs, but for simple programs it's not used that much.

---

### Post by Tanchistu on 2006-04-23
Maybe you havent noticed that I already tried what you told me, so this is my message again:

after ./configure I get this:

configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

---

### Post by kh4nh on 2006-04-23
This is atrracted from INSTALL file of linABX
"To build LinABX you need the scons build system.
It can be get from [www.scons.org](www.scons.org)

To build just type 'scons'
No installation is supported yet, so you have to move everything in place by
hand.
Actually all you need is to do is to put linabx in some dir like /usr/local/bin
There is a menuitem (linabx.desktop) which you can place
/usr/share/applications . Don't forget to put linabx.png in /usr/share/pixmaps
then, otherwise the menuitem will miss a nice icon :(." - linABX

you gonna have to get install scons first

---

### Post by mostwanted on 2006-04-23
[QUOTE=Tanchistu]Maybe you havent noticed that I already tried what you told me, so this is my message again:

after ./configure I get this:

configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.[/QUOTE]

That's because you haven't installed a compiler. You need a compiler before you can compile anything.

```
sudo apt-get install build-essential
```

That will install all normal compiler tools.

---

### Post by Tanchistu on 2006-04-23
So I have this file scons_0.96.1-0.1_all.deb , as I know ubuntu is a version of Debian, so how do I install it?

---

### Post by kh4nh on 2006-04-23
[QUOTE=Tanchistu]So I have this file scons_0.96.1-0.1_all.deb , as I know ubuntu is a version of Debian, so how do I install it?[/QUOTE]

in Terminal where the  scons_0.96.1-0.1_all.deb is, type:

sudo dpkg -i  scons_0.96.1-0.1_all.deb

---

### Post by Tanchistu on 2006-04-23
:D So who do I follow now? I install scons or build-essential? or I have to do them both? 

thank you for your time.

---

### Post by Biltong (Dee) on 2006-04-23
Use google to search - sometimes you can get faster help than using the seach on the ubuntu forums.
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

---

### Post by kh4nh on 2006-04-23
[QUOTE=Tanchistu]:D So who do I follow now? I install scons or build-essential? or I have to do them both? 

thank you for your time.[/QUOTE]

Installing build-essential would not hurt since you might need it to compile other softwares later on.

For linABX specifically, you need scons as it is said in the INSTALL file. After installing scons, move to linABX folder and type:

                  - scons
                  - mv linabx /usr/local/bin (put linabx in /usr/local/bin directory)

---

### Post by Tanchistu on 2006-04-23
](*,)  so if I want to install scons I need  python2.2 first, anyone knows what is this? I used Synaptic to find it but I couldn't, I also used google, but with little succes since it is such a common word.

How do I install gnome 2.10, I think now I have version 2.0.

A little summary of what I found out I need to install this little aplication:

    * Gnome >= 2.10
    * Jack audio connection kit
    * libsamplerate
    * libsndfile
    * scons
    * python2.2
    * ...and counting

it would be easier to choose windows in grub, run the installer and use the program, but now is not that important to use the program, it's more important to succed in installing it.

---

### Post by gr0kzer0 on 2006-04-23
Whenever you try to install a program that isn't from a repository, there's a chance you may run into dependency crap. It's happened to me enough now!

Unfortunately, all you can do is get a list of dependencies and see which you already have. Synaptic can help here.

Then, you got to go round looking for the dependencies that you don't already have. [http://packages.ubuntu.com](http://packages.ubuntu.com) is good for this, as they'll all be packaged as .deb. Otherwise, look on the developer's site. They may have the necessary there, or links to it.

Whenever you get a tarred package, after extraction have a look in what you've got and read the README. Commands like ./configure are usually the way, but not always, and the README will tell you. If there isn't a README, look at the names of what is there. If there's no file called configure, but there is one called Configure, the necessary command will be ./Configure. Files whose names are all in capitals (eg README and CONFIGURATION) are there for you to read. Do so. It's all helpful, and often necessary.

---

### Post by Tanchistu on 2006-04-23
Thank you, I have now founded a program written in java, that does the same thing and it works, I'm now trying to install a port from windows of a similar program, I'll see with what result. Thank you, I've learned a lot of things even if couldn't do what I've wanted in the first place. Your last post was of big help.

What is that a repository?, I belive something like Synaptic. Any other such tools?

P.S. I now realize how bad my english grammar is ](*,) I guess reading forums isn't enough, I'll post more :???:

---

