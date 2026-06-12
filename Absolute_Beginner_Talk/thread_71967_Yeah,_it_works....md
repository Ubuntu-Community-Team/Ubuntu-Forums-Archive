---
title: "Yeah, it works..."
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by nerdman on 2005-10-04
I decided to switch from windows XP to a Linux OS. (yay, I'm the same as 98% of the other people on this forum.) I even managed to figure out the infathomable Mounting of drives. I was slick and used Partition Magic to make my windows NTFS storage drive into a FAT32, just in case.
...but still I have read-only access to the drive that is inside my case. Did I mount it wrong? I was showed to make a folder in the /mnt (directory?), but it says I don't have write access to the parent folder.

My guess is I need to mount my drive somewhere else, but I'd like to hear a little more technical background, it helps me understand how it works.

and its true I probally could have read considerably more... and if you don't feel like explaining I'll settle for links.

---

### Post by brentoboy on 2005-10-04
[http://ubuntuguide.org/](http://ubuntuguide.org/)

use this to get the latest universe repositories. (and other goodies)

then, use synaptic to get ntfsprogs

then google ntfsprogs for directions on how to mount readwrite.

I dont know for sure, because I backup up to CD and dumped my win partitions, but I remember seing the ntfsprogs in synaptic, and the desription seems to be what you are looking for.

---

### Post by thespinesplitter on 2005-10-04
in the fstab line you added, it says somewhere RO this is read only change it to RW

is that easy, but i dont take any respossibiity since ive only mounted NTFS as read-only, i just looked up the option for read-write for fstab

---

### Post by aysiu on 2005-10-04
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by nerdman on 2005-10-05
Yeup, progress made.

Maybe I wouldn't seem like the technical sort, but I'm a little disappointed at the terminal **-?** help switch listings... **sudo -?** doesn't even tell me what the command does, although using it does get my drive mounted :???: 

Anyone care to point me at a more technical explanation of the whole concept?

oooh, or how about a list of Linux terminal commands and their purposes as well as syntax >=D

---

### Post by nerdman on 2005-10-05
...That's odd, open /etc/fstab into gedit and it's read only too. >_<
*(edit: that was odd, running if from the applications menu and browsing to the file opens it RO, but terminal line, it makes it RW.)*

anyways, is Filesystem an abstaction for the partition Ubuntu is installed on?

---

### Post by SilentCacophony on 2005-10-05
Hello. The **sudo** command is Ubuntu's way of allowing *superuser* (sometimes referred to as *root*) permissions for running the command that follows it. Most files on the system belong to 'root', so that the core system is protected from users without admin permissions. In general, it also helps protect from accidental or malicious changes to the system.

If you're looking for more info on installed programs or commands, you can look through the */usr/share/doc* directory where docs are stored in subdirectories for each program. Alternatively, you can issue a **man** or **info** command from the terminal like so:

**info**

for general information, or

**info <command>**
**man <command>**

for specific info about a command, using different formats.

On a linux system, filesytem refers to the / mount point (also sometimes referred to as the root.) Everything in the system, including all devices and files, are accessible from within /.

Here are some links you may want to looks at:

[https://wiki.ubuntu.com/BasicCommands]("https://wiki.ubuntu.com/BasicCommands")

[https://wiki.ubuntu.com/UserDocumentation?action=show&redirect=NewToUbuntu]("https://wiki.ubuntu.com/UserDocumentation?action=show&redirect=NewToUbuntu")

[http://www.linuxdevcenter.com/linux/cmd/]("http://www.linuxdevcenter.com/linux/cmd/")

---

### Post by wmcbrine on 2005-10-05
[QUOTE=nerdman]I'm a little disappointed at the terminal **-?** help switch listings...[/QUOTE]BTW, programs in Linux don't actually use "-?".  The only reason that *sometimes* works is that it's interpreted as a syntax error, so some programs will print out a syntax summary. Some might give a better result with "-h" instead. But generally, you want the man page: "man progname".

IMHO, "info" is only really usable if you grok Emacs, but it's the preferred doc format of the FSF, so many programs have better info pages than man pages. You can get alternative info (and man) viewers that are a little easier to use.

---

### Post by nerdman on 2005-10-06
ah yes, the manual, that'll keep me occupied for a while. Thanks much.

---

### Post by nerdman on 2005-10-06
My drive resolved, I now want to install a few toys, but the whole process of 'Making' is throwing me off a bit. I suppose its because parts of the program have to be installed on your system because of diversity between each machine running Linux... 
but I still end up listening to the sound of silence V.V Trying to install XMMS, it wants me to 'make' it, but throw it in a folder and it says there's nothing to be made.

---

### Post by tehwa on 2005-10-06
[QUOTE=nerdman]My drive resolved, I now want to install a few toys, but the whole process of 'Making' is throwing me off a bit. I suppose its because parts of the program have to be installed on your system because of diversity between each machine running Linux... 
but I still end up listening to the sound of silence V.V Trying to install XMMS, it wants me to 'make' it, but throw it in a folder and it says there's nothing to be made.[/QUOTE]
That's because it hasn't been configured. The age old process goes something like this:
```
./configure
./make
./sudo make install
```
Basically, running configure will configure the make, since without said configuration, make doesn't know how to make whatever you're trying to make :p . It will also pick up any needed libraries that have not been installed on your machine, and make sure it's OK to go ahead and build the app.

However, you probably won't need to compile xmms, I don't use it but a lot of Ubuntu users seem to, so a precompiled binary should be available via Synaptic, ready for download and installation without any compilation.

---

### Post by UbuWu on 2005-10-06
[QUOTE=wmcbrine]BTW, programs in Linux don't actually use "-?".  The only reason that *sometimes* works is that it's interpreted as a syntax error, so some programs will print out a syntax summary. Some might give a better result with "-h" instead. But generally, you want the man page: "man progname".
[/QUOTE]

"--help" will work for most programs.

---

### Post by nerdman on 2005-10-06
>_<

I sorta like Linux for the terminal typing only concept, and (from what I understand) Synaptic is just a graphical addaption of the optional extensions downloader (right?)
do I *need* synaptic or do I have to use a GUI / yucky hands off the keyboard and click ?

---

### Post by brentoboy on 2005-10-06
[QUOTE=nerdman]>_<
do I *need* synaptic or do I have to use a GUI / yucky hands off the keyboard and click ?[/QUOTE]

There is nothing in synaptic that cant be done using the apt command line.
look up apt in the wiki, it has a wonderful description of all the ins and outs of issuing command requests for package info and all that stuff.

Synaptic is for the rest of us, who think that klick, click, click is faster than typing (and requires less memorization).

---

### Post by nerdman on 2005-10-06
[QUOTE=brentoboy]
Synaptic is for the rest of us, who think that klick, click, click is faster than typing (and requires less memorization).[/QUOTE]

haha, its not a matter of oppinion, using a mouse probally is faster, but if I didn't have time to kill I would have stuck with windows and not bothered learning :cool: 

x_x and about **apt-get install <thing>**... I've followed instructions to install about 3 MP3 codecs and yet still Music Player can't read my MP3s. sigh~

---

### Post by brentoboy on 2005-10-06
there are other players, maybe one of them would work.
I wonder if it is just music player...

I havent fiddled much with MP3s on ubuntu yet (now that I think about it, I cant imagine why I havent, 6 months ago, that was the first thing I would have done)

---

### Post by Mustard on 2005-10-06
I've had more luck getting XMMS, or alsaplayer to work with mp3's than I have using MPlayer.

---

### Post by nerdman on 2005-10-06
*blinks*

okay, whoever said installing linux software was hard was just slow (sorta like me)...

**apt-get install xmms**

[i]After unpacking 9146kB of additional disk space will be used.
Do you want to continue [Y/n]? y
[/i]

...I find that hilarious.
Whats the name of the lib for actual MP3 codec support?

---

### Post by nerdman on 2005-10-06
=/ well, it looks like Winamp. And the title even scrolls when I load an MP3. Then I hit the play button and it locks up.

meh, just got off work, playing with all this stuff...  Should I try restarting? lol

also, on the topic of freezing applications, is there a way to link pressing CTRL+ALT+DEL to open up the System Monitor (application, would I call it that?) Or, am I just going to have to get over the old windows habits?

**edit:** restart mo worky. ...I honestly wasn't expecting it to.

---

### Post by Wolki on 2005-10-06
xmms lockup: Set output plugin in the xmms preferences window to esd (eSound).

system monitor: [http://www.ubuntuforums.org/showthread.php?t=41174](http://www.ubuntuforums.org/showthread.php?t=41174)

---

### Post by nerdman on 2005-10-07
[QUOTE=Wolki]xmms lockup: Set output plugin in the xmms preferences window to esd (eSound).

system monitor: [http://www.ubuntuforums.org/showthread.php?t=41174](http://www.ubuntuforums.org/showthread.php?t=41174)[/QUOTE]


OH MY GOD

YOU WIN SIR.

*tosses Windows XP cd out of 10th story window* Okay, I'm happy ^_^

I appreciate everybody's help, and its good to know Ubuntu has such a strong, knowledgable, responsive community. Now I need to play with things (breaking and fixing FTW) and maybe I'll get to help someone. yesssss...

---

### Post by Mustard on 2005-10-07
[QUOTE=nerdman]=/ well, it looks like Winamp. And the title even scrolls when I load an MP3. Then I hit the play button and it locks up.

meh, just got off work, playing with all this stuff...  Should I try restarting? lol

also, on the topic of freezing applications, is there a way to link pressing CTRL+ALT+DEL to open up the System Monitor (application, would I call it that?) Or, am I just going to have to get over the old windows habits?

**edit:** restart mo worky. ...I honestly wasn't expecting it to.[/QUOTE]

With regards to misbehaving applications, I find the easiest way to get rid of them using the graphical interface is to click rapidly on the window close button, and then wait for a little dialogue to pop up asking you if you want to kill the application, or additionally you can install a little gnome applet that sits on your one of your panels (the top panel most likely) and you can click on that once, then click on the application and it will kill the process.  There is another applet that provides system information which has the additional benefit of loading up System Monitor when you click on it.

---

### Post by xmastree on 2005-10-07
[QUOTE=nerdman]well, it looks like Winamp.[/QUOTE]Did you know you can also use Winamp skins with XMMS?
See [this thread]("http://www.ubuntuforums.org/showthread.php?t=57874").
:cool:

---

### Post by nerdman on 2005-10-08
XD

Linux pwns. 'nuff said.

---

### Post by nerdman on 2005-10-09
haha, lets just reuse my thread if possible.

Okay. Played with xserver to get a higher desktop resoluton.  BUT! now applications don't show up on the bottom bar. When I started up it gave me funny "process unexpectedly terminated" for about 3 things... My Show Desktop icon and thumbnails of workspaces are gone.

---

### Post by nerdman on 2005-10-09
actually...

holy crap! I am amazed at how many panel widgets there are. (is that the term? lol) ...besides getting my workspace swapper and list of windows back, I have about 10 eyeballs staring at my mouse. Kill CPU cycles, who doesn't want that?

....where can I get more of these neat little toys?

---

### Post by SilentCacophony on 2005-10-09
Try entering into a terminal:

**sudo killall gnome-panel**

to straighten out the panel.

---

### Post by nerdman on 2005-10-09
>=D

with a command line like killall, how can you NOT like it? bruahaha.

---

### Post by nerdman on 2005-10-09
Oops. ...what would the widget for system tray be called? I can't seem to close my GAIM window and get the tray icon anymore =/

---

### Post by Wolki on 2005-10-09
[QUOTE=nerdman]Oops. ...what would the widget for system tray be called? I can't seem to close my GAIM window and get the tray icon anymore =/[/QUOTE]

They're called "applets", and the notificato area is called "Notification Area" :)
There are some more panel applets available in synaptic, and a even more on GnomeFiles.

---

### Post by nerdman on 2005-10-09
[QUOTE=nerdman]Linux pwns. 'nuff said.[/QUOTE]
QFT.

got my notification area fixed again. Would the room grow quiet if I asked what Windows can actually do just as good as Linux?

---

### Post by Hobbsee on 2005-10-09
I doubt it would go quiet...

You would be more likely to get a resounding sound of no, seeing as they havent managed to do it so far, and have had many years to try...

---

