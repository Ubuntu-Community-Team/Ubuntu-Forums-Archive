---
title: "Hwere do games go?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Vuto on 2007-05-31
i am absolutely new to ubuntu and i downloaded some ubuntu game s (Scorched 3d & Wormux) i can't seem to find them could someone plz tell me where they are so i can play them 

thnx

~~~Vuto~~~

---

### Post by plcdfa on 2007-05-31
Did you install them through the package manager? In that case they should be in your applications menu. (I think, in fact I use Kubuntu. ;) )

---

### Post by Wraith's Hand on 2007-05-31
Did you install them from Synaptic or did you download the compressed files?  If you downloaded it from the package manager, apt-get, or the program manager, I think they would be installed under "Games" in the menu.    If you don't see them in the folder and you used one of these methods, you might try right clicking on the menu to get the menu editor to see if the programs are install but not being displayed.  

If you downloaded the compressed files, you'll need to locate the .zip or .tar file and unzip them and then compile the program.

---

### Post by Vuto on 2007-05-31
i downloaded them as a .deb file and installed them i checked under applications and not there and i checked if not being showed not there either

---

### Post by Bigdog60 on 2007-05-31
Did you install them from symantic package downloader or did you use compressed file if you used symatic then it should be in your games category. If u did a compress install them.

---

### Post by lakersforce on 2007-05-31
download them from the package manager instead of from the internet.

---

### Post by Vuto on 2007-05-31
dumb it down plz my first time using ubuntu 

whats package manager?

---

### Post by lakersforce on 2007-05-31
Applications -> Add/remove programs

and go to games.

---

### Post by ncappel1 on 2007-05-31
Yeah, the package manager is much easier, you'll find everything you really need in there. Before you install anything, check to make sure it is in the package manager first, it will save you a headache if you are new to it!

---

### Post by Shadoweater12081980 on 2007-05-31
Try bringing up a Konsole and typing

# wor

then at the end of wor - hit tab, it should complete the command for you. If nothing appears, press it twice and it will show you all the programs beginning with wor..

you can then execute the game this way if it appears. I can imagine it has :D

\\:D/

---

### Post by Vuto on 2007-05-31
the games arent in the package manager what does that mean?

---

### Post by jfinkels on 2007-05-31
If you installed from a .deb file, open the file with GDebi by double-clicking on it. Then click on the "Included Files" tab. You should see a long list of files and directories. Binary (executable) files for launching programs will usually be in the directory "/usr/bin" or perhaps "/usr/local/bin".

If you want to install programs the easy way, go to "System > Administration > Synaptic Package Manager". From here you can select applications that you want, mark them for installation, click apply, and they will be installed along with packages that they depend on. To view included files for packages installed in Synaptic Package Manager, right click on a listing for a package, select "Properties", then "Installed Files".

Here's more info on installing things: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Vuto on 2007-05-31
i did wat u sed and found it in "/usr/share/games/wormux" but there is no file to launch the game just the files for the game so where can i launch it?

---

### Post by jfinkels on 2007-05-31
> **Vuto said:**
> i did wat u sed and found it in "/usr/share/games/wormux" but there is no file to launch the game just the files for the game so where can i launch it?

Well you can do a couple of things.

1.

Open the terminal at "Applications > Accessories > Terminal". Change the current working directory to /usr/share/games like this:
```

cd /usr/share/games

```

You can view the files in this directory by typing lowercase L lowercase S, like this:
```
ls
```

You can run the binary (executable) file like this:
```

./wormux

```

