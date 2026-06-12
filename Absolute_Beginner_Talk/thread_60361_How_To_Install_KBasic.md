---
title: "How To Install KBasic"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by limva on 2005-08-27
I'm an absolute Linux newbie and I'm trying to install Kbasic on ubuntu Linux with Gnome.  The installation file I have has a .bin extension and I've been getting an error when I try to open it.

The Kbasic site tells me to run it with Konqueror but I think it is found only in KDE.

Please help me run this install file.

Thanks!

---

### Post by edwina on 2005-08-27
Welcome to Ubuntu. I'm still learning myself, but think that I can help you get some of the way. No final answer though, I'm afraid. You'll have to wait for someone else or do some more searching on the net.

Konqueror is just a file manager, essentially, so you should be able to do whatever you are told to do by using Nautilus (the Gnome file manager).

It is generally best to try and install programs using Synaptic, but I expect that you already know that. Besides, it isn't available on Synaptic by the looks of it  :-? 

Making the file executable is all that you are being asked to do through Konqueror. In Nautilus this involves right-clicking, going to "Properties" and ticking the "Executable" box next to your user name. The alternative is to use "chmod" in a terminal, which you'll need to do some research into first. This doesn't help in this case, unfortunately, as left-clicking the file will still give you the error message.

I believe the problem may be to do with the file itself, or possibly just the way it interacts with Ubuntu. It was made for Linux 2.2.5 (I checked with the "file" command in a terminal), and Hoary is 2.6 or something, but they should be compatible. It doesn't work under KDE either (I checked), so I'm out of ideas. Anybody else?

Sorry I couldn't be more helpful. At least you may have picked up a few simple Linux tricks from my gabbling!

---

### Post by stimpack on 2005-08-27
is it executable?

in a shell: chmod a+x filename
or
in kde: properties/click 'is execuatable'

not sure about gnome but will be similier.

---

### Post by N'Jal on 2005-08-27
Genrally KDE app's don't work well under GNOME without a lot of the KDE library's etc, you can use synaptic to install KDE in place of GNOME to get all the libs etc and use konqurer but even then if it was for Linux 2.2.5 it could be too old to run anyway.

---

### Post by limva on 2005-08-27
I checked the Execute boxes in Permissions from Properties.  I tried running it with the "bin" extension, and without it, but neither worked.  I ran it off my desktop, and from the main bin folder, and also from another bin folder that I created withing my user folder.  Nothing seems to work!

---

### Post by edwina on 2005-08-28
I would suggest that you e-mail the KBasic people. After all, Ubuntu is one of the most popular Linux formats around, so they would probably want their software to run under it.

---

### Post by isTHEr3mOr3 on 2005-08-28
You can install Kbasic with Ubuntu. Just install KDE and libpng (probably libpng-dev too) with Synaptic.

---

### Post by limva on 2005-08-28
Thanks everyone for your suggestions.

After I made the file executable, I do not get an error message anymore when I try running it.  Nothing happens.  I'm beginning to think that this might be a hardware issue.  I'm running this on an old 166 mhz box with 32meg ram and 4.3 gig HD.  Maybe it's the cpu speed that's to blame.

Anyway, let me email the kBasic people and see what they say.

---

### Post by isTHEr3mOr3 on 2005-08-28
I've installed it and it works. Maybe you could try Kubuntu.

---

### Post by limva on 2005-08-28
You may be right, isTHEr3mOr3.  The kBasic site mentions KDE but not Gnome.  I had just installed ubuntu a week ago (my first linux installation).  How easy is it to switch to kubuntu?

---

### Post by linuxfanatic1024 on 2005-08-28
[QUOTE=limva]How easy is it to switch to kubuntu?[/QUOTE]

Very easy. Go into Synaptic and install the package named "kubuntu-desktop" and remove the package "gdm". Then, log out and reboot. Type in your user name at the Kubuntu log-in screen, Click Session Type, and click "KDE". Then enter your password and hit Enter.

Note that you won't have to use the "session type" menu on subsequent log-ins.

I am a KDE user and have preferred KDE since I started with Linux. It's much more newbie-friendly, and it's also power-user-friendly. :grin: I just don't like GNOME.

---

### Post by wvslkr on 2005-08-28
Just a point.  It is not necessary to remove GDM.  It will work just the same as KDM.  One can use whichever one prefers. :)

---

### Post by limva on 2005-08-29
I ran synaptic and installed "kubuntu-desktop", then I removed gdm.  It downloaded and installed a bunch of files.  During installation it even asked me which desktop I wanted and I chose kdm.  After reboot, it showed me the kubuntu login screen and it seemed to be logging into the kde desktop.  But somehow it brought me back to the gnome desktop, and I'm showing kde files as well as gnome files in the Main Menu!

What can I do to get rid of gnome and use only kde?  By the way, kBasic still doesn't run. :-?

---

### Post by limva on 2005-08-29
OK, at the login screen there is an option for logging into either desktops.  I'll try logging into kde then run kbasic.

---

### Post by isTHEr3mOr3 on 2005-08-29
Don't forget to install libpng (I needed ver. 3) and to be sure install the libpng-lib too.
I can use Kbasic with Gnome as well.

---

### Post by limva on 2005-08-30
Hi guys, I'm back.  I got myself a faster pc (800 mhz) and installed kubuntu on it.  I tried running the kBasic installer again and, again, nothing happens!  I'm pretty sure I'm doing something wrong.  I just don't know what else to try.

---

### Post by limva on 2005-08-30
Just a quick note here.  I don't know if it makes any difference from which directory the file should be run from.  I downloaded it to my desktop, made it executable and tried running it from there, to no avail.

---

### Post by limva on 2005-08-30
My problem is solved!  I decided to forget about kBasic, so I downloaded and installed RealBasic instead, and it worked!  :wink: 

Thanks everyone!

---

### Post by cronus83 on 2006-09-07
i read your threads as i was also installing kbasics ... and i am using ubuntu 6 with Gnome i just did chmod a+x installer kbasics (full file name)and then installed libpng3 and libpng3-dev with synaptic and now i am using kbasics without any problems....

---

### Post by ct1egh on 2007-09-23
Hi,
Just go to Synaptic and install libpng3 (1.2.15~beta5-1ubuntu1) it works fine on Feisty Fawn with  Gnome desktop. 

Regards

---

### Post by oldefoxx on 2008-05-06
I got kbasic installed and working on Ubuntu 8.04 with Gnome.  The problem for most people is that they are told to use Konguorer to execute the downloaded bin file after making it an executable, but with Gnome, you have to use the Terminal Console and sudo mode and call the installer program directly to get it to install.

Another problem then was not having Qt4 installed, but that was handled by using apt-get install libQt4-sql.  However, part of the download went to the wrong place, so I had a link problem.  After talking with kbasic and being pointed in the right direction, I got that straightened out.

For more specific instructions, check out this post:
[http://www.kbasic.com/doku.php?id=installation](http://www.kbasic.com/doku.php?id=installation)
[http://www.jose.it-berater.org/smfforum/index.php?topic=1658.0](http://www.jose.it-berater.org/smfforum/index.php?topic=1658.0)

---

### Post by mpie on 2008-06-18
... hmm needed more than that for me
```
$ sudo apt-get install libqt4-sql  qt4-dev-tools  
```

just clicking on the bin installed it as a user, has anyone asked if it can be put in a deb?

---

### Post by Nxx on 2008-07-12
I tried to install Kbasic, but experienced a problem: it tries to create shortcuts in /home/user/Desktop, but there is no such folder as I use Russian locale and the desktop folder has name "&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;". The installes report an error and exits.

---

