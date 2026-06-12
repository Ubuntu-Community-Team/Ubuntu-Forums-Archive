---
title: "apt-get doesnt work 90% of the time"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by Nesagwa on 2005-06-21
The only packages its been able to get are kino and vorbis tools.

Nothing else will work.

Help?

---

### Post by sapo on 2005-06-21
what erros do you get when you try to install and app?

try it before trying to install something:

```
apt-get update
```

And paste the contents of this file /etc/apt/sources.list
so we can take a look at your repositories

---

### Post by Dragonfly_X on 2005-06-21
You have to edit the sources.list file.

Open the terminal and type

sudo chmod 777 /etc/apt/sources.list

Then close the terminal window and then navigate to your filesystem and open these folders "etc" and then "apt" in witch you will find sources.list, open this file and uncomment the lines by removing the hash infront of the line. the the contents of the file should look like this when u r done.


deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) hoary main restricted 
## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) hoary-updates main restricted 
deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) hoary-updates main restricted 

## Uncomment the following two lines to add software from the 'universe' 
## repository. 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted 
deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) hoary universe 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe



after you have done this, save your changes and run 

sudo apt-get update from the terminal window

---

### Post by Nesagwa on 2005-06-21
Oh, I didnt un comment two of those servers.

But now it wont let me save the sources.list file after I change it.

EDIT:  Nevermind, Fixed it.

Testing it out now.

I keep getting messages like this :

sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386

---

### Post by Nesagwa on 2005-06-21
sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
Package mplayer-386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer-386 has no installation candidate


I dont know why its doing this.  Should have just stuck with windows.  ](*,)

---

### Post by PMO6022 on 2005-06-21
mplayer-386 is in mulitverse.  Do you have that repository in your /etc/apt/sources.list, and is it uncommented?

---

### Post by Nesagwa on 2005-06-21
## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted



Yes.

---

### Post by PMO6022 on 2005-06-21
type  ```
sudo apt-get update
``` 
and try to ```
sudo apt-get install mplayer-386
``` again.

---

### Post by Nesagwa on 2005-06-21
Reading package lists... Done
Building dependency tree... Done
Package mplayer-386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer-386 has no installation candidate


Still not working.

---

### Post by PMO6022 on 2005-06-21
Well, I don't know what to tell you.  It works for me.  Maybe someone else can jump in with some ideas.

---

### Post by Mr. Electric Wizard on 2005-06-21
Already been shut down possibly?

---

### Post by poofyhairguy on 2005-06-21
Hello. Sorry I wasn't here earlier.

[QUOTE=Nesagwa]
I dont know why its doing this.  Should have just stuck with windows.  ](*,)[/QUOTE]

I don't really know how this can be. Something must be wrong with the sources.list that we don't see. No matter.

The question is - why do you want mplayer? It is an so-so media player (in my opinion) and I haven't messed with it since I first installed Ubuntu.

There is one I think is a lot better.

Try this line:

> sudo apt-get install gxine

and run the command "gxine" to get it to work (I made it so that it automatically opens when I click on media files, I can tell you how).

But first, do that and tell me what happens.

---

### Post by chaumurky on 2005-06-21
[QUOTE=Nesagwa]sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
Package mplayer-386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer-386 has no installation candidate


I dont know why its doing this.  Should have just stuck with windows.  ](*,)[/QUOTE]
 see what you have available:

```
 apt-cache search mplayer
```

---

### Post by Xian on 2005-06-21
Post the *entire* output of the commands below. 
I'm specifically interested in what output you get when running 'update'.

```
$ sudo apt-get update
$ sudo apt-get install mplayer-386
```

---

### Post by jdong on 2005-06-21
[QUOTE=Dragonfly_X]You have to edit the sources.list file.

Open the terminal and type

sudo chmod 777 /etc/apt/sources.list[/QUOTE]

**TIME OUT!!!**

chmodding sources.list to 777 has **VERY SERIOUS** security implications. Use **sudo gedit /etc/apt/sources.list** instead.

If you've followed these instructions, revert the change with **chmod 644 /etc/apt/sources.list**.

---

### Post by az on 2005-06-21
[QUOTE=jdong]**TIME OUT!!!**

chmodding sources.list to 777 has **VERY SERIOUS** security implications. Use **sudo gedit /etc/apt/sources.list** instead.

If you've followed these instructions, revert the change with **chmod 644 /etc/apt/sources.list**.[/QUOTE]

