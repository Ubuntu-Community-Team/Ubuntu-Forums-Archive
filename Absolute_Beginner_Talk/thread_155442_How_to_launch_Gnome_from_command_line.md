---
title: "How to launch Gnome from command line"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by SteveHoffmanUK on 2006-04-05
Have installed Dapper and am command line. How do I start Gnome?

---

### Post by trent dillman on 2006-04-05
sudo /etc/init.d/gdm start

---

### Post by SteveHoffmanUK on 2006-04-05
Hmm

```
sudo: /etc/init.d/gdm: command not found
```

---

### Post by trent dillman on 2006-04-05
ok, you need the desktop environment installed.

sudo apt-get install ubuntu-desktop

---

### Post by SteveHoffmanUK on 2006-04-05
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-desktop

```

---

### Post by trent dillman on 2006-04-05
wiki.ubuntu.com/AddingRepositoriesHowto

---

### Post by SteveHoffmanUK on 2006-04-05
> wiki.ubuntu.com/AddingRepositoriesHowto

Hmmm. All the instructions in the Wiki are in the form of screen shots of Gnome. My problem of course is that I can't follow them without Gnome up and running. Any other suggestions?

Trent: I really appreciate your help and am not trying to be difficult!

---

### Post by meborc on 2006-04-05
are you sure you don't have gnome installed?
you tried: **sudo /etc/init.d/gdm start** with start? ... start is important :)

if you don't you can add the repositories manually from the command line...

first do:
**sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup**
to back up your sources list

then do
**sudo nano /etc/apt/sources.list**
to edit it and make it look like this... 
**[COLOR="DarkRed"]EDIT: took away the link, it was for breezy, follow the instructions on the second page![/COLOR]**

to save press ctrl+x and then y (for yes)

now
**sudo apt-get update**
**sudo apt-get install ubuntu-desktop**
to install gnome ;)

---

### Post by SteveHoffmanUK on 2006-04-05
> are you sure you don't have gnome installed?


I don't know whether I have Gnome installed or not. All I know is that I successfully boot Dapper but Gnome never appears. All I get is the command line blinking at me. Why would Dapper not come with Gnome?

How do I find out if Gnome is already installed?

---

### Post by meborc on 2006-04-05
well... you could do 
**ls -a**

to see if you have .gnome folder in your home...

if you installed the normal version of dapper, then the gnome is installed... there might be problem with your video-card drivers...

try 

**dpkg-reconfigure -phigh xserver-xorg**

EDIT: also, what happens if you type **startx**

---

### Post by SteveHoffmanUK on 2006-04-05
meborc: thanks for your help

> well... you could do
ls -a

```
.     .bash_history   .bash_profile  .sudo_as_admin_successful
..    .bash_logout  .bashrc
```

Looks like it's not there? I installed the normal (Flight6) version of Dapper without any changes and, as far as I could tell, successfully.

> try

dpkg-reconfigure -phigh xserver-xorg

Results:

```
Package 'xserver-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files, 
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed

