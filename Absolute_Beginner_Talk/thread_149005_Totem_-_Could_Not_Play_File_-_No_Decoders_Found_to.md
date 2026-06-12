---
title: "Totem - Could Not Play File - No Decoders Found to Handle Stream"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by elitemerlin on 2006-03-23
Please help me tonight is my first time touching a Linux OS of anykind. I am trying to  play just some simple MP3's and no matter what i play i get 

Totem - Could Not Play File - No Decoders Found to Handle Stream, you might need to install the corresponding plugins.

It doesnt tell me what the corresponding plugins are though? ANY ideas?

---

### Post by Perfect Storm on 2006-03-23
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by elitemerlin on 2006-03-23
[QUOTE=Artificial Intelligence][https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)[/QUOTE]

Ok i went there, im very new to the *NIX enviroment, i went there , 

on the page i seen this:

> The Codecs

    *

      mplayer, xine and totem-xine can play MPEG-1, -2 & -4, DivX, Quicktime, Real Media 8 & 9, Windows Media Video 9, and many other formats with the proper support. This support has been bundled into the w32codecs package.

      As Windows is generally still in 32 bit land on the desktop, virtually no proprietary codecs are available in 64 bit DLL form, so there is no 'w64codecs' packages. Some people on AMD64 solve this problem by installing a 32-bit version of the operating system inside a chroot (such as via Linux Vserver or [WWW] dchroot), and this works very well. PowerPC users are generally out of luck entirely on this front - no-one has yet volunteered to collect binary codecs written for commercial operating systems on those platforms, nor to integrate the ability to use them via any of the above media players.

      If your country's laws allow you to play media using the w32codecs, in a terminal, type:

  wget -c [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
  sudo dpkg -i w32codecs_20050412-0.0_i386.deb
  

{i} Note: wmv files encoded with DRM (Digital Rights Management) are not playable by the codecs.

{i} Note: If you are experiencing choppy audio when playing WMV files, try [WWW] this fix. 

I type in what it said, and it appeared like i got connected to a FTP and a download began and finished inside the terminal itself.

Now this is all new too me, as im new to Linux, did this just download the codecs or install them as well? And if not how do i install them? im used to the Windows .exe Installers etc...

---

### Post by OffHand on 2006-03-23
type this in the terminal: sudo apt-get install  gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg

---

### Post by elitemerlin on 2006-03-23
[QUOTE=subsonic_shadow]type this in the terminal: sudo apt-get install  gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg[/QUOTE]

Thanx, i typed that in and i get this back in return, is this right?

> merlin@ubuntu:~$ sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
Password:
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
merlin@ubuntu:~$


as always thanx in advance

EDIT: After doing this im still recieving the same error, when trying to play the MP3's.

---

### Post by dcstar on 2006-03-23
[QUOTE=elitemerlin]
.......
Now this is all new too me, as im new to Linux, did this just download the codecs or install them as well? And if not how do i install them? im used to the Windows .exe Installers etc...[/QUOTE]
Firstly, don't muck around with terminal command line stuff, put the relevant win32codecs repositories in Synaptic and use that tool to install them.

You then need to install the totem-xine package (which will un-install the totem-gstreamer, which is what you want).

Once you do this, Totem should play most formats.

---

### Post by OffHand on 2006-03-23
[QUOTE=dcstar]Firstly, don't muck around with terminal command line stuff[/QUOTE]There's nothing wrong with the command line. You make it sound like it is an evil thing. This might scare people away from it, though it can be very useful. I'll be back in an hour..... dentist for me now  :S

---

### Post by dcstar on 2006-03-23
[QUOTE=subsonic_shadow]There's nothing wrong with the command line. You make it sound like it is an evil thing. This might scare people away from it, though it can be very useful. I'll be back in an hour..... dentist for me now  :S[/QUOTE]
There is very little point telling new Linux users to use arcane command line stuff when there are perfectly good GUI alternatives - that in a lot of cases work better -  available.

The best way to turn people off a product - and Ubuntu is a product - is to make using it unnecessarily difficult.

---

### Post by elitemerlin on 2006-03-23
Im a native windows user, used win systems since early  91, this is my first time ever messing with a *nix platform, some of the things you said confused me.

put the relevant win32codecs repositories in Synaptic and use that tool to install them.

repositories? i have no idea what that is

Synaptic? Where can i get that or do i have it preinstalled already? if so how do i access it i didnt see it in any menus?

totem-xine package? Links to this or how can i get it?

Im very sorry for sounding n00b, which i am on Linux. But im trying to make the golden switch from Win to Nix and never go back.

---

### Post by dcstar on 2006-03-23
[QUOTE=elitemerlin]Im a native windows user, used win systems since early  91, this is my first time ever messing with a *nix platform, some of the things you said confused me.

put the relevant win32codecs repositories in Synaptic and use that tool to install them.

repositories? i have no idea what that is

Synaptic? Where can i get that or do i have it preinstalled already? if so how do i access it i didnt see it in any menus?

totem-xine package? Links to this or how can i get it?

Im very sorry for sounding n00b, which i am on Linux. But im trying to make the golden switch from Win to Nix and never go back.[/QUOTE]
A repository is somewhere that has pre-compiled software available for you to install, Synaptic is the GUI tool to make this process as easy as possible, so go:

System-Administration-Synaptic Package Manager

Start it up and go to: Settings-Repositories

Do: Add-Custom and put the following in the Apt line:
```
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
```
After you reload the repository data, you can then do a search in Synaptic for w32codecs, and then select that to install.

Do the same search and select for totem-xine, and then select "Apply".

You should see the packages download and then install, once this is done you should be able to play multimedia in Totem.

---

### Post by akiro.yamamoto on 2006-03-23
I have to agree with you dcstar I feel if there is a GUI app to do the job, direct 
newbies there first.
The [**Source.list Generator**]("http://www.ubuntulinux.nl/source-o-matic")
May be of assistance in getting a source list with the appropriate repos.
All you have to do is replace the default source.list with the one they provide..
Hope this helps ;)

