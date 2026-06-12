---
title: "Zen vision M"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by llzero1337 on 2007-09-17
i can transfer with gnomad but is there a way i can play stuff directly of it and is there a guide that can help me im a complete idiot with the terminal so i need a For Dummines sorta guide lol thanks for the help

---

### Post by llzero1337 on 2007-09-17
help please

---

### Post by Hobo Joe on 2007-09-17
Use Amarok.

```

sudo aptitude install amarok

```
When you plug in your Zen, just click the devices tab, and click connect, it should work that way.

---

### Post by llzero1337 on 2007-09-18
it doesnt dock or show up with amarock

---

### Post by Slychilde on 2007-09-18
Amarok doesn't work with Zen's out of the box, at least mine didn't.  To get it to work:

```
sudo apt-get install libmtp
```

```
sudo vi /etc/udev/rules.d/10-libmtp.rules
```

This will make a new udev rule for libmtp that should give you access to it in amarok.  Add this to the file:

```
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="libmtp_rules_end"

# Creative Zen Vision:M
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413e", SYMLINK+="libmtp-%k", MODE="666", GROUP="audio"
LABEL="libmtp_rules_end"

```

If you'd like to test out if it worked, restart your pc and type mtp-detect in terminal.  It should spit out some information about your Zen.  After that go into Amarok, Settings -> Configure Amarok -> Media Devices, and select MTP Device as the plugin.  Apply, OK.  Click on the Devices tab and in the drop down menu at the top select MTP Device again.  Plug in  your Zen and hit the connect button.  It should work.  Cheers!

---

### Post by llzero1337 on 2007-09-18
Omfg I Love You Somuch Thank You But How Can I Play Stuff From My Zen?

---

### Post by Slychilde on 2007-09-18
I'm glad it worked! :)

However, I have never tried to play music on Amarok from my Zen, so I can't be of much help there.  When you open the Zen's library can you double click any of the songs to play them or does that just transfer them?

---

### Post by maGot on 2007-10-01
Hello! I get this message when I try to do "sudo apt-get install libmtp" "E: Could not find the package libmtp"

What am I doing wrong?

---

### Post by maGot on 2007-10-04
Please help. Someone :)

---

### Post by cohoking on 2007-10-04
install directly from here:

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Flibm%2Flibmtp%2Flibmtp-doc_0.2.1-0ubuntu3_all.deb&md5sum=79176891a0956b9d704f76efa2d42bfa&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Flibm%2Flibmtp%2Flibmtp-doc_0.2.1-0ubuntu3_all.deb&md5sum=79176891a0956b9d704f76efa2d42bfa&arch=all&type=main)

---

### Post by maGot on 2007-10-05
Yeah! Thank you! It work's perfect!

---

### Post by JungleJoker on 2007-10-17
This works great for transferring songs! Much better than Gnomad2, but do you have a solution for video files?

---

### Post by sullenx on 2007-10-18
I also own a vision zen w, i got it working with gnomad, but i was wondering if the libmpt has some function that would allow it to be mounted as a regular drive (like windows Vista does)?

---

### Post by sullenx on 2008-01-29
I found a solution to this, use the mpt-fuse package.  All you would need to do is: 

```
#mtpfs mountpoint
```

It basically mounts your device as a regular disk.

---

### Post by PDG1 on 2008-04-02
MTPFS?
I've heard about this but I've yet to actually get it to work on my machine
do you know where I can find an easy way to get it to work?
I'm still pretty new to this linux thing... I can't even remember what Ubuntu I installed... I think it's 7.10

and also
do you know how do I get the Hard Drive section of my Zen to work?

---

### Post by sullenx on 2008-04-02
MTPFS fuse allows you to mount your Zen. This is the project website:
[http://www.adebenham.com/mtpfs/](http://www.adebenham.com/mtpfs/)

Get the stuff you need to compile it: 
```
sudo apt-get install libfuse2 libfuse-dev  libglib2.0-0 libglib1.2-dev libglib1.2 libmtp-dev libmtp6 
```

Then download the package: 

```
wget http://www.adebenham.com/mtpfs/mtpfs-0.7.tar.gz
```

Then untar it: 

```
tar -xvvf  mtpfs-0.7.tar.gz 
```

Move to directory: 

```
cd mtpfs-0.7
```

Run the Config: 
```
./configure
```

The script will stop if you are missing any packages needed to compile.

```
make && sudo make install

```

That should install it, all you need to do now is connect your zen, find a folder and issue the command: 

```
mtpfs any_folder
```

This way you can transfer movies, files in and out like you do in windows, which is better for me since i have perl scripts that automatically upload movies into my zen and the other options don't allow you to put things in folders.

---

### Post by DishBreak on 2008-04-16
Hi all,

I've got a big problem...my gutsy system does not see my zen vision:m. i've tried finding it using lsusb, but this is what i get:

```

vishal@dishbreak-ix:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 006: ID 05ac:1260 Apple Computer, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 04b8:0819 Seiko Epson Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:c517 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```

i can sync this device under xp, so the player is definitely in good order. also, whenever i plug it in, rhythmbox pops up., so something is being triggered. do i need to change settings somewhere? 

Thanks for the help!

---

### Post by aigelonic on 2008-04-27
Hi,
I have a Zen Vision, but not the M - version. 
Today I installed Amarok and wanted to connect the mp3-player. Like most other people, Ubuntu did not find my player when I plugged it in.
But I found out that if I just started Amarok and then went to Settings->Configure Amarok->Media Devices and then instead of letting Amarok search for a device I added it manually with the MTP Media Device plugin. After this I just pressed connect and ho! my device was found :)

It now listed all the albums and songs on the player, but when trying to play a song I get an error message:
Error Loading media: 
xine could not find the URL


I did no other installations, but when I checked via Synaptic, libmtp was already installed.



cheers
Aigle

---