```

---

### Post by meborc on 2006-04-05
ok... then do the steps i posted earlier... BUT i gave the wrong link to the sources.list... it was for breezy... so follow these steps:

first do:
**sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup**
to back up your sources list

then do
**sudo nano /etc/apt/sources.list**
to edit it and make it look like this... 

[B]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse[/B]

to save press ctrl+x and then y (for yes)

now
[B]sudo apt-get update
sudo apt-get install ubuntu-desktop[/B]

---

### Post by SteveHoffmanUK on 2006-04-05
Before anyone asks the obvious question:
"What is a beginner doing loading Dapper anyway?" (good question), the answer is that when I load Breezy, it hangs at Installing Hotplug thingeys. I found a message from someone who had that problem and said that it doesn't happen with Dapper.

The workaround for the Breezy problem involves cancelling the hotplug function, but that messes up (or can mess up) networking. The whole object of this exercise is to get my laptop onto my wireless network, so that doesn't sound to me like a good workaround for my situation.

Catch-22 anyone?](*,)

---

### Post by Mustard on 2006-04-05
If your networking was not setup during the install, then its not going to be able to download ubuntu-desktop from the online repositories.  The packages for ubuntu-desktop are on the CD though, so you would need an entry in your sources.list that refers to the CD.  I think you would then need to run apt-get with just the CD source enabled (no internet sources enabled).

To add a CD rom to your sources.list you would use the apt-cdrom command.  The manual for this command can be found with this command.

```
man apt-cdrom
```

---

### Post by SteveHoffmanUK on 2006-04-05
[QUOTE=meborc]ok... then do the steps i posted earlier... BUT i gave the wrong link to the sources.list... it was for breezy... so follow these steps: [COLOR="Red"][snip][/COLOR] [/QUOTE]

But doesn't this assume that I have Internet access (all those "http"s)? 
I don't on the machine I'm trying to install Ubuntu on. I'm using an XP machine for this forum.

---

### Post by meborc on 2006-04-05
yeah... i got carried away there :mrgreen: ... i don't know how you managed to install Dapper without gnome... are you sure you didn't do the SERVER install? it sure looks like it...

i would try to reinstall then from the cd...

sorry, thought you had internet cable connected (if you can do that you can get your internet working from the command line)

---

### Post by SteveHoffmanUK on 2006-04-05
Mustard wrote:
> If your networking was not setup during the install, then its not going to be able to download ubuntu-desktop from the online repositories. The packages for ubuntu-desktop are on the CD though, so you would need an entry in your sources.list that refers to the CD. I think you would then need to run apt-get with just the CD source enabled (no internet sources enabled).

You've got it. However, I'm a beginner, so could you do a step-by-step for me? How to put that entry in my sources.list that refers to the CD? How to enable the CD source? I'm getting in deeper and deeper; glug glug. :)

---

### Post by SteveHoffmanUK on 2006-04-05
meborc wrote:
> are you sure you didn't do the SERVER install? it sure looks like it...

i would try to reinstall then from the cd...

If I did a server install, it was surely unintentional. As far as I know, it was a straightforward, plain old vanilla client install. HOWEVER, I agree that a reinstall might be the best approach.

I'm off to reinstall; fingers crossed. Thanks everyone for your help.

---

### Post by Mustard on 2006-04-05
[QUOTE=SteveHoffmanUK]Mustard wrote:


You've got it. However, I'm a beginner, so could you do a step-by-step for me? How to put that entry in my sources.list that refers to the CD? How to enable the CD source? I'm getting in deeper and deeper; glug glug. :)[/QUOTE]

I think if you just run the apt-cdrom command with no options it might work. :)  I'm guessing here, as I haven't used it myself. ;)

Assuming that you would do this..
```
sudo apt-cdrom add

#I suspect this will need superuser privileges
#hence the use of the 'sudo' command
```

Once you have added it successfully, you would need to edit the sources.list and put a '#' symbol in front of all the 'sources' that are trying to connect to the internet.  This will essentially disable them, as anything that follows a '#' symbol is considered to be a comment within the configuration file.

To edit the sources.list file..

```
sudo nano /etc/apt/sources.list
#opens the sources.list file in a text editor (command line)
```

Comment out the internet related lines from the sources.list with a # symbol, and only leave the reference to the cdrom in place.

Use ctrl + o to save the file, and ctrl +x to exit the nano editor.

Then..

```
sudo apt-get update
#updates the package list from the sources listed in sources.list file
```

Then..

```
sudo apt-get install ubuntu-desktop
#installs all packages referred to by the ubuntu-desktop meta package
```

Then..

```
sudo /etc/init.d/gdm start
#starts the gnome desktop manager
```

---

### Post by Mustard on 2006-04-05
[QUOTE=SteveHoffmanUK]meborc wrote:


If I did a server install, it was surely unintentional. As far as I know, it was a straightforward, plain old vanilla client install. HOWEVER, I agree that a reinstall might be the best approach.

I'm off to reinstall; fingers crossed. Thanks everyone for your help.[/QUOTE]

Doh..I just had it all typed out!! ...hehehe..

I'm hopeful that a reinstall will work too. :)

---

### Post by SteveHoffmanUK on 2006-04-05
I think it's my time to go "doh"

I looked again at the Dapper download page and, yes, I think I must have downloaded the server version. So I am now downloading the client one.

Profuse apologies to you guys for wasting your time. You're all stars. :-D

---

### Post by meborc on 2006-04-05
hey, no problem.. that's why we are here... 

for more help on dapper, look at my sig, there is a link to dapper guide...

and for other questions conserning dapper, refer to the dapper subforum as this is still the beginners forum for ubuntu, and it would not be a good idea to discuss some things here about dapper, which will not work under breezy..

good luck ;)

---

### Post by Mustard on 2006-04-05
[QUOTE=SteveHoffmanUK]I think it's my time to go "doh"

I looked again at the Dapper download page and, yes, I think I must have downloaded the server version. So I am now downloading the client one.

Profuse apologies to you guys for wasting your time. You're all stars. :-D[/QUOTE]

I didn't even know there was a server only install. :)

Normally, you just type, 'server', in at the boot prompt to install the server only.

What is the link to that download page?

---

### Post by SteveHoffmanUK on 2006-04-05
Mustard wrote:
> What is the link to that download page?

Well, at least I can answer that one:
```
http://www.ubuntu.com/testing/flight6
```

---

