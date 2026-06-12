---
title: "Audacity"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by etomic13 on 2006-08-29
I need help installing audacity. I have this folder with some stuff that came from the package but im not sure how to install it. [http://www.flickr.com/photos/46545958@N00/227986803/](http://www.flickr.com/photos/46545958@N00/227986803/)

---

### Post by aysiu on 2006-08-29
Step 1. Paste this command in the terminal to delete whatever you downloaded: ```
rm -rf ~/Desktop/audacity-src-1.2.4b
```

Step 2. Enable extra repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Step 3: Install Audacity by pasting this command in the terminal: ```
sudo aptitude update && sudo aptitude install audacity
```

If you can't copy and paste commands in the terminal, read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by etomic13 on 2006-08-29
This is so frustrating everything i try to download fails i dont get this package thing and whenever i download one i get some error like dependancy is not satisfiable:libwxgtk2.4-1. All i need is audacity the new open office suite and mp3 file decoder and ive tried to download each and i have no f******* clue how to install or what to install for audacity and openoffice is doing the same thing and i cant download the automatix file and what is gedit and the other text editor they mention i guess according to terminal i dont have them god installing is so confusing is ther like a dummies guide to installing on linux. anyway thnx for listening.

---

### Post by etomic13 on 2006-08-29
Im still really consufed what is a tar.gz file whenever i extract it Its a bunch of folders and files but no install. what does an install icon even look like

---

### Post by atomkarinca on 2006-08-29
ok, here's what i did: from [http://audacity.sourceforge.net](http://audacity.sourceforge.net) i downloaded the .deb file for my system (i386 & dapper in my case) and the .deb file took care of the rest. i would suggest that :)

in your case (in most cases) you could try on console:

./configure
make
sudo make install

under the folder you extracted your tar file. if this is not the case you should read the install or readme file under that folder. and we don't have install.exe or setup.exe :)

---

### Post by etomic13 on 2006-08-29
I keep getting this error [http://static.flickr.com/62/228233024_ef569b573e.jpg?v=0](http://static.flickr.com/62/228233024_ef569b573e.jpg?v=0) when i double click on the file. Do you want me to enter those codes in the terminal also. do each of this lines have to be entered seperatly i tried that and i gave me an invalid file command

---

### Post by deadgobby on 2006-08-29
Isn't Audacity in Synaptic???

---

### Post by etomic13 on 2006-08-29
whats synaptic

---

### Post by xyz on 2006-08-29
Point to the top left of your screen and click on System>Administration>Synaptic Package Manager...(it will prompt you for your root password)
This being open, click on Search and type Audacity. Audacity is in Synaptic.

---

### Post by xyz on 2006-08-29
From Juergen Haas:
> Definition: synaptic: GUI-frontend for APT Synaptic (previously known as raptor) is a graphical package management program for Debian. It provides the same features as the apt-get command line utility with a GUI front-end based on WINGs and can handle RPMs as well.

Basically it allows you to easily search,download and install programs and what they need to function properly (dependencies).

It may be a good idea to keep this thread on the theme of Audacity...

---

### Post by Marsolin on 2006-08-29
[Audacity]("http://linuxappfinder.com/package/audacity") is in the Ubuntu repositories, but the universe section must be enabled to see it. You can enable it by selecting Repositories from the Settings menu in Synaptic and uncommenting any lines that say universe. In my opinion, Ubuntu really should enable it by default.

---

### Post by aysiu on 2006-08-29
Read my reply to your original message and follow the links and actually do the instructions I gave you.

Then, you won't be frustrated.

If you want to keep doing things your way, you'll keep whining about how hard it is to install Audacity.

---

### Post by etomic13 on 2006-08-29
the synoptic found no files. Is still compressed it is deb file is that okay. Am i even getting the right file. Is installing things this difficult.

---

### Post by etomic13 on 2006-08-29
Thanks for helping out a noob i figured out how to install apps including audacity.(holy crap theres alot of them)

---

### Post by xyz on 2006-08-31
As a side thing, **etomic13** and anybody else for that matter, you might want to keep an eye on that one:

**_jokosher**_...for some reason the site seems to be down right now so I can't give you the straight link to it. Just type the word in Google.

---

### Post by xyz on 2006-09-01
Site seems to be back up...just in case someone is interested:
[http://www.jokosher.org/](http://www.jokosher.org/)

---

