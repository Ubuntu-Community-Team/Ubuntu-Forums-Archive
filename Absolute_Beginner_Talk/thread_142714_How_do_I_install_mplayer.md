---
title: "How do I install mplayer"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by UbuntuPhil on 2006-03-11
Cause Totem isn't playing jack for me.

It's not listed in the SPM.

I went to the site but have no clue, why is it so difficult?

---

### Post by eriefisher on 2006-03-11
First make sure you have a good sources.lst [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

sudo apt-get update
sudo apt-get install mplayer

this should work

eriefisher

---

### Post by UbuntuPhil on 2006-03-11
I got this.....

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```

Soooooo where does this go?

---

### Post by akiro.yamamoto on 2006-03-11
that file goes to /etc/apt
;)

Edit:
Ok if you saved the file to your Desktop the following should work for you:
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
sudo cp /home/user/Desktop/sources.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get install mplayer

```

Hope this helps ;)

Edited for clarity ;)

---

### Post by UbuntuPhil on 2006-03-11
Isn't it supposed to go into a text file IN that directory, I'm lost.

---

### Post by eriefisher on 2006-03-11
Open up a terminal and type:
sudo gedit /etc/apt/sources.lst

compare whats in there with what you generated and add or modify it. Click on the save button at top and close the window then do:

sudo apt-get update  (this will reload the package list)
sudo apt-get install mplayer (this will install whatever package you name)

There is also a way to back up your sources list before you play with it but I will have to find the line to enter for that, I will look.

eriefisher

edit:I got beat to it(not fast enough I guess)

---

### Post by UbuntuPhil on 2006-03-11
And why can't the default Totem install play ANY .avi or .mpg files?

---

### Post by akiro.yamamoto on 2006-03-11
Hmmm....
It can, I use totem-xine with the w32codecs for my dvd and multimedia playback.

---

### Post by eriefisher on 2006-03-11
The source list generator should give you the repos for codecs such as w32codecs and lame for mp3s. You probably need libdvdread and libdvdcss etc.
Search the guide and the wiki for different codecs to install.

eriefisher

---

### Post by UbuntuPhil on 2006-03-11
Where those codecs included in the default Ubuntu install?

Cause I can play nada

---

### Post by UbuntuPhil on 2006-03-11
```
philhanson@ubuntu:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer

```


????

---

### Post by akiro.yamamoto on 2006-03-11
Nope! You have to install them seperately....
Check the first link in my sig for more info...
read up on the Restricted Formats section! ;)

---

### Post by UbuntuPhil on 2006-03-11
Am I doomed on this mac, the package I get from those instructions is for 1386, I have a Power PC CPU.

:(

---

### Post by akiro.yamamoto on 2006-03-11
Why not use Synaptic to do your software install?
It should make it a little easier!
Here's a shot of mine.

---

### Post by UbuntuPhil on 2006-03-11
mplayer is not in SPM, I looked.

---

### Post by paquito on 2006-03-11
Try use automatix.... follow instructions:

[http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix]("http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix")

it makes it EASY to install further usefull apps without having to compile. it's how i got Mplayer to work.

---

### Post by akiro.yamamoto on 2006-03-11
w32codecs:
Taken from: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
> 
wget -c [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
  sudo dpkg -i w32codecs_20050412-0.0_i386.deb


If you have totem or totem-xine installed all you need for .mpg playback is the codecs ;)

---

### Post by UbuntuPhil on 2006-03-11
[QUOTE=akiro.yamamoto]w32codecs:
Taken from: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)


If you have totem or totem-xine installed all you need for .mpg playback is the codecs ;)[/QUOTE]

Um I'm on a Mac, I don't think anything i386 is gonna work.

---

### Post by akiro.yamamoto on 2006-03-11
[http://ubuntuforums.org/showthread.php?t=88399&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=88399&highlight=mplayer)

[http://ubuntuforums.org/showthread.php?t=100015&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=100015&highlight=mplayer)

Apparently it will ;)

---

### Post by Peter41az on 2006-03-11
I had a problem with the codecs too, i ended up just installing automatix (script based installer tool great for newbies) there is another called easy ubuntu, which isnt supposed to be as security lax as automatix is. To date, however, i havent had any problems, and it installed all my codecs and a slew of other programs i like, all selectable during install.

---

