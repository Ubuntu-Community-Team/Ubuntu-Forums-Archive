---
title: "Nvu"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by filemanager on 2005-07-08
Does anyone know how to install Nvu?

I'm running amd64

[http://www.nvu.com/download.html](http://www.nvu.com/download.html)

There aren't any .deb packages, which is what I'm used to...

---

### Post by Mr. Electric Wizard on 2005-07-08
Administration --> Synaptic Package Manager
You will most likely have to add repositories like this:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by AntiDragon on 2005-07-08
You will need to build it from source - the source files are available from the NVU web site. Follow the instructions there and you should be good to go!

If building from source is a bit daunting though, I found a deb package for AMD 64 [here](http://ftp.psn.ru/debian-amd64/pool/main/n/nvu/) and I'm sure there's others. Download and install with dpkg -install <package> and that should be it.  ;-)

---

### Post by AntiDragon on 2005-07-08
[QUOTE=Mr. Electric Wizard]Administration --> Synaptic Package Manager
You will most likely have to add repositories like this:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)[/QUOTE]


Umm, or you could do that..errr... :?

---

### Post by Mr. Electric Wizard on 2005-07-08
But, compiling from source is sooo much fun! :-P

---

### Post by filemanager on 2005-07-08
How do you build something from source?

---

### Post by manicka on 2005-07-08
[QUOTE=filemanager]How do you build something from source?[/QUOTE]
 downlaod the source package and untar it to a directory

in that directory run form a terminal

./configure
make
sudo checkinstall

I use 'checkinstall' insead of 'make install' because it creates an nice deb package and is easily removed via apt/synaptic if you're not happy with it.

You'll need to install checkinstall with apt to take advantage of it

---

### Post by filemanager on 2005-07-08
[QUOTE=manicka]downlaod the source package and untar it to a directory

in that directory run form a terminal

./configure
make
sudo checkinstall

I use 'checkinstall' insead of 'make install' because it creates an nice deb package and is easily removed via apt/synaptic if you're not happy with it.

You'll need to install checkinstall with apt to take advantage of it[/QUOTE]

Untar?

I tried doing a search in Synaptic for "nvu" but it didn't come up with anything, and I just ran "sudo apt-get update"

---

### Post by manicka on 2005-07-08
[QUOTE=filemanager]Untar?

I tried doing a search in Synaptic for "nvu" but it didn't come up with anything, and I just ran "sudo apt-get update"[/QUOTE]


untar = extract

you'll need to add the backports repositories to apt to install nvu

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by filemanager on 2005-07-08
[QUOTE=manicka]untar = extract

you'll need to add the backports repositories to apt to install nvu

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)[/QUOTE]
 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


Those two lines were already in my etc/apt/sources.list file, before I ran apt-get update =\

Or is there something else you have to do to access the backports?

---

### Post by manicka on 2005-07-08
are they uncommented?

---

### Post by filemanager on 2005-07-08
[QUOTE=manicka]are they uncommented?[/QUOTE]
 Yep

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by manicka on 2005-07-08
Then I'm stumped. It should be there

---

### Post by poofyhairguy on 2005-07-09
Are you using the 64 bit version? It lacks many backports (actually all I think).

---

### Post by kc1di on 2005-07-09
Open root terminal- mkdir /home/(xxx)/NVU (replace xxx with your personal info.)

Now download NVU to this new directoryl.

Simply extract the downloaded file there by right mouse clicking on the file downloaded (one of the options should be extract here)  
once the file is extracted there is no further install needed.  use a file manager and scroll down to the NVU Script-  double clicking on that will run the program.

you will want to add the program to your menu.  the comand in the above example will be something like /home/(XXX)/NVU/nvu-1.0(xxxxx)/nvu

The NVU Icons can be found in the Icon folder of the NVU directory.

It's a great program.  Enjoy
Dave KC1DI  ;-)

---

### Post by filemanager on 2005-07-09
[QUOTE=kc1di]Open root terminal- mkdir /home/(xxx)/NVU (replace xxx with your personal info.)

