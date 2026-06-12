---
title: "OMG I feel so stupid!"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by ionizd on 2005-12-17
First of all, I'm using Kubuntu breezy 5.10 and I know nothing about Linux. That being said, I am a computer guy and I'm trying to set up a stable second system to donate computer cycles to the Folding@home project. I have no idea how to run the executable file that I downloaded to my desktop, and the command line instruction the F@h download website tells you to use doesn't work. It says that the file doesn't exist, even though I correctly entered the filename(which was wrong in their instructions). Here is the link to the website:
[http://www.stanford.edu/group/pandegroup/folding/download.html]("http://www.stanford.edu/group/pandegroup/folding/download.html")
 Second, where are the extra desktop themes I downloaded using Adept?!? I Got what looked to be some cool themes and adept supposedly downloaded and installed them, so where are they?:mad:

---

### Post by ubuntu27 on 2005-12-17
Folding@home

here:
[http://ubuntuforums.org/showthread.php?t=101817](http://ubuntuforums.org/showthread.php?t=101817)

---

### Post by ionizd on 2005-12-17
Thanks for the informational link. I'll try that method, but it's really disturbing that I can't seem to figure out how to run executable files.

---

### Post by ionizd on 2005-12-17
O.k. I got the program installed and working, but since it's an executable fille and not actually installed, is there any way to ensure the folding@home program runs automatically at startup, and without having to keep Konsole open as long as I want to run it?
Thanks!

---

### Post by ubuntu27 on 2005-12-17
[QUOTE=ionizd]O.k. I got the program installed and working, but since it's an executable fille and not actually installed, is there any way to ensure the folding@home program runs automatically at startup, and without having to keep Konsole open as long as I want to run it?
Thanks![/QUOTE]
You can add which application/program to run on startup by

System/Preferences/Sessions

and in Startup programs click on "Add"

then type the complete directory of the application. 

Since I haven't try Folding@Home.. I don't know where it is "installed"


.... Or you can always create a Launcher, so you could double click and start the application.

Do the folwoing:

1)Right Clicke on Desktop, choose "Create Launcher"
2) in basic, click on "Browse..."
3)  then select the application [search for it]
4) open
5) Then fill the camp/form :) You can name it whatever you want. 
6) Click ok. And you are done!! notice there is a new icon on the desktop, that's the new launcher that you just created ;)

---

### Post by ionizd on 2005-12-17
Thanks, I'll try that as soon as I get a chance. Any ideas on where those themes are, how to find them or how to get them in the settings so I can use them?

---

### Post by ionizd on 2005-12-18
[QUOTE=ubuntu27]You can add which application/program to run on startup by

System/Preferences/Sessions

and in Startup programs click on "Add"

then type the complete directory of the application. 

Since I haven't try Folding@Home.. I don't know where it is "installed"


.... Or you can always create a Launcher, so you could double click and start the application.

Do the folwoing:

1)Right Clicke on Desktop, choose "Create Launcher"
2) in basic, click on "Browse..."
3)  then select the application [search for it]
4) open
5) Then fill the camp/form :) You can name it whatever you want. 
6) Click ok. And you are done!! notice there is a new icon on the desktop, that's the new launcher that you just created ;)[/QUOTE]

I don't seem to have any of the options you are telling me to do! I'm using Kubuntu- does that make a difference?

---

### Post by bscbrit on 2005-12-18
Yes it does make a difference.  You can achieve the same thing under KDE but not by using Gnome/Nautilus commands.  You need a KDE person - I've not used KDE for quite a while.

---

### Post by ionizd on 2005-12-18
Are there any terminal commands that'll do it? It seems that every important thing I've done to my configuration has been done there anyway.:rolleyes:

---

### Post by estel on 2005-12-18
You can make it startup by writing an init.d file.

I can't remember how to do this though, so sorry :(. Examine some of the files in /etc/init.d

---

### Post by estel on 2005-12-18
I think that adding the start executable command to somewhere in the middle of
/usr/bin/startkde

Might work as well... though I don't know if it'll break it.

---

### Post by ionizd on 2005-12-18
[QUOTE=estel]You can make it startup by writing an init.d file.

I can't remember how to do this though, so sorry :(. Examine some of the files in /etc/init.d[/QUOTE]
Any ideas on how to do this?

---

### Post by ubuntu27 on 2005-12-18
[QUOTE=ionizd]I don't seem to have any of the options you are telling me to do! I'm using Kubuntu- does that make a difference?[/QUOTE]
Sorry, I didn't know you were using KDE, Kubuntu.
I'm a Ubuntu user (GNOME) so I cannot help you :(

---

