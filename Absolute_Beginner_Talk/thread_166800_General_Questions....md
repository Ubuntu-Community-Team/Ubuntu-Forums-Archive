---
title: "General Questions..."
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by penywise on 2006-04-27
Hi again... actually I wrote a quite big post, while the forum ended my session, when I logged to post it, the post field was empty... Cool, will write it again (using Ctrl+C often)...

I get a little frustrated on writing posts and getting new threads... For decades of developement I doubt there is a question, that doesn't have its answer already somewhere in the Internet...
But reading the "rules of the forum" made me a little more confident. As you might guess I just started with Linux (2 days ago).
I set up an Ubuntu 5.04 with Gnome.
All the time I read from a variety of resources, guides, tutorials, write both in that forum and the "local" ones here in Bulgaria, trying to get, write, do and remember all the info I get... So far, so good ;)

Last night I ran:
sudo apt-get update
sudo apt-get upgrade

The Questions...:

1. Meanwhile (with running the "**sudo apt-get upgrade**") I tryied to perform some other operations -> like getting codecs to rung mp3, avi, etc.
I tried to get things like *"sudo apt-get install flashplayer-mozilla"*... It didn't want to isntall them, telling that... "the process is already being used..."
Q: Was that because I upgraded at the same time?

2. General Question for the "**sudo apt-get install**":
Q: Is it something like the "default way" to get a program on you Linux? Is it always that... simple (like sudo apt-get install **flashplayer-mozilla**)?

3. Installation...
Q: Is that process (in Question 2) automated - getting the program from internet, installing it automatically? How do I run it? How do I UnInstall it if I would like to?

4. Control Panel?
Q: I read about a Control Panel - "The only place that from wher you can modify you Gnome". I found no Control Panel on my system (after the default installation)

5. X Window system?
Q: By reading and looking at images of desktopes I saw that my default interface of Gnome is different from the one I found. How do I install the X Window System? How do I initialize it (would it change the "interface" automatically?). How do I operate it? How can I UnIstall it if I would like to?

6. Programs?
Q: I saw I have some default programs coming with the installation of Ubuntu. There was a..."Gnome BitTorrent" or something... Do I need:
sudo apt-get install azureus


I you require any information regarding my questions above, please let me know.

Basically I use [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) , getting all the info from there. However the thing explained there are... "not explained" (you just see the command you have to enter in the Terminal to get the program)...

I would prefer to know what I do... Maybe after some time of "doing what is written", whitout understanding it I won't advance in any way (I guess so...)

Final:
Sorry for the "I..." -> english is a language that requires a lot if "I's":mrgreen: 

I would also like to apologize for writting longs posts... and asking very simple and... dumb questions. I know how annoying can be to teach and repeat the basics for a long period of time, starting all over with someone new, telling him the same things again, and again...

Thank you in advance for you patience.

---

### Post by mostwanted on 2006-04-27
[QUOTE=penywise]Hi again... actually I wrote a quite big post, while the forum ended my session, when I logged to post it, the post field was empty... Cool, will write it again (using Ctrl+C often)...

I get a little frustrated on writing posts and getting new threads... For decades of developement I doubt there is a question, that doesn't have its answer already somewhere in the Internet...
But reading the "rules of the forum" made me a little more confident. As you might guess I just started with Linux (2 days ago).
I set up an Ubuntu 5.04 with Gnome.
All the time I read from a variety of resources, guides, tutorials, write both in that forum and the "local" ones here in Bulgaria, trying to get, write, do and remember all the info I get... So far, so good ;)

Last night I ran:
sudo apt-get update
sudo apt-get upgrade

The Questions...:

1. Meanwhile (with running the "**sudo apt-get upgrade**") I tryied to perform some other operations -> like getting codecs to rung mp3, avi, etc.
I tried to get things like *"sudo apt-get install flashplayer-mozilla"*... It didn't want to isntall them, telling that... "the process is already being used..."
Q: Was that because I upgraded at the same time?

