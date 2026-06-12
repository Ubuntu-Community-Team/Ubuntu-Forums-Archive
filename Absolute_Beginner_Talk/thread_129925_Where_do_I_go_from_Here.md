---
title: "Where do I go from Here?"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by USA1 on 2006-02-15
Okay,

I installed ubuntu, I configure the ATI driver and got the WIFI working.

Now I am staring at a brown desktop, what do I do, where do I go from here?

For starter, lets play a few tunes to liveup the mood... Looking through gnome menus I found the rhytimbox and toten.

As it is, rhythimbox refues to play MP3 files from a CD and when I try to load toten, it crashes and reboot log me out automatically.

Search this forum for an MP3 player, find that a lot of people uses XMMS. Kool...

I find the ubuntu user guide website with step by step instructions to install XMMS.

Guess what, the file is no longer avilable.  Fine, do a google search and land at the xmms website.  Download the tar file, extract all the files, now what do I do.

I read the install txt file, it advices to start by doing ./configure.... fail it won't do it.

It is late, I have not eaten, I spent the whole day messing with this, I am tire and not able to listen to any of my tunes....

If anyone can help please do....

USA1

---

### Post by cwaldbieser on 2006-02-15
[QUOTE=USA1]Okay,

I installed ubuntu, I configure the ATI driver and got the WIFI working.

Now I am staring at a brown desktop, what do I do, where do I go from here?

For starter, lets play a few tunes to liveup the mood... Looking through gnome menus I found the rhytimbox and toten.

As it is, rhythimbox refues to play MP3 files from a CD and when I try to load toten, it crashes and reboot log me out automatically.

Search this forum for an MP3 player, find that a lot of people uses XMMS. Kool...

I find the ubuntu user guide website with step by step instructions to install XMMS.

Guess what, the file is no longer avilable.  Fine, do a google search and land at the xmms website.  Download the tar file, extract all the files, now what do I do.

I read the install txt file, it advices to start by doing ./configure.... fail it won't do it.

It is late, I have not eaten, I spent the whole day messing with this, I am tire and not able to listen to any of my tunes....

If anyone can help please do....

USA1[/QUOTE]
xmms sholuld be in the repositories.  From the terminal:
```

$ sudo apt-get update
$ sudo apt-get install xmms

```
OR open the Synaptic Package Manager, reload button, search for xmms, mark that you want to install it, apply.

If you have any trouble with either of those methods, please let us know what went wrong.

---

### Post by nanotube on 2006-02-15
here, might want to read this:
[https://wiki.ubuntu.com/Repositories](https://wiki.ubuntu.com/Repositories)
and also this, for making a good sources list for synaptic:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Ubuntu_Repositories_and_sources.list](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Ubuntu_Repositories_and_sources.list)

---

### Post by anirban.sam on 2006-02-15
try installing vlc

sudo apt-get install vlc

---

### Post by anirban.sam on 2006-02-15
as a desktop i found kubuntu a better option

---

### Post by USA1 on 2006-02-15
I tried, but it did not worked.

Here is what went down:

root@GUIRA:~# apt-get update
Reading package lists... Done
root@GUIRA:~# apt-get install xmms
Reading package lists... Done
Building dependency tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate
root@GUIRA:~#

Any clues?



[QUOTE=cwaldbieser]xmms sholuld be in the repositories.  From the terminal:
```

$ sudo apt-get update
$ sudo apt-get install xmms

```
OR open the Synaptic Package Manager, reload button, search for xmms, mark that you want to install it, apply.

If you have any trouble with either of those methods, please let us know what went wrong.[/QUOTE]

---

### Post by USA1 on 2006-02-15
Tried but it did not worked either:

root@GUIRA:~# sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc
root@GUIRA:~#

Did I missed anything?

thx for trying :)

[QUOTE=anirban.sam]try installing vlc

sudo apt-get install vlc[/QUOTE]

---

### Post by weasel fierce on 2006-02-15
Have you enabled the extra repositories ? 

check [http://ubuntuguide.org/](http://ubuntuguide.org/) as an excellent place to figure out how to do all sorts of things :)

---

### Post by nanotube on 2006-02-15
the vlc package is called "wxvlc"

---

### Post by polpak on 2006-02-15
Please don't recommend ubuntuguide.org. It is horribly out of date.

They should be using the official getting started guide 

[http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html)

---

### Post by ferebee on 2006-02-15
[QUOTE=USA1]Okay,

I installed ubuntu, I configure the ATI driver and got the WIFI working.

Now I am staring at a brown desktop, what do I do, where do I go from here?

For starter, lets play a few tunes to liveup the mood... Looking through gnome menus I found the rhytimbox and toten.

As it is, rhythimbox refues to play MP3 files from a CD and when I try to load toten, it crashes and reboot log me out automatically.

Search this forum for an MP3 player, find that a lot of people uses XMMS. Kool...

I find the ubuntu user guide website with step by step instructions to install XMMS.

Guess what, the file is no longer avilable.  Fine, do a google search and land at the xmms website.  Download the tar file, extract all the files, now what do I do.

I read the install txt file, it advices to start by doing ./configure.... fail it won't do it.

It is late, I have not eaten, I spent the whole day messing with this, I am tire and not able to listen to any of my tunes....

If anyone can help please do....

USA1[/QUOTE]

In order to play mp3's and some other types of multimedia files you need to install the plugins and codecs your programs
 need to be able to use them. Try this guide, it might help.
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
It also explains why they are not included in the install.

You can use Synaptic or Add Applications to install Xmms.
Both programs take care of downloading and installing for you.
You just need to make sure the 'Universe' and 'Multiverse' 
repositories are enabled. Here is how.
[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

---

### Post by Snorri Kristjánsson on 2006-02-15
Well I found that using the packet manager works best (beeing rather new to the world Linux/Unix)
After loding the packet manager got to reproties and press add then mark the unticked Universes and then the manager will get lots new of programs that you can then install.

---

### Post by cwaldbieser on 2006-02-15
[QUOTE=USA1]I tried, but it did not worked.

Here is what went down:

root@GUIRA:~# apt-get update
Reading package lists... Done
root@GUIRA:~# apt-get install xmms
Reading package lists... Done
Building dependency tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate
root@GUIRA:~#

Any clues?[/QUOTE]

Maybe you don't have the required repository enabled?  Try posting the output of
```

$ cat /etc/apt/sources.list | awk NF

```
That will show your repositories (and drop the blank lines to save some space).

---

### Post by raul on 2006-02-16
i had the exact same problem. you just need to enable the extra repositories. here's how: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

once you're done with that, just go to the command window to install xmms  (just enter: sudo apt-get install xmms). 

also, here's a good description of the difference between installing software in windows/os x and in ubuntu: [https://wiki.ubuntu.com/Repositories](https://wiki.ubuntu.com/Repositories)

hope that helps!

---