---

### Post by akiro.yamamoto on 2006-03-23
Here are some pics....

---

### Post by elitemerlin on 2006-03-23
thanks alot for all that it really helped me learn the proccess of installing/uninstalling/updating without the use of the command line. Everything went well and everything succeeded, i then went to play my MP3's and get a error message but it's a different one now, here it is.

Totem could not play "xxx.mp3"
Audio Codec 'MPEG 1 Layer 3 CBR' is not handled.
You might need to install addition plugins to play some types of Movies.

Im not sure why it says movies, cause its a music track but yea. Any ideas with this?

AS ALWAYS THANKS IN ADVANCE.

---

### Post by OffHand on 2006-03-23
[QUOTE=dcstar]There is very little point telling new Linux users to use arcane command line stuff when there are perfectly good GUI alternatives - that in a lot of cases work better -  available.

The best way to turn people off a product - and Ubuntu is a product - is to make using it unnecessarily difficult.[/QUOTE]I agree the UI is usually easier than a command line. In this case though, copy/paste 1 line in the terminal is very easy. 
To the OP: We will get your sound going :) No worries

---

### Post by OffHand on 2006-03-23
[QUOTE=elitemerlin]
Totem could not play "xxx.mp3"
Audio Codec 'MPEG 1 Layer 3 CBR' is not handled.
You might need to install addition plugins to play some types of Movies.[/QUOTE]Did you try to play it in other players like beep or rhythmbox?

---

### Post by elitemerlin on 2006-03-23
I just now tried it in rythm box, and when i go to import the music into it, it tells me the following error:

This is not an audio stream.

which i know it is.

Then i looked for another media player installed i found one named Kaffien, and it gives me this error:

There were no decoders found to handle the stream, you might need to install the corresponding plugins.

Then i tried Amorok, which also gives me an error:

The engine cannot run these MP3 files. 

These same files played fine on my win box there has to be a fix for this >_<

As always thanks in advance P.S. I couldnt find the bleep program on my box, but im sure ill get the same type of errors =D

---

### Post by OffHand on 2006-03-23
Alright. You just don't have the right codecs..... yet. I will try to talk you through this step by step.

1) Go to System>Administration>Synaptic Package Manager

2) In Synaptic go to Settings>Repositories. In the new window click Settings again. Activate 'show disabled software resources' and close the window.

3) Activate all the resources in the list and press Ok. Press Reload in the left upper corner.

4) Open the terminal (Applications>Accessories>Terminal

5) copy/paste: sudo apt-get install  gstreamer0.8-mad

6) copy/paste: sudo apt-get install  gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg


I tried to be as clear as possible. If you have any questions just ask :)

---

### Post by elitemerlin on 2006-03-23
OKay i did all that, up to the point where i c&p into then Konsole i get this error

```
merlin@ubuntu:~$ sudo apt-get install gstreamer0.8-mad
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail                                           able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc                                           ess using it?
merlin@ubuntu:~$ sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
merlin@ubuntu:~$

```

---

### Post by OffHand on 2006-03-23
Did you close the synaptic before you used the terminal?
You need to close it before you paste the commands. My bad, sorry.

---

### Post by elitemerlin on 2006-03-23
no it wasnt closed i closed Synaptic and it fixed it, the first one went well, the second one returned an error. ```
merlin@ubuntu:~$ sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg Reading package lists... Done Building dependency tree... Done E: Couldn't find package gstreamer0.8-plugins-multiverse 
```

EDIT: MY MUSIC IS WORKING NOW!!! w007!, THANX TO EVERYONE FOR MAKING THIS POSSIBLE! (still wondering about that last error though, though now it seems like it doesnt matter)

---

### Post by OffHand on 2006-03-23
You got sound now?

---

### Post by OffHand on 2006-03-23
Glad you got sound  :D It's usually the first thing I need to get working myself :mrgreen: The other codecs we'll get fixed too. Maybe someone has a nice resource.list for you. It seems like it doesn't connect properly.

---

### Post by OffHand on 2006-03-23
Ok. Lets try this. Open the terminal and copy/paste:

sudo gedit /etc/apt/sources.list

This will open the sources.list (where synaptic and apt-get are getting their software from) in gedit (a text editor).

Select everything and copy and paste it in a new text file. 
Save it on your desktop and name it sources.list_back

Then remove everything in the original sources.list and copy/paste this into it:

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 



Now close and save.
Then in the terminal type: sudo apt-get update
and then: sudo apt-get install  gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg

---