2. General Question for the "**sudo apt-get install**":
Q: Is it something like the "default way" to get a program on you Linux? Is it always that... simple (like sudo apt-get install **flashplayer-mozilla**)?

3. Installation...
Q: Is that process (in Question 2) automated - getting the program from internet, installing it automatically? How do I run it? How do I UnInstall it if I would like to?
[/QUOTE]

Yes it was because you upgraded at the same time. For the two other questions: I've created a guide specifically aimed at explaining installation and installation issues to new Ubuntu users, it's available from this url:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by Sef on 2006-04-27
> Last night I ran:
sudo apt-get update
sudo apt-get upgrade

The Questions...:

1. Meanwhile (with running the "sudo apt-get upgrade") I tryied to perform some other operations -> like getting codecs to rung mp3, avi, etc.
I tried to get things like "sudo apt-get install flashplayer-mozilla"... It didn't want to isntall them, telling that... "the process is already being used..."

Q: Was that because I upgraded at the same time?

Yes, that is correct.

> 2. General Question for the "sudo apt-get install":
Q: Is it something like the "default way" to get a program on you Linux? Is it always that... simple (like sudo apt-get install flashplayer-mozilla)?

Yes, sudo apt-get install package-name

> 3. Installation...
Q: Is that process (in Question 2) automated - getting the program from internet, installing it automatically? How do I run it? How do I UnInstall it if I would like to?

Yes it is installed.   Either from the appliations menu or type the program name in the terminal.  

> 4. Control Panel?
Q: I read about a Control Panel - "The only place that from wher you can modify you Gnome". I found no Control Panel on my system (after the default installation)

Need to check before answering.

> 5. X Window system?
Q: By reading and looking at images of desktopes I saw that my default interface of Gnome is different from the one I found. How do I install the X Window System? How do I initialize it (would it change the "interface" automatically?). How do I operate it? How can I UnIstall it if I would like to?

Need to check before answering.

> 6. Programs?
Q: I saw I have some default programs coming with the installation of Ubuntu. There was a..."Gnome BitTorrent" or something... Do I need:
sudo apt-get install azureus

Only if you want azureus.

---

### Post by penywise on 2006-04-27
Why thank you for your quick responses :)

I will carefully read the provided links and info.
I also think to "update" this Thread with any further questions I have, rather than posting and spamming the forum with new threads.

The next Question I would like to ask you is about fonts:
I met a problem. I was told to execute the following command in the Terminal:
```
sudo apt-cache search cyrillic fonts
```
problem -> the result I got was:

```
# sudo apt-cache search cyrillic fonts
console-terminus - Fixed-width fonts for fast reading on the Linux console
xterm - X terminal emulator
```

