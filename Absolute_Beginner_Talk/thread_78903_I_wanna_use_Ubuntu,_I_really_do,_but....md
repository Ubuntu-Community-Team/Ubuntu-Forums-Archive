---
title: "I wanna use Ubuntu, I really do, but..."
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by karishbhr on 2005-10-19
I just dont get a few things. 


One: How the hell do I install a new application? (Like one I download, so... yamipod)

Two: How do I get the back button on my mouse to work (Its logitech)

Three: I tried adding a library file to the sys/usr/lib or w/e it is, but it says Im not owner and cant do that... but Im the only user account on the PC!

Four: I really just need a guide, to everything linux for ubuntu, one that assumes I know nothing

---

### Post by Lord Illidan on 2005-10-19
Have you tried the Ubuntu Guide?

You can't install .exe files in Ubuntu, unless you use Wine.

As for your mouse try this : [https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons](https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons)

For installing most apps, use Synaptic...check in the Ubuntu Guide for details.

Also, what libraries were you installing?

---

### Post by DrMoxie on 2005-10-19
Well, for Yamipod it looks like it is a standalone app, you just need to copy libfmodex.so.4.00.35 to /usr/lib.  Just unpack the archive--you can do this through Nautilus [Places-->Home] and at the terminal [Applications-->Accesories-->Terminal] navigate into the directory ```
cd yamipod
``` and then copy it ```
sudo cp libfmodex.so.4.00.35 /usr/lib
``` In the above code the sudo is key (BTW, it stands for Super User Do and allows you to perform activities as root.  When it asks for a password use yours.  

Beyond Yamipod, Synaptic has a wealth of applications availble for two-click installs (System-->Administration-->Synaptic, again use your password).

As for books, I've been getting by with two: Linux for Dummies and The Pocket Guide To Linux.  Beyond that searching through these forums and over at [LinuxQuestions.org]("http://www.linuxquestions.org") is a good way to discover answers to most questions.  Another good resource is the free digital magazine [Tux]("http://www.tuxmagazine.com/"), which is aimed at those new to Linux. 

Hope this helps!  :p

---

### Post by singlecell on 2005-10-19
There seems to be two ways of installing applications as far as I can tell - 
 Applications->add application - which seems to be an organised list of applications that can be installed (anybody know where they come from, or who organises this list)
 System->Administration->Synaptic package manager

Synaptic is definately the one to use.

Applications are wrapped up as "packages", and the install system manages any dependancies (shared libraries etc.) required to get the applications fully installed. The packages are then placed on a central server (feed) to be downloaded by the package manager on your machine.

I don't know who manages what packages are made available, but there seem to have everything I've wanted so far. You can add extra feeds, and some applications provide their own feeds. Anything outside of the feeds seems to be just a case of downloading the files and copying to the correct places.

Anybody know how we get any missing packages added?

---

### Post by Lambert on 2005-10-19
Welcome to Linux. You sound new to it.

You'll find it's different in many ways then windows, especially when it comes to installing applications.

You'll want to spend some time reading the wiki page and ubuntuguide. 

Also look around the help pages. Some of the wiki pages and good information can be found in there. I'm not on my ubuntu box right now but I believe there is a section for new users that helps with some basics.

I switched from Windows about 5 months ago. There has been a learning curve as linux is different but I'm finding ubuntu is much better and more stable then my xp box.

---

### Post by patrick295767 on 2005-10-19
[QUOTE=karishbhr]I just dont get a few things. 


One: How the hell do I install a new application? (Like one I download, so... yamipod)

Two: How do I get the back button on my mouse to work (Its logitech)

Three: I tried adding a library file to the sys/usr/lib or w/e it is, but it says Im not owner and cant do that... but Im the only user account on the PC!

Four: I really just need a guide, to everything linux for ubuntu, one that assumes I know nothing[/QUOTE]

after changing the /etc/apt/sources.list 
and having internet connection !

sudo su
apt-get update
apt-get -f install prog_wished


to install sthg downloaded *.deb
dpkg -i prog_downloaded.deb



u can have a look there :
_____________________
[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)


&

[http://www.ubuntuforums.org/showthread.php?t=64557](http://www.ubuntuforums.org/showthread.php?t=64557)

---

### Post by patrick295767 on 2005-10-19
[QUOTE=Lambert]Welcome to Linux. You sound new to it.

You'll find it's different in many ways then windows, especially when it comes to installing applications.

You'll want to spend some time reading the wiki page and ubuntuguide. 

Also look around the help pages. Some of the wiki pages and good information can be found in there. I'm not on my ubuntu box right now but I believe there is a section for new users that helps with some basics.

I switched from Windows about 5 months ago. There has been a learning curve as linux is different but I'm finding ubuntu is much better and more stable then my xp box.[/QUOTE]

As you, but 1-2 months ago, I installed XP and ... after usign it ... I thougth : 
damn damn Is it possible that windows are getting worst and worst ?? speed and fast pc even with a damn good config !!
Then, I decided to return to Windows2000 ... 
... and result of not being able to do anything in network home admin (even with ssh) I decided to pass to linux world : 
  
the results are amazign ... even my very old PC now is running as server !!! and I can even play movies, even DIVx, ... 
Really, Why Windows Exist since Such Linux Ubuntu can do the same even More ?
  
Results: I converted to Linux Now ! One More !

Thanks for this nice ubuntuforums.org !!

:-) Pat'

---

### Post by karishbhr on 2005-10-19
Ok, I got the yami-pod working, and I got some other things as well... still cant get the mouse... I did everything it said, but it still wont work... I probably screwed something up... there needs to be a better way to do that. The PC knows there is more buttons, becuase when I use the foward and back buttons it treats them like right and left clicks.

I also dont understand why I cant edit conifg files without the nano script thing, when I try to do it another way it says Im not the owner!

---

### Post by aysiu on 2005-10-19
[QUOTE=karishbhr]
I also dont understand why I cant edit conifg files without the nano script thing, when I try to do it another way it says Im not the owner![/QUOTE] Some people recommend nano because it works in both KDE and Gnome. If someone tells you to type in ```
sudo gedit /etc/apt/sources.list
``` that may work fine in Gnome but not KDE. If someone tells you to type ```
sudo kwrite /etc/apt/sources.list
``` that may work fine in KDE but not Gnome. ```
sudo nano /etc/apt/sources.list
``` however, works fine in both KDE *and* Gnome.

And you don't have access to those config files because you're a regular user. Unlike Windows, Ubuntu does not default the user to be an administrator--that way you can't accidentally screw up your computer or accidentally allow other programs (like spyware) to screw up your computer). *sudo* allows you to temporarily assume administrative privileges.

---

### Post by erikpiper on 2005-10-19
Welcome to linux!

Btw- The "Add applications" app is an apt-get frontend. So is synaptic. They all use the same repos.

---

### Post by djh3 on 2005-12-31
[QUOTE=karishbhr]Ok, I got the yami-pod working, and I got some other things as well... still cant get the mouse... I did everything it said, but it still wont work... I probably screwed something up... there needs to be a better way to do that. The PC knows there is more buttons, becuase when I use the foward and back buttons it treats them like right and left clicks.

I also dont understand why I cant edit conifg files without the nano script thing, when I try to do it another way it says Im not the owner![/QUOTE]

HI.  I am also new to Ubuntu and I am trying to get my iPod working.  I first tried gtkpod but couldn't figure it out (doesn't seem to be well document).  I then downloaded yamipod, extracted the tar file and copied the libfmodex file to /usr/lib.  Now I can't figure out how to start yamipod running!  How did you do it?  Yamipod seems to be fairly well documented on its website but assumes more knowledge than I have.  It says just double click on yamipod's binary.  What and where is that?

