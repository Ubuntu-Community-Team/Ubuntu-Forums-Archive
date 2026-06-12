---
title: "just migrated from xp. can i use ANyTHING?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by mikhsoj on 2007-11-26
ive been using xp since its release and swear by it today, however, i recently got a job as a computer tech so i feel like i must learn how to run linux. figured this would be a less painful way to start.

seems like i dont understand it at all. i installed it and stared at the desktop for 20 minutes. :confused:

so anyways, i decided to plug in my external hard drive, and got an error saying that i cant boot the HDD cuz of improper removal. tried using terminal to do the force mount thing but got an error that said "must be done in root" or something.
however i solved it by going to my pc and safely remove hardware on my hdd. then linux recognized it.

so i tried running some programs on it. hahahaha.. nothing works. exiting. so here goes the real questions:
does linux require a virus scanner? is it like windows where it has vulnerabilities that trojans, spyware whatnot can take root in?

is there a way to install windows (.exe) files? i read somtehing about sudo or wine or something but still dont understand it.

is there a list of terminal commands? i know ubuntu 7.10 is supposed to limit terminal use but i might wanna learn it anyways.

is this similar to unix? or is learning unix a whole world of difference?

where is the penguin?

---

### Post by bluepowder7 on 2007-11-26
i can't say much to most of your questions, but as far as i know the penguin is out shagging the butterfly in a most unspeakable way.

linux is similar to unix, so once you learn one it probably won't be a big jump to learn the other.  as for a list of commands, there's a few posts / threads around here that list the common commands, and you can likely find them in a linux-for-dummies book.

.exe files won't work here the same way .deb packages won't work in winxp.  you can use wine or some other layer to run windows type stuff within linux, but i've never tried it.



ps - LINUX - **L**inux **I**s **N**ot **U**sed like **X**p

---

### Post by FuturePilot on 2007-11-26
No Antivirus required:) Linux doesn't get hit with viruses and spyware and such like Windows does. You can read more on Ubuntu and security here
[http://www.psychocats.net/ubuntu/security]("http://www.psychocats.net/ubuntu/security")

You can get certain Windows applications to work through Wine. It's basically a compatibility layer. Though success with it is kind of hit and miss. I would suggest looking for a native Linux equivalent before installing something under Wine.

I know there's some sites that list a whole bunch of terminal commands but I can't think of any off the top of my head.

Yes, Linux is based off of Unix after all ;)

The penguin is right here
[IMG]http://www.greentree.com/newsletters/november_04/images/linux-penguin.JPG[/IMG]

:lolflag:

And welcome to the Ubuntu community :D

---

### Post by scrooge_74 on 2007-11-26
Lots of questions, welcome aboard.

Linux comes from Unix, most commands came from there, is very usefull to know your way in the command line.
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/linux-basics.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/linux-basics.html)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

