---
title: "How to install Lsongs"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-06-27
Can anyone help me how to install this application: [http://www.lsongs.com/](http://www.lsongs.com/)

I would like to try it, but i cant find it in the Synapic thing in Ubuntu, and there doesent seem to be a package for ubuntu on their homepage. So do I have to install all the libs myself, or can i Download one of the other distros?

---

### Post by Brynster on 2006-06-27
Lsongs is a good App

posiibly the best thing to come from Linspire. The way i did it was to download the .rpm file and use alien to create a .deb

then used the terminal to ```
 sudo dpkg -i nameofpackage.deb
```

Fired it through terminal by typing Lsongs at the prompt and saw what i was missing from dependencies and synaptic'd them.

Lsongs is a very good itunes replacement including syncing to iPod. the downside to it is (depending on th drive you have) a little "click" noise at the start of anything you ripp using it. Duane the author (good good guy, Linspire must miss his skills) once explained it as being caused by cdrao ( ithink) which is the program it uses as the ripper.

---

### Post by patbuntu on 2006-06-27
You can probably find most if not all of the dependencies in synaptic

> 
    *  Python 2.3
    * PyQt
    * PyKDE
    * pyxine
    * pyid3lib (see note below)
    * pynjb


Additional packages required to perform certain operations:

    * cdrecord - for CD burning
    * cdparanoia - for CD ripping
    * cdda2wav - for CD ripping
    * mpg321 - for CD burning
    * sox - for CD burning
    * vorbistools - for CD ripping and burning of Ogg Vorbis files
    * pylame - for CD ripping of MP3 files
    * faad - for CD ripping and burning of M4A files
    * trmxml - for automatic tagging
    * howlxml - for network sharing
    * daapd - for network sharing (see note below)


Typical packages required by the previously listed packages:

    * libxine
    * id3lib
    * libhowl
    * libmusicbrainz
    * libnjb
    * liblame



Then download the source tarball and try to install...

> 

To build and install, untar the archive, enter the directory, and type:

    python install.py


Not tried this yet, but see how you get on.

-Pat

---

### Post by jincast90 on 2006-06-27
All these things just seems so overwelming for a newcomer to linux like me.. But I guess I have to give it a shot if theres no other ways.

---

### Post by mozetti on 2006-06-27
[QUOTE=jincast90]All these things just seems so overwelming for a newcomer to linux like me.. But I guess I have to give it a shot if theres no other ways.[/QUOTE]

There's no better way to learn. I'm new to Linux myself, and I really appreciate the ability to use apt-get/synaptic for pretty much point-and-click installation. But, the way to really learn the system is to dabble in the command line. Good luck!

---

### Post by jincast90 on 2006-06-27
[QUOTE=patbuntu]You can probably find most if not all of the dependencies in synaptic



Then download the source tarball and try to install...



Not tried this yet, but see how you get on.

-Pat[/QUOTE]

Doesent all this take all the "easyness" away from linux. Everyone says its so much easy on linux, but if I were on windows, I would just download an .exe file and launch it press forward a couple of times and it would be there. From what I understand here, I have to install 10+ packages and afterwords use some kind of command I have no idea what meens, and afterwords, if im lucky, I will get it to work? Is this so called easy? Or am I mistaking :-k

---

### Post by mozetti on 2006-06-27
Debian-based systems are typically "easier" than plain-Linux because of 'apt-get' - it knows dependencies and associated programs that are needed. But, the program you want to install doesn't use a debian package and/or apt-get, so you need to do it the old fashioned way. That's all.

---

### Post by patbuntu on 2006-06-27
[QUOTE=jincast90]Doesent all this take all the "easyness" away from linux. [/QUOTE]

In this case, yes, theres more work involved unfortunately.  If the developer had made a deb file, you would be able to download it and double click to install.  That would find all these dependencies for you and install them automatically.  Its all a case of what you are trying to install at the end of the day.

-Pat

---

### Post by jincast90 on 2006-06-28
Ok so I downloaded the rpm package. Then downloaded alien, and used this command: sudo alien -i/home/myname/desktop/lsongs but it wouldent install it.
What did I do wrong?

---

### Post by aysiu on 2006-06-28
It looks as if you're missing a space between *-i* and */home/username/Desktop/LSongs*

*Desktop* is also supposed to be capitalized.

---

### Post by jincast90 on 2006-06-28
Ok when I try to do that. It says the file is not found I tried all these commands:

sudo alien -i/home/myname/desktop/lsongs.rpm

sudo alien -i/home/myname/desktop/lsongs

sudo alien -i /home/myname/desktop/lsongs.rpm

sudo alien -i /home/myname/desktop/lsongs

Neither of these work. The 2 last commands tells me there is no such file.

Just to be sure, the place where I put my name, is suppose to be the name of ur account right?

---

### Post by aysiu on 2006-06-28
*Desktop* needs to be capitalized. Everything is case-sensitive.

So ```
/home/username/desktop
``` is different from ```
/home/username/Desktop
```

Try this. Copy and paste these commands. Do not retype them. ```
cd ~/Desktop
ls
sudo alien -i *.rpm
```

---

### Post by jincast90 on 2006-06-28
[QUOTE=aysiu]*Desktop* needs to be capitalized. Everything is case-sensitive.

So ```
/home/username/desktop
``` is different from ```
/home/username/Desktop
```

Try this. Copy and paste these commands. Do not retype them. ```
cd ~/Desktop
ls
sudo alien -i *.rpm
```[/QUOTE]

Your so clever!

Anyways, when I do these things, I get a bunch of warnings instead of an installed package. 

I feel so stupid #-o 

Anyone know whats wrong?

---

### Post by aysiu on 2006-06-28
I think the Python script is looking for packages you don't have installed. People earlier in the thread said you can just install these through Synaptic, but I don't think you can get *pyxine* in Synaptic, for example.

---

### Post by turkenator on 2006-11-05
hi im trying to install lsongs did any 1 end up installing this thing its so bloody hard to get all the dependency requirements met does any 1 have a link of pyxine their site wont open

---

### Post by aysiu on 2006-11-05
> **turkenator said:**
> hi im trying to install lsongs did any 1 end up installing this thing its so bloody hard to get all the dependency requirements met does any 1 have a link of pyxine their site wont open
No. As far as I know, no Ubuntu user has ever successfully installed LSongs in Ubuntu.

---

### Post by maxpower on 2006-11-06
Check these out:

[http://www.ubuntuforums.org/showpost.php?p=1722659&postcount=12](http://www.ubuntuforums.org/showpost.php?p=1722659&postcount=12)

mAx

---

### Post by some1_genius on 2007-04-11
hay guys, take a lookat that

[http://thoc.blogspot.com/search/label/lsongs](http://thoc.blogspot.com/search/label/lsongs)

moustafa

---

### Post by aysiu on 2007-04-11
> **some1_genius said:**
> hay guys, take a lookat that

[http://thoc.blogspot.com/search/label/lsongs](http://thoc.blogspot.com/search/label/lsongs)

moustafa
Cool. Thanks for the link. Wonder if it'd work on Feisty, too.

---

### Post by Moamen on 2007-08-17
it can be done easily now
[http://jacksparrow.blogsome.com/2007/08/17/how-to-install-lsongs-on-ubuntu-feisty-704-2/](http://jacksparrow.blogsome.com/2007/08/17/how-to-install-lsongs-on-ubuntu-feisty-704-2/)

---

### Post by gonon on 2007-11-02
great link used his tutorial and now i have working lsongs thanks to you and captain Sparrow :popcorn:

---

