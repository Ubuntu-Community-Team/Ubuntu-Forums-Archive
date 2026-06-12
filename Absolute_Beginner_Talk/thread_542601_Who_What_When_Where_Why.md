---
title: "Who? What? When? Where? Why?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Shoot3r101 on 2007-09-04
Hi I *just* installed ubuntu and so far everything is going good. I'm understanding beryl and all the cool features that ubuntu has to offer! Then when I go to download something thats when im stuck. I am from windows; I was *born* in windows since I was a kid and now I have no clue as to where "My Documents" is located and where "C:\" is since I switched to linux. And if someone could please tell me what the basic files are(such as in windows it was .exe executable). I am a newbie(only at Linux >.>) but at least I admit that ;)...

---

### Post by mikeyphi on 2007-09-04
> **Shoot3r101 said:**
> Hi I *just* installed ubuntu and so far everything is going good. I'm understanding beryl and all the cool features that ubuntu has to offer! Then when I go to download something thats when im stuck. I am from windows; I was *born* in windows since I was a kid and now I have no clue as to where "My Documents" is located and where "C:\" is since I switched to linux. And if someone could please tell me what the basic files are(such as in windows it was .exe executable). I am a newbie(only at Linux >.>) but at least I admit that ;)...

Have a look here: [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by mlentink on 2007-09-04
I would try and read [this]("http://help.ubuntu.com") first. Secondly, reading the stickies in this forum will help you (I know they did help me!)

---

### Post by hyper_ch on 2007-09-04
Also have a read here:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

and here:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

and here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

That should answer quite a few questions :)

---

### Post by Shoot3r101 on 2007-09-04
I C. Thanks for help guys...

---

### Post by Shoot3r101 on 2007-09-04
Okay after reading all that none seemed to help my issue. I need help understanding directory's (such as C:\Documents and Settings\Shooter\My Documents) and the basic files that Linux supports(such as in windows the main program file was .exe "Executable").

---

### Post by Anzan on 2007-09-04
The file system in Linux is completely different than Windows.

Your Home folder is where your stuff goes. The executables will tend be in /bin.

Create folders in your home folder for documents, sound files etc. Call them whatever you want. Nautilus (the file manger) will be able to find them.

Just install from Add/Remove or Synaptic for the time being.

It will all make sense soon.

---

### Post by Tyke91 on 2007-09-04
alright :) quick explanation on how the file system works 

everything is based off of the "   /   " file, also called root. from there you can go into different directories. 

the biggest directories to worry about are /home (this is where you will store most of your stuf-  it is your "my documents" folder.  /etc is also handy (you can configure xorg.conf from here... useful for fixing grapics issues)  /bin is where you can find files created by the debian/ubuntu linux equivilent of .exe (.deb) as well as basic commands for your computer.  /usr is where you will find many user related things like games and such. finally, /media is where you can find CDs. extra hard drive partitions, and anything else that you "plug in"


you cannot usually run .exe files, the equivalent is a .deb file (or .rpm , but you will need a program called alien to convert it into a .deb)

you will mostly NOT NEED to use .deb files, because the ubuntu "Add/Remove" programs list actually ADDS PROGRAMS! there is a huge online repository of programs (called the repos) that all run on ubuntu.


here's a picture of the system
[http://www.oreilly.com/catalog/debian/chapter/book/figs/deb.0403.gif](http://www.oreilly.com/catalog/debian/chapter/book/figs/deb.0403.gif)

it's incomplete... there are a few others as you can see :)

---

### Post by Paul133 on 2007-09-04
Unlike Windows, there are not different drives in Linux. There's only one super drive, "/", root. You probbaly want to store your files in /home/YOURUSERNAME. Files on your desktop are in /home/YOURUSERNAME/Desktop. 

Note that Linux slashes (like those used on the web) are / while Windows slashes are \. Don't confuse them.

Most of your programs will be in /usr/bin, some important ones (necessary for runing Linux) wil be in /bin. If you want to browse your files, go to Places -> Computer and then click on filesystem. There, you can browse all your files.

Another very important part of Linux is the terminal. You can access this by going to Applications -> Accessories -> Terminal. It's probably a good idea to drag this into the tray, too, so you have easy access to it. The terminal is like the Windows commandline, but much more powerful. In fact, all of the graphics you have in Ubuntu right now are running on top of the commandline. If you're having a problem and someone says to you to type ```
ls -l
``` what they mean is that they want you to opena terminal, type whatever is in the code box and then hit enter. By the way, that command will list all the files or directories in your current directory (a directory in Linux is a folder in Windows; same thing, different names). 

To make a code box, just do open one with ['code'] and close it with ['/code'] without the quotes but with the brackets. It's vB code, similar to HTML but for forums.

THis may seem like a lot, but don't worry; you'll get the hang of it. Just post on the forums if you need any help. Good luck with Ubuntu!

---

### Post by MozartlovesUbun2 on 2007-09-04
I thought I'ld be up and running in no time when i switched from windows to ubuntu, streaming / ripping / burning / gaming / getting the iPod synced / converting video formats / mounting virtual CD's, etc.... but that was a wrong idea,

it took a little time to learn all the basic stuff

it's frustrating sometimes, but there's not much reason to cry, the forum here is great and there's lots of info on the web.

just read up a little here at the forum from time to time and tackle one problem at a time, I found this a whole lot easier, if you have a hoard of questions, make a note of them and strike them out one by one :)

also if you wanna run some apps that are non existent in ubuntu, you can run them in Wine, Cedega or CrossOver, or otherwise run windows itself in VMWare.

---

### Post by steveneddy on 2007-09-04
> **MozartlovesUbun2 said:**
> I thought I'ld be up and running in no time when i switched from windows to ubuntu, streaming / ripping / burning / gaming / getting the iPod synced / converting video formats / mounting virtual CD's, etc.... but that was a wrong idea,

it took a little time to learn all the basic stuff

it's frustrating sometimes, but there's not much reason to cry, the forum here is great and there's lots of info on the web.

just read up a little here at the forum from time to time and tackle one problem at a time, I found this a whole lot easier, if you have a hoard of questions, make a note of them and strike them out one by one :)

