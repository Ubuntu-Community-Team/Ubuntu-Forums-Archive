---
title: "login as root?"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by zorlab on 2006-04-11
ok did my search but the info I found is not useful, remeber this is a beginners forum. A sugestion that was made was use the command "sudo"  errrr  well great but then what?? all it gives is otions for the parameters :-k 

I was kind of surprised, having install quite a few linux op sys's  that there was no option to make a root password.
So far a number of things I need to do, require, I beieve, root priveleges, like the simple task of installing flash player plugin for firefox. doing it otherwise did not work:mad: 

oh well,  any help would be appreciated

---

### Post by aysiu on 2006-04-11
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by The Mekon on 2006-04-11
It is possible to set up a root accont by clicking System > Aministration > Users and Groups,  enter you normal password,  enable "Show all users and groups".

Now you should be able to find the root user.

Double click on it to show the root user settings and enter a new password and confirm. Click OK

Now you can enter su in a terminal and then the password and walla you are logged in as the root user.

But why bother?   It can be very dangerous as you can easily wipe your system as root ( I have done it) and web surfing as root can also leave you machine open to attack (so I am advised).

Stick with sudo is my advice.

---

### Post by aysiu on 2006-04-11
[QUOTE=The Mekon]
But why bother?   It can be very dangerous as you can easily wipe your system as root ( I have done it) and web surfing as root can also leave you machine open to attack (so I am advised).[/QUOTE] There are pros and cons to the *sudo* model (as opposed to the *root* model), and they're outlined [here](https://wiki.ubuntu.com/RootSudo#head-6cfb89699f99dbeee57c81c64945454d6ded2fac). I believe the pros of *sudo* outweigh the cons, but it's definitely not cut and dry.

For me, *sudo* is better just for the convenience... at least *gksudo* and *kdesu* are might convenient.

---

### Post by zorlab on 2006-04-11
Ok let me see if I have this right.....     2 choices,  creat an admin (root) acount
or
 use [COLOR="DarkOrange"]gksudo nautilus[/COLOR]  ie. "Most new Linux users just want to be able to click and drag and drop. So these two new commands should be your new best friends...

If you're using Ubuntu (Gnome), the command you want is gksudo nautilus "

I tried the command line [COLOR="DarkOrange"]sudo[/COLOR] and got the following:

[B]While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/B]
As a directory appeared

Please  Now what?  :-?

---

### Post by ignorance on 2006-04-11
if you want to use sudo try sudo su for a change maybe that will work.

---

### Post by aysiu on 2006-04-11
*sudo* should be used with command-line commands.
*gksudo* should be used with graphical commands.

For example: ```
sudo apt-get update
``` ```
gksudo nautilus
```

---

### Post by dcstar on 2006-04-11
[QUOTE=zorlab]Ok let me see if I have this right.....     2 choices,  creat an admin (root) acount
or
 use [COLOR="DarkOrange"]gksudo nautilus[/COLOR]  ie. "Most new Linux users just want to be able to click and drag and drop. So these two new commands should be your new best friends...

If you're using Ubuntu (Gnome), the command you want is gksudo nautilus "

I tried the command line [COLOR="DarkOrange"]sudo[/COLOR] and got the following:

[B]While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/B]
As a directory appeared

Please  Now what?  :-?[/QUOTE]
"sudo" is for command line executables, gksudo is for graphical applications - if you used sudo for graphical stuff you get strange messages (like above).

---

### Post by zorlab on 2006-04-12
arrrrrg! 
Thanks all for yopur generous help onthis topic, but  still get permissin denighed after sucessfull root access  ( see below)

barry@SCSI:~$ sudo su
root@SCSI:/home/barry# cd Desktop
root@SCSI:/home/barry/Desktop# cd mpg123-0.59r
root@SCSI:/home/barry/Desktop/mpg123-0.59r# ./Makefile
bash: ./Makefile: Permission denied
root@SCSI:/home/barry/Desktop/mpg123-0.59r#


Trying to install a Mp3 player what is wrong above??

**Maybe I should just get the codecs or whatever you call the in Linux so I can use the included player, but then again why wouldnt Ubuntu have a working mp3 player,  by default???**

This getting frustrated, I had hoped to find a Linux that had cought up with MS Windows in "Ease of Use" - Wanna see some serious competition with Microsoft.

Perhaps I need to approach this another way, the Graphical way?  ~~> how?  what? where??

Any help is appreciated,  Thaks all. :-?

---

### Post by wylfing on 2006-04-12
Linux cannot legally come "out of the box" with working mp3 playback unless they pay royalties to the mp3 patentholders, which means passing that cost along to you. So, since you didn't pay any royalties, you aren't allowed to use the patented technology. Sorry to sound harsh, but it bothers me a lot when people say "Linux hasn't caught up to Windows in usability!" when they neglected to consider they haven't *paid* for Linux to do anything at all.

So, rants over. You shouldn't be trying to compile your own player (I assume mplayer or something like that). What you need to do is read this:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by zorlab on 2006-04-12
thanks wylfing   
I was not trashing Linux, just having great expectations and I am sure there is anMP3 plauer for Linux. Am I wrong??   Maybe I have to buy Mp3 rights, but I have done google searches for Linux mp3 players and come up with several that do not meantion any  problems.