A dot, a slash, followed by the name of the file ( dot-slash means "look in the current directory for this file).

2.

If you would like to make a graphical menu item, open the menu editor by going to "System > Preferences > Main Menu" (it might be labelled "Menu Layout" on versions of Ubuntu before 7.04). Click on the "Games" section (or wherever you want it), select the "New Item"   button on the right. Name it "Wormux" (or whatever), and the command to run will be the location that you gave above for the binary file (/usr/share/games/wormux). Enter that info, then there should be a launcher in your menu.

3.

You could provide a "symbolic link" to /usr/share/games/wormux in your /usr/bin directory by typing this in the terminal:
```

sudo ln -s /usr/share/games/wormux /usr/bin/wormux

```
Enter your password when prompted. After you do this, all you will have to do is type "wormux" in the terminal, or type "wormux" in the Run Application dialog (press <Alt>+<F2> to access the Run Application dialog) to start the game.

---

### Post by Vuto on 2007-05-31
i tired making an application on the men u and wen i run it it comes up with "Failed to execute child process "/usr/share/games/wormux" (Permission denied)"

so i tired all the other stuff and keep coming up with password i type it in and it says incorrect password is there anyway i could see the password or change?

---

### Post by icechen1 on 2007-05-31
in a terminal tape:
Wormux and see if the game come out.
Some program installs but does not add itself in the application list.

---

### Post by Vuto on 2007-05-31
that doesnt make sense type clearer and dumb it down plz im super noob i just got ubuntu

---

### Post by icechen1 on 2007-05-31
> **Vuto said:**
> that doesnt make sense type clearer and dumb it down plz im super noob i just got ubuntu

Sometime,restart the computer and the new program magically appears!This happened to me sometimes.

---

### Post by icechen1 on 2007-05-31
Hello i got something,can you go to the application->add/remove and try to install Wormux there?I just install it there and it displays in the game menu.

---

### Post by jfinkels on 2007-05-31
> **Vuto said:**
> i tired making an application on the men u and wen i run it it comes up with "Failed to execute child process "/usr/share/games/wormux" (Permission denied)"

so i tired all the other stuff and keep coming up with password i type it in and it says incorrect password is there anyway i could see the password or change?

Can you post the output of typing this command from the terminal:
```
ls -l /usr/share/games
```
and also
```
ls -l /usr/share/games/wormux
```

---

### Post by Vuto on 2007-05-31
with ls "ls -l /usr/share/games" it came up with "
> total 8
drwxr-xr-x  2 root root 4096 2007-04-15 21:52 fortunes
drwxr-xr-x 13 root root 4096 2007-05-31 22:28 wormux
 

and with "ls -l /usr/share/games/wormux" it came up with
> total 100
-rw-r--r--  1 root root   459 2007-02-21 22:48 authors.dtd
-rw-r--r--  1 root root 18203 2007-02-21 22:48 authors.xml
drwxr-xr-x 15 root root  4096 2007-05-31 22:28 body
drwxr-xr-x  2 root root  4096 2007-05-31 22:28 game_mode
drwxr-xr-x  2 root root  4096 2007-05-31 22:28 gfx
-rw-r--r--  1 root root   637 2007-02-21 22:48 graphism.dtd
-rw-r--r--  1 root root  7535 2007-02-21 22:48 graphism.xml
drwxr-xr-x  3 root root  4096 2007-05-31 22:28 interface
drwxr-xr-x 29 root root  4096 2007-05-31 22:28 map
drwxr-xr-x  3 root root  4096 2007-05-31 22:08 menu
drwxr-xr-x  4 root root  4096 2007-05-31 22:28 music
drwxr-xr-x  2 root root  4096 2007-05-31 22:28 object
drwxr-xr-x  6 root root  4096 2007-05-31 22:08 sound
drwxr-xr-x 15 root root  4096 2007-05-31 22:28 team
drwxr-xr-x 32 root root  4096 2007-05-31 22:28 weapon
-rw-r--r--  1 root root   503 2007-02-21 22:48 weapons.dtd
-rw-r--r--  1 root root 10331 2007-02-21 22:48 weapons.xml
-rw-r--r--  1 root root   732 2007-02-21 22:48 wormux.desktop


and i checked the synaptic package managerand it is there

> data files for the game wormux
Wormux  is  a  free game where funny animals fight on a 2D map with funny
weapons. Though currently under heavy development, it is already
very playable, with lots of weapons (Dynamite, Baseball Bat, Teleportation,
etc.). For the moment, you can not play against computer opponents.

There are also lots of maps available for your battling pleasure!  Wormux
takes the genre to the next  level,  with  great  customisation
options  leading  to  great  gameplay. There is a wide selection of teams,
from the Aliens to the Chickens. Also, new battlefields can be
downloaded from the Internet, making strategy an important part of each battle.

This package contains data like maps and teams.  If you want to play the
game, you need to install the package wormux.

 Homepage: [http://wormux.org/](http://wormux.org/)

Does the 2nd last paragraph mean anything?

---

### Post by Vuto on 2007-05-31
help plz

---

### Post by jfinkels on 2007-06-01
> **Vuto said:**
> help plz

Patience, friend.

> **Vuto said:**
> with ls "ls -l /usr/share/games" it came up with "


and with "ls -l /usr/share/games/wormux" it came up with


and i checked the synaptic package managerand it is there



Does the 2nd last paragraph mean anything?

When you list the files and directories contained in /usr/share/games with "ls -l /usr/share/games", you see the letter 'd' at the very first position on the line containing 'wormux'? That means that's a directory. Since /usr/share/games/wormux is a directory, it is most certainly not the executable binary file you are looking for. This is what I recommend doing: uninstall wormux because you installed it manually with a .deb file. Type the following in the terminal:```
sudo dpkg -r wormux
```

Next, install it from the official Ubuntu repositories using Synaptic Package Manager, or simply by typing this:
```
sudo aptitude install wormux
```
(which is much easier).

Next, type the following in the terminal:
```
wormux
```

If that doesn't work, come back.

---

### Post by Vuto on 2007-06-02
thnx so much u rock

---

### Post by smallz on 2007-06-02
what the ****? this is kinda silly, i download a game and it takes forever and then you gotta do all this **** just to play. Cant you just run the ******* thing? I kinda hate Ubuntu.

---

### Post by jfinkels on 2007-06-02
> **smallz said:**
> what the ****? this is kinda silly, i download a game and it takes forever and then you gotta do all this **** just to play. Cant you just run the ******* thing? I kinda hate Ubuntu.

No, you don't have to go through all this, all you have to do is type the following in the terminal:
```

sudo aptitude install somegame

```
and then once it's installed and downloaded, just type the following to start it:
```

somegame

```

See more info on installing programs here: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by rickycodie on 2007-06-02
really you have to get used to the fact that Ubuntu is not windows. there is a lot less graphical interface. meaning that not everything has a picture that you can click and it works.  if you want that you can get automatix which can install a debian menu under Applications. the debian menu will keep track of everything that is installed on your computer, and then give you a one click start. the difference is that most of us consider typing a command easier than hunting through gui's(graphical user interface). but if you like that, it's cool, at least your not using windoze.

---

### Post by Lucifiel on 2007-06-02
No offense. But a lot of users start to hate Linux after they face a long string of problems like accidentally overwriting their system files, accidentally installing the wrong drivers, etc.

But you're giving up after something minor like this? :p 

Ubuntu is NOT Windows. Ubuntu belongs to Linux. Linux is an operating system which is much more powerful than Windows if you put in the effort to master it. 

As it is said, you do not master a skill if you don't persevere. You must have persevered and put in effort to learn Windows, which was why you were able to use it.

So, put in the same effort for Linux and you will be fine.

---

### Post by dkaddict on 2007-06-02
All games I use can be found in /usr/bin

The corresonding command in /usr/bin is usually esy to find if one knows the name of a given game. I have always added them to the 'games' drop down menu in menu editor and used the /usr/bin path.

Make sense?

Does 2 me anyway

---

### Post by weblordpepe on 2007-06-02
Yeah software in Linux is typically installed to more than one directory. Its a bit awkward, really. Especialy for ex-windows nubs.

But don't be put off by this. My job is at a helpdesk. Beleive me...Windows is not any better in the 'why doesnt it work, what do I do?' department. I WISH I could just give someone something to copy-paste and it magically fixes stuff.

Some times the GUI is NOT the easy way.

---