Then I was told that my "Repositories" were with... poor indexation.
That's why I followed the [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) guide, adding some new... "stuff" into ```
sudo gedit /etc/apt/sources.list
```

Then ran the ```
sudo apt-get upgrade
```

Q:
After all the operations done above, would ```
sudo apt-cache search cyrillic fonts
``` "work" now?
and of course after putting Cyrillic (Bulgarian) how would I switch between the languages...

Thank you very much for the help

---

### Post by penywise on 2006-04-27
The guide for istallation of programs is simply beautifully written and easy to understand, teaching you how to do the job... Great work, thanks a lot!

And of course here come several new Questions:

1. Synaptic -> Do I have it "by default", or I have to manually download and install it, then have it and use it. 

2. Debian Menu?
```
Usually your Applications menu is updated with a launcher to your new program, but sometimes this doesn't happen automatically.
```
Can I install it on Ubuntu? Do I "need" it, and how can I start newly installed program.
I guess by finding its installation folder and creating a "shortcut" on the Desktop... So - any way to run it by Terminal? (just curious)

Thank again

---

### Post by gingermark on 2006-04-27
Going back to your queston before, you already have X - GNOME, or any other Desktop Environment or Window Manager run within X. So I wouldn't worry about it unless it stops working :)

You have Synaptic. Should be in your menus. I use Kubuntu, so I can't tell you exactly where, but just have a look.

Install the Debian Menu, it's just an additional entry in your main menu. If you later don't like it, you can remove it.

As far as the cyrillic fonts, that command (apt-cache search) just searches the contents of the repositories. You can use Synaptic Package manager to do this graphically. As it's a search, it will "work" I guess if the package you are after is in the repositories.

---

### Post by Rinzwind on 2006-04-27
Synaptic is under system/administration.

---

### Post by penywise on 2006-04-27
GR8, 10x for the answers again!

As for the fonts, when I started getting a cyrilic fonts with apt-cache search, then sudo apt-get install resutls_found -> I couldn't reach it...

But my repositories were the default ones then, besides I didn't have any idea what a repository was ;)

Further I edited the file (sudo gedit /etc/apt/sources.list) with the results I found on [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) and ran the updates - I guess I won't meet troubles when I get to the installation of fonts, codes, etc tonight.

**Question:**
(Menu Editor)
```
sudo apt-get install smeg
``` -> is it something like that Debian Menu?

---

### Post by Bloch on 2006-04-27
Hi Pennywise;
Synaptic package manager is just a user-friendly interface to the apt-get command. It is on your system by default.
Do a search (e.g. games) and see what software is available. (this search is looking through the same repositories as apt-get search) There is a panel which will describe the new software, and it is all much nicer and informative than using apt on the commandline.
But it is easier for people to tell you "Enter apt-get install mozilla" than it is to describe how to find the package using synaptic.

To set up a working system you only need the installation disk, and then download and run easyubuntu. This little program will install multimedia codecs etc.
If you find yourself getting bogged down, you might like to reinstall from the beginning again. Then you know you'll have a clean system.
There is a "Configuration Editor" in the Applications > system menu.  It's not very informative and the defaults of the gnome desktop are fine. I think it's better to use your time in 
A. Learning about synaptic and the repositories
B. Learning the basic terminal commands: ls, cd, pwd, rm, mkdir, sudo . . . 
C. Getting easyubunbtu, reading a little bit about what it does and then running it.

---

### Post by Rinzwind on 2006-04-27
smeg is a menu editor. You can add stuff to your menu.
see [http://www.ubuntuforums.org/forumdisplay.php?f=67](http://www.ubuntuforums.org/forumdisplay.php?f=67)  for some explanation.


Debian menu is a menu (like sound and vision or internet inside applications). It shows everything that can be started in 1 menu under 'applications/debian menu/'. Sometimes programs are not (or not correctly) designed for gnome and forget to add a startup to the menu. Or it's not intended to be in a menu ;) Then debian menu is more than likely to have it inside this menu.

After that all you need to do is copy that menu item into your normal menu and are set to go.

---

### Post by gingermark on 2006-04-27
```
sudo apt-get install menu
```
is what you're after.

But Synaptic is graphical front-end for apt-get, and makes life easier, especially when searching for stuff.

But sure, if you know what you want then using the command line is quickest.

---

### Post by penywise on 2006-04-27
**Bloch**

That was helpful, thank you.
I would like to write a major off-topic right here (sorry about it)

It's "peNywise", not "peNNywise"... I know it's a nice band, but my nick doesn't "represent" it.

PeNNywise (again with double N) is a character of Stewen King, so I write my nickname with just a single N for differentiation...

Well I will get to know and understand everything written so far ASAP.

There is a thing that bothers me...
If I get to learn mainly using the cappabilities of the GUI (Gnome), rather than the Terminal -> would that be "suitbable".
I wish to advance with Linux in order to become a sysadmin... It's a real pleasure to learn, read and do it all by myself everything I read about Linux.

I have a chance to get a possition as a sysadmin after I advance the system as a whole. I would need to run a MySQL, Apache servers...

So - would that mean I will "have to" use Terminal more often than walking through the GUI? If it's like this - I would like to master the Terminal more than learning the GUI and use Linux as I use Windows...

I told you - I'm new with it and I really collect and try to remember, execute and understand a lot of info on many different topics, so my head gets full at some point...

Thanks again for all your answers. I will surely have more coming... but... time is needed :)

Have a great day!

---

### Post by gingermark on 2006-04-27
Check out [http://linuxcommand.org/](http://linuxcommand.org/) - an excellent site.

---

### Post by steve.horsley on 2006-04-27
Sorry to rain on your party, but 5.04 (Hoary) is a little old now. 5.10 (Breezy) has been out for 6 months, and 6.06 (Dapper) is due out in a few weeks (the beta looks good). I would like to suggest that you upgrade when Dapper is released - there have been a LOT of improvements in the last year. One of them is that a menu editor is included in the default gnome install.

Linux gurus do tend to rely on the command line much more than the GUI, and for several reasons. Here a few I can think of:

* It's easier to tell someone else exactly what to do with a command line quote than to say click this, look for that, etc...
* The GUI doesn't always work, but the command line is still available even when X won't start. See the number of threads here about fixing the video drivers
* Many servers don't even have a GUI installed - they are command line only. Saves loads of memory. 
* Even when a GUI is installed and working, which one? Are you using Gnome, KDE, XFCE, FVWM etc... They are all very different.
* It can help you understand if you know what commands a GUI is using. Yes, many GUI programs simply run commands in the background and present the output and options prettily. ANY linux firewall is using the **iptables** command to do its business. All the CD burners that I know of (nautilus, gnome-baker, k3b, gcombust) use **mkisofs** and **cdrecord** commands to actually do anything.

Welcome to the forum.

---

### Post by gingermark on 2006-04-27
If you do upgrade via apt-get make sure you upgrade to Breezy first, and then (when you decide to) on to Dapper. It is my understanding that a direct upgrade from Hoary to Dapper would cause a lot of problems.

This is just my understanding though - I am not 100% - if anyone wants to confirm or correct this that would be great.

---

### Post by penywise on 2006-04-27
Oki... a great new "project" for me to deal with ;)
I'm starting to like this :mrgreen: 

So... how do I upgrade my Ubuntu to the newest available version now (5.10)?

I thought (here we laugh;)) that that update I did last night was going to "do the job"... It was about 200 Mb of... stuff

---

### Post by gingermark on 2006-04-27
Before you start I'd make sure the ubuntu-desktop metapackage is installed (sudo apt-get install ubuntu-desktop) - this makes upgrading less painful.

You have a file located in your /etc/apt directory called "sources.list". This file contains a list of the repositories that are available to you. These need to be changed from hoary ones to breezy ones.
Do ```
gksudo gedit /etc/apt/sources.list
```
You might want to save a backup.

Then change all the instances of the word "hoary" to "breezy". If you have any unofficial repositories that you've added yourself, they might not work, so you might want to put a # in front of the relevant lines, so that they are ignored for now.

You could also go to the source-o-matic page (in my sig) and get a breezy sources.list produced for you - just go with the official ones for now.

Anyways, when you've sorted your breezy sources.list save the file, and do
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Read what apt is going to do - if it is going to remove lots of important things say no, and come back to us. It will be a problem with your sources.list.

Once the process is complete, reboot.

Good luck!

---

### Post by penywise on 2006-04-27
Cool :)

Yesterday I did exactly as written here:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

I cut the info written there and placed it over my excisting file and saved, then ran the updates

As I might guess:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
created a backup file of my original **sources.list** file right?

So if I do this now I will have a backup of my current, then experiment with the... (what was written till here)

Well... to what content should I change that file now so I can upgrade?
And afterwards should I change it with the one I have now (that I got from the URL I provided above)...

Thanks

---

### Post by gingermark on 2006-04-27
Hoary is the old version, Breezy is the current version. After the upgrade, don't use ubuntuguide.org anymore. Once you've upgraded there are other guides (and additional repositories) for Breezy.

But if you like ubuntuguide.org (and it is a good guide for hoary) here's your chance to use it one last time: 
[http://www.ubuntuguide.org/#upgradehoarytobreezy](http://www.ubuntuguide.org/#upgradehoarytobreezy)

---

### Post by penywise on 2006-04-27
Whoa ;)

I really like the sound of
```
Warning! This is still in it's development stage. Only use it for experimental purposes
         Doing this might break your entire system
