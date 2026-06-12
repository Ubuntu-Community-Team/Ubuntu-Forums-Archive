---
title: "Moving from Windows XP to Ubuntu:  This in XP is now THIS in Ubuntu"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Morthane on 2005-11-16
This sounds a bit similar to the "need a program" thread, but I want to be a bit more encompassing.

I think there's stuff posted elsewhere, but I would expect a sticky in this section of the forum that answers the basic questions on the average day in Ubuntu, and goes something like this:


**Windows**
The important folders are My Documents, Windows, Program Files, ....
The root of my hard drive is C:
I install programs by clicking the *.exe file
I uninstall programs by going to "add/remove programs"
important keyboard shortcuts are...
when something messes up, I use the task manager to kill it

**Ubuntu**
The important folders are..
The root of my hard drive is...
I install programs by...
I uninstall programs by...
important keyboard shortcuts are...
when something messes up, I ...

i think this would allow everyone a starting platform.  At least for me, the most intimidating aspect is moving away from the windows directory structuring.  Anyone want to roll out on this or provide a sticky thread with a redirect to these answers?

---

### Post by Kyral on 2005-11-16
[quote=Morthane]This sounds a bit similar to the "need a program" thread, but I want to be a bit more encompassing.

I think there's stuff posted elsewhere, but I would expect a sticky in this section of the forum that answers the basic questions on the average day in Ubuntu, and goes something like this:


**Windows**
The important folders are My Documents, Windows, Program Files, ....
The root of my hard drive is C:
I install programs by clicking the *.exe file
I uninstall programs by going to "add/remove programs"
important keyboard shortcuts are...
when something messes up, I use the task manager to kill it

**Ubuntu**
The important folders are..
The root of my hard drive is...
I install programs by...
I uninstall programs by...
important keyboard shortcuts are...
when something messes up, I ...

i think this would allow everyone a starting platform. At least for me, the most intimidating aspect is moving away from the windows directory structuring. Anyone want to roll out on this or provide a sticky thread with a redirect to these answers?[/quote]

The important folders are... For you /home. For the system, /etc, /usr, /boot, /var. 

The root of the hard drive... there isn't one per say. At least in that style. The root of the FILESYSTEM is /

When you want to install something. Use Apt or Synaptic (Same way to remove)

When something goes wrong, call us :D

I have a kickass tutorial that goes over some terminal basics and how to handle Apt-Get (The most awesome way to install stuff EVER :D)

---

