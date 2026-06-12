---
title: "I have no clue what to do..."
date: 2005-06-26
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-06-26
I just installed ubuntu as I have had enough of Windows. I can't do anything....literally...I can use pre-installed apps etc but I can't install anything. I have downloaded stuff to "desktop" which does not appear on the desktop. And even once I found it I don't know what to do with it.

What is the command line for installing a program located on the desktop?

According to sound monitor my Audigy 2 is installed but CD player loads and starts playing a CD but I have no sound.

I have a dual monitor set up on a radeon 9800 pro that I can't use.

I have 20gb of mp3's on my iAudio M3 DAP that I can't access because according to the file explorer my M3 has no file system...

The beginners guide just is not beginner enough!

All help / advice greatly appreciated.

---

### Post by Sionide on 2005-06-26
What file types have you downloaded? *.deb files? .rpm files? .tar.gz files even??


Have you been reading the Ubuntu Guide at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

Follow these instructions; [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Now run "Synaptic" - go to System->Admin->Synaptic Package Manager

This program will update all your systems programs...

Try using the search button on the forums / [wiki](http://wiki.ubuntu.com) :)

Try looking elsewhere online for "Linux for Newbies" to understand the very basic basics of using Linux. You'll soon get the hang of it!

---

### Post by royg1234 on 2005-06-26
[QUOTE=gammyhand]I just installed ubuntu as I have had enough of Windows. I can't do anything....literally...I can use pre-installed apps etc but I can't install anything. I have downloaded stuff to "desktop" which does not appear on the desktop. And even once I found it I don't know what to do with it.

What is the command line for installing a program located on the desktop?
[/QUOTE]

I'm kind of new also, so this is all I can help you with.

First thing you should do is add the extra repositories as per the guide.  Easiest way to do this: Go into the terminal:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```
and replace this file's contents with the  guide's [sample](http://www.ubuntuguide.org/sample/sources.list_extrarepositories).

Best way to install apps now is via Synaptic.  Or if what you're looking for's not there, search for it in Debians (this should be pre-installed in Firefox search bar--the reddish swirl).  And to install these *.debs you go into the terminal and type:

```
sudo dpkg -i Desktop/package*.deb
``` 

where "package" denotes the name (the * is so you don't have to get confused with the version numbers and stuff).  And this is assuming you downloading the *.deb straight onto the desktop.

And if you don't know what to look for, the stuff recommended in the [guide](http://www.ubuntuguide.org/) is all high-quality stuff.

Of couse, there are some of the more esoteric programs that you have to complie yourself.  That I haven't messed around with yet.

---

### Post by aysiu on 2005-06-26
Whoa! Slow down. One problem at a time. First of all, I have to say that I love Ubuntu. It is a great distribution. However, it is not for everyone (no distro can be for everyone). Consider... consider trying something else (maybe Mepis--it's a little more bloated and there's less support, but it's fully GUI and relies very little on the command line).

Okay, that said...

1. There's some weird quirk with Firefox in Linux I've found. Even if it says "Desktop" is the default location for downloads, it may not actually go there. Instead of picking "Desktop," choose a new download location and click on "home," your username, then "Desktop." You'll notice that instead of saying *Desktop*, it'll now say */home/username/Desktop*. Now things will download to your actual desktop.

2. Can you explain why you're downloading programs to your desktop to install? Can you not find them through Synaptic Package Manager? Name the program, and most likely it'll be in the Ubuntu repositories (you may have to enable extra repositories, though). Installing programs through Synaptic or apt-get is far easier than downloading a .deb or .rpm and installing it that way.

3. All of your other problems are most likely addressed in

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

If you think that isn't beginner enough for you, honestly... try another distro. The command-line isn't so bad. It's actually quite easy. You just cut and paste the commands. I think eventually you may find your way back to Ubuntu, but if you're truly afraid of the command-line, I'd start with Mepis first.

---

### Post by gammyhand on 2005-06-26
[QUOTE=aysiu]Whoa! Slow down. One problem at a time. First of all, I have to say that I love Ubuntu. It is a great distribution. However, it is not for everyone (no distro can be for everyone). Consider... consider trying something else (maybe Mepis--it's a little more bloated and there's less support, but it's fully GUI and relies very little on the command line).

Okay, that said...

1. There's some weird quirk with Firefox in Linux I've found. Even if it says "Desktop" is the default location for downloads, it may not actually go there. Instead of picking "Desktop," choose a new download location and click on "home," your username, then "Desktop." You'll notice that instead of saying *Desktop*, it'll now say */home/username/Desktop*. Now things will download to your actual desktop.

2. Can you explain why you're downloading programs to your desktop to install? Can you not find them through Synaptic Package Manager? Name the program, and most likely it'll be in the Ubuntu repositories (you may have to enable extra repositories, though). Installing programs through Synaptic or apt-get is far easier than downloading a .deb or .rpm and installing it that way.

3. All of your other problems are most likely addressed in

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

If you think that isn't beginner enough for you, honestly... try another distro. The command-line isn't so bad. It's actually quite easy. You just cut and paste the commands. I think eventually you may find your way back to Ubuntu, but if you're truly afraid of the command-line, I'd start with Mepis first.[/QUOTE]
 Thanks everyone. I am not at all afraid of the command line. My actual *nix commands are not that bad as I am a web developer and our servers are all *nix. However I have never used the *nix platform as an operating system and I have no idea how it works. I was unaware you had to install a file in order to install it for example.

I was downloading the files to the desktop because it was default and as nothing appeared on the desktop started debugging at the download process and not the file path. 

I think it is the firefox bug you talk about :)

I have heard good things about Ubuntu and even if I was afraid of the command line I don't see the point in giving up at the first hurdle.

---

### Post by Kvark on 2005-06-26
To answer 2 of those questions...

[QUOTE=gammyhand]What is the command line for installing a program located on the desktop?[/QUOTE]
With a root terminal the command is:
apt-get install programName

With a normal terminal, add sudo in front of the command. So for example to install for example the chat program kopete from a normal terminal:
sudo apt-get install kopete

The synaptic package manager does the same thing as apt-get but with a graphical interface, cathegories and search function. You don't need to download the program before installing it. You will however need to do this to make apt-get/synaptic find most of the programs:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

[QUOTE=gammyhand]I have a dual monitor set up on a radeon 9800 pro that I can't use.[/QUOTE]

You need to install drivers for your video card. I use nivida so only 95% sure but I think the ati drivers are called xorg-driver-fglrx, so just do:
sudo apt-get install xorg-driver-fglrx

---

### Post by aysiu on 2005-06-26
What an awesome attitude!

Yeah, go for it. Ubuntu is a great distro, and the Ubuntu Guide answers almost all newbie questions. Let us know how it goes!

---

### Post by Kvark on 2005-06-26
[QUOTE=gammyhand]I have a dual monitor set up on a radeon 9800 pro that I can't use.[/QUOTE]

You need to install drivers for your video card. I use nvidia so only 95% sure but I think the ati drivers are called xorg-driver-fglrx.

---

### Post by gammyhand on 2005-06-26
[QUOTE=aysiu]What an awesome attitude!

Yeah, go for it. Ubuntu is a great distro, and the Ubuntu Guide answers almost all newbie questions. Let us know how it goes![/QUOTE]
 Well...I am guessing it will go slowly :)

I have been a windoze user for about 13 years or so so old habits die hard.

Stupid question 1...does linux support MP3 files or will I need to convert everything to OGG?

I think I will go print out the ubuntu guide :)

---

### Post by Kvark on 2005-06-26
[QUOTE=gammyhand]Stupid question 1...does linux support MP3 files or will I need to convert everything to OGG?[/QUOTE]

All file types works on linux, if you can find a linux program that can open them, or manage to run a windows program that can with Wine.
(...I bet now you think "ahh even .exe files work, you just gotta use Wine for those.", don't get too excited though, many windows programs run less well in an emulator then then on real windows)

---

### Post by Sionide on 2005-06-26
And that program, if you used Winamp under Windows? Will be "XMMS"

Go to Synaptic as explained before and search for "xmms" - install that program and it'll install all the bits and bobs needed to play mp3s - that's what I found when I tried first time :)

Ps. The Ubuntu Guide is *long* - I wouldn't print it, unless it was at school/work on their ink and paper :P

---

### Post by gammyhand on 2005-06-26
[QUOTE=Sionide]And that program, if you used Winamp under Windows? Will be "XMMS"

Go to Synaptic as explained before and search for "xmms" - install that program and it'll install all the bits and bobs needed to play mp3s - that's what I found when I tried first time :)

Ps. The Ubuntu Guide is *long* - I wouldn't print it, unless it was at school/work on their ink and paper :P[/QUOTE]
 I will leave it printing overnight then. My home laser does 28ppm in mono (about 0.001 in colour!).

---

### Post by aysiu on 2005-06-26
[QUOTE=gammyhand]
Stupid question 1...does linux support MP3 files or will I need to convert everything to OGG?

I think I will go print out the ubuntu guide :)[/QUOTE]

First, try this:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Then, try this:

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

Then, you should be all set with MP3 support.

---

### Post by davidgypsy on 2005-06-26
This is the best Linux distro there is, nothing else seems quite the same when you have used it a while. I know the feeling though, went through a steep learning curve for a while, but now I can't imagine going back to windows.

---

### Post by gammyhand on 2005-06-26
[QUOTE=aysiu]First, try this:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Then, try this:

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

Then, you should be all set with MP3 support.[/QUOTE]
Thanks. I am more worried about my iAudio M3 not working under Ubuntu at the moment :(

---

### Post by monchichi on 2005-06-26
the iAudio MP3 should just be detected as a usb hard drive.. try running the following in a terminal to see if the kernel is loading the applicable module:```
lsmod | grep usb-storage
```If it returns "usb-storage" then the module is loaded. If it returns nothing, then the module is not loaded and you should run ```
sudo modprobe usb-storage
``` to load it. ;-) then the device node should come up in /dev/usb/, check for it by running ```
ls /dev/usb/*
``` Then let us know what happens :)

edit: oh wait my bad, after rereading your post I guess the device is detected but not the filesystem... try running the following in a terminal, but replacing the sd0 with whatever the applicable device node is: ```
sudo mkdir /media/mp3player;sudo mount /dev/usb/sd0 /media/mp3player
```

---

### Post by royg1234 on 2005-06-26
[amaroK](http://amarok.kde.org/)  <-- In my correct opinion, the best media player anywhere.

---

### Post by gammyhand on 2005-06-27
[QUOTE=monchichi]
edit: oh wait my bad, after rereading your post I guess the device is detected but not the filesystem... try running the following in a terminal, but replacing the sd0 with whatever the applicable device node is: ```
sudo mkdir /media/mp3player;sudo mount /dev/usb/sd0 /media/mp3player
```[/QUOTE]
Thanks. Will I lose the MP3's on my player though?

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=gammyhand]Thanks. Will I lose the MP3's on my player though?[/QUOTE]

No. Those commands will make a directory (mkdir) for the player to be mounted so you can access it (mount).

---

### Post by gammyhand on 2005-06-27
[QUOTE=poofyhairguy]No. Those commands will make a directory (mkdir) for the player to be mounted so you can access it (mount).[/QUOTE]
But the player is already mounted as USB0 in the file explorer. I just can't browse it. Would mounting it to another directory change that then?

---

### Post by monchichi on 2005-06-30
Ooooopps, its already mounted. 

So, either you dont have correct permissions, or it's not detecting the correct filesystem. Try in a terminal: ```
sudo ls /media/usb0/
```and if it shows you the contents, then it's a permissions issue.

Otherwise, unplug and plug the thing in and type ```
dmesg | tail
``` to see if there's any fishy business when it mounts the filesystem.

---

### Post by gammyhand on 2005-06-30
[QUOTE=monchichi]Ooooopps, its already mounted. 

So, either you dont have correct permissions, or it's not detecting the correct filesystem. Try in a terminal: ```
sudo ls /media/usb0/
```and if it shows you the contents, then it's a permissions issue.

Otherwise, unplug and plug the thing in and type ```
dmesg | tail
``` to see if there's any fishy business when it mounts the filesystem.[/QUOTE]
 Can you just confirm that neither of those commands are destructive please. I only have my mp3's on my mp3 player and can't afford to lose them.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=gammyhand]Can you just confirm that neither of those commands are destructive please. I only have my mp3's on my mp3 player and can't afford to lose them.[/QUOTE]


One links a file (tells another file its there) and the other is checking to see if the computer even recognizes the player.

---

