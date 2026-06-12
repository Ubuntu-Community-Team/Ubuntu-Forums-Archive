---
title: "Whats this mean? What do I do?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by domromer on 2007-09-03
I am a brand new linux user and have already ran into some problems. When I go to download a file I get this error.

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

What should I do?

Remember I'm a long time windows user, so explain as simply as possible! Thanks.

---

### Post by pizzutz on 2007-09-03
open a terminal window and type

sudo dpkg --configure -a

---

### Post by irish_flu on 2007-09-03
Open up the terminal (it's under Applications ---> accessories).

Type
```

sudo dpkg --configure -a

```

Welcome to Linux, home of (sometimes) useful error messages!  :)

BTW the "sudo" part tells the computer "do this with root (administrator) rights".

---

### Post by Celegorm on 2007-09-03
Start off with following the suggestion in the error. Open up a terminal from applications->accessories->terminal. Type in or copy and paste ```
sudo dpkg --configure -a
``` and press enter. Type your password and press enter again. Your password will not echo to the screen, this is normal. Let it run until you get the command prompt back again (should look something like username@hostname:~$) and then see if that's fixed the problem.

---

### Post by pizzutz on 2007-09-03
ahh, I remember the first time I got that error message.  It said "type this" I typed it, It said I didn't have permission to type it.  I barely knew enough to know that meant I had to type sudo first..  I did it again, and It solved my problem.  That was about when I fell in love with linux.

---

### Post by domromer on 2007-09-03
Wow you guys are really fast, so I typed that command in and everything seemed to go ok. but now when I select a highlight a game to download, the the cursor keeps running the spinning ( thinking) icon and won't let me click on anything to begin the download.

---

### Post by pizzutz on 2007-09-03
can you click on the details tab to see what is happening?  Where is it freezing?  if you know the package name, try installing it manually from the terminal using

sudo apt-get install <package name>

---

### Post by domromer on 2007-09-03
here is a screen shot, When I get to these stage the cursor just keeps rotating like it's doing something, but if I press ok, the whole window dissapears.

