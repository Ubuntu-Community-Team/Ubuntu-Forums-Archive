---
title: "Ex xp user questions about file system/programs"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-05-07
This is kind of a vague thread I guess but I am trying to get a handle how ubuntu organises its files/programs/hard disks and things.

I have a fairly long history with XP and the like but have recently seen the light and have come over to ubuntu and am totally converted. I dont really understand much of the linux terminology. Should any of this sound critical its genuinely not meant to.

I have various things like Gaim, firefox and thunderbird running so for day to day net use I am more or less ok.  I can mange to install and remove programs but I would like to know what is acctually happening.

First question,  What is the difference between Add/Remove, Automatix2 and the synaptec package manager? They all seem to do more or less the same thing to me. 

Second question, I have my HD formated to dual boot XP so I have 4 partitions first is an NTFS partition with windows, second is an ntfs partition with all my documents and mp3s and stuff on, third is my swap partition and fourth is my ubuntu (feisty) install. 

The windows partition appears to be called sda1 and the second ntfs partion is called "media" as I named it under my XP install. These both appear on my desktop for some reason, can I remove them from the desktop as the both seem accessible from the "places" menu. I think I will need to reformat the "media" disk to ext3 to use the data in ubuntu?

The ubuntu disk seems to be called "filesystem" but I cant find it under "places" instead I can see "documents" which I guess is like "my documents" from windows? and something else called "home" which I am guessing is like "documents and settings"? "home" seems to include a folder called "myusername" which in turn has a random bunch of files and folders from my windows "documents and settings" folder but nothing like profiles for gaim or firefox or thunderbird which I was expecting. 

The profiles would be very handy to find as I am trying to point the useful looking mail notification tool at my thunderbird inbox but cant find the profile.

Lastly (promise!) my C: drive contained a folder called "programs" with all my software in it but I can find an equivalent for ubuntu. I guess I dont NEED this as everything is easily accesible from the applications tab but I am curious.

Thanks for anyone who stuck with my through all that!

I am trying to point the rather handy mail notification tool at my thunderbird inbox but I can

---

### Post by rich.bradshaw on 2007-05-07
"First question, What is the difference between Add/Remove, Automatix2 and the synaptec package manager? They all seem to do more or less the same thing to me."

Nothing really - they are all interfaces for apt, the package manager that deals with software installation with Ubuntu. Automatix isn't officially supported, and can break things as it adds extra repositories that aren't supported.

"Second question, I have my HD formated to dual boot XP so I have 4 partitions first is an NTFS partition with windows, second is an ntfs partition with all my documents and mp3s and stuff on, third is my swap partition and fourth is my ubuntu (feisty) install.

The windows partition appears to be called sda1 and the second ntfs partion is called "media" as I named it under my XP install. These both appear on my desktop for some reason, can I remove them from the desktop as the both seem accessible from the "places" menu. I think I will need to reformat the "media" disk to ext3 to use the data in ubuntu?"

You don't need to reformat. Ubuntu can read NTFS by default, it needs to download drivers to write to the drives.

In feisty (probably others, but Feisty is the newest and hence easiest!) Search for ntfs 3g in add/remove programs and install if you want to write to these drives.


"The ubuntu disk seems to be called "filesystem" but I cant find it under "places" instead I can see "documents" which I guess is like "my documents" from windows? and something else called "home" which I am guessing is like "documents and settings"? "home" seems to include a folder called "myusername" which in turn has a random bunch of files and folders from my windows "documents and settings" folder but nothing like profiles for gaim or firefox or thunderbird which I was expecting."

/home/yourusename is the equivalent of Documents and Settings, except it much simpler to get to! Contains all your settings and files. Hidden files in Linux start with a full stop, there are lots of directories in there with your settings such as .gnome, .firefox etc. This means that you can c opy settings around very easily.

Programs are stored in /bin, /sbin or /usr/bin depending on whether they are system binaries, user binaries etc. You never need to manually find these unless you are programming software, so it doesn't really matter.

All system configuraion files are in /etc, which you may need sometimes. 

"The profiles would be very handy to find as I am trying to point the useful looking mail notification tool at my thunderbird inbox but cant find the profile."

~/.mozilla-thunderbird

A hidden file in your home directory. ~/ means home, . means it's hidden by default. In the file manager you can choose view/ hidden files to let you see them.

"Lastly (promise!) my C: drive contained a folder called "programs" with all my software in it but I can find an equivalent for ubuntu. I guess I dont NEED this as everything is easily accesible from the applications tab but I am curious."

Again, /bin, /sbin, /usr/bin no need to every touch this manually for 99% of users...

---

### Post by Cypher on 2007-05-07
OK..When you install a program, and do so the "apt-get"/"aptitude"/Synaptec Package Manager way then you are downloading a .DEB file from a repository somewhere. There are a set of standard Ubuntu repositories managed by the good Ubuntu folks that contain all of the OS files. There are numerous other people who've created their own repositories for other files that you could download.

When a .DEB file is installed, it contains within in essentially 2 things. One is a compressed 'tarball' of the files with their directory structure in tact. The second is a series of scripts that perform various actions (stop services, remove previous versions) before the installation happens and more actions after (start services, run configuration tool, etc)

Once the package is properly installed, you will find the newly installed item in many locations (Add/Remove Program, Synaptic Pkg Mgr, "dpkg -l") and so on. From the command line you can easily query the contents of each packge which will tell you where they are located.

Add/Remove and Synaptic Pkg Mgr are Ubuntu creations to install packages. They do both essentially provide the same functionality, but it looks like Add/Remove is less powerful than Synaptic and will relegate work to the latter whenever it can't do something.

Automatix2 is a third-party installer tailored to install/remove packages that the previous two don't handle.

I'm going to skip the question about how to remove your Windows partitions from the desktop, as I don't know. :) But as far as accessing your media partition goes, you don't have to reformat. You just need to get the "ntfs-3g" package and you can easily ready from the media partition.

When you create a new user, a new directory with their username is created in the "/home" directory. This is their home directory and will contain all of their files, programs and customizations. This could be equivalen to "Document and Settings/<User>" under WinXP. All programs are usually installed under "/usr" and this could be the same as "Program Files" in WinXP.

I'm going to skip the mail notifcation ques., as I have no clue.

---

### Post by rich.bradshaw on 2007-05-07
Oh yeah, to get rid of drives showing on desktop, you can run

gconf-editor

which you may have to install using sudo apt-get install gconf-editor

run gconf-editor, go to apps/nautilus and find the bit about showing drives on the desktop.

gconf-editor is a GUI to let you edit some common gnome configuraiton files.

---

### Post by tabithaboof on 2007-05-07
Wow! That was incredibly informative and helpful, thanks very much to everyone who contributed. I solved a couple of problems I had and managed to get a pretty firm grip on my new OS. Thanks alot!

---