### Post by mpettitt on 2005-11-16
Important folders are /home/, / (can't really divide it into OS and system, as there is too much overlap)
Root of hard drive is /
Install programs with Synaptic, or by downloading a *.deb file, right clicking, then choosing "Install"
Uninstall programs with Synaptic
Important shortcuts are dependent on the programs you are using, just as in Windows
When something messes up, open a Console, and type "pkill progname", where progname is the name of the task (tab for a list of current processes, assuming you have Bash tab-complete installed)

---

### Post by kruz on 2005-11-16
[QUOTE=Morthane]This sounds a bit similar to the "need a program" thread, but I want to be a bit more encompassing.

I think there's stuff posted elsewhere, but I would expect a sticky in this section of the forum that answers the basic questions on the average day in Ubuntu, and goes something like this:


**Windows**
The important folders are My Documents, Windows, Program Files, ....
The root of my hard drive is C:
I install programs by clicking the *.exe file
I uninstall programs by going to "add/remove programs"
important keyboard shortcuts are...
when something messes up, I use the task manager to kill it

**Ubuntu**
The important folders are..not 100% positive /home/(usrname)
The root of my hard drive is.../
I install programs by...sudo apt-get install (name of program)
of if you manually download them
sudo dpkg -i blah.i386(ithinkthatsurpro).deb

you can of course compile everything through
./configure && make && make install
but using dpkg and apt-get is easy
if you want to delete them
sudo dpkg -u package.deb
sudo apt-get (cant remember name) i think its delete
sudo apt-get delete (program)
I uninstall programs by...sry i mixed that in with the upper question

important keyboard shortcuts are...

when something messes up, I ...always make backup files before
for example
you wana edit
sources.list which i expect u to do
as there prolly not unticked
sudo cp sources.list sources.list.bak
sudo gedit sources.list

i think this would allow everyone a starting platform.  At least for me, the most intimidating aspect is moving away from the windows directory structuring.  Anyone want to roll out on this or provide a sticky thread with a redirect to these answers?[/QUOTE]

come ot think of it
i could use some directory structuring classes also
because im so addicted to apt-get lol

---

### Post by Kyral on 2005-11-16
*makes a note to explain the Filesystem in his next Terminal for Beginners*

---

### Post by kruz on 2005-11-16
[QUOTE=Kyral]*makes a note to explain the Filesystem in his next Terminal for Beginners*[/QUOTE]


lol i can help
but i also need to learn some
thanx again for saving me kyral lol

---

### Post by Morthane on 2005-11-16
I started to think "wouldn't it be great to just have a thread that lists the howto's and FAQ guides as links?" but realized that is pretty unmanageable and seems like I'd be recreating the official wiki... Instead, perhaps there can be a section of the forum that is devoted ONLY to HOWTO posts.  The HOWTO's can be however big or small it takes to handle a topic, etc.


In regards to my previous posts,  I was trying to find exact correlations - especially when it came to the directories, like My Documents = 'X'

of course, there isn't exacts, but the tasks are the same ("I want to do this..")

> when something messes up, I ...always make backup files before
for example
you wana edit
sources.list which i expect u to do
as there prolly not unticked
sudo cp sources.list sources.list.bak
sudo gedit sources.list

I was thinking more along the lines of "kill 9 task" or whatever the command is..

---

### Post by kruz on 2005-11-16
oh
psmod

find ur process
i think its psmod -c? or -e to list all processes going on
towards the bottom will be your processes that ur running or just opended
and BE CAREFUL
pkill (process id)
is a good command, sends sigterm to the process
and the process will delete temps and close
however
the -9 command, use sparangly this is an extremely powerful command
pkill -9 or kill -9 id
will send sigkill i believe which will automatically just stop responding to the program and exit it

but it pkill and kill wont work
-9 is a good alternative

also look for GNU bases task managers
i saw one that installs and u just hit
ctrl+alt+del
thats the only function i miss of M$

---

### Post by canuck45 on 2005-11-16
I know the feeling.  I can find what I need in windows but in linux, where is everything hiding.  Where should I put files and how do I get them.

ie type apt-get  install  Well that tells me absolutely nothing....
open a terminal window and then type apt-get install...

some people forgot how intimidating linux can be with all these command prompts and everything.  Its improved vastly (1000%, thank you ubuntu) but is still a little tough at times for us newbies.  Only took me 2 hrs to get java working in firefox and when I thought I had everything done firefox wouldn't launch.  Went back in a rm'd my symbolic links  (ln -s /home/adrian/Desktop/Programs/jre1.5.05/plugin/i586/ns7-gcc29/libjavaplugin_oji.so and had to change it to  (ln -s /home/adrian/Desktop/Programs/jre1.5.05/plugin/i586/ns7/libjavaplugin_oji.so 
Like that was obvious  hahahahahaha


ie I downloaded jre (Java runtime environment) and saved it to a folder on my desktop.  Then tried to install and configure.  Do I leave it in the folder I downloaded it to, do I put it in /usr/local or in /bin or or or and then I had to find mozilla/plugins someplace to create a symbolic link.  After going through dozens of /usr/bin or usr/local/bin or usr/usr/usr/home/usr/bin/local/mozilla/plugins......I installed everything in /home/adria/Desktop/Programs/jre1-0_5 or something like that.  If any linux expert ever has to work on my machine good luck  LOL

So where should I store downloaded binaries, what directory is recommended to install them too or is it completely up to each user.  ie, should the java and realplayer both be installed to /usr/bin or usr/local or or or.

Regardless with all the trials and tribulations, this is REALLY a GREAT forum and lots of helpful answers....just so worried about doing the wrong thing and killing linux.  Maybae if I delete windows from my harddrive (dual boot) I wouldn't have the opportunity to fall back and have to learn more and more quickly.  

ps, I lost my dualboot when I upgraded but managed to find grub and menu.lst and put in the correct values to have windows available again, it disappeared during my upgrade...found the answer in the forums.....YEAH you guys are great!

---

### Post by kruz on 2005-11-16
no
think of the ./configure && isntall process as executing exe's in windows
or installing programs

open the folder where u extracted the tar file

type

./configure && make && make install

ie for u
apt-get is a simple program, well not simple, but simple to use program
that when u type a program it goes to the website sources listed in sources.list
and finds that package

so type

sudo apt-get install gftp

and itll download the package, upon, verifiy dependencies, and compile and install the package, right before ur eyes

then just type gftp to open it

---

### Post by BobSongs on 2005-11-17
I think with distributions like Ubuntu/Kubuntu/Edubuntu dual-booters will increase and they're going to want to find out how to make their way around this new and somewhat puzzling system. Of course it isn't as puzzling to those who've used it for quite some time. And we new users are grateful for such posts as the [Breezy Customization Guide]("http://doc.gwos.org/index.php/BreezyCust").

Linux's learning curve is steeper. Ubuntu Forums is well-organized and the answers are friendly, patient and very informative.

Thanks guys.

Bob

---

### Post by jpkotta on 2005-11-17
[QUOTE=canuck45]I know the feeling.  I can find what I need in windows but in linux, where is everything hiding.  Where should I put files and how do I get them.[/QUOTE]

I prefer to think of everything being at the same level of obscurity.  Or everything being at the same level of clarity, if you're a glass-is-half-full sort of person.

[QUOTE=canuck45]ie I downloaded jre (Java runtime environment) and saved it to a folder on my desktop.  Then tried to install and configure.  Do I leave it in the folder I downloaded it to, do I put it in /usr/local or in /bin or or or and then I had to find mozilla/plugins someplace to create a symbolic link.  After going through dozens of /usr/bin or usr/local/bin or usr/usr/usr/home/usr/bin/local/mozilla/plugins......I installed everything in /home/adria/Desktop/Programs/jre1-0_5 or something like that.  If any linux expert ever has to work on my machine good luck  LOL

So where should I store downloaded binaries, what directory is recommended to install them too or is it completely up to each user.  ie, should the java and realplayer both be installed to /usr/bin or usr/local or or or.
[/QUOTE]

I keep my downloaded binaries, .debs, source tarballs, etc., in ~/installed, which is basically what I used to do in windows.  It really doesn't matter where you keep stuff like that.  As for where to install things, almost always there is a default that will work well.  If there isn't, putting it in /usr is usually OK.  Another option is to install it to your home, e.g. ~/usr.

---

### Post by steve.horsley on 2005-11-17
[QUOTE=Morthane]I started to think "wouldn't it be great to just have a thread that lists the howto's and FAQ guides as links?" but realized that is pretty unmanageable and seems like I'd be recreating the official wiki... Instead, perhaps there can be a section of the forum that is devoted ONLY to HOWTO posts.  The HOWTO's can be however big or small it takes to handle a topic, etc.[/QUOTE]

Like this one, perhaps?
[http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by Morthane on 2005-11-17
OK, that's what I was looking for, but the word "customization" wasn't what I was thinking - that makes me think of changing your desktop image, making some sort of screensaver, etc.

What I saw offhand and really liked was Bobsong's link to [Linux Lessons]("http://www.linux.org/lessons/index.html"), but it isn't tailored to Ubuntu really.  If someone could reinvent the necessary parts of that doc for (k)ubuntu, it would be great.  Either that or create something like "A day in the life of Mr. Ubuntu as he does his basic tasks".  I know I can get howtos on doing amazing stuff, but I think there's a lot of people who want to just see how everyday life may be changed/improved in the realm of Ubuntu.  Mr. Ubuntu would install some programs, listen to some music, create some documents, burn an audio CD, send an email, maybe set up an account for his children, and maybe organize a few folders on the computer so he could store some digital pictures of the family... etc.

EDIT:  the rest of this post was forum creep, so I removed it.

---