One multimedia player, amaroK, I installed from the Add Aplications desktop utility, however this also will not play them.
BUT  I found here [http://amarok.kde.org/amarokwiki/index.php/MP3_on_Ubuntu_5.10](http://amarok.kde.org/amarokwiki/index.php/MP3_on_Ubuntu_5.10)
[COLOR="Purple"]the waytoget it to work :)[/COLOR]

---

### Post by Project 318 on 2006-04-12
[QUOTE=zorlab]arrrrrg! 
barry@SCSI:~$ sudo su
root@SCSI:/home/barry# cd Desktop
root@SCSI:/home/barry/Desktop# cd mpg123-0.59r
root@SCSI:/home/barry/Desktop/mpg123-0.59r# ./Makefile
bash: ./Makefile: Permission denied
root@SCSI:/home/barry/Desktop/mpg123-0.59r#
[/QUOTE]
I'm going to jump in and say you need to chmod it as executable before you can run it 
```
chmod +x filename
```
then you can run it.  Although, I don't think you're executing the file there. Run the configure script or simply run make.

---

### Post by zymbian on 2006-04-12
use command line -> sudo passwd root

---

### Post by wylfing on 2006-04-12
I think continuing to advise him on how to enable root is (ahem) moot. The solution to his particular compiling problem was to run 'make' not 'Makefile'. But as I said, it's much better to understand the legal restraints that Linux distributions are under and to learn how to work around them. He's not the first person in the world to want to play MP3 files on Linux :-)

---

### Post by zorlab on 2006-04-12
Thanks all for your suggestions...:D 

[COLOR="SeaGreen"]**Project 31**[/COLOR]8: I did as you suggested [COLOR="DarkOrange"]chmod +x Makefile[/COLOR] and then[COLOR="DarkOrange"] ./ Makefile [/COLOR]again....  this time the process started but with errors.  Also there was no '*Make*' file,
and there was no configure file as I have used before... There is a preconfigure dir in this application setup directory. With all this I figured Makefile was the logical next step.
** Should I have used other parameters? Inintiated another command?**
Any help is appreciated! ](*,)

here is what I got:
root@SCSI:/home/barry/Desktop/mpg123-0.59r# ./Makefile
./Makefile: line 8: PREFIX: command not found
./Makefile: line 9: PREFIX: command not found
./Makefile: line 18: nothing-specified:: command not found
./Makefile: line 19: @echo: command not found
./Makefile: line 20: @echo: command not found
./Makefile: line 21: @echo: command not found
./Makefile: line 22: @echo: command not found
./Makefile: line 23: @echo: command not found
./Makefile: line 24: @echo: command not found
./Makefile: line 25: @echo: command not found
./Makefile: line 26: @echo: command not found
./Makefile: line 27: @echo: command not found
./Makefile: line 28: @echo: command not found
./Makefile: line 29: @echo: command not found
./Makefile: line 30: @echo: command not found
[<----------the rest of the lines ---------->]
./Makefile: line 606: wav.o:: command not found
./Makefile: line 607: readers.o:: command not found
./Makefile: line 608: term.o:: command not found
./Makefile: line 614: clean:: command not found
./Makefile: line 617: prepared-for-install:: command not found
./Makefile: line 618: syntax error near unexpected token `then'
./Makefile: line 618: ` @if [ ! -x mpg123 ]; then \'

---

### Post by 3rdalbum on 2006-04-13
If you want to play MP3s, go into Synaptic and search for gstreamer. Install everything there. When you open Synaptic, you'll be asked for a password - that password is your normal user password. After the gstreamer stuff is installed, the Rhythmbox and Totem programs will be able to play MP3s. By the way, the gstreamer plugins are free (as in, they don't cost you anything).

In order to be able to compile from source, you must install the build-essential package.
```
sudo apt-get install build-essential
```

To compile whatever package you've got there, you don't execute the Makefile. You usually type the following commands into your terminal:

```

./configure
make
sudo make install

```

However, having said that, I don't recommend that you try compiling from source until you've been using Ubuntu for a month. The repositories definately have enough to keep you occupied until then :-)

---

### Post by ProjectGod on 2006-04-13
speaking of root accounts. i didnt want to start a new thread related to this ... sooo...

how can i set the root accounts password? is it the password that i had to input when initially installing ubuntu?? is the root account the first one i created during the installation process???

cheers.

---

### Post by steve.horsley on 2006-04-13
**zorlab**: Did you read the link wylfing gave you about restricted formats? The answers are all there, including the names of the packages to install. There really is no need to put yourself through the learning curve of compiling stuff this early on.

**ProjectGod**:  zymbian has already said that to change the root password, you can use **sudo passwd root**. The root password is disabled by default on install. Search the forum for "root password" and you will find plenty of explanations, including links to a web page that explains it. aysiu posted a link to such a page in this thread, but there are other pages too.

---

### Post by ProjectGod on 2006-04-13
cheers. :D

---

### Post by zorlab on 2006-04-13
yes yes yes, I get it,  thanks all no need for the player, just trying to figure out how to install a package through the terminal. 

**What I did do was find the thread on Automatix, and installed it**  !!!
All my Multimedia, (and then some) poblems solved~!!
[COLOR="Sienna"]Great effort on the part 0f those involved, Kudos :-D[/COLOR]

---