Now download NVU to this new directoryl.

Simply extract the downloaded file there by right mouse clicking on the file downloaded (one of the options should be extract here)  
once the file is extracted there is no further install needed.  use a file manager and scroll down to the NVU Script-  double clicking on that will run the program.

you will want to add the program to your menu.  the comand in the above example will be something like /home/(XXX)/NVU/nvu-1.0(xxxxx)/nvu

The NVU Icons can be found in the Icon folder of the NVU directory.

It's a great program.  Enjoy
Dave KC1DI  ;-)[/QUOTE]
 I am indeed running amd64

[http://www.nvu.com/download.html](http://www.nvu.com/download.html)

Which file do I download?

---

### Post by filemanager on 2005-07-12
[QUOTE=AntiDragon]You will need to build it from source - the source files are available from the NVU web site. Follow the instructions there and you should be good to go!

If building from source is a bit daunting though, I found a deb package for AMD 64 [here](http://ftp.psn.ru/debian-amd64/pool/main/n/nvu/) and I'm sure there's others. Download and install with dpkg -install <package> and that should be it.  ;-)[/QUOTE]
 "nvu_0.99+1.0pre-1_amd64.deb"

Do I download that file? I don't know how to compile from source =\

---

### Post by AntiDragon on 2005-07-12
The .deb file I mentioned is a package - just like the Synaptic ones. It's already pre-compiled for AMD64 systems (it's a binary, not source).  I haven't tried it myself yet as I've been away from my PC for a while...but..I'm...coping.... :---) 

Deb packages are installed with [FONT=Courier New]dpkg -i[/FONT] followed by the package name. The package contains all the information about required dependencies and where to put the various files. (You probably already know that, but hey - covering all the bases :) )

Word of warning - this is a Debian package. However, I've yet to see any issues with pure Debian packages on my own AMD64 Ubuntu system!

Let us know how it goes!

---

### Post by filemanager on 2005-07-12
[QUOTE=AntiDragon]The .deb file I mentioned is a package - just like the Synaptic ones. It's already pre-compiled for AMD64 systems (it's a binary, not source).  I haven't tried it myself yet as I've been away from my PC for a while...but..I'm...coping.... :---) 

Deb packages are installed with [FONT=Courier New]dpkg -i[/FONT] followed by the package name. The package contains all the information about required dependencies and where to put the various files. (You probably already know that, but hey - covering all the bases :) )

Word of warning - this is a Debian package. However, I've yet to see any issues with pure Debian packages on my own AMD64 Ubuntu system!

