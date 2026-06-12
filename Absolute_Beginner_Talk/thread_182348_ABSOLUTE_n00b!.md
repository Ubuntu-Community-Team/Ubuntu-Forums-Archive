---
title: "ABSOLUTE n00b!"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by dgmorr on 2006-05-25
Hi Everyone!

This is my first time REALLY using Ubuntu, and Linux all together. I've installed it a few times in the past, but never really did anything with it other than mess around. I really want to stick with this, but can't find any help. Here are my problems.

1) How do I install applications? I'm not familiar with Lunux extensions. I downloaded an mp3 player program called XMMS or something of that sort. I have tried a couple other programs and only get tar.gz files. The instructions say to use ./configure and I try just that, but nothing works for me. I've installed a C compiler using the Synaptics Manager, but now I'm pretty much lost. Can anyone help me step by step?

2) I do moderate Java programming at school and am really familiar with the command line dos for windows. How can I do that in Ubuntu? I first have to figure out how to install Java, then actually learn how to learn my way aroudn it in Ubuntu

Please help me. I don't want to give up on Ubuntu!

I'm using Ubuntu 32 bit on my HP NX6110

---

### Post by aysiu on 2006-05-25
For installing applications, nothing beats this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by Sef on 2006-05-25
> 2) I do moderate Java programming at school and am really familiar with the command line dos for windows. How can I do that in Ubuntu? I first have to figure out how to install Java, then actually learn how to learn my way aroudn it in Ubuntu

To install java, read the top of and then go to the bottom of [RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats").

---

### Post by dgmorr on 2006-05-26
Thanks for the replies. I was able to find more extensions and packages using the Synaptics manager by selecting those other repositories! Things are looking good. Now a couple more questions (sorry)

1) I have Totem media player installed and I can't play any of the video files I used to be able to play in Windows ie. avi, divx, wma (is this windows only?). I have installed VLC and this seems to work, but for things such as online videos in Firefox, I believe it tries to use Totem. How do I change this and how do I set the default program that launches for each file type? Right now everything is set to open in Totem.

2) I can't play more than one sound at once. I have a built in SoundMax audio card in my laptop. Are there better drivers that I should be using?

---

### Post by Klaidas on 2006-05-26
[QUOTE=dgmorr]Thanks for the replies. I was able to find more extensions and packages using the Synaptics manager by selecting those other repositories! Things are looking good. Now a couple more questions (sorry)

1) I have Totem media player installed and I can't play any of the video files I used to be able to play in Windows ie. avi, divx, wma (is this windows only?). I have installed VLC and this seems to work, but for things such as online videos in Firefox, I believe it tries to use Totem. How do I change this and how do I set the default program that launches for each file type? Right now everything is set to open in Totem.[/QUOTE]
See my 2nd link in signature ;)

---

### Post by 3rdalbum on 2006-05-26
[QUOTE=dgmorr]
2) I can't play more than one sound at once. I have a built in SoundMax audio card in my laptop. Are there better drivers that I should be using?[/QUOTE]

Try changing the sound output settings in Multimedia Systems Selector, and also in XMMS if you're using it.

---

### Post by dgmorr on 2006-05-26
Thanks to everyone for the help! I'm getting used to it now.

I have another question. I want to turn on DMA for my cdrom drive because of choppy dvd playback. I am able to turn it on for my current session but it does not stay on during reboot. I tried to edit the hdparm.conf script, but I am unable to edit anything in the folder because of permissions. I am the only user of this laptop and not sure why most of the files in there are locked. How can I change this? Right clicking and selecting properties does not work because it says something like "you are not the owner of this file ...."

---

### Post by Mustard on 2006-05-26
[QUOTE=dgmorr]Thanks to everyone for the help! I'm getting used to it now.

I have another question. I want to turn on DMA for my cdrom drive because of choppy dvd playback. I am able to turn it on for my current session but it does not stay on during reboot. I tried to edit the hdparm.conf script, but I am unable to edit anything in the folder because of permissions. I am the only user of this laptop and not sure why most of the files in there are locked. How can I change this? Right clicking and selecting properties does not work because it says something like "you are not the owner of this file ...."[/QUOTE]
You don't want to change the permissions of the system files.  They are that way for security reasons.  You have access to them when you execute commands in  conjuction with the 'sudo' command, which equates to 'superuser do'.  When you edit them make sure you are editing them as a superuser ie open the particular file with a text editor of your choice, but include 'sudo' in the command ie...

```
sudo nano /etc/hdparm.conf
#this will open the nano command line editor
#with superuser privileges to edit/create
#the file called hdparm.conf in the /etc/ directory
```

---

### Post by dgmorr on 2006-05-26
Wow, thanks. That explained a LOT of other questions I probably would have had. I never knew Linux was this cool!

---

### Post by dgmorr on 2006-05-27
I've been reading the link on how to install tar.gz files and I'm still stumped. 

I'm trying to get my Creative Zen Micro to work using this package [http://libnjb.sourceforge.net/](http://libnjb.sourceforge.net/) and I can't get it to install. I have done ./configure and it runs through some stuff, and then I try to type 'make' but it says something like no makefile found. Can anyone help me on this specifically?

---

### Post by mostwanted on 2006-05-27
[QUOTE=dgmorr]I've been reading the link on how to install tar.gz files and I'm still stumped. 

I'm trying to get my Creative Zen Micro to work using this package [http://libnjb.sourceforge.net/](http://libnjb.sourceforge.net/) and I can't get it to install. I have done ./configure and it runs through some stuff, and then I try to type 'make' but it says something like no makefile found. Can anyone help me on this specifically?[/QUOTE]

The configure script fails because of a missing dependency and then the Makefile is  never created. Look at the output it gives you and see if you can find the missing dependencies in Synaptic. Remember to install any packages with a *-dev extension if they look like the ones the script says are missing.

---

### Post by PingunZ on 2006-05-27
Good that you're sticking to linux ;)
Kill bill ^^
I recommand you to ready[ this ]("http://easylinux.info/wiki/Ubuntu")

In that you can find how to install java ;)
in this case it tells you to install automatix wich is a good idea :p

In install automatix like this :
```
sudo apt-get install xterm
wget http://beerorkid.com/automatix/automatix_5.8-3_i386.deb
sudo dpkg -i automatix_5.8-3_i386.deb
```

---

