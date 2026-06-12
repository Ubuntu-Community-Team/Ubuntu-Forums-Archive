---
title: "Error trying to run racer"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by voidoid on 2007-05-16
Hello again, I've just installed racer (hopefully) but when I try to run the racer program I get the following message

/media/sda2/ProgramFiles/racer/racer0.5.0/bin$ gnome-open racer
Error showing url: There is no default action associated with this location.

Presumably this means ubuntu doesn't know what to do with the file, so what do I do to make the system recognise this file and run it?

---

### Post by Najand on 2007-05-16
How did you install it? Did you use WINE? Please be more specified.

---

### Post by dstew on 2007-05-16
The command **gnome-open** takes as its argument a url (web address). I am not sure if racer is a url. If it is a program, just type **racer**.

---

### Post by voidoid on 2007-05-16
sorry, its a native linux game, and is installed by extracting the files to the install directory. I have tried just typing racer from the directory above, and it tells me that 'command not found'. when I try bin/racer it tells me that the directory or file is not found, however I know for a fact that the file is there. So basically I have no idea whats going on and hope you can help

---

### Post by slemmy on 2007-05-16
> **voidoid said:**
> sorry, its a native linux game, and is installed by extracting the files to the install directory. I have tried just typing racer from the directory above, and it tells me that 'command not found'. when I try bin/racer it tells me that the directory or file is not found, however I know for a fact that the file is there. So basically I have no idea whats going on and hope you can help

cd to the directory that contains the executable and type './racer' 

(the ./ prefix above indicates that you want to execute a binary in the current directory. (if you just type 'racer' in any directory you are just searcing your PATH environment variable for a binary named 'racer'))

---

### Post by voidoid on 2007-05-17
OK, thank you that seems to have got me to the right place, but I'm still getting errors, this time its saying

./racer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Which I'll assume means exactly what it says. Could it be linked to another of my threads [http://ubuntuforums.org/showthread.php?t=442686]("http://ubuntuforums.org/showthread.php?t=442686")

---

### Post by Terl on 2007-05-17
Have you installed the libraries it is looking for?

---

### Post by voidoid on 2007-05-17
I thought I had, but obviously not, as apt-get install just returns an error message of 'could not find package for any of that little bunch

---

### Post by Terl on 2007-05-17
You may want to open synaptic and search for lib.  It will return a lot of things but then you can scroll through and check the listings.  I would help check but I am at work right now.

---

### Post by voidoid on 2007-05-17
Thanks for the advice, I've had a look and can't find the libs that are mentioned, if it helps this is what my source list looks like

deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main main-all
deb [http://mirror3.ubuntulinux.nl/](http://mirror3.ubuntulinux.nl/) dapper-seveas freenx
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) feisty universe

---

### Post by Terl on 2007-05-17
I searched for libstdc++ and got hits in synaptic.  I did also find files that start with libc6.  I am not positive these are what you need.  Where did you get this program?  Is there anything on their website?

You could look as I did thru synaptic and see if those are installed.  I would check the site where you got the game first though.

EDIT:  I found it.  I get the same errors.  Hmmm, I will check around too.  I did not see mention of this in their faq at all.  I did find the files as an rpm.  Could always alien them and go from there.

EDIT AGAIN:  Looking at the web page ([Troubleshooting Page]("http://www.racer.nl/trouble.htm#knownlinux") I don't see any mention of this problem.  I do notice on the main page that he is using SuSe and that he mentions SuSe again for the download link.  I think to fix this you will have to download the rpms.  They are at [freshrpms]("http://freshrpms.net/") then you will need to download alien via synaptic and run that on the downloaded rpm to make it a deb package.

It does look like an interesting game, I will say that.  Have you tried [Torcs]("http://torcs.sourceforge.net/") ?  It is also a racing game.  It is available through synaptic.  I had some fun with it.

---

### Post by voidoid on 2007-05-18
sorry, still a bit new to all this, so could you tell me which rpm I'm likeyl to need?

---

### Post by voidoid on 2007-05-18
OK, I've managed to install the missnig libraries, which means its time for my computer to throw an entirely new hissy fit. And it looks something like this

** Warning: QInfo: can't open 'gfx.ini'  local host: 'loorollholder'/127.0.0.1
** Warning: QInfo: can't open './racer.ini'
** Warning: QInfo: can't open './gfx.ini'
** Warning: QInfo: can't open './debug.ini'
RTime:Reset()
** Warning: QImage ctor: can't load 'data/images/skidmark.bmp'
** Warning: QImage ctor: can't load 'data/images/smoke.tga'
** Warning: QImage ctor: can't load 'data/images/repbuts.tga'
RAudio ctor
RAudio:Load(); enable=0
FMOD initializing
Disabling FSOUND output (NOSOUND)
** Error: Can't init FMOD: An invalid parameter was passed to this function

I tried changing permissions to allow the first bunch of files to run as executable, but didn't seem to make a difference. still this is all on a learning curve I suppose

---

### Post by Terl on 2007-05-18
Are you starting it from the right location?  I recall it said to cd into the racer folder but not the bin forlder.  When in the racer folder type:  bin/racer

For example, mine is in /home/john/racer so I cd to racer and then just type bin/racer and it would start (well it would kick out the errors).  He mentions it more than once to make sure you start it from the racer folder.  I hope it is this simple :)

for fmod... go to the site I linked and download it.  Extract it and then, as root (sudo) copy the extracted file to /usr/lib.

I did it this way, password when asked after you hit enter after typing command:

```
sudo cp whatever-the-filename-is /usr/lib/whatever-the-filename-is
```

Run that from the folder the fmod file is in.  The download was very fast.

---

### Post by voidoid on 2007-05-19
Thanks, I can now get in and play, but have no sound and no joystick. 

Fmod is loading according to my terminal and playing through channel 0, but I'm not getting any sound (although something entitled Rmenu destroy is right below, don't know wether that means anything or is just an unfortunate coincidence.

My joystick is recognised by Ubuntu, and has been calibrated, but isn't get picked up on by racer, so I;m guessing that I need to modify my /ini files, but I'm not quite sure what to do with them.

---