```

I am doing it now... let's see if that works 
(except that my international traffic is at too slow speed... ) :(

---

### Post by penywise on 2006-04-27
Oki, I got to the point...

```
The following packages will be REMOVED:
  aspell-bin capplets dbus-1 dbus-glib-1 libcamel1.2-3 libebook1.2-3
  libedataserverui1.2-4 libesd0 libgc1 libhal-storage0 libhal0 libid3-3.8.3
  libmusicbrainz2 libmusicbrainz4 libmyspell3 libnautilus-burn1
  libopenh323-1.15.2 libostyle1 libpt-1.8.3 libsigc++-1.2-5c102 libsmpeg0
  libstlport4.6 mozilla-firefox-gnome-support openoffice.org-thesaurus-en-us
  postfix-tls ubuntu-quickguide xlibmesa-dri xlibmesa-gl xlibmesa-glu
```

So.. is that the "if it will remove important things..."
or should I get it upgrade the distribution?

(a little more info at the end)
```
694 upgraded, 314 newly installed, 29 to remove and 0 not upgraded.
Need to get 536MB of archives.
After unpacking 473MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

EDIT:

The good part is that this upgrade will take like.... hours, tens of hours... (my international speed is like 3-9 kb/sec)

---

### Post by gingermark on 2006-04-27
First off, that seems fine. Nothing too important there.