Thanks.

---

### Post by cjm5229 on 2005-12-31
[QUOTE=djh3]HI.  I am also new to Ubuntu and I am trying to get my iPod working.  I first tried gtkpod but couldn't figure it out (doesn't seem to be well document).  I then downloaded yamipod, extracted the tar file and copied the libfmodex file to /usr/lib.  Now I can't figure out how to start yamipod running!  How did you do it?  Yamipod seems to be fairly well documented on its website but assumes more knowledge than I have.  It says just double click on yamipod's binary.  What and where is that?

Thanks.[/QUOTE]

Hi, That would probably be in usr/bin. The easy way to get a shortcut set up when a program doesn't install one, is to go to Applications>System Tools>Application Manager. Just click "new" Type in the Apps name, browse to the usr bin file, enter the App, and then click on the icon and try to find one that fits. If The app isn't in usr bin, then start Synaptic, search for the app there, right  click the app and click "properties", then go to "installed files" That will list the whereabouts of the files and you can look for the one that will launch the app from there. Play with it awhile and it won't take long to figure it out. Carl
PS the Ubuntu 5.10 user guide is here,  [URL="http://makuchaku.info/amnesty/#downloadguide"]
 Good luck, it's a lot of fun learning once you get into it. The Forums and Howtos will help a lot.

---

### Post by djh3 on 2006-01-01
[QUOTE=cjm5229]Hi, That would probably be in usr/bin. The easy way to get a shortcut set up when a program doesn't install one, is to go to Applications>System Tools>Application Manager. Just click "new" Type in the Apps name, browse to the usr bin file, enter the App, and then click on the icon and try to find one that fits. If The app isn't in usr bin, then start Synaptic, search for the app there, right  click the app and click "properties", then go to "installed files" That will list the whereabouts of the files and you can look for the one that will launch the app from there. Play with it awhile and it won't take long to figure it out. Carl
PS the Ubuntu 5.10 user guide is here,  [URL="http://makuchaku.info/amnesty/#downloadguide"]
 Good luck, it's a lot of fun learning once you get into it. The Forums and Howtos will help a lot.[/QUOTE]
Thanks.  I am using Ubuntu 5.04 (Hoary).  I used Applications>System Tools>File Browser to go to the directory (yam-linux) in my Home directory where I knew YamiPod was created after downloading the tar file.  In that directory I noted the file YamiPod (with an icon) and copied it to my desktop.  Works like a charm!:smile:

---