[[IMG]http://img339.imageshack.us/img339/3858/screenshottv6.png[/IMG]](http://imageshack.us)

---

### Post by pizzutz on 2007-09-03
hmmm ok, try this.  open a terminal window again and type the following

```
sudo apt-get install kbounce
```
You will need to close synaptic first.  Post the output if it doesn't work.  It will help to see if there are any errors through the terminal.  (you may just need a restart to get synaptic running again)

---

### Post by domromer on 2007-09-03
> **pizzutz said:**
> can you click on the details tab to see what is happening?  Where is it freezing?  if you know the package name, try installing it manually from the terminal using

sudo apt-get install <package name>

Tried what you said, here is what I got.

dan@dan-desktop:~$ sudo apt-get install <KBounce>
bash: syntax error near unexpected token `newline'
dan@dan-desktop:~$ sudo apt-get install <KMines>
bash: syntax error near unexpected token `newline'
dan@dan-desktop:~$

---

### Post by domromer on 2007-09-03
> **pizzutz said:**
> hmmm ok, try this.  open a terminal window again and type the following

```
sudo apt-get install kbounce
```
You will need to close synaptic first.  Post the output if it doesn't work.  It will help to see if there are any errors through the terminal.  (you may just need a restart to get synaptic running again)

Ok, I think I'm already over my head.

I tried what you said to do and here is what I got

If id did download, it's not in my games folder.

dan@dan-desktop:~$ sudo apt-get install kbounce
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kbounce: Depends: kdelibs4c2a (>= 4:3.5.5-1) but it is not going to be installed
           Depends: libarts1c2a (>= 1.5.0-1) but it is not going to be installed
           Depends: libkdegames1 (>= 4:3.5.5) but it is not going to be installed
           Depends: libqt3-mt (>= 3:3.3.8) but it is not going to be installed
  sun-java5-bin: Depends: sun-java5-jre (= 1.5.0-11-1ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dan@dan-desktop:~$

---

### Post by wormser on 2007-09-03
> **domromer said:**
> Tried what you said, here is what I got.

dan@dan-desktop:~$ sudo apt-get install <KBounce>
bash: syntax error near unexpected token `newline'
dan@dan-desktop:~$ sudo apt-get install <KMines>
bash: syntax error near unexpected token `newline'
dan@dan-desktop:~$

Take out the brackets <>

```
sudo apt-get install KBounce
```

Update:

With the error now run:

```
apt-get -f install
```

---

### Post by cookies on 2007-09-03
> **domromer said:**
> Tried what you said, here is what I got.

dan@dan-desktop:~$ sudo apt-get install <KBounce>
bash: syntax error near unexpected token `newline'
dan@dan-desktop:~$ sudo apt-get install <KMines>
bash: syntax error near unexpected token `newline'
dan@dan-desktop:~$


... without the <>

---

### Post by pizzutz on 2007-09-03
don't put <> around them.  that was just to indicate text that should be replace with your actual packages

---

### Post by pizzutz on 2007-09-03
Don't worry we will get there.  Post the output of this command

```
cat /etc/apt/sources.list
```

---

### Post by domromer on 2007-09-03
ok, still having no luck. Here is what it says now

dan@dan-desktop:~$ sudo apt-get install KBounce
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package KBounce
dan@dan-desktop:~$

---

### Post by pizzutz on 2007-09-03
That is because linux is case sensitive.  kbounce is a package, KBounce is not

---

### Post by waggygee on 2007-09-03
> **domromer said:**
> Ok, I think I'm already over my head.

I tried what you said to do and here is what I got

If id did download, it's not in my games folder.

dan@dan-desktop:~$ sudo apt-get install kbounce
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kbounce: Depends: kdelibs4c2a (>= 4:3.5.5-1) but it is not going to be installed
           Depends: libarts1c2a (>= 1.5.0-1) but it is not going to be installed
           Depends: libkdegames1 (>= 4:3.5.5) but it is not going to be installed
           Depends: libqt3-mt (>= 3:3.3.8) but it is not going to be installed
  sun-java5-bin: Depends: sun-java5-jre (= 1.5.0-11-1ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dan@dan-desktop:~$

Now, excuse me if I am mistaken but isn't KBounce for KDE desktops? Isn't he using a Gnome desktop? I expirience the same thing when  I tried installing Kaffiene but the I installed KDE later and found that Kaffiene worked properly

---

### Post by domromer on 2007-09-03
> **pizzutz said:**
> Don't worry we will get there.  Post the output of this command

```
cat /etc/apt/sources.list
```

here is what you wanted

dan@dan-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
dan@dan-desktop:~$

---

### Post by pizzutz on 2007-09-03
Nah, it shouldn't matter.  I checked. I installed kmines and kbounce without the kubuntu-desktop package with no problems.

---

### Post by domromer on 2007-09-03
none of this is working, I think part of the problem is that I am just doing what you guys are telling me to do. I have no idea what it is I'm actually doing. It's like your speaking french. I know your talking but what are you saying?? 

I think I need to start at square 1. What should I begin reading so I have some notion of what is going on?

Also How can I get my regular add/remove programs app to start working again. it's still just spinning/thinking when i try to add a program.

---

### Post by waggygee on 2007-09-03
> **domromer said:**
> Ok, I think I'm already over my head.

  kbounce: Depends: kdelibs4c2a (>= 4:3.5.5-1) but it is not going to be installed
           Depends: libarts1c2a (>= 1.5.0-1) but it is not going to be installed
           Depends: libkdegames1 (>= 4:3.5.5) but it is not going to be installed
           Depends: libqt3-mt (>= 3:3.3.8) but it is not going to be installed
  sun-java5-bin: Depends: sun-java5-jre (= 1.5.0-11-1ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dan@dan-desktop:~$

Have you tried using Synaptic to install the libs it depends on, because aparently you don't have them. Open Synaptic then search for and install kdelibs4c2a, libarts1c2a, libkdegames1, libqt3-mt, sun-java5-jre.... just tick the box next to the packages for installation then click apply

---

### Post by Outrunner on 2007-09-03
Or you can install these deps with the terminal

```
sudo apt-get install kdelibs4c2a libarts1c2a libkdegames libqt3-mt sun-java5-bin sun-java5-jre
```

Then you can try installing kbounce again
```

sudo aptitude install kbounce
```

---

### Post by pizzutz on 2007-09-03
Sorry man, I'm not trying to confuse you, I'm just trying to figure out what is wrong.  Your add/remove programs app is a front end for a program called apt-get.  apt-get often provides more useful error messages that the program does.  In this case the programs you are trying to install require libraries that should be automatically installed with the program, but for some reason they are not being installed.  I'm just trying to figure out why.  The file I had you post shows me that you have all the necessary ports installed to get the files.  Are you able to click the reload butting in your add/ remove programs app?  That will reset the available file list.

the info on installing software that you requested is here

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by domromer on 2007-09-03
> **pizzutz said:**
> Sorry man, I'm not trying to confuse you, I'm just trying to figure out what is wrong.  Your add/remove programs app is a front end for a program called apt-get.  apt-get often provides more useful error messages that the program does.  In this case the programs you are trying to install require libraries that should be automatically installed with the program, but for some reason they are not being installed.  I'm just trying to figure out why.  The file I had you post shows me that you have all the necessary ports installed to get the files.  Are you able to click the reload butting in your add/ remove programs app?  That will reset the available file list.

the info on installing software that you requested is here

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

No, you guys are great. I've made some progress, my add/remove has started to work again. I also learned there is more than one way to download apps. I'm going to do some more reading on linux, so I have some notion as to what is going on. Could you guys reccomend a good basic book for first time Ubuntu users?

---

### Post by Lord Illidan on 2007-09-03
There are books available for Ubuntu, but sticking around in these forums and in the Ubuntu Wiki offers just as much help if not more.

You seem to have the right frame of mind - not quitting after the first few problems or so, like some newcomers here, so Welcome to Ubuntu, and hope you enjoy it!

---

### Post by waggygee on 2007-09-03
> **domromer said:**
> No, you guys are great. I've made some progress, my add/remove has started to work again. I also learned there is more than one way to download apps. I'm going to do some more reading on linux, so I have some notion as to what is going on. Could you guys reccomend a good basic book for first time Ubuntu users?

Well, Ubuntu comes with a pretty usefull help document that covers alot. On default it apears as a question mark on the panel. Click it, then read. or you might want to read a little from here [http://www.linuxlots.com/~jam/](http://www.linuxlots.com/~jam/) another site that realy helped me (and still does) is [http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)

---

### Post by Outrunner on 2007-09-03
[Here you go]("http://www.linuxcommand.org/learning_the_shell.php") :) It's not specifically for Ubuntu, but it's still a very useful howto for learning the basics of the terminal. It's how I learned. Have fun!

---