Secondly, if you use the source-o-matic link in my sig, and create a sources.list just out of the official repositories you could then use local repositories.

I'll tell you what, if you're not sure, I'll do it for you. Where do you live?

Oh, and don't worry about the experimental bit. The ubuntuguide was written a while ago, when Breezy wasn't the current version. It's not experimental anymore. I just pointed to that because you seemed to have a hard time following my instructions, and appear to be comfortable with that guide.

---

### Post by penywise on 2006-04-27
Well I live in Bulgaria, 10x for asking ;)

I decided to skip the upgrade for now - I don't need the last version to learn the basics.... I will surely :censored: up the system at some point, so will install the newest later from CD directly...

So - few more problems:

I have motherboard EPOX 8RDA+ with onboard 5.1 sound card.
I have Hercules 5100 XPS speakers
---
How can I get my 5.1 sound with the sub-woofer running here?

Second Question:
I have cyrillic fonts. I can read them.
How can I switch the languages... something like a FlexType or sth...
NOTE: I don't have any Control Center (who the :censored: knows why ;)...)

Thanks again

---

### Post by gingermark on 2006-04-27
Assuming your country code is BG (sorry, I'm not that knowlegable about Bulgaria) then your sources.list for Breezy might look something like
```
# Ubuntu supported packages
deb http://bg.archive.ubuntu.com/ubuntu breezy main restricted
deb http://bg.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages
deb http://bg.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://bg.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```
They're just the official repositories. But of course, feel free to wait.

The Control Centre is where most configuration is done in KDE - I assume you are running Gnome.

---

### Post by penywise on 2006-04-27
Yep, I am running Gnome...

Now came the new, the great problem (if I only knew what happened](*,) )
There we go - step by step -> I did... something, so my Ubuntu got all messed up, the X graphic environment could run (sth like that)... Whatever - I reinstalled - so no matter...

