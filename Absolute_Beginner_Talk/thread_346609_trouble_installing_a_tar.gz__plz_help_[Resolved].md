---
title: "trouble installing a tar.gz  plz help [Resolved]"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by the Burning on 2007-01-25
i install a program onto my desktop and it is a tar.gz  i cant run it or turn it into anything that can be ran not that I know how to

for the past few days I have been punching in command line from these fourums changeing them to suit my program

help!:confused:

---

### Post by riven0 on 2007-01-25
Have you already extracted the file? Most programs come with a readme file that give instructions. 

As a general rule, though, you can run these commands once in the extracted file directory:

> ./configure
make
make install

You may have to run those commands with sudo access depending. You also may want to install the build essential files before going any further:

> sudo apt-get install build-essential


EDIT: Oh yeah, to extract the file, double-click on it.

---

### Post by aysiu on 2007-01-25
What's the program? Are you sure it needs to be installed from source?

---

### Post by the Burning on 2007-01-26
I type  ./configure when im in the directory and it says 
bash: ./configure: No such file or directory
what now?

---

### Post by taurus on 2007-01-26
```
ls -la ~/Desktop
```

---

### Post by the Burning on 2007-01-26
uhhh that did something
it showed almost every thing i have installed on this computer, even a bit of coloured words
whats next?

---

### Post by taurus on 2007-01-26
You said you downloaded a program to your desktop, I assume it's in ~/Desktop.  What's the name of that program then?  Otherwise, paste the output of this command here.

```
ls -la ~/Desktop
```

---

### Post by po0f on 2007-01-26
the Burning,

What are you trying to install?  As aysiu stated above, you might not have to install this program from source.  If you do, we can help you out.  It's much easier explaining how to install a specific program then just "some program".  ;)

---

### Post by Circus-Killer on 2007-01-26
okay, nobody has bothered mentioning this to you, tar.gz is a compressed format, much like a zip file.

so what you first of all need to do is extract the files using the *tar* command.

once you done that, well, then it depends on the program you wanna install. if its source code you will need to compile and install it like so:

./configure
make
make install

however if it is not source code, and contains ready to run binaries, then your should have no worries. now, the bright green files are executable (correct me if im wrong), the red are compressed files, and whats purple/blue are the directories (this is assuming the default bash color scheme).

let us know what package you are trying to install though, because 95% of things you can find in linux, you will find in the repositories. 4% of those that arent in the repos do have downloadable .deb files for easy installation. it is extremely rare that you will ever need to install something from source, especially as a new user. so again i ask, what are you trying to install?

---

### Post by the Burning on 2007-01-26
this is what it says


bark@bark-desktop:~/Desktop/campgen-0.23$ ls -la ~/Desktop
total 12208
drwxr-xr-x  7 bark bark    4096 2007-01-26 17:19 .
drwxr-xr-x 58 bark bark    4096 2007-01-26 17:19 ..
-rw-r--r--  1 bark bark   43520 2006-11-30 16:06 A chronicle of the Europe invasions and the fall of Rome.doc
-rw-r--r--  1 bark bark  255488 2006-11-30 16:13 a map of Visigoths migrations.doc
-rw-r--r--  1 bark bark 5583888 2007-01-18 19:54 amsn-0.96.tar.gz
-rw-r--r--  1 bark bark     505 2006-03-28 00:47 blender.desktop
-rw-r--r--  1 bark bark     208 2006-12-04 18:15 blobwars.desktop
-rw-r--r--  1 bark bark     209 2006-12-04 18:10 blobwars.desktop~
drwxr-xr-x  4 bark bark    4096 2007-01-16 10:17 bonnies destop folder
drwxr-xr-x  4 bark bark    4096 2006-12-29 07:19 campgen-0.23
drwxr-xr-x  8 bark bark    4096 2006-12-16 10:13 desktop
-rw-r--r--  1 bark bark   30391 2006-12-06 21:25 double-wires.swf
-rw-r--r--  1 bark bark     380 2006-04-17 22:12 enigma.desktop
-rw-r--r--  1 bark bark     564 2006-04-07 06:39 freeciv.desktop
-rw-r--r--  1 bark bark     222 2006-05-10 17:52 glob2.desktop
-rw-r--r--  1 bark bark    5241 2006-08-03 00:18 gnometris.desktop
-rwx------  1 bark bark    2094 2006-12-07 16:01 greasy-00eeaa40b0.desktop
-rw-r--r--  1 bark bark   14900 2006-12-04 21:01 HACKING
drwxr-xr-x  2 bark bark    4096 2006-12-05 13:09 install_flash_player_7_linux
-rw-r--r--  1 bark bark 1017790 2007-01-09 21:20 install_flash_player_7_linux.tar.gz
-rw-r--r--  1 bark bark     324 2006-03-23 15:43 liquidwar.desktop
-rw-------  1 bark bark       0 2006-12-04 18:14 new file~
drwxr-xr-x  2 bark bark    4096 2005-05-16 05:25 n_v1linux
-rw-r--r--  1 bark bark 1430315 2007-01-11 20:08 n_v1linux.tar.gz
-rw-r--r--  1 bark bark 3997622 2007-01-19 16:29 tcl8.5a5-src.tar.gz
-rw-r--r--  1 bark bark     234 2005-11-13 14:45 wings3d.desktop
-rw-r--r--  1 bark bark     213 2005-11-10 22:46 xconq.desktop
-rw-r--r--  1 bark bark     187 2005-12-10 13:48 xgalaga-hyperspace.desktop

---

### Post by taurus on 2007-01-26
And which program/file do you want to install again?

---

### Post by Circus-Killer on 2007-01-26
we didnt ask what it said, we asked what you are trying to install? if you dont tell us, we cant help you!!!

---

### Post by po0f on 2007-01-26
the Burning,

Is [this](http://www.wesnoth.org/wiki/CampGen) what you are trying to install?  From the website, it says you have to install wxpython ([python-wxgtk2.6](http://packages.ubuntu.com/edgy/python/python-wxgtk2.6) for Ubuntu users).  Apart from that, just cd into the directory and run `./campgen` inside the directory.


Circus-Killer,

Notice the directory of the terminal output.  
```
[FONT="Courier New"]bark@bark-desktop:~/Desktop/**campgen-0.23**$[/FONT]
```

---

### Post by the Burning on 2007-01-26
to those who have asked the name is campgen-0.23

---

### Post by po0f on 2007-01-26
the Burning,

```
[FONT="Courier New"]$ sudo aptitude update
$ sudo aptitude install python-wxgtk2.6
$ cd ~/Desktop/campgen-0.23
$ ./campgen[/FONT]
```

[EDIT]

If you have trouble installing python-wxgtk2.6, make sure you have the universe repos enabled.

---

### Post by the Burning on 2007-01-26
ok i will see if that works thanks

---

### Post by the Burning on 2007-01-26
thanks Everyone who helped its working now

---

