---
title: "Few Questions..."
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-07-06
I love ubuntu and I have installed kubuntu on my desktop. I have few questions to ask you.

1. I have installed mp3 support manually I am having xine engine in amarok. But the quality of the sound is not that great*. Do I have to install 'Intel Graphics Media Accelerator Driver for linux'  or any other software  to enable good audio quality. ( Having Creative 2.1 Inspire, Motherboard supports HD audio
*Compared to XP)

2. Can .rpm files be installed in kubuntu. I have a modem with divers for red hat. I think it is a 'o' file. Can that be installed in kubuntu?

3. Will kubuntu be nice and stable with or without automatix? I have read the other posts but some say it is good and some say that it messes up the system. I it would do better with automatix, where can I download automatix in XP. ( I am not having Internet Connection in kubuntu)

4. I have a logitech keyboard. Kubuntu seems to recognise it and it detects my hot keys. Whan I press the volume hot key,  a small window like thing appears showing the increase or decrease of sound but actually there is no change of sound. Similar effect in the volume icon in the botton panel.

5. When I finish using kubuntu I cannot shut it down directly. About 7 to 8 out of 10 trials ends up in a blank screen, but it is not shutting down ( even after long waiting hours. I have to always first logout first and then shut it down).


Pleaese post your answers. I have searched the forum but i am still not able to figure out the way.


Thanks in Advance.

---

### Post by MoxJet on 2007-07-06
Why would you want to use Automatix on a computer without internet? It uses the internet to download the packages you select. However, I would not recommend to use Automatix. I would, however, not use a computer without an internet connection either but that's another issue.

You can convert .rpm to .deb (which you use dpkg to install) using the program called Alien.

You can shut down your computer from the terminal. There are several ways to do that, one is sudo init 0

Did you install the gstreamer plugins for mp3? They are the best.

The thing with your volume changing buttons on your keyboard I think only changes the system sounds, like when you click buttons, login/logoff sounds etc, and not your mp3 audio player, that is Amarok. I have not used Amarok, but I am certain that you can bind your keys to change the volume in Amarok instead of system.

Good luck!

---

### Post by linuxwizard on 2007-07-06
Info rpm
[https://help.ubuntu.com/community/SoftwarePackagingFormats](https://help.ubuntu.com/community/SoftwarePackagingFormats)

i would not use automatix. you can install everything you want without it the safe way.

---

### Post by seek3r on 2007-07-06
Hi.

I am kind of new here too, but I think I can answer one of your questions:

2. Can .rpm files be installed in kubuntu?

I am pretty sure that the command to do so would be (from the terminal):

alien -i "package.rpm" 

making substitutions as needed for the filename. You probably will have to prefix this with the standard sudo also.

I would suggest reading the man files for alien (man alien) before you begin, as there are some warnings and notations to be taken into account.

My information also has it that the process isn't perfect, nor is it reccomended, but it *does* work (most of the time), Basically you reallly should try to get the application from the repositories with apt-get if possible, and resort to this only if you just cant get the application anywhere else. Also you shouldnt use this for "critical" installs or the like.

Hope this helps.

(enjoy, you were my first "assist", so to speak. :D)

---