Now I changed the Repositories again as shown on [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
The file was edited and saved...

Then of course I run ```
sudo apt-get update
```

Here comes the END of that update...:

```
Fetched 4150kB in 11m37s (5953B/s)
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Well - now I can't run ANY ```
sudo apt-get
```

People are running server for 6 years without rebooting, and in 6 minutes I crashed the **** out of my system

I guess you need a tallent to do that](*,) :evil:

---

### Post by penywise on 2006-04-27
I am getting happier :)
The file is edited and saved in the exactly same way as shown on that guide site. There ain't nothing difficult in the copy-paste operation all right...

I just tried to run the ```
sudo apt-get update
``` again...

Let me show you the great end (I bet you will never be able to accomplish anything like it!)

penywise@penywise:~$ sudo gedit /etc/apt/sources.list
penywise@penywise:~$ sudo apt-get update
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release.gpg
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary ReleaseIgn cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
  404 Not Found
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Fetched 4B in 16s (0B/s)
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
penywise@penywise:~$

Well... 
Am I going on the reinstall Ubuntu part again? I kinda get use to it ;)

---

### Post by penywise on 2006-04-28
So... is there any way of fixing this?
The whole command "sudo apt-get" "doesnt' work", I can't dowload a program, can't update or upgrade...

And the repositories file as shown in the ubuntuguide.org

---

### Post by gingermark on 2006-04-28
I don't think those repositories exist any more - the official ones do, but the mirrormax ones were unofficial, and I'm pretty certain they are gone now (as we said, Hoary and the guide you are using is old). You'll also want to put a '#' in front of the CD entry to stop the error with that,

I would encourage you to upgrade - using that sources.list I gave you should mean you use a bulgarian mirror (unless bg isn't the country code for Bulgaria),

---

### Post by cjm5229 on 2006-04-28
You would really be better off if you would download and burn a Breezy cd. then reinstall from that. A lot of the issues you are having were solved in Breezy. Dapper is even a lot better than Breezy but right at the moment is still under development and can occasionaly break. [http://makuchaku.info/amnesty/#downloadguide]("http://makuchaku.info/amnesty/#downloadguide")
This is the guide for Breezy. Stay with it, it is worth the extra effort. Good Luck.

---

### Post by penywise on 2006-04-28
wow... can I get all the info I need from that BG mirror? (yes, BG is the code of Bulgaria)

My connection inside Bulgaria is like 400 kb/sec.. and my International one varies at an avarage of 5 kb/sec

And afterwards should I change back to those repositories that in the guide site, or I can stay with those bg mirrors?

For that CD line the sources.list file - I will check and do everything as soon as I get back home

Thanks a lot
(PS I posted such topic in the Repositories part of the forum here, as it was more targeted for that problem, and got the same answer... there I wrote some other stuff as well)
10x again8)

---

### Post by penywise on 2006-04-28
I have a problem with writing in Bulgarian...
I can read cyrillic when some writes me, but how can I add "Bulgariant language" and switch between it and the default one (english)

Ubuntu 5.04, no Control Center (I looked everywhere on the system - there is no such thing...)

---

### Post by Bloch on 2006-04-28
Hi Penywise;
Yes, you will have to learn a bit about the terminal if you want to be a systems administrator. The terminal on ubuntu uses the "bash" shell (bourne again shell). There are some other, older shells. But people often use the words "terminal" "bash shell" or "command line" interchangeably.
The bash shell is used on almost all linux systems, so you can use any guide to it, or get a book about it.

ubuntu tries to make many things possible through the GUI (graphical user nterface) and Dapper Drake continues this trend. Pretty much everything you do by clicking on the menus can be done by a command at the terminal. Because it is easier to tell a person to type "apt-get install dillo" than to click on Administration, then click on . . . . a lot of the help on these forums uses the terminal.

My advice is for you to look on this month as a period of learning and then install a fresh copy of Dapper Drake when it is released on June 1. Most people on the forums now are probably using Breezy (the current release) and are not too sure what applies to Hoary Hedgehog. A fresh install will always be easier than trying to update. And trying to update from Hoary hedgehog --> Breezy Badger --> Dapper Drake is guaranteed not to be simple!! (and it could even be a bigger download than downloading Dapper Drake)

To see what languages you have installed, System --> Log out and choose Log out (rather than shutdown restart or hibernate)
You will be returned to a screen where you will have a choice of languages for the session. If Bulgarian is not there then you need too install it (using synaptic). 
I switch my sessions between English and Polish. I believe there is a way to switch language in the middle of a session, without Logging out,  but I haven't been able to manage it. 
Is it enough for you to be able to Log out and then Log in using a different language? It takes about 15 -20 seconds.

There is no control centre on ununtu. There are just the System Administration programs you can see on the menu.
My advice is to either get Breezy Badger or wait a month and get Dapper Drake. If you have constant broadband and want to experiment then you can do both. But don't break your head trying to get Hoary Hedgehog working perfectly - in a couple of months no-one on the forum will be using it and will have difficulty helping you.

---

### Post by penywise on 2006-04-28
Cool, I found some quite useful info in your post, thanks for that!

Few questions about it:
That Dapper... I will have to format and install it as a new "thing", deleting the 5.04 right? That's fine with me.. as you said - it will be a month of learning.

The language changes -> Upon Log Out -ing all the programs will be terminated right? Cause Log Off, change to Bulgarian, Log In, write here and there (forum and chat for example), then switching back so I can run the terminal, etc... it's not worthed...

I saw a thread here these days, a guy asked for a way of quick changing the language without needing to log out... I will look for it and read it again.

---

### Post by Bloch on 2006-04-28
You might have already seen the thread started by amubu. He just installed Greek on his system.
When you Log out the current "session" will end. All programs end except the low level system operations. I understand now that Bulgarian uses the Cyrillic alphabet, so you can't write on this forum when the session is set to Cyrillic. It's asking a lot to be able to switch completely in the middle of a session! I guess if it's not on the ubuntu menu then it might not be easy, but I'm sure some people have done it.


Yes, when you install Dapper it will wipe out everything. There are many people talking about "apt-get upgrade" to install Dapper. This is because they don't want to wipe out all the programs and settings they have made. However all these people are upgrading from Breezy. many will have minor problems when they upgrade, but when you don't have knowledge, every problem is major. 
It is always better to have a clean new installation, then get easyubuntu - I think it is a puzzle for some beginners why mp3s dvds mpegs etc cannot be played using a fresh installation of ubuntu. If you have Hoary then you have to use an older version of easyubuntu. (you see how things are more difficult when you have an old version of ubuntu?)

Also when you have an older installation disk, there will be a lot more automatic updates. I use the standard sources list and I am in Ireland. It works fast enough for me. But I am sure I could find a "mirror" of those sources in the UK (or maybe even in Ireland)  that would work faster.

---

### Post by Bloch on 2006-04-28
Here is the website which will give you the "mirror" closest to your country. As the word suggest, it is simply a copy of the repositories.
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
I ran it for choosing Bulgaria and Hoary and the sources are below.
The lines beginning # are comments and don't matter to apt-get

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) hoary universe multiverse
deb [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) hoary-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse

---

### Post by penywise on 2006-04-28
penywise@penywise:~$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  language-support-en: Depends: mozilla-firefox-locale-en-gb but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
penywise@penywise:~$


The update was done just fine...

Then when I try to use ANY command with "sudo apt-get..." -> I get this message...

It's the "n"-th time to change the repositories...

](*,)

---

### Post by gingermark on 2006-04-28
The sources.list Bloch gave you is for Hoary.

Penywise, can you confirm if you upgraded or not?? If you upgraded to Breezy, then that sources.list is wrong. In that case use the source-o-matic (again, as I said before, the link is in my signature) to make a Breezy one, as I can imagine any you have on your system will be a bit of a mess by now.

---

### Post by Bloch on 2006-04-29
Penywise is running Hoary, I believe.
Penywise, you should really try to get your hands on a Breezy Badger installation disk. People are going to assume you have Breezy and give you conflicting advice. The kind of technical people who can give good advice will have moved to Breezy long ago.
 It is possible to upgrade from Hoary to Breezy, but I understand your internet connection is very slow. A complete new download of the current version is the best option. 
Or else you can wait for June 1 and the new release of Dapper Drake.
Do you have a CD-burner?

Don't worry about reinstalling. People do it all the time :-) It can be easier to reinstall than fix a broken system. 

The continued existence of 
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
is a criminal offence. It should have OUTDATED in big letters over it. How many people using Breezy have wrecked their systems using this????
Once again, most people don't have to go through this agony of trying out different sources. They use easyubuntu at the beginning.

---

