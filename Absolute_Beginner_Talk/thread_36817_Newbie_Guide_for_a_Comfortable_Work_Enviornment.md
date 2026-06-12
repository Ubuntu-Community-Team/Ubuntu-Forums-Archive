---
title: "Newbie Guide for a Comfortable Work Enviornment"
date: 2005-05-24
forum: Absolute Beginner Talk
---

### Post by cinematography on 2005-05-24
Even though Ubuntu is one of the best, if not the best, Linux distributions available, it still lacks certain standard features many of us have become accustomed to. This tutorial will help point out easy ways to install and setup some useful things to make working in Ubuntu easier.

NOTE: This tutorial is still a work in progress. If you have a category that you would like to add, or an answer to a category listed, please post it below. :)


[color=red][SIZE=3]*** Helpful Tip: Installing Programs**[/SIZE][/color]
Use the Symantic Package Manager under System -> Administration to add, remove, and update programs. It makes life a lot easier.


[color=red][SIZE=3]*** Helpful Tip: Updating Programs**[/SIZE][/color]
Some programs like Azureus apply updates automatically when you open them. To update these programs without hitches, be sure that you open them through your root terminal.


[color=red][SIZE=3]*** Turning off Ubuntu Spatial**[/SIZE][/color]
If you want to keep the last folder open while navigating through folders.

Open Configuration Editer in Applications -> System Tools -> Configuration Editor. 

In the Configuration Editor, go to Nautilus Preferences under Apps -> Nautilus -> Preferences. 

Under Nautilus Preferences, find and select 'no_ubuntu_spatial'. 


[color=red][SIZE=3]*** Associating files with programs of your choice**[/SIZE][/color]
Right click the file -> Properties -> Open With


[color=red][SIZE=3]*** Installing codecs for mp3 and mpeg**[/SIZE][/color]
Ubuntu Addon Package: 
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

or Unofficial Ubuntu 5.04 Starter Guide
[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#codecs](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#codecs)


[color=red][SIZE=3]*** Installing TrueType fonts[/SIZE]**[/color]
Ubuntu Addon Package: 
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

Default font settings for Firefox Windows:
Proportional --- Serif --- 16
Serif --- Times New Roman
Sans-Serif --- Arial
Monospace --- Courier New --- 13

Minimum Font Size [none]


[color=red][SIZE=3]*** Installing Java for Firefox internet browser**[/SIZE][/color]
Ubuntu Addon Package: 
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

After you have Java installed, enter the following code into your root terminal: 
[COLOR=Blue][i]cd /usr/lib/mozilla-firefox/plugins
ln -s /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so .[/i][/COLOR]


[color=red][SIZE=3]*** Installing a visible CD burning program with GUI**[/SIZE][/color]
To install Gnomebaker, the Nero for Linux Ubuntu, go to Applications -> System Tools -> Add/Remove Programs.

Click 'Advanced'

Click 'Search'

Type 'gnomebaker' in search and click search.

Select 'gnomebaker' in window and then click apply at the top.


[color=red][SIZE=3]*** Installing Rar for Linux**[/SIZE][/color]
Enter the following into a root terminal: 
[COLOR=Blue]*sudo apt-get install rar unrar*[/COLOR]


[color=red][SIZE=3]*** Installing Wine**[/SIZE][/color]
Open repository source file by entering the following into the root terminal:
[COLOR=Blue]*nano /etc/apt/sources.list*[/COLOR]

Paste these lines at end of file:
[COLOR=Blue][I]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/[/I][/COLOR]

Press Ctrl-O (O as in orange) to save and update file.

Enter the following into root terminal:
[COLOR=Blue][I]sudo apt-get update
sudo apt-get install wine winesetuptk[/I][/COLOR]

Right click .exe file, left click 'open with other...", and enter 'wine' into the custom command space.


[color=red][SIZE=3]*** Accessing files on a Windows partition**[/SIZE][/color]
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

[COLOR=Blue][I]sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222[/I][/COLOR]

Then go to /media/windows to access your Windows files.


[color=red][SIZE=3]*** To navigate through the GUI as root**[/SIZE][/color]
Enter [COLOR=Blue]**gksudo nautilus**[/COLOR] into a terminal.


[color=red][SIZE=3]*** Editing your Repository Source File**[/SIZE][/color]
Enter [COLOR=Blue]**sudo gedit /etc/apt/sources.list**[/COLOR] into a terminal.


[color=red][Size=3]*** Hear multiple sounds using Both ESD & ALSA?**[/size][/color]
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

Following this guide could help solve other problems you may encounter with Realplayer and XMMS.


[color=red][Size=3]*** Windows floppies have shortened file names and you want to see full name?**[/size][/color]
Make sure you make a backup of the fstab file before editing it.

Enter the following into your terminal: 
[color=blue]*sudo gedit /etc/fstab*[/color]

Replace this line: 
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

With this line: 
/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

Save and reboot.

---

### Post by Kyral on 2005-05-24
[QUOTE=cinematography]Even though Ubuntu is one of the best, if not the best, Linux distributions available, it still lacks certain standard features many of us have become accustomed to. This tutorial will help point out easy ways to install and setup some useful things to make working in Ubuntu easier.

NOTE: This tutorial is still a work in progress. If you have a category that you would like to add, or an answer to a category listed, please post it below. :)



[SIZE=3]*** Turning off Ubuntu Spatial**[/SIZE]
Open Configuration Editer in Applications -> System Tools -> Configuration Editor. 

In the Configuration Editor, go to Nautilus Preferences under Apps -> Nautilus -> Preferences. 

Under Nautilus Preferences, find and select 'no_ubuntu_spatial'. 


[SIZE=3]*** Installing codecs for mp3 and mpeg**[/SIZE]
...........................
...........................


