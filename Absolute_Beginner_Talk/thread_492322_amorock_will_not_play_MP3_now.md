---
title: "amorock will not play MP3 now"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-07-04
I have no clue what happened....but amorock will not play MP3 files now.  It did earlier today.  The only thing I have done is install the updates that came down from the repositories......is one broke and how do I get it out to bring amorock back?

Noah

---

### Post by nynoah on 2007-07-04
When I launch amarok, I get a message about it not being able to play MP3 files and that it needs me to download something.  I hit OK and it does nothing...........

---

### Post by forestpixie on 2007-07-04
download what exactly?

---

### Post by nynoah on 2007-07-04
Just the updates that my update manager sent me.  The usual repository updates.........Nothing else.

I tried rebooting too with CTRL ALT BACKSPACE and nada.........still no worky

I tried this too but still no worky either.

sudo apt-get install libxine-extracodecs

---

### Post by forestpixie on 2007-07-04
run amarok from the terminal - it should give so more info on what's going on. Post that here.

Not saying I'll be able to help - but let's see.

---

### Post by nynoah on 2007-07-04
Sorry but how do I run it from the terminal..........I am not the best at terminal use.....I cut and paste what a lot of people tell me and learn as I go.

Noah

---

### Post by forestpixie on 2007-07-04
open the terminal

type amarok and hit enter :)

you should be able to run any of your apps like that

---

### Post by nynoah on 2007-07-04
noah@noah-desktop:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x7d9150 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x7d9150 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
noah@noah-desktop:~$ QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image

---

### Post by nynoah on 2007-07-04
I also tried reloading it in the synaptic package manager and also this too "ibxine1-ffmpeg"

Noah

---

### Post by nynoah on 2007-07-04
so what is device 169?  I see error next to that

---

### Post by ceelo on 2007-07-04
Go to Settings > Configure Amarok > Engine and see if the Xine Engine is loaded. If not, you may need to (re)install the amarok xine engine. I forgot how the package is titled exactly, but you can search for it in Synaptic.

---

### Post by nynoah on 2007-07-04
It is there according to what I see

---

### Post by forestpixie on 2007-07-04
Okay that means ..... erm nothing to me I'm afraid
 this is from this thread

[http://ubuntuforums.org/showthread.php?t=448106](http://ubuntuforums.org/showthread.php?t=448106)

```
sudo aptitude remove --purge amarok
```

then go to post 4 and follow that

then reinstall in terminal


```
 sudo apt-get install amarok libxine-extracodecs
```

---

### Post by forestpixie on 2007-07-04
slow down - can't  keep up :D

have no idea about the driver

---

### Post by nynoah on 2007-07-04
Nope

---

### Post by forestpixie on 2007-07-04
ok one at a time - and are you running Ubuntu/Kubuntu/

do the purge command and post the output

---

### Post by nynoah on 2007-07-04
Kubuntu................for some reason (this is a total separate problem...........I can not log in anymore under Gnome interface....Only KDE and Xinterface work?  but that is  another problem)


I tried it and reinstalled then restarted and nothing


I will try again

---

### Post by nynoah on 2007-07-04
Need to get 0B of archives. After unpacking 32.3MB will be freed.
The following packages have unmet dependencies:
  amarok-engines: Depends: amarok (= 2:1.4.6-0ubuntu1~feisty1) but it is not installable
  amarok-xine: Depends: amarok (= 2:1.4.6-0ubuntu1~feisty1) but it is not installable
               Depends: amarok but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
amarok-engines
amarok-xine

Leave the following dependencies unresolved:
kde-extras recommends amarok
Score is -852

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
amarok-engines
amarok-xine
kde-extras

Score is -1003

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  amarok-engines amarok-xine kde-extras
The following packages will be REMOVED:
  amarok amarok-engines amarok-xine kde-extras
0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 32.6MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 214980 files and directories currently installed.)
Removing amarok-engines ...
Removing kde-extras ...
Removing amarok ...
Removing amarok-xine ...
noah@noah-desktop:~$

---

### Post by forestpixie on 2007-07-04
do the purge command in terminal then the install command and post the whole lot here.

did you check for the directory?

---

### Post by nynoah on 2007-07-04
Tried reinstal under adept manager and it still gives me the MP3 problem

---

### Post by nynoah on 2007-07-04
Ok doing this again this time I did this too

~/.kde/share/apps/amarok

---

### Post by forestpixie on 2007-07-04
Right at this moment you have 

purged amarok

deleted the shared folder

is that correct.

---

### Post by nynoah on 2007-07-04
noah@noah-desktop:~$ sudo aptitude remove --purge amarok
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  amarok-engines amarok-xine
The following packages will be REMOVED:
  amarok
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 32.3MB will be freed.
The following packages have unmet dependencies:
  amarok-engines: Depends: amarok (= 2:1.4.6-0ubuntu1~feisty1) but it is not installable
  amarok-xine: Depends: amarok (= 2:1.4.6-0ubuntu1~feisty1) but it is not installable
               Depends: amarok but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