Tell it brotha!  I couldn't scroll down this thread fast enough (on a pentium one...) to get to that!

---

### Post by chaumurky on 2005-06-21
[QUOTE=azz]Tell it brotha!  I couldn't scroll down this thread fast enough (on a pentium one...) to get to that![/QUOTE]
 That's like saying "hey everyone, come and redecorate my house - and change the locks too, if you like. Heck, you can even demolish the house! Be my guest"

---

### Post by polo_step on 2005-06-21
[QUOTE=Dragonfly_X]You have to edit the sources.list file...[/QUOTE]
As a quick aside, can anyone explain to me why this file has all the needed data commented-out in the first place?

I've been wondering about that.

---

### Post by chaumurky on 2005-06-21
[QUOTE=polo_step]As a quick aside, can anyone explain to me why this file has all the needed data commented-out in the first place?

I've been wondering about that.[/QUOTE]
 I think it's because universe and multiverse are not supported and verified as stable. It requires the user to activate these repositories at their own risk.

---

### Post by polo_step on 2005-06-21
[QUOTE=chaumurky]I think it's because universe and multiverse are not supported and verified as stable. It requires the user to activate these repositories at their own risk.[/QUOTE]
That would explain it, but it seems that this is the first thing a new user has to do to get a fully-functioning working system up with his customary programs, and it's a real scary thing for a lot of new users who are not used to command lines, let alone modifying files critical to the OS -- think how many people have been taught never, **EVER** to do this in Windows! :)

---

### Post by jdong on 2005-06-21
Only official, 100% Canonical-supported, security/bugfix-wise maintained repository locations are enabled by default. :)

---

### Post by Wolki on 2005-06-21
[QUOTE=polo_step]That would explain it, but it seems that this is the first thing a new user has to do to get a fully-functioning working system up with his customary programs, and it's a real scary thing for a lot of new users who are not used to command lines, let alone modifying files critical to the OS -- think how many people have been taught never, **EVER** to do this in Windows! :)[/QUOTE]

Well you can do all of this with a gui in synaptic. ^^; It takes a longer to explain over the internet, however, and the people here can help better if they have the detailed outputs of command line programs.

---

### Post by TristanMike on 2005-06-21
[QUOTE=polo_step]That would explain it, but it seems that this is the first thing a new user has to do to get a fully-functioning working system up with his customary programs, and it's a real scary thing for a lot of new users who are not used to command lines, let alone modifying files critical to the OS -- think how many people have been taught never, **EVER** to do this in Windows! :)[/QUOTE]
Thanks for saying it.  You're so right.  I've been so bred to the Micoshaft's way of teaching, that even tho I'm told modifying this stuff is ok, and I trust the knowledge, it's a bit frightening.  So getting past that is a big step, sometimes I just open the terminal, staring at it, not wanting to mess my whole system up, yea, I like learning, not that way really.

So when using apt-get, if you find the program in the repositories, you can just type sudo apt-get install (what ever the program name is in synaptic)?

TristanMike

---

### Post by bored2k on 2005-06-21
[QUOTE=TristanMike]So when using apt-get, if you find the program in the repositories, you can just type sudo apt-get install (what ever the program name is in synaptic)?

TristanMike[/QUOTE]

Yes.
Example:

> apt-cache search bittorrent
bittorrent - Scatter-gather network file transfer
bittorrent-gui - Scatter-gather network file transfer (GUI files)
gnome-btdownload - Gnome interface for 'executing' BitTorrent files.
azureus - BitTorrent client 
```
sudo apt-get install azureus
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  azureus
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4657kB of archives.
After unpacking 5280kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  azureus
Install these packages without verification [y/N]?

```

---

### Post by TristanMike on 2005-06-22
Thank You Very Much for clarifying that for me.  That was a huge peice of the Linux puzzle that has now finally been fit together.
TristanMike

---

### Post by bored2k on 2005-06-22
[QUOTE=TristanMike]Thank You Very Much for clarifying that for me.  That was a huge peice of the Linux puzzle that has now finally been fit together.
TristanMike[/QUOTE]
 Rock on. Synaptic can be a slow hassle at times..

Tip: to see info for a certain file:

