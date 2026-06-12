---
title: "[SOLVED] Transition from Windows"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-01
I installed Feisty last night, and seem to love it.
 
All my hardware worked out of the box except the NVidia Drivers for which I had to 'activate' the restricted drivers. Screen res, Wireless. No problems !
 
While using Firefox in Ubuntu, I have this nagging habit of hitting 'backspace' to go to the previous page. However, I noticed that backspace doesnt take you to the previous page like it does in Windows. Is there a key which does ?
 
How can we configure short cut keys in Ubuntu?
 
Also, I was looking at Amarok to use as my music player. Can it be used to transfer music to and from an iPod?
 
I am not too keen on using iTunes as it is very heavy on resources (atleast the Windows version 7) So I am looking for a good iTunes replacement.
 
But I have Ubuntu...not Kubuntu. Will Amarok have issues with that?
and finally, how do i remove software from Ubuntu?
I used the Add/Remove utility, but when I clicked on the software that I wanted to remove, it gave me an error saying
"Could not uninstall XXX software. Please use the Synaptics Manager to uninstall it along with its dependencies"
 
When I went into the Synaptics Manager, it was hard to figure out what software is dependent on what other software. Could someone point me in the right direction here?
 
Thanks a bunch !

---

### Post by Seisen on 2007-05-01
In firefox to go back a page it's ALT+Left Arrow Key. When you open synaptic you can search for packages. Do a search and once you find the package your want to delete right click it and select complete removal. If it has any other dependicies it will tell you. If you have questions about what whether the dependicies can be removed let me know. As long as you don't hit apply it won't remove the files just so you know.

---

### Post by juantovarm on 2007-05-01
-Amarok is an excellent choice for media player, and also an excellent substitute for itunes. It will have no problems running under ubuntu (gnome), simply look for it in add/remove
-If you go to synaptic and choose to uninstall a certain application, it will take care of the dependencies too. 

I once deleten an app and all my dektop was gone. only happened once, though, i imagine it is not too common and it happened with ubuntu 6.04

---

### Post by mikewhatever on 2007-05-01
> While using Firefox in Ubuntu, I have this nagging habit of hitting 'backspace' to go to the previous page. However, I noticed that backspace doesnt take you to the previous page like it does in Windows. Is there a key which does ?


Type [COLOR="DarkRed"]about:config[/COLOR] in the address bar. In the new window type [COLOR="DarkRed"]backspace[/COLOR] in the Filter bar. You will see one entry called [COLOR="DarkRed"]browser.backspace_action[/COLOR]. Double click on it and set the value to 0. Now restart Firefox.
You may also want to check some more tricks for Firefox [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Customizing_your_Firefox_install](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Customizing_your_Firefox_install)

---

### Post by webjames on 2007-05-01
in regards to media players, you could try Exaile, it is an excelent choice for Gnome and is quite amarok like, also it has tabular playlists like firefox so you might be impressed, it also has ipod support. get the latest version from [here]("http://www.exaile.org").

---

### Post by Josey on 2007-05-01
> **Inxsible said:**
> 
Also, I was looking at Amarok to use as my music player. Can it be used to transfer music to and from an iPod?

Yes it works great with my 30gb Ipod  :)

 
> But I have Ubuntu...not Kubuntu. Will Amarok have issues with that?

It doesn't seem to have any issues as far as I can tell... I use amarok daily in gnome.

> and finally, how do i remove software from Ubuntu?

either with terminal commands or synaptic package manager.
if we wanted to remove amarok...
in terminal -   sudo apt-get remove amarok
in synaptic -   uncheck it and hit apply

> I used the Add/Remove utility, but when I clicked on the software that I wanted to remove, it gave me an error saying
"Could not uninstall XXX software. Please use the Synaptics Manager to uninstall it along with its dependencies"
 
When I went into the Synaptics Manager, it was hard to figure out what software is dependent on what other software. Could someone point me in the right direction here?

This im not so sure about but I'm fairly certain it's an easy fix.
I'm not totally certain but I think using the option "remove complety" removes dependancies too.  (probably wrong about that)   :( 

I know that installing software with aptitude and removing with aptitude will remove dependancies though.
examples...
```
sudo aptitude install amarok
```
```
sudo aptitude remove amarok
```

This is the best way to install/remove software as far as I know.

---

### Post by Inxsible on 2007-05-01
I think using the command line is a much better option than browsing all those pages in Synaptic Manager !
 
Hail Command Line !! :)

---

### Post by GrueTamer on 2007-05-01
> **Inxsible said:**
> I think using the command line is a much better option than browsing all those pages in Synaptic Manager !
 
Hail Command Line !! :)Well, you're not going to have the problems of those people who refuse to use the command line, will you? :)

My media player of choice is [Songbird]("http://www.songbirdnest.com/").  It has an iTunes-like interface (or at least it looks like it to me), playing music is simple, and you can even find music on the internet to listen to/download.  Plus, there are ways to buy your music off of online stores that Songbird works with, in case downloading music for free is something you don't like :) .

And finally, if you want Kubuntu, or if Amarok or something seems to require it, there's a simple way to get it, in the terminal that you like a lot, just type

```
sudo apt-get install kubuntu-desktop
```

This will download and install Kubuntu, in essence.  You can change which desktop environment you want to boot in the boot menu, under options, menu, session type, something along those lines.

Oh, and I'm glad you enjoy Feisty so far! :KS

---

### Post by Josey on 2007-05-01
> **GrueTamer said:**
> Well, you're not going to have the problems of those people who refuse to use the command line, will you? :)

My media player of choice is [Songbird]("http://www.songbirdnest.com/").  It has an iTunes-like interface (or at least it looks like it to me), playing music is simple, and you can even find music on the internet to listen to/download.  Plus, there are ways to buy your music off of online stores that Songbird works with, in case downloading music for free is something you don't like :) .

And finally, if you want Kubuntu, or if Amarok or something seems to require it, there's a simple way to get it, in the terminal that you like a lot, just type

```
sudo apt-get install kubuntu-desktop
```

This will download and install Kubuntu, in essence.  You can change which desktop environment you want to boot in the boot menu, under options, menu, session type, something along those lines.

Oh, and I'm glad you enjoy Feisty so far! :KS

use aptitude though instead of apt-get in case you want to remove it in the future.

---

### Post by Inxsible on 2007-05-01
> **Josey said:**
> use aptitude though instead of apt-get in case you want to remove it in the future.

Do you mean we can't uninstall if we use aptitude ?

---

### Post by Josey on 2007-05-01
> **Inxsible said:**
> Do you mean we can't uninstall if we use aptitude ?

Aptitude removes dependencies if installed with aptitude.  Apt-get doesn't.
Most people in the know recommend using aptitude instead of apt-get.... that's all.
Same commands are used as with apt-get.

```
sudo aptitude install someprogram
```

```
sudo aptitude remove someprogram
```

---

