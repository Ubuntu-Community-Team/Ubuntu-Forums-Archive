---
title: "Installing tar.gz"
date: 2005-07-31
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-07-31
I'm sure that this is a classic newbie question, although i couldn't find a recent thread that dealt with it.

So,

How does one install tar.gz files? I'd like to know once and for all, because in the past the mere sight of tar.gz has frightened me  (not one of those again!  :???:  )

1.I want to install wallpapoz - wallpapoz-0.2.tar.bz2
2.i need to install dependecy libxml - libxml++-2.10.0.tar.gz

I realise they are kinda different tar packages. But if someone can first show me how to deal with 'tar.gz' packages

So, i've got libxm.++-2.10.0.tar.gz sitting on my Desktop. I believe i have even extracted it to /tmp. Where do i go from here? 

thank you

--sophtpaw

---

### Post by ubuntp on 2005-07-31
Well what do you want to do with that .tar.gz, is it an application or the source of an application? First of all extracting it was the right choice, since tarballs are archives (like zip or rar). Then you either got an application inside that you can execute or you've got the source code and need to compile it first.

The .bz2 or .gz is just the compression used (**bz**ip**2** and **gz**ip). The file can be extracted by right clicking on it and chosing extract here (or whatever it's called) or from the command line (see below).

For .tar.bz2 use: *tar -**j**vxf name_of_file.tar.bz2*
And for tar.gz: *tar -**z**vxf name_of_file.tar.gz*

---

### Post by sophtpaw on 2005-07-31
[QUOTE=ubuntp]Well what do you want to do with that .tar.gz, is it an application or the source of an application? First of all extracting it was the right choice, since tarballs are archives (like zip or rar). Then you either got an application inside that you can execute or you've got the source code and need to compile it first.

The .bz2 or .gz is just the compression used (**bz**ip**2** and **gz**ip). The file can be extracted by right clicking on it and chosing extract here (or whatever it's called) or from the command line (see below).

For .tar.bz2 use: *tar -**j**vxf name_of_file.tar.bz2*
And for tar.gz: *tar -**z**vxf name_of_file.tar.gz*[/QUOTE]


well the libxml++-2.10.0.tar.gz is to fulfill a dependency requirement of wallpapoz. i don't know if that makes it an application or the source of an application.

As regards to wallpapoz itself i would more comfortable, yet still haphazardly, gues that it is an application that i can execute after compilation. But i would certainly need to compile first

thank you

--sophtpaw

---

### Post by ubuntp on 2005-07-31
I'm pretty sure you can get libxml through synaptic, it might not be the same version but will work regardless. Then about compiling that other app, usually just go into the directory you extracted it in and type from the command line:

./configure
./make
./make install

That works with most apps. Note that you'll need to get that libxml++ before doing that. Actually you'll probably also need libxml++-dev to compile that package.

---

### Post by sophtpaw on 2005-07-31
[QUOTE=ubuntp]Well what do you want to do with that .tar.gz, is it an application or the source of an application? First of all extracting it was the right choice, since tarballs are archives (like zip or rar). Then you either got an application inside that you can execute or you've got the source code and need to compile it first.

The .bz2 or .gz is just the compression used (**bz**ip**2** and **gz**ip). The file can be extracted by right clicking on it and chosing extract here (or whatever it's called) or from the command line (see below).

For .tar.bz2 use: *tar -**j**vxf name_of_file.tar.bz2*
And for tar.gz: *tar -**z**vxf name_of_file.tar.gz*[/QUOTE]

i go to /tmp and i see both : libxml++-2.10.0 and libxml++-2.10.0.tar.gz 

when i tar xzvf ~/ i get: 

tar xzvf ~/libxml++-2.10.0.tar.gz
tar: /home/conrad/libxml++-2.10.0.tar.gz: Cannot open: No such file or directorytar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Can you explain?

thank you

-sophtpaw

---

### Post by lol on 2005-07-31
> tar xzvf ~/libxml++-2.10.0.tar.gz 

with this command, you are asking tar to extract an archive located in your home directory... which is obviously not what you want, since you said yourself that the archive is in /tmp.

The correct command to use would then be :
```
cd /tmp 
tar xvfz libxml++-2.10.0.tar.gz
``` 

About installing from sources, I strongly suggest:
1 - don't recompile libraries that you could install from the repository.
2 - use checkinstall to build a .deb package instead of using "make install"

So, how would I install Wallpapoz...
1 - download the source tarball (which you did already)
2 - extract it : tar xvfj wallpapoz-0.2.tar.bz2
3 - cd wallpapoz-0.2
4 - make => this is going to fail with the error: daemon_wallpapoz.cpp:19:31: libxml++/libxml++.h: No such file or directory
5 - look on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to find which package is providing libxml++.h => libxml++2.6-dev
6 - apt-get install libxml++2.6-dev
7 - make => failing again, with: wallpapoz.h:19:28: libglademm/xml.h: No such file or directory
8 - look again on [http://packages.ubuntu.com/](http://packages.ubuntu.com/), this time for the file xml.h. There are several packages providing this file, but if you look more carefully at the error message, you will see that it is looking for the package 'libglademm-2.4'
9 - apt-get install libglademm-2.4-dev
10 - make => this time it is successful (unless you are missing other libs), time to install
11 - checkinstall => follow the instructions, it's quite easy.

and that's it. checkinstall creates a .deb package AND install it. You can start using wallpapoz. And if you want to remove it, all you have to do is: dpkg -r wallpapoz-0.2

hope this can help.

---

### Post by manicka on 2005-07-31
[QUOTE=lol]
2 - use checkinstall to build a .deb package instead of using "make install"
[/QUOTE]

I'd support this advice. Checkinstall makes it much easier to remove a package later on if needed.

You may need to install checkinstall before starting using synaptic, or

sudo apt-get install checkinstall

---

### Post by sophtpaw on 2005-07-31
[QUOTE=ubuntp]I'm pretty sure you can get libxml through synaptic, it might not be the same version but will work regardless. Then about compiling that other app, usually just go into the directory you extracted it in and type from the command line:

./configure
./make
./make install

That works with most apps. Note that you'll need to get that libxml++ before doing that. Actually you'll probably also need libxml++-dev to compile that package.[/QUOTE]


Thx. I did have Synaptic install libxml packages, so hopefully i should be ok now

However, i tried ./configure unsuccessfully
transcript:
conrad@x1-6-00-0b-6a-16-78-f0conrad:/tmp$ ./configure
bash: ./configure: No such file or directory

 :-k  hmmm....

---

### Post by manicka on 2005-07-31
[QUOTE=sophtpaw]Thx. I did have Synaptic install libxml packages, so hopefully i should be ok now

However, i tried ./configure unsuccessfully
transcript:
conrad@x1-6-00-0b-6a-16-78-f0conrad:/tmp$ ./configure
bash: ./configure: No such file or directory

 :-k  hmmm....[/QUOTE]
 Have you changed directories in the terminal to the directory that the configure file is in when running this command.

---

### Post by sophtpaw on 2005-07-31
[QUOTE=lol]with this command, you are asking tar to extract an archive located in your home directory... which is obviously not what you want, since you said yourself that the archive is in /tmp.

The correct command to use would then be :
```
cd /tmp 
tar xvfz libxml++-2.10.0.tar.gz
``` 

About installing from sources, I strongly suggest:
1 - don't recompile libraries that you could install from the repository.
2 - use checkinstall to build a .deb package instead of using "make install"

So, how would I install Wallpapoz...
1 - download the source tarball (which you did already)
2 - extract it : tar xvfj wallpapoz-0.2.tar.bz2
3 - cd wallpapoz-0.2
4 - make => this is going to fail with the error: daemon_wallpapoz.cpp:19:31: libxml++/libxml++.h: No such file or directory
5 - look on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to find which package is providing libxml++.h => libxml++2.6-dev
6 - apt-get install libxml++2.6-dev
7 - make => failing again, with: wallpapoz.h:19:28: libglademm/xml.h: No such file or directory
8 - look again on [http://packages.ubuntu.com/](http://packages.ubuntu.com/), this time for the file xml.h. There are several packages providing this file, but if you look more carefully at the error message, you will see that it is looking for the package 'libglademm-2.4'
9 - apt-get install libglademm-2.4-dev
10 - make => this time it is successful (unless you are missing other libs), time to install
11 - checkinstall => follow the instructions, it's quite easy.

and that's it. checkinstall creates a .deb package AND install it. You can start using wallpapoz. And if you want to remove it, all you have to do is: dpkg -r wallpapoz-0.2

hope this can help.[/QUOTE]


Very helpful.

Howerver, 

conrad@x1-6-00-0b-6a-16-78-f0conrad:~/wallpapoz-0.2$ checkinstall

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:

Preparing package documentation...OK

Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
mkdir: cannot create directory `/usr/share/doc/wallpapoz-0.2': Permission denied
****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


did i do something wrong?

---

### Post by lol on 2005-07-31
you use "./configure" only if there is a "configure" script in the sources directory, which is not the case for wallpapoz.

To build the sources, the command you need is "make".
"make" is a command that is using a kind of configuration file called "Makefile".

There is usually 2 cases:
* the "Makefile" is already present => you can just type "make"
* the "Makefile" is not present => there is probably a "configure" script, that is going to generate the "Makefile". So before running "make", you need to call the script wit "./configure".

So depending on the case, the correct way to build your sources will be:
```
make
checkinstall (or make install)
```

or

```
./configure
make
checkinstall (or make install)
```

---

### Post by lol on 2005-07-31
you need to run "checkinstall" or "make install" as root.

so instead of just 'checkinstall", try "sudo checkinstall"

---

### Post by sophtpaw on 2005-07-31
[QUOTE=manicka]Have you changed directories in the terminal to the directory that the configure file is in when running this command.[/QUOTE]

well, i don't know what directory the configure file is in. I thought i was supposed to do ./configure in the directory where i had extracted the wallpapoz.tar.gz, which as you can see from the transcript i did. 

So, i don't know how i'm supposed to do ./configure. 
But since then i have taken the advice that there is wisdom in letting checkinstall do it as it is safer or/and easier should i wish to uninstall in the future

-sophtpaw

---

### Post by manicka on 2005-07-31
Okay, Wallpapoz doesn't configure in the usual way. You won't be able to use checkinstall for this one. Follow the installation instructions at the wallpapoz website and all should be well.

[http://wallpapoz.sourceforge.net/](http://wallpapoz.sourceforge.net/)

As a side note I found wallpapoz a bit clunky and slow to change wallpapers between desktops  for my liking.

---

### Post by lol on 2005-07-31
you can use checkinstall with wallpapoz, i just did it :)

Please, have a look at my 2 previous posts: the fact that "configure" is missing is not a problem, because the "Makefile" is already present.

But again, you need to run "checkinstall" as root! ("sudo checkinstall" if you don't have a root account).

---

### Post by manicka on 2005-07-31
[QUOTE=lol]you can use checkinstall with wallpapoz, i just did it :)
[/QUOTE]
 okay, good to know :D

---

### Post by manicka on 2005-07-31
If you have a problem with the libxml dependency, then a deb is available here

[http://ubuntuforums.org/showpost.php?p=267137&postcount=25](http://ubuntuforums.org/showpost.php?p=267137&postcount=25)

---

### Post by sophtpaw on 2005-07-31
[QUOTE=lol]you can use checkinstall with wallpapoz, i just did it :)

Please, have a look at my 2 previous posts: the fact that "configure" is missing is not a problem, because the "Makefile" is already present.

But again, you need to run "checkinstall" as root! ("sudo checkinstall" if you don't have a root account).[/QUOTE]


Thank you people,

sudo checkinstall did do the trick. It should be installed. I'm slightly disheartened to hear that somone found it clunky. So, i'll see. I do value being able to have each window unique in flavor. 
How do i go about this now? ooops  :oops: 

-sophtpaw

---

### Post by lol on 2005-07-31
well, it's too early to thank us...

Sorry about that, but I just realised that the wallpapoz cannot be installed the usual way :(

If you try this: dpkg -L wallpapoz-0.2, you will see that only the documentation has been included in the package built by checkinstall.
Why? The usual way to install a program is to type "make install". make will try to find the tag "install" in the Makefile, and execute the instructions specified here.
But there is no "install" tag in the Makefile provided with Wallpapoz, therefore "make install" doesn't do anything. This is a problem because "checkinstall" actually call "make install" by default to build the package...

In the case of Wallpapoz, there is a script included to install the program. You are supposed to call this script like this: "./install.sh /usr/local".

There is no way checkinstall can guess this, so you have to tell him how to install wallpapoz.

So the correct way to call checkinstall in the particular case of wallpapoz is:
```
sudo checkinstall -si ./install.sh /usr/local
```

Now, if you try again "dpkg -L wallpapoz-0.2", you will see that this time, all the files are correctly included in the package... and you should now be able to use it.

[EDIT]: well yes, you should be able to use it IF your path includes the "/usr/local/bin" directory.

---

### Post by sophtpaw on 2005-07-31
[QUOTE=lol]well, it's too early to thank us...

Sorry about that, but I just realised that the wallpapoz cannot be installed the usual way :(

If you try this: dpkg -L wallpapoz-0.2, you will see that only the documentation has been included in the package built by checkinstall.
Why? The usual way to install a program is to type "make install". make will try to find the tag "install" in the Makefile, and execute the instructions specified here.
But there is no "install" tag in the Makefile provided with Wallpapoz, therefore "make install" doesn't do anything. This is a problem because "checkinstall" actually call "make install" by default to build the package...

In the case of Wallpapoz, there is a script included to install the program. You are supposed to call this script like this: "./install.sh /usr/local".

There is no way checkinstall can guess this, so you have to tell him how to install wallpapoz.

So the correct way to call checkinstall in the particular case of wallpapoz is:
```
sudo checkinstall -si ./install.sh /usr/local
```

Now, if you try again "dpkg -L wallpapoz-0.2", you will see that this time, all the files are correctly included in the package... and you should now be able to use it.

[EDIT]: well yes, you should be able to use it IF your path includes the "/usr/local/bin" directory.[/QUOTE]

great! but use how? where do i find it? has it got an icon in gui (loader?) under Applications/ ? or is it integrated into the Ubuntu system itself?

-sophtpaw

---

### Post by lol on 2005-08-02
I don't use gnome, so I cannot really help you here...

What I know is that wallpapoz is composed of 2 parts : the setup tool and a daemon. You probably have to do the setup with the command "wallpapoz", but it is the "daemon_wallpapoz" who is probably taking care of changing the wallpaper when you change desktop, which means that you certainly have to start it when you start your gnome session.

---

### Post by manicka on 2005-08-02
It's been a while since I used it, but I think you just run ```
wallpapoz
``` from a command line and the control panel will start up.

The daemon automaticaly starts at each session once installed

---