amarok-engines
amarok-xine

Score is -652

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
amarok [2:1.4.6-0ubuntu1~feisty1 (feisty-backports, now) -> 2:1.4.5-0ubuntu7
(feisty)]
amarok-engines [2:1.4.6-0ubuntu1~feisty1 (feisty-backports, now) ->
2:1.4.5-0ubuntu7 (feisty)]
amarok-xine [2:1.4.6-0ubuntu1~feisty1 (feisty-backports, now) ->
2:1.4.5-0ubuntu7 (feisty)]

Score is -10219

Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  amarok amarok-engines amarok-xine
0 packages upgraded, 0 newly installed, 3 downgraded, 0 to remove and 0 not upgraded.
Need to get 0B/15.5MB of archives. After unpacking 3576kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg - warning: downgrading amarok-xine from 1.4.6-0ubuntu1~feisty1 to 1.4.5-0ubuntu7.
(Reading database ... 214977 files and directories currently installed.)
Preparing to replace amarok-xine 2:1.4.6-0ubuntu1~feisty1 (using .../amarok-xine_2%3a1.4.5-0ubuntu7_amd64.deb) ...
Unpacking replacement amarok-xine ...
dpkg - warning: downgrading amarok-engines from 1.4.6-0ubuntu1~feisty1 to 1.4.5-0ubuntu7.
Preparing to replace amarok-engines 2:1.4.6-0ubuntu1~feisty1 (using .../amarok-engines_2%3a1.4.5-0ubuntu7_amd64.deb) ...
Unpacking replacement amarok-engines ...
dpkg - warning: downgrading amarok from 1.4.6-0ubuntu1~feisty1 to 1.4.5-0ubuntu7.
Preparing to replace amarok 2:1.4.6-0ubuntu1~feisty1 (using .../amarok_2%3a1.4.5-0ubuntu7_amd64.deb) ...
Unpacking replacement amarok ...
Setting up amarok-xine (1.4.5-0ubuntu7) ...
Setting up amarok (1.4.5-0ubuntu7) ...

Setting up amarok-engines (1.4.5-0ubuntu7) ...
noah@noah-desktop:~$
noah@noah-desktop:~$
noah@noah-desktop:~$

---

### Post by nynoah on 2007-07-04
noah@noah-desktop:~$ ~/.kde/share/apps/amarok
bash: /home/noah/.kde/share/apps/amarok: No such file or directory
noah@noah-desktop:~$ ~/.kde/share/apps/amarok delete
bash: /home/noah/.kde/share/apps/amarok: No such file or directory
noah@noah-desktop:~$

---

### Post by forestpixie on 2007-07-04
ok first we need to deal with the broken packages =, I'm assuming Adept is your package manager - is there an option to deal with broken packages? In Synaptic (Ubuntu package) in status there's a Broken.

See if they are there and deal with them first.

```
noah@noah-desktop:~$ sudo aptitude remove --purge amarok
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
amarok-engines amarok-xine
The following packages will be REMOVED:
amarok
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 32.3MB will be freed.
The following packages have unmet dependencies:
amarok-engines: Depends: amarok (= 2:1.4.6-0ubuntu1~feisty1) but it is not installable
amarok-xine: Depends: amarok (= 2:1.4.6-0ubuntu1~feisty1) but it is not installable
Depends: amarok but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
amarok-engines
amarok-xine

Score is -652

Accept this solution? [Y/n/q/?] [COLOR="Red"]n[/COLOR]
```


Alternatively where you are saying N I think you need to say Y, it's seeming to give you the option to fix the broken package but you're not.

---

### Post by nynoah on 2007-07-04
strange thing happened...............my apdate manager came on and I ran it.....It had Amarok listed in there............Now this is AFTER I completely deleted it files and all..............>So I installed it that way.............still did not work..............but why did it come up in my update manager?

---

### Post by forestpixie on 2007-07-04
ok if there's no directory purge has purged it all - now we need to concentrate on the broken packages.

---

### Post by nynoah on 2007-07-04
OK try again

---

### Post by nynoah on 2007-07-04
noah@noah-desktop:~$ sudo aptitude remove --purge amarok
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  amarok-engines amarok-xine
The following packages will be REMOVED:
  amarok
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 32.3MB will be freed.
The following packages have unmet dependencies:
  amarok-engines: Depends: amarok (= 2:1.4.6-0ubuntu1~feisty1) but it is not installable
  amarok-xine: Depends: amarok (= 2:1.4.6-0ubuntu1~feisty1) but it is not installable
               Depends: amarok but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
amarok-engines
amarok-xine

Score is -652

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  amarok-engines amarok-xine
The following packages will be REMOVED:
  amarok amarok-engines amarok-xine
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 32.6MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 214976 files and directories currently installed.)
Removing amarok-engines ...
Removing amarok ...
Removing amarok-xine ...
noah@noah-desktop:~$