You can run certain windows programs using wine or Cross Over Office
[http://winehq.com](http://winehq.com) they have list of which programs run and which does not

Virus scanner is only needed if you are running a mail server or don't want to resend some virus to a friend using XP.  Virus are written mostly for Windows and the way Linux is design makes virus infections difficult and at this point very unlikely.

Gnome will let you see those external drives and usb and as in windows where you have to "disconnect" it before removing it, in Linux the command is **umount** (unmount)

From the command line you need to have administrative rights to remove or un mount a drive: **sudo umount -f /dev/name_of_drive**

If you want to learn you will get the hang of it, check [http://help.ubuntu.com](http://help.ubuntu.com) for more info, also check this site [http://www.psychocats.net/](http://www.psychocats.net/)

There are tons of information for you to check, just take it one step at a time. Ask questions when you are lost someone will answer.

My suggestion for you bookmark those sites that have usefull information

---

### Post by mikhsoj on 2007-11-26
> **bluepowder7 said:**
> i can't say much to most of your questions, but as far as i know the penguin is out shagging the butterfly in a most unspeakable way.

linux is similar to unix, so once you learn one it probably won't be a big jump to learn the other.  as for a list of commands, there's a few posts / threads around here that list the common commands, and you can likely find them in a linux-for-dummies book.

.exe files won't work here the same way .deb packages won't work in winxp.  you can use wine or some other layer to run windows type stuff within linux, but i've never tried it.



ps - LINUX - **L**inux **I**s **N**ot **U**sed like **X**p

so what about all the fun programs i have? do i need to download linux (.deb) counterparts? to they EXIST? programs like vlc player, 

i dont think games come linux ready... :(

---

### Post by bluepowder7 on 2007-11-26
VLC is probably part of the base ubuntu install.  LOTS of programs exist, and you can look for them through either Applications - Add/Remove or through System - Admin - Synaptic.  find what you like, and download / install it.  from those two sources, they're self-installing packages.  if you find a program online that is a .deb file, that's also self-installing in ubuntu.

games?  nexuiz.  warsow.  alien somethingorother.  quite a few available, actually.

---

### Post by scrooge_74 on 2007-11-26
Check in the repositories and in help.ubuntu for more ideas on which programs replace the windows versions.

As for games, some run under wine other are linux native like Wolfstein Enemy Territory or the latest version of Quake

---

### Post by wolfen69 on 2007-11-26
go to [www.getdeb.net](www.getdeb.net) for .deb apps.(double click to install)

---

### Post by jfinkels on 2007-11-26
Read the links in my signature for great introductory information.

---

### Post by philinux on 2007-11-26
First place to look for an app is in Add/remove or system>admin>synaptic package manager.

Only if its not there will need to activate more sources. You'll find sources under admin>software sources.

---

### Post by mikewhatever on 2007-11-26
> sudo apt-get install vlc

Wasn't very hard, was it.

> Re: just migrated from xp. can i use ANyTHING?

No. You can learn to.

---

### Post by mikhsoj on 2007-11-26
> **mikewhatever said:**
> Wasn't very hard, was it.



No. You can learn to.

lols. man thanks guys still trying to get a hold of using ubuntu.
also, can anybody recommend me a wireless pcmcia card? somthing that has easy linux support?

---

### Post by aysiu on 2007-11-26
> **bluepowder7 said:**
> VLC is probably part of the base ubuntu install. VLC is not part of the base Ubuntu installation. It's in the Universe repositories.

So you would have to [enable extra repositories](http://www.psychocats.net/ubuntu/sources) before installing VLC.

For more information on installing software, read these two links:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by anemptygun on 2007-11-26
Hey welcome to the linux family! Glad to see your asking questions! that is the key to learning, I first started learn to use linux about a year ago, now i almost use linux 99% of the time. Just give it time and don't rush yourself! You have to train yourself to use it...

---

### Post by roaldz on 2007-11-26
Wow, thats a bunch of questions.. 

I´m assuming you´ve installed Ubuntu Gutsy 7.10. If you installed Kubuntu, this may be confusing. 
Let´s start from here:
> **mikhsoj said:**
> 
so i tried running some programs on it. hahahaha.. nothing works. exiting. so here goes the real questions:
does linux require a virus scanner? is it like windows where it has vulnerabilities that trojans, spyware whatnot can take root in?

How do you mean nothing works? Then something must be seriously wrong, which I doubt it is.
Linux does not need a virus scanner to protect itself from Windows viruses, and actually not even from Linux viruses. You only need someone to prevent himself from doing things he should not do, like executing commands like ¨rm -rf /¨. Do NOT use commands like that if you´re not knowing what you´re doing.
You can install a virus scanner to protect other windows pc´s in your network, but that´s another story.

> **mikhsoj said:**
> 
is there a way to install windows (.exe) files? i read somtehing about sudo or wine or something but still dont understand it.

You can install and launch windows programs using the program ¨wine¨. It´s a sort of windows-emulator, but not actually (doesn´t matter).
The sudo command people told you about makes you able of running programs with Super User (su)  privileges. This is the ¨root¨ user. This command is often used for installing programs with apt-get. Apt get is a utility that can download, install and maintain software on your computer. U can do that too with synaptic.
For installing wine, I recommend using the Synaptic Package Manager. Search for it in Applications --> Administration. First you have to set your repository´s right. You can do that in that program too (don´t ask me exactly how to, I don´t have that program available right now). Just enable all repository´s you can find, and disable the cdrom one. Then hit update. Search for wine, mark it, hit apply. Now you can right-click launch the exe´s with wine.

> **mikhsoj said:**
> 
is there a list of terminal commands? i know ubuntu 7.10 is supposed to limit terminal use but i might wanna learn it anyways.

is this similar to unix? or is learning unix a whole world of difference?

where is the penguin?

I recommend you go to [http://ubuntuguide.org/](http://ubuntuguide.org/) for some short howto´s. Its quite similar to unix, but it´s GNU, and **GNU** is **N**ot **U**nix.
The pinguin is in your computer! And it can fly!

---

### Post by kevindubrow on 2007-11-26
Hey, I'll try to make this a little easier for you. If you tell me which programs you need, I will give you the Linux equivalent.

Trust me, I am fairly new to Ubuntu and I have found everything I need and more. If anything, the people on this website are incredibly helpful and kind and will try to make your experience with Linux as easy as possible.

---

### Post by aysiu on 2007-11-26
> **kevindubrow said:**
> Hey, I'll try to make this a little easier for you. If you tell me which programs you need, I will give you the Linux equivalent. I'll make it even easier than that. Visit this website:
[http://linuxappfinder.com/](http://linuxappfinder.com/)

---

### Post by Daveski on 2007-11-26
> **mikhsoj said:**
> is there a list of terminal commands? i know ubuntu 7.10 is supposed to limit terminal use but i might wanna learn it anyways.

There is a HUGE number of commands as in Linux everything can be done from the terminal. Are you familiar and happy with the Windows command line, and what sort of commands do you use there?

Some tips for the terminal are:

```
man <command>
```
e.g.
**man sudo** or even **man man**

to get the manual entry for that command. Scroll with the mouse, or cursor keys and q quits.

To find out related commands you can type

```
apropos <command>
```
e.g.
**apropos sudo**

---

### Post by linuxlizard on 2007-11-26
ubuntu isn't free windows. 

LOL- cracks me up how many people lately want to run their windows games and apps on linux. I don't ever hear mac users complaining they can't play their favorite windows games on their mac...

To get more software move your mouse to the upper left corner of your screen and click applications, then at the bottom of the menu that appears click add/remove

Also go here:
[http://www.getdeb.net/browse.php](http://www.getdeb.net/browse.php)

---

