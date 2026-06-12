---
title: "add mp3 support (offline)"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by YoungLady on 2007-02-23
i still cant get my dial up modem to work (im new to this)

i just want to first be able to play my mp3s so its not too quiet while im making my way around the new environment.

ive downloaded gstreamer 8 mad and gstreamer 8 misc along the way ive found out it needed something else (i think it was libc6 im not entirely sure im not at my pc right now). when i installed the libc6, it said it was already installed.

is there anyone who could point me to the files i need and their dependencies? thats where im having trouble really, the dependencies. since i have to download them from a windows box.

thanks folks.

god bless.

---

### Post by Jussi Kukkonen on 2007-02-23
That sounds a little dangerous... libc is a core system package, and upgrading it could be disastrous.
> 
is there anyone who could point me to the files i need and their dependencies?
No, not really -- that's the point of dependency handling: your system knows which files it needs. Others can only guess.

To find out the dependencies of a package run this command:
```
apt-get -s install <packagename>
```
Find the part that says "The following NEW packages will be installed" and you should have your list of needed packages. Download the packages from packages.ubuntu.com, not from any third party sites.

---

### Post by luke411 on 2007-02-23
I would recommend that you get your pc online first and then worry about the mp3's. It's much easier to get the packages you need, and safer too, if you do it from within Ubuntu and allow the operating system to get it.

---

### Post by Cursed on 2007-02-23
First do this:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

Then, do this:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

---

### Post by Jussi Kukkonen on 2007-02-23
Cursed, he does not have a network connection.

---

### Post by YoungLady on 2007-02-23
its just that i did a scanmodem test earlier, and its a conexant. (internal and rests in a pci)  what to do after the scan im still unsure.

i should get a bettr connection and hardware but its quite tight atm. still saving up for a new system (will be quite long though)

i probly could live with ubuntu being offline, but without songs to play, its gona be pretty dull since i play songs 101% of the time when im on a pc (at home.)

thanks folks for the replies. really appreciate it. good day.

---

### Post by luke411 on 2007-02-24
Using one pc to get the libraries for another pc is going to be a little tough. But what you are missing are the codecs for MP3, MP4, etc. They can be downloaded from the Gstreamer web site here,
[http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)
There is a lengthy list of them and you'll have to read each one to see if you think you need it for your own pc. 
The reason I suggested you get online first is that all of these can be retrieved easily by searching for "gst" packages in SYnaptic Package Manager but if that's not possible, you'll have to give it your best guess and keep adding libraries until you get your mp3's playing.

Good Luck

---