> breaks@windows:~$ **apt-cache show bittorrent**
Package: bittorrent
Priority: optional
Section: net
Installed-Size: 536
Maintainer: Michael Janssen <jamuraa@debian.org>
Architecture: all
Version: 3.4.2-3ubuntu4
Depends: python (<< 2.5), python (>= 2.4)
Recommends: mime-support
Suggests: bittorrent-gui
Filename: pool/main/b/bittorrent/bittorrent_3.4.2-3ubuntu4_all.deb
Size: 88658
MD5sum: 0afdb6332429d4d8073f78f2e1a5eeef
Description: Scatter-gather network file transfer
 BitTorrent is a tool for distributing files. It's extremely
 easy to use - downloads are started by clicking on hyperlinks.
 Whenever more than one person is downloading at once
 they send pieces of the file(s) to each other, thus relieving
 the central server's bandwidth burden. Even with many
 simultaneous downloads, the upload burden on the central server
 remains quite small, since each new downloader introduces new
 upload capacity.
 .
 This package contains the tools which are used for console-only
 downloading.  If you want the GUI interface, install the
 bittorrent-gui package.
 .
  Homepage: [http://bitconjurer.org/BitTorrent/](http://bitconjurer.org/BitTorrent/)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop 

For more information,
> man apt-get

---

### Post by polo_step on 2005-06-22
If I'd have known how easily programs could be added with apt-get or its shells, I would have been using Linux much sooner.

---

### Post by polo_step on 2005-06-22
[QUOTE=jdong]Only official, 100% Canonical-supported, security/bugfix-wise maintained repository locations are enabled by default. :)[/QUOTE]
The reality-disconnect here, of course, is that all that is just relative at best, especially the bug-free part.

As I said in another thread, all this list-uncommenting is...well...a *load.*

There should simply be a GUI in Synaptic or somewhere with a disclaimer about the repositories, an "I agree" button and the list gets auto-uncommented.  This is trivial programming, and the people doing the distro should be doing that, not the new user.

That's ridiculous.

---

### Post by bored2k on 2005-06-22
[QUOTE=polo_step]If I'd have known how easily programs could be added with apt-get or its shells, I would have been using Linux much sooner.[/QUOTE]
 LOL.
I remember back when I tried Xandros v1. I was sort of OK, until I couldn't find a way to get *somethingX* (don't remember). There I had NEVER installed anything. The second I heard the word "compile" I went bananas. Eventually (**very** short after), I went back to Windows :roll:.

---

### Post by TravisNewman on 2005-06-22
[QUOTE=polo_step]The reality-disconnect here, of course, is that all that is just relative at best, especially the bug-free part.

As I said in another thread, all this list-uncommenting is...well...a *load.*

There should simply be a GUI in Synaptic or somewhere with a disclaimer about the repositories, an "I agree" button and the list gets auto-uncommented.  This is trivial programming, and the people doing the distro should be doing that, not the new user.

That's ridiculous.[/QUOTE]
 Well, he didn't say bug-free, he said bugfix-manitained. So when bugs come up they fix them. 

And there IS a gui in synaptic. Go to repositories and check the boxes.

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=polo_step]
There should simply be a GUI in Synaptic or somewhere with a disclaimer about the repositories, an "I agree" button and the list gets auto-uncommented.  This is trivial programming, and the people doing the distro should be doing that, not the new user.
[/QUOTE]

You can do it in synaptic. We always tell people the command line way because its all copy and paste and it error proof almost. Plus personally I like for people to not be scared of the cli (and telling them "copy this line" is easier than pages of screenshots with circled areas).

Go to "settings" then "repositiories." Then you can add or edit all you like.

I think it even says something like "this is unofficial" when you add those repos.

---

### Post by polo_step on 2005-06-22
[QUOTE=poofyhairguy]We always tell people the command line way because its all copy and paste and it error proof almost. Plus personally I like for people to not be scared of the cli (and telling them "copy this line" is easier than pages of screenshots with circled areas).

Go to "settings" then "repositiories." Then you can add or edit all you like.
[/QUOTE]
Well, cool.

I was shocked that I could cut & paste command lines into terminal.  After all those years of entering hideous long uneditable command lines in CP/M and MSDOS only to find a typo in the fifth character sort of burned me out on command line stuff.

When dealing with new users from Windows, you should always at least *mention* that there's a GUI way to do something, but that command line is quicker, more foolproof or whatever.  It keeps them from being totally freaked out.

Seems like doing this particular task in synaptic might actually be faster and  less hassle; I managed to initially screw up the editing of the list and it caused me some trouble later.

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=polo_step]
When dealing with new users from Windows, you should always at least *mention* that there's a GUI way to do something, but that command line is quicker, more foolproof or whatever.  It keeps them from being totally freaked out.
[/QUOTE]


Deal.

---