---

### Post by nynoah on 2007-07-04
noah@noah-desktop:~$ ~/.kde/share/apps/amarok
bash: /home/noah/.kde/share/apps/amarok: No such file or directory
noah@noah-desktop:~$

---

### Post by nynoah on 2007-07-04
OK I wait now.............tell me exactly what to do so I don't keep on doing something wrong

---

### Post by nynoah on 2007-07-04
I am getting frustrated....I am going to walk away from this and try later..........Thank you.....If you are on when I am on later, I would much appreciate any further help.....................Thank you
Noah

---

### Post by forestpixie on 2007-07-04
Ok I won't be here later but to reinstall amarok now we have finally got rid of everything in terminal do 

```
sudo apt-get install amarok amarok-engines amarok-xine
```

See if it's working now. Good Luck :D

If not I really don't know - I use amarok in Ubuntu so not sure of engines it needs in Kubuntu, or whether I have them or not. 
 
I understand that you're getting frustrated but you need to give people enough time to see what 's happening before you post more in between ;)

---

### Post by nynoah on 2007-07-05
No I was not really too frustrated....It is just the 4th of July and I needed to meet family.  I hope you understand.  I just know that if I did not stop, I would be at it for a while.

Thank you so much.....I will try that now.

Noah

---

### Post by nynoah on 2007-07-05
noah@noah-desktop:~$ sudo apt-get install amarok amarok-engines amarok-xine
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kde-core libxalan110 kdelibs libxerces27
Use 'apt-get autoremove' to remove them.
Suggested packages:
  libvisual-0.4-plugins libqt0-ruby1.8
The following NEW packages will be installed:
  amarok amarok-engines amarok-xine
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/13.7MB of archives.
After unpacking 32.6MB of additional disk space will be used.
Selecting previously deselected package amarok-xine.
(Reading database ... 213843 files and directories currently installed.)
Unpacking amarok-xine (from .../amarok-xine_2%3a1.4.6-0ubuntu1~feisty1_amd64.deb) ...
Selecting previously deselected package amarok.
Unpacking amarok (from .../amarok_2%3a1.4.6-0ubuntu1~feisty1_amd64.deb) ...
Selecting previously deselected package amarok-engines.
Unpacking amarok-engines (from .../amarok-engines_2%3a1.4.6-0ubuntu1~feisty1_amd64.deb) ...
Setting up amarok-xine (1.4.6-0ubuntu1~feisty1) ...
Setting up amarok (1.4.6-0ubuntu1~feisty1) ...

Setting up amarok-engines (1.4.6-0ubuntu1~feisty1) ...
noah@noah-desktop:~$

---

### Post by forestpixie on 2007-07-05
> **nynoah said:**
> No I was not really too frustrated....It is just the 4th of July and I needed to meet family.  I hope you understand.  I just know that if I did not stop, I would be at it for a while.

Thank you so much.....I will try that now.

Noah

Morning - aaah yes I understand - we don't do that here! Hope you had a good time :D

Well it appears to have installed it properly. Is it working? Hope so 'cos I don't think I'd be able to help with it anymore. I've done what I can with it.add

EDIT - if you get the can't play mp3 message now - try installing the extra codec pack - as I said not too sure about Kubuntu

```
sudo apt-get install libxine-extracodecs 
```

---

### Post by nynoah on 2007-07-06
Noooo I tried that too............still no go...................>WTF

Anyone else care to try?

---

### Post by Lolicon on 2007-07-06
Can other applications use MP3? If you want to use something different try Wine+Foobar2000.

---

### Post by nynoah on 2007-07-06
Noatun does not work, NOTHING will play an MP3

Noah

---

### Post by nynoah on 2007-07-06
Now the strange part is M4A, AAC files all work????????  Why?  SO I know I have the codecs........usually MP3 is easy and M4A are harder to get to run.

Noah

---

### Post by Lolicon on 2007-07-06
Codac problem then. Download an Mp3 Codec.

---

### Post by nynoah on 2007-07-06
How and where?

---

### Post by nynoah on 2007-07-06
I ask because I think I already have them, but they don't work now

---

### Post by Lolicon on 2007-07-06
Synaptic has MP3 codecs. I just installed linuxmint to save myself this trouble. I'm sure there was a media center for Ubuntu that did these things but I forgot the name.

---

### Post by Lolicon on 2007-07-06
Try a reinstall then.

---

### Post by nynoah on 2007-07-06
I have reinstalled SEVERAL times.............what is linuxmint?

---

### Post by Lolicon on 2007-07-06
[http://www.linuxmint.com/index.html](http://www.linuxmint.com/index.html)

---

### Post by fac on 2007-07-07
I have just had a similar problem. 

My solution was to go the terminal and remove the setting library for xine. Go to the terminal and type:

mv .xine .xine_old

This way you do not delete the library you just rename it, and therefor you can easily get it back again.

---

