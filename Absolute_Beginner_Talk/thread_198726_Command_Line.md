---
title: "Command Line"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by djlyx on 2006-06-17
Greetings Everyone!!!

I am trying to install libmp4v2-o so that i could install gtkPod but I think I need to do so by command line.  I am very very new to Linux and ubuntu and I feel quite illiterate.  what is command line? how do i initiate the install? I have used MS windows since 1994 and I feel discouraged.  Please help, thanx

-LYX
PPC iBook 500mhz dual USB
Running Ubuntu since yesterday

---

### Post by Marcelino on 2006-06-17
Try with Gdebi (if you are using Dapper), or in the Terminal: sudo dpkg -i packagename.deb .

---

### Post by darkali on 2006-06-17
You don't need to do that to install gtlPod, just open Synaptic:
System > Administration > Synaptic
Choose gtkPod from the list on the right. Right click it and select 'mark to install', now click the big 'Apply' button and Synaptic will take care of everything.

The terminal is a place for you do type commands (it is a command prompt), it's a different way to do same thing, it's on.
Applications > Accessories > Terminal

To install GtkPod on the Termianl just type:
```
sudo apt-get install gtkpod
```
Or copy and paste there.

PS: To paste on the Terminal is Control+Shift+V.

---

### Post by djlyx on 2006-06-17
ok, I installed GTKPod however it was an older version (i think) I tried the steps you had suggested, gdebi appeared to work.

However, when I try to play a song it says at the bottom "could not find command line 'xmm' specified for 'play now'

I am unable to play any songs

---

### Post by raptros-v76 on 2006-06-17
sudo aptitude install xmms

---

### Post by djlyx on 2006-06-17
wow, very interesting.  That was amazing!

Unfortunately, when I try to "play now" in gtkpod XMMS is initiated and a gray window pops up asking for directories.  I don't see my IPOD listed..

?

---

### Post by djlyx on 2006-06-17
no dice

---

### Post by nashife on 2006-06-17
In a clean install of Dapper + restricted formats so that it can play mp3s, I was able to transfer songs to and from my ipod with the music player Banshee.  Look for it in synaptic and try it.

I was also able to play music off my ipod in rhythmbox.

I've had no need for gtkpod as of yet. Have you tried Banshee?

---

### Post by djlyx on 2006-06-17
I am using Dapper

I dont see the program banshee in Synaptic nor does my ipod work in Rhythmbox.  When I tried GtkPod, it would automatically open xmms with a gray window asking for a directory.  I dont know what to do, i'm completely lost.

---

### Post by nashife on 2006-06-17
you'll want to make sure that the extra repositories are enabled. 

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

it's there once those are enabled correctly.  

You'll also want to make sure that all the restricted formats are enabled if you want to be able to play mp3s.  

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

In general, are you able to play mp3s at all?  can you play local mp3s at all?

---

### Post by cjm5229 on 2006-06-17
Automatix, Bumps, and Easy Ubuntu, are the noobs best friends. You'll find them in 3rd Party Ubuntu Projects. Bumps is just codecs, Easy Ubuntu and Automatix, also can install a lot of the extra programs that make life easy for the beginner. I know a lot of the people on these forums say that you need to learn to do it manually, so you shouldn't use the shortcuts, but I promise you will learn it, and in the mean time you have an OS that will do what you need.

---