Let us know how it goes![/QUOTE]
 But here: [http://ftp.psn.ru/debian-amd64/pool/main/n/nvu/](http://ftp.psn.ru/debian-amd64/pool/main/n/nvu/)

There are a bunch of files, which is the .deb package you're talking about? Or do I need all of them? (trying to figure out what to d/l)

---

### Post by AntiDragon on 2005-07-12
Just the AMD64 one. Click [right here](http://ftp.psn.ru/debian-amd64/pool/main/n/nvu/nvu_0.99+1.0pre-1_amd64.deb) to download it now.

---

### Post by filemanager on 2005-07-12
[QUOTE=AntiDragon]Just the AMD64 one. Click [right here](http://ftp.psn.ru/debian-amd64/pool/main/n/nvu/nvu_0.99+1.0pre-1_amd64.deb) to download it now.[/QUOTE]
 DL'ing it now! Thanks so much!!

I hope this works!

---

### Post by AntiDragon on 2005-07-12
Cool. Let us know!

---

### Post by filemanager on 2005-07-12
I got this error:

jen@computer:~$ sudo dpkg -i nvu*
Password:
Selecting previously deselected package nvu.
(Reading database ... 61790 files and directories currently installed.)
Unpacking nvu (from nvu_0.99+1.0pre-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of nvu:
 nvu depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 nvu depends on libfontconfig1 (>= 2.3.0); however:
  Version of libfontconfig1 on system is 2.2.3-4ubuntu7.
dpkg: error processing nvu (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvu


When I opened Synaptic it said the package was "broken", so I uninstalled it, then when I went to reinstall it I get this error in a pop up box:

nvu:

Package nvu has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

### Post by AntiDragon on 2005-07-12
There's a common probblem with some of these dependencies when you install a stand-alone deb file.

What you can do is [FONT=Courier New]dpkg -i -force <package name>[/FONT] to ignore the dependency errors.

If you have problems, you can run [FONT=Courier New]apt-get -f install[/FONT] but be warned - this will remove all "broken" packages from your system.

---

### Post by filemanager on 2005-07-12
[QUOTE=AntiDragon]There's a common probblem with some of these dependencies when you install a stand-alone deb file.

What you can do is [FONT=Courier New]dpkg -i -force <package name>[/FONT] to ignore the dependency errors.

If you have problems, you can run [FONT=Courier New]apt-get -f install[/FONT] but be warned - this will remove all "broken" packages from your system.[/QUOTE]
 root@computer:/home/jen # sudo dpkg -i -force nvu*
dpkg: conflicting actions --field and --install

Type dpkg --help for help about installing and deinstalling packages [*];
Use dselect for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !


Same error message before and after I did the -f install thing

---

### Post by AntiDragon on 2005-07-12
Sorry - typos. You need two (--) dashes before "force" I believe. Could someone else confirm that here? I'm a bit tied up and can't check the exact syntax.... :(

Actually, type ```
man dpkg
``` to get the manual page to make sure. Use PgUp, PgDn and "q" to quit. Basically you need to tel the dpkg program to ignore dependecies as the versions you have are good enough.

---

### Post by filemanager on 2005-07-12
[QUOTE=AntiDragon]Sorry - typos. You need two (--) dashes before "force" I believe. Could someone else confirm that here? I'm a bit tied up and can't check the exact syntax.... :(

Actually, type ```
man dpkg
``` to get the manual page to make sure. Use PgUp, PgDn and "q" to quit. Basically you need to tel the dpkg program to ignore dependecies as the versions you have are good enough.[/QUOTE]
 So it would be:

sudo dpkg -i --force-depends-version nvu*

or

sudo dpkg -i --force-depends-conflicts nvu*

?

---

### Post by manicka on 2005-07-12
I learnt the hard way to not force packages unless you are absolutely sure it won't mess up your system. This looks like it will probably be okay, but you never know what conflicts it might cause down the track. 

I wouldn't get into the habit of forcing packages and maintaining a broken system.

---

### Post by manicka on 2005-07-12
There's a suggestion at the link below on creating your own package that might be useful, using 'alien' to make your own deb

[http://www.imilesi.it/lore/linux/notsoweirdprograms.html](http://www.imilesi.it/lore/linux/notsoweirdprograms.html)

search for Nvu-*-amd64.rpm. There's a few rpm's  there that might do the job. (i586 package from packman installs okay but doesn't run, maybe the amd64 package will work better)

HTH

Edit: You could also have a crack at building it from source. The instructions are on the nvu site.

Edit2: Have you tried the deb packageavailable in breezy?
[http://packages.ubuntu.com/breezy/web/nvu](http://packages.ubuntu.com/breezy/web/nvu)

---

### Post by filemanager on 2005-07-12
[QUOTE=manicka]There's a suggestion at the link below on creating your own package that might be useful, using 'alien' to make your own deb

[http://www.imilesi.it/lore/linux/notsoweirdprograms.html](http://www.imilesi.it/lore/linux/notsoweirdprograms.html)

search for Nvu-*-amd64.rpm. There's a few rpm's  there that might do the job. (i586 package from packman installs okay but doesn't run, maybe the amd64 package will work better)

HTH

Edit: You could also have a crack at building it from source. The instructions are on the nvu site.

Edit2: Have you tried the deb packageavailable in breezy?
[http://packages.ubuntu.com/breezy/web/nvu](http://packages.ubuntu.com/breezy/web/nvu)[/QUOTE]
 I downloaded the package from breezy and it didn't work, "dependency" issues or whatever, so I think I'll try building it from source next...

---

### Post by manicka on 2005-07-12
[QUOTE=filemanager]I downloaded the package from breezy and it didn't work, "dependency" issues or whatever, so I think I'll try building it from source next...[/QUOTE]
 Good luck, let us know how it goes.

---

### Post by filemanager on 2005-07-13
I downloaded the sources, but now on step #4 from here:
[http://www.nvu.com/Building_From_Source.html](http://www.nvu.com/Building_From_Source.html)

I can't find the .mozconfig folder in the mozilla folder =\

---

### Post by filemanager on 2005-07-13
Ok now I'm stuck on #5 (heh, I figured out the .mozconfig was a file, not a folder):

> jen@computer:~$ make -f client.mk build_all
make: client.mk: No such file or directory
make: *** No rule to make target `client.mk'.  Stop.


---

### Post by filemanager on 2005-07-13
Ah, I seem to have got it, but I got this error at the end:

> 
checking for gtk+-2.0 >= 1.3.7... Package gtk+-2.0 was not found in the pkg-conf ig search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adj usting the PKG_CONFIG_PATH environment variable if your libraries are in a nonst andard prefix so pkg-config can find them.
*** Fix above errors and then restart with "make -f client.mk build"
make: *** [/home/jen/mozilla/Makefile] Error 1



---

### Post by filemanager on 2005-07-16
[QUOTE=filemanager]Ah, I seem to have got it, but I got this error at the end:[/QUOTE]
 ... anyone?

I have the GTK+ files installed (or so it says in Synaptic), but I guess they aren't the right ones. Which ones should I install?

---

### Post by jpoe on 2005-07-19
Hi,

I think I found a way to solve your problem.  I too am on an AMD64 and wanted to install it.  You can install the .deb package from Breezy, but you first need to get the lib6 package and install it using the same procedure from Breezy, since that is the dependancy that it needs that it can't get from the Hoary repositories (at least not the right version).

So, this is what I *just* did and worked:

download:

[http://ftp.cs.umn.edu/pub/ubuntu/pool/main/g/glibc/libc6_2.3.5-1ubuntu7_amd64.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/main/g/glibc/libc6_2.3.5-1ubuntu7_amd64.deb)
[http://ftp.cs.umn.edu/pub/ubuntu/pool/universe/n/nvu/nvu_0.99+1.0pre-1_amd64.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/universe/n/nvu/nvu_0.99+1.0pre-1_amd64.deb)

then, open a terminal and in the directory you downloaded to:

sudo dpkg -i libc6_2.3.5-1ubuntu7_amd64.deb
sudo dpkg -i nvu_0.99+1.0pre-1_amd64.deb

No need to force, as long as you try the libc6 package first, should install fine with what is available in Hoary AMD64.

Hope this helps,

James

---

### Post by jpoe on 2005-07-19
Ok never mind, don't take my last advice.

It installs, but it doesn't actually run; and its causing other dependency issues on my system.

---

### Post by jpoe on 2005-07-20
Okay I think I really have it this time!

I found this page:

[https://wiki.ubuntu.com//HowToInstallNVUHTMLEditor](https://wiki.ubuntu.com//HowToInstallNVUHTMLEditor)

Which worked like a charm on my machine (I actually installed AND ran this time).  Simply download the Linspire binary (shrug) from the NVU website.  Here is a direct link if you want it:

[http://cvs.nvu.com/download/nvu-1.0-pc-linux2.6.10-gnu.tar.bz2](http://cvs.nvu.com/download/nvu-1.0-pc-linux2.6.10-gnu.tar.bz2)

Then issue this command:

sudo tar xvfj nvu-1.0-pc-linux2.6.10-gnu.tar.bz2 -C /opt/

Thats it! You can run the program with this command:

/opt/nvu-1.0/nvu

---

