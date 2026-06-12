---
title: "How do I install anything?"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by crstacy on 2007-02-21
I am using ubuntu until I can get me Windows machine fixed.  I have tried to get around in it for a few days now, but one thing is still bothering me.  I  have downloaded the N game which is in a tar.gz file.  How can I install this game?  I am so used to windows games and it doing all of the hard work for me.  

Can anyone help me with this game please? I did a search with no luck

---

### Post by bodhi.zazen on 2007-02-21
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/) 

Try to install from the ubuntu repositories if at all possible :)

---

### Post by macogw on 2007-02-21
Double click the tarball and open it with the archive manager, extract it to a folder inside your home folder (don't do it straight into the home folder or you might get stuff all over the place, make a folder for source stuff, for instance "src" is short for source).  After you extract it, go to that folder where you extracted it (extract is like unzip on a .zip file).  Read the readme.txt.  It'll tell you how to install.  *Most* programs you can use the command line (that's the only way to compile from source) and go to that folder, for instance
cd ~/src/game
 
then you have to
./configure
sudo make
sudo make-install

but not all programs work like that.  Some will have other instructions in the readme and you might get some errors telling you to install some library or some such.  

Did you check that the game isn't in the repos first?  Repos = easiest way to install anything ever

---

### Post by crstacy on 2007-02-21
I've tried the first link and tried the synaptic package manager with no luck.

I've extracted the folder out of the tar.gz and placed it into my user directory

I have used the terminal to go to user/n_1v14

I then tried to use the ./configure command with no luck.  No such command or file name error.

---

### Post by macogw on 2007-02-21
I said that works on *most* things.  Not all things use makefiles.  Did you read the readme?  The readme will tell you how that specific program needs to be installed.  Always read the readme.

---

### Post by aysiu on 2007-02-21
What's the name of the game you're trying to install?

---

### Post by macogw on 2007-02-21
aysiu, it's called N.  OP said that in FP

---

### Post by crstacy on 2007-02-21
> **macogw said:**
> I said that works on *most* things.  Not all things use makefiles.  Did you read the readme?  The readme will tell you how that specific program needs to be installed.  Always read the readme.

Yes the read me only includes game hints and what files to keep in order for game progress to be tracked.

It's [http://www.harveycartel.org/metanet/downloads.html]("http://www.harveycartel.org/metanet/downloads.html")

I can't figure it out.

---

### Post by Tomosaur on 2007-02-21
Correct me if I'm wrong, but N is a flash game, right? If so, you need to download and install the [flash player](http://blogs.adobe.com/penguin.swf/2007/01/flash_player_9_for_linux_x86.html).

---

### Post by macogw on 2007-02-21
oh, it doesn't need to be installed, just executed...the file n_v14 inside that folder is the game itself, but ./n_v14 didnt make it go (which it normally would...)

tomosaur, i have flash installed and can't run it

i'm out of ideas...off to work now.

---

### Post by aysiu on 2007-02-21
The README file isn't terribly helpful: ```
N v1.4 / Ned v1.1
copyright (c) 2005 by Metanet Software Inc.
Raigan Burns / Mare Sheppard
metanet at harveycartel dot org






N readme  - table of contents

1. Before you Begin
2. Backing up your N progress 
3. New in v1.4
4. Tips and Gameplay
5. Custom Levels
6. Updates, News and More Information




-------------------- Section One: Before you Begin ------------------------------


Please read the included license agreement "license.txt".  
N is freeware, and is freely distributable as long as the archive remains intact.  


When you start N for the first time, a Local Storage window may pop up, 
requesting permission to store data on your hard drive.  

You must allow this in order to save any progress.  

See section 2 for information on how to back up your N progress.




---------Help with N's Performance

Please set your monitor to 1024x768 resolution;
For optimal performance, close all background tasks.

You will notice a slight improvement in performance if the
mouse cursor is _not_ over the window in which N is playing, 
or if you set your display to 16-bit color.



*NEW*

Linux users rejoice!  Many of the problems with N's awful
performance are related to sound, possibly the interaction of
OSS and the Flash player.  Try these fixes suggested
by Linux users on our forum:

1. try playing a song using XMMS or another music player

2. if that doesn't work, try this tip from another Linux user:

------
XMMS did not work for me, and since I am using Fluxbox WM I 
cannot easily tag a sound event to N, unlike KDE. But I found 
that if I use my browser (for verbosity, Mozilla Firefox 1.01 
with Flash plugin installed) to access a Flash page with sound 
(such as the menu for homestarrunner.com) I was able to then start 
N and play without the lag experienced previously.
------

3. and finally, you might notice some improvement if you set N's
priority to high:

------
start N in console like this:

nice -n 20 ./n_v14
------
(by Jehu)


Also, the above musical/sound fix seems to improve performance
on Mac and PC also -- playing a song in iTunes, Windows Media 
Player or WinAmp has been effective in reducing lag for _some_ users.  
Apparently the ninja enjoys listening to music!




---------News/Etc

N was the recipient of the 2005 IGF Audience Choice Award in the Web/
Downloadable category.  We want to take this opportunity to once again
thank everyone who voted for us.  You guys rock!




-------------------- Section Two: Backing up your N progress ------------------------------


When you start N for the first time, a Local Storage window may pop up, 
requesting permission to store data on your hard drive.  You must 
allow this in order to save any progress.

For a variety of reasons, .sol files sometimes get corrupted or overwritten, 
so it's important to keep a copy of your N .sol file just in case.  
For transfer or storage of this backup file, we recommend first zipping, 
stuffing, or otherwise compressing it.  

Shared objects are special files created by Flash with the extension .sol. 
In order to back up your N progress, you'll first have to search for the file.  
In Windows, search for '*.sol' in system and hidden files and folders, which can 
be selected in the advanced search options.  
In Mac OSX, use Find to search for files with extension 'sol' in Home or everywhere.


*** IMPORTANT! ***
Your N .sol file is called 'N_v14b_userdata.sol'.  When you find it, make sure you record the
location of this file, since that is where you'll have to copy your backup file in the event 
that your progress is lost.


Copy the .sol file and paste it into a new directory on your hard drive.  
We recommend making a new text file where you can record the directory in which 
you found the .sol file. Then compress these two files, and email the archive to yourself 
or whatever.


If your progress is corrupted, close N, copy your backup shared object to the 
correct directory and restart N.  Your progress should be restored.




-------------------- Section Three: New in v1.4 ------------------------------


-= HIGHSCORES AND TIMETRIALS =-

We made a few changes to N's highscores menu page, notably merging the Time Trials and
Highscore pages so you can more quickly try to beat a highscore when you're watching
a replay. 

To play a timetrial level, choose an episode from the [select episode] grid, 
then choose a level from the [view scores] menu -- if you've unlocked that level,
a "play level" button will appear. Click on it to begin playing in timetrial mode.


The highscores page now indicates game progress,showing you which episodes and levels 
you've unlocked "properly" (by beating previous ones), which you've unlocked via cheating, 
and which you've yet to see.  As always, to qualify for highscores and personal bests, 
you must play levels you've unlocked properly.


The submit button is now visible permanently. Highscores should be uploaded automatically
as you get them while you play N, but sometimes due to server or connection problems, the 
data is sent improperly.  If you see that one of your personal bests should be a highscore but 
isn't, just click submit and your score will be added.


Online highscore are accessible outside of the game at:
http://www.harveycartel.org/metanet/n_highscores_e.php

Very shortly these will feature a new Search page!  



-= USER LEVELS MODE =-

You can now play custom levels in N's game mode -- just click on User Levels from N's main menu.  You'll
see a list displaying your current collection of custom levels.  Clicking on entries in the list loads the 
level so you can play it immediately.  Click on a column heading ("level name", "author", etc.) to sort levels 
by that column. 


Included in your N download is a .txt file called userlevels.txt.  This file contains all the user level data
which will be loaded into the game.  We've started it with a sampling of our favourite user maps which didn't 
make it into N1.4.  When you add your own levels and levels you've downloaded from NUMA to this text file, 
they'll appear on the list you see in User Levels mode.  


*** EXTREMELY IMPORTANT ***
DO NOT DELETE userlevels.txt!! 


View the instructions in userlevels.txt for more information on adding and organising user maps.


User Levels mode also features a way for you to save and share replay data.  
After you play a level and return to the user levels menu, the replay will be available in a textbox 
on the left side of the screen.  You'll have to manually copy and paste the data to a text file, 
but this new feature allows you to swap game mode replays with other N players.

User Levels records personal bests as well -- not for highscores, but to indicate that you've 
beaten a user level, and to allow you to replay your best run at any time.  If you've beaten a user
level, a button will appear beside its entry in the list of levels.  Click the button to watch your 
personal best replay. As usual, the replay data will be available in the textbox to the left of the list.



-= CONFIGURE MENU =-

New to the Configure menu is the email field.  Entering an address in this field is optional, 
but if you want/need your password changed, you'll have to fill in a valid email address 
so we can mail you a new password.

Also new to the Configure menu is the Import Progress button.  Your progress from previous versions
of N should have been automatically imported the first time you started N v1.4; however, in the event
that it didn't, or if you've played an older version since then, you can use this button to get 1.4
up to date.  

NOTE:  This button will not clear your current data, but will supplement it.

Also new, the password field has been changed so your password is not visible after you type it in.  
Note however, it may be more difficult to remember your password since you can no longer see it.  If you 
do forget your password, enter your email in the email field and then send an email from that address to 
metanet at harveycartel.org.  
Include your username and what you'd like your new password to be and we'll reset it for you. 


And most excitingly, the flavour selection menu -- as you complete each column of episodes, you will 
unlock a new flavour of ninja.  Impress your friends -- collect all 9!




-= IMPROVEMENTS TO NED =-

Ned has been updated from a beta version to official version 1.1.  There are some exciting new changes!

Ned now boasts added feature documentation, viewable gridlines, visually linked door and door trigger 
objects, and the ability to copy and paste tiles.  No more tedious duplication of your favourite tiled 
shapes or images, now Ned will do all the work!

Note that some of the editor controls have changed as well: holding [ctrl] now allows you to drag
the ragdoll around, and pressing [tab] enters boss mode.


For more information, please read the editor_manual.txt or editor_manual.doc included in your N
download, where everything is thoroughly documented.  





-= PRACTICE MODE =-

We've added a level skip cheat to practice mode -- now you can skip through the levels in 
an episode by simply pressing [enter] before you begin a level.  This feature only works if practice
mode is turned on via the Configure menu.

Note that highscores/personal bests cannot be acquired when you're in practice mode, or for any 
levels you've only beaten while cheating.



-------------------- Section Four: Tips and Gameplay ----------------------------


---------In General

For information on rules, how to play, etc., view the 
In-game Help and Story sections (accessible from the main menu)
Check it out!  There are a lot of different moves to master.



---------Default Key Configuration

You can configure custom keys via the main menu.
The default keys are:

[left and right arrows]: accelerate left/right
[shift]: jump (hold key down for higher jump)

[k]: kill yourself (useful if you get stuck or trapped, or just for fun)
[p]: pause game/quit to main menu

[tab]: boss mode



---------Controlling the Ninja

Learning to control the ninja may take some time, but almost
any maneuver is possible given enough skill. And practice ;)



---------Making Custom Levels

*** Read included files editor_manual.doc or editor_manual.txt to find out 
how to make your own levels.




-------------------- Section Five: Custom Levels ------------------------------


Nick Johnson has created NUMA, the N User Map Archive:
http://numa.notdot.net/

You can download maps created by other N users, and upload maps of your own.  

You can also visit our forum for map contests, help and discussion:
http://metanet.forumer.com



-------------------- Section Six: Updates, News and More Information ------------


comments/bug reports/etc:
n at harveycartel dot org


updates and news about N can be found at:
http://www.harveycartel.org/metanet/ 


and at our forum:
http://metanet.forumer.com



Visit the forum for support with bugs and other issues!




enjoy!


---------------------------------------------------

(c) 2005 Metanet Software Inc. (Raigan Burns / Mare Sheppard)
``` It looks as if n_v14 is a precompiled binary.

You might want to try: ```
wget -c http://www.harveycartel.org/metanet/n_v1linux.tar.gz
tar -xvzf n_v1linux.tar.gz
cd n_v1linux
chmod +x n_v14
./n_v14
```

---

### Post by crstacy on 2007-02-21
I installed Flash player 9 and tried to run the main file.  When I did I got this error.

./n_v14: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

Is it just a bad file?

I tried it and while I sat back in wow of what it was doing I still got the same error.

---

### Post by bodhi.zazen on 2007-02-21
From the README :

> start N in console like this:

nice -n 20 ./n_v14

You may have to make n_v14 executable :

```
chmod a+x n_v14
nice -n 20 ./n_v14
```

---

### Post by crstacy on 2007-02-21
I'm still getting the same error even after I try both of those scripts

I have a strange feeling that these sorts of issues are the reason why Linux won't become a mainstream OS.  I am actually a power user of Windows and can do most tricks and such.  Linux is like a different world.

---

### Post by bodhi.zazen on 2007-02-21
Try installing libgtk1.2

Either via synaptic or :

```
sudo aptitude install libgtk1.2
```

---

### Post by crstacy on 2007-02-21
> **bodhi.zazen said:**
> Try installing libgtk1.2

Either via synaptic or :

```
sudo aptitude install libgtk1.2
```

Finally got that one installed,  now the error is
./n_v14: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

I take it I just keep finding the files to install until it works?

OK, it seems to be working now.  I installed most of the files I could find and it now works.  Thank you to everyone who helped me.  Linux may not be very user friendly, but the community is!

---

### Post by Spalatum on 2008-01-16
I would also like to get this game running but I have a hard time doing so. Non of the above mentioned has helped me.

---

### Post by macogw on 2008-01-16
> **Spalatum said:**
> I would also like to get this game running but I have a hard time doing so. Non of the above mentioned has helped me.

What kind of errors do you get?

---

### Post by Walter Melon on 2008-07-12
Here's what I did: I just copied and pasted from windows to linux.  When I downloaded it, it was just an .exe file.  I didn't have to turn it into an archive(tar.gz).  I use wine to execute it and it runs fine.  The only problem I'm having is that I don't know how to import my saved game data.  I have the .sol file but I don't know where its supposed to go.

---

### Post by PandaLinux on 2008-07-12
./configure
sudo make
sudo make-install

worked for me

make sure your in your ~ (home) directory

---