[SIZE=3]*** Installing TrueType fonts[/SIZE]**
...........................
...........................


[SIZE=3]*** Knowing where programs are installed**[/SIZE]
...........................
...........................


[SIZE=3]*** Upgrading Firefox to proper location**[/SIZE]
...........................
...........................


[SIZE=3]*** Installing Java for Firefox internet browser**[/SIZE]
...........................
...........................


[SIZE=3]*** Installing a visible CD burning program with GUI**[/SIZE]
To install Gnomebaker, the Nero for Linux Ubuntu, go to Applications -> System Tools -> Add/Remove Programs.

Click 'Advanced'

Click 'Search'

Type 'gnomebaker' in search and click search.

Select 'gnomebaker' in window and then click apply at the top.


[SIZE=3]*** Installing Winrar and Winzip**[/SIZE]
...........................
...........................


[SIZE=3]*** Installing Wine**[/SIZE]
Open repository source file by entering the following into the root terminal:
*nano /etc/apt/sources.list*

Paste these lines at end of file:
[I]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/[/I]

Press Ctrl-O (O as in orange) to save and update file.

Enter the following into root terminal:
[I]sudo apt-get update
sudo apt-get install wine winesetuptk[/I]

Right click .exe file, left click 'open with other...", and enter 'wine' into the custom command space.


[SIZE=3]*** Programs and scripts for one click .deb install**[/SIZE]
...........................
...........................[/QUOTE]



You don't need winzip. Its built into File-Roller. As for Rar...

```
sudo apt-get install rar unrar
```

---

### Post by cinematography on 2005-05-24
Did you really need to quote the entire post? :lol: 

Thank you very much for your info though. I'll edit it in the tutorial.

---

### Post by jeremy on 2005-05-25
BTW, it's called rar, not winrar. Winrar is a version of rar created especially for a commercial OS.

---

### Post by jeremy on 2005-05-25
Sorry if I sound pedantic, its just that I can't stand the use of the 'w' word as a generic!

---

### Post by cinematography on 2005-05-25
[QUOTE=jeremy]BTW, it's called rar, not winrar. Winrar is a version of rar created especially for a commercial OS.[/QUOTE]
Correction made. :) Thank you.

---

### Post by zaxer on 2005-05-25
Great post. 

Found so many interesting things!

Keep it growing!

Thanks.

---

### Post by cinematography on 2005-05-25
[QUOTE=zaxer]Great post. 

Found so many interesting things!

Keep it growing!

Thanks.[/QUOTE]
Thanks. :)

---

### Post by cinematography on 2005-05-26
Could someone move this thread to this room? 
[http://ubuntuforums.org/forumdisplay.php?f=58](http://ubuntuforums.org/forumdisplay.php?f=58)

---

### Post by stevenyu on 2005-08-15
great website for newbie, maybe this should be add as a refernce in the ubuntu guide

---

### Post by TristanMike on 2005-08-15
Hi, great guide, very coherent for a new learner, however I think you missed something small. Under the "Helpful Tip: Updating Programs" when saying you should open them in the root terminal, you should give the code to run the program (azureus in the case of your example). That way noobs like me don't have to post and say, "Ok, how do I know what to type in the root terminal?"

Just a suggestion, awesome none-the-less.

---

### Post by Kyral on 2005-08-15
Newbies shouldn't even be running in a root terminal....you know what will happen, one day someone will type rm -rf * while at / and BOOM! [-X

---

### Post by Stormy Eyes on 2005-08-15
[QUOTE=Kyral]Newbies shouldn't even be running in a root terminal....you know what will happen, one day someone will type rm -rf * while at / and BOOM! [-X[/QUOTE]

Every newbie should get to do it at least once -- like little kids with a stove top. :evil:

---

### Post by bonjun on 2005-08-16
finally a guide for a newbie like me... new to ubuntu... new to linux

---

### Post by sophtpaw on 2005-08-16
[QUOTE=Kyral]Newbies shouldn't even be running in a root terminal....you know what will happen, one day someone will type rm -rf * while at / and BOOM! [-X[/QUOTE]


Hmmm...  :-k   and what does rm -rf* do exactly?
I'm tempted,

--
sophtpaw

---

### Post by a8o on 2005-09-15
[QUOTE=sophtpaw]Hmmm...  :-k   and what does rm -rf* do exactly?
I'm tempted,

--
sophtpaw[/QUOTE]

Me too :S

---

### Post by cstudent on 2005-09-15
[QUOTE=sophtpaw]Hmmm...  :-k   and what does rm -rf* do exactly?
I'm tempted,

--
sophtpaw[/QUOTE]

It will delete everything in the drive.

rm means remove, -rf means recursively files and directories and /* is a wildcard character that means include everything under the root folder, which is all the files and directories on that drive. If done as root the command will execute. If done as a user it would not because the user would not have the permissions to execute.

---

### Post by Lord Illidan on 2005-09-15
But how will a newbie type rm -rf * if he has no prior knowledge of what it means. It's not like it is a combination of random characters. Chances are 90% he won't do it.

---

### Post by NZ-Wanderer on 2005-09-22
Very interesting reading... - Thank you...

Maybe you could explain why even tho you do use add/remove advanced etc and it tells you the program installs, yet sometimes you never see the program in your menus??
(Case in point: I used your guide to installing visible CD program and it worked perfectly, I then used the guide again to install Mondo which I really want cause I wish to backup a complete working system before I start playing again (I tend to break it when I play)
However, after doing what was outlined, and according to synaptic is IS installed, I cannot find it in add/remove, nor is it in any of the menus..
It's starting to become very frustrating this happening, because I know it's been installed, but it just aint there for me to click on.)

Regards - John...

---

