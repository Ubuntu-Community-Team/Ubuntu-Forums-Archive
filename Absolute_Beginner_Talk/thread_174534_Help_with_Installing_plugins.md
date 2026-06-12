---
title: "Help with Installing plugins"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by grnida on 2006-05-12
Just got Ubuntu and fairly new to Linux.  I need to install plug in's such as Java and Real time.  How do I install once I have downloaded and saved to a file on my computer?  Also, trying to install Quicktime.  All help is greatly appreciated.  Thanks!](*,)

---

### Post by uzi09 on 2006-05-12
hey,

here is a great guide to help u setup and be on ur way:
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu) (for breezy)

if ur using dapper, look up on top, they provide u a link for it too.
good luck

---

### Post by Clay85 on 2006-05-12
I'm new to Linux Ubuntu as well and having the same problems. I'm like 'why doesn't it install when I double click?!' haha! This will be like the blind leading the not so blind. (It won't upset my feelings if you don't read this. I really have no idea what I'm doing, but it's better than pounding your head on the keyboard.)
So here I go:

I'm using Linux Ubuntu Breezy Gnome. 

There is a graphical user interface way to download programs; on your Menu click on System, Administration, Synaptic Package Manager. 

I believe this is the GUI way to download files (which is easier for me at the moment, coming from WINXP). But I can't figure out where the files are going. Still, I've gotten further with this than with the commandline user interface. I have no idea what's going on, there.

Okay, you have the Synaptic Package Manager open. This is a really neat peice of software (coming from WINXP, where you have to google your downloads). You can search for all sorts of programs in this, but first you have to open what they call the Universe and the Multiverse (Servers that host the files, I guess?). You access these by clicking on Settings and then Repositories. Click the Add button, then check Universe and Multiverse, then click OK. Click yes, then the software will do some updating.

Now you can click Search on the Menu, and type in Quicktime. Right click the files you want to download, and select 'mark'. From here you're on your own. I can't figure out where the files go, but you definately have them now! Some files also have to download extra peices so they can run properly. This is different than WINXP because in WINXP the files already come with all their peices. So, when something you mark says it also has to download other things, it's a good idea to allow it to do so.

There is a program called Debian Menu, which -I think- keeps track of your downloads. I found it on the synaptic thing, but I don't know what to do after I have marked it for installation & installed it. 

Well I hope this helps you somewhat. I think it helped me, haha!

---

### Post by Clay85 on 2006-05-12
I just did a search in the Synaptic Package Manager for a music program called Muine, installed it, and it is now on my Menu under Applications, Sounds and Video. So I don't know why nothing else has shown up.

---

### Post by confused57 on 2006-05-12
How to enable extra repositories:

[http://help.ubuntu.com/starterguide/C/ch02.html](http://help.ubuntu.com/starterguide/C/ch02.html)

How to install Automatix(if you're using Breezy):

[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

Automatix can automatically & easily install apps.

---

### Post by nalmeth on 2006-05-12
sometimes entering:
```
killall gnome-panel
```
in the terminal makes the apps show up, as it resets the panel. 
You might like a tool called xfce-appfinder, it's a little app browser, that shows ALL your installed programs. I like it.
```
sudo apt-get install xfce4-appfinder
```
Use automatix to install java, as suggested.
You can download the quicktime media plug-in aswell, included in the extra codecs package in automatix. 
For future reference, if you ever need to download something and manually install it, [this]("http://www.psychocats.net/linux/installingsoftware.php") might be a good guide to inform you

---

### Post by grnida on 2006-05-12
Tried the quicktime part under the packages and still wont work.

---

### Post by grnida on 2006-05-12
Okay, installed Automatix in the termianl however now I'm getting a message that reads "Permission denied"?

---

### Post by rahelvey on 2006-05-12
try easy ubuntu in the how tos page of the forms.
got me up and running in a few minutes and lead the way to being able to free hand in this os

---