Great advice, Mozart - OP - just take baby steps ans you will get there faster than you would imagine.

BTW - thanks for the bean!

---

### Post by oldos2er on 2007-09-04
Linux doesn't use drive letters. Google "linux directory structure" and you'll find more info.

---

### Post by mikewhatever on 2007-09-04
> **Shoot3r101 said:**
> Okay after reading all that none seemed to help my issue. I need help understanding directory's (such as C:\Documents and Settings\Shooter\My Documents) and the basic files that Linux supports(such as in windows the main program file was .exe "Executable").

The equivalent of C:\Documents and Settings\ in Linux is /home/your-usernamme. There is no My Documents or Pictures, videos, etc, but you can create the folders you want yourself. For instance, I have Pics, Downloads and Text files along with a few more.
More on filesystem [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
The equivalent of an .exe in Ubuntu is a .deb.

PS: Could you not have come up with a better thread title then 'Who? What? When? Where? Why?'? First, you forgot which, second, read this [http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/](http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/)

---

### Post by Error403 on 2007-09-04
If there is more than one person using the computer and you want to give each person it's profile (like in Windows), I suggest creating a /pub directory and put all the common data files like pictures, music and movies in there to reduce redundancy.  Then I ln -s the /pub directory to each user's home directory so everyone gets something like /home/user/pub/ and that's really useful.

---

### Post by hyper_ch on 2007-09-05
just some small addons:

I'd rather compare .deb files with .msi ;)

Whether you can execute a file or not does not depend on its ending but on the file permissions it has...

---

### Post by alienexplorers on 2007-09-05
Here is a chart showing the basic linux file structure:
[IMG]http://img95.imageshack.us/img95/8707/linuxfilestructurewd0.jpg[/IMG]

---

### Post by freesitebuilder on 2007-09-05
Here are my Ubuntu bookmarks - I switched in April, and they include a lot of "how-to" pages. Hope you're enjoying Ubuntu as much as I am!
[http://memo.yoono.com/buzzlog/links.jsp?login=freesitebuilder](http://memo.yoono.com/buzzlog/links.jsp?login=freesitebuilder)

---

### Post by nilufer on 2007-09-05
hi. why don't you have a look at the ubuntu desktop guide. it starts with basic concepts such as linux file structure, what reside in each directory. explains what are the applications mostly used. for example for multimedia totem player, for graphics gimp, browser firefox .. etc.

also to get done some other things. for example you cant play mp3 files once u install ubuntu ( coz it is proprietary so it is not directly included in ubuntu ) . but default player plays excellent open formats such as ogg,  flac and so. so you can rip your audio cds to these formats. but if you already got mp3s, you have to get mp3 support to ur ubuntu. of course it is possible. the guide shows you how to get done that. and also many other supporting applications those won't be installed by default. and some customizations and making ubuntu looks good.

here is the link to the ubuntu desktop guide.
[https://help.ubuntu.com/pdf/ubuntu/C/desktopguide.pdf]("https://help.ubuntu.com/pdf/ubuntu/C/desktopguide.pdf")

and also i got some help from softpedia.com. for example 'how to manage ur partitions in linux' which are common for every linux distribution. but it is not ubuntu specific.
 so have a good life with ubuntu.

---

### Post by sailor2001 on 2007-09-05
surprised nobody mentioned in places/homefolder if you ctrl/h you see all your hidden files

---

### Post by erfahren on 2007-09-05
I like that chart up there. first time I've ever seen that.

I liked this tutorial: [http://www.linux.org/lessons/index.html](http://www.linux.org/lessons/index.html)

---

### Post by Shoot3r101 on 2007-09-05
Thank you thank you guys I really appriciate all the help.

---

