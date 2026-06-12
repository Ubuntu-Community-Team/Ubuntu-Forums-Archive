---
title: "Installation troubles"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by .Maleficus. on 2006-06-26
Hi, I'm completely new to Ubuntu, and I'm having some problems installing a game I just downloaded.  The game is Warsow.  So far I have downloaded it to my desktop (I guess it did that automatically) and that's it.  I have no idea what to do, so any help is greatly appreciated.

---

### Post by Jagot on 2006-06-26
Have a look here - may help:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Brunellus on 2006-06-26
[http://doc.gwos.org/index.php/Warsow](http://doc.gwos.org/index.php/Warsow)

there seems to be an install script linked on the page.

---

### Post by catlett on 2006-06-26
You're not going to believe how easy this is. Right-click on the file that is on your desktop. Select "extract here". This will give you a folder on your desktop. Open the folder by double clicking on it. Inside will be a bunch of files that look like blue squares. Go to the file that is labeled "warsaw". Double click it and the game begins.


P.S. The screenshot is the inside of the warsaw folder. You want the first blue square after release. Hopefully it will be the same in your folder. The other squares are for other types of computer installation i.e. 64bit, etc but the plain warsaw should work for you.

---

### Post by .Maleficus. on 2006-06-26
Well, I downloaded the Loki Installer for it before, and when I clicked on it I got some sort of error message, saying it couldn't open the file.  I'm downloading the installer again to see if it was a bad download or something.

---

### Post by .Maleficus. on 2006-06-26
To catlett:  I did that, but when I click on Warsow, the screen went black and went back to my desktop.  Am I missing something that the file needs to run?

---

### Post by catlett on 2006-06-26
Don't download the installer. Download "FULL" in the linux section. Forget about the installer. Just download  the "full" linux version from the site. Right-click that file and choose extract here. That will give you the folder with the contents in the screenshot. Double click on the blue warsaw square and the game launches.

P.S. Figuring out how to play is up to you. I'm no gamer but I tried playing for the sake of it since you got me interested and I can't even get the setup configured correctly. Have you played this before? It appears to be an online game where you connect to others and all play. Just the same, I'd just be killed in under 30 seconds anyway :-D  Post if you have issues but I didn't use the installer.

---

### Post by catlett on 2006-06-26
What type of video card do you have? That may? be it. I have an ATI Radeon 128mb card. It is graphic intensive, that may be it. Or you may need the better drivers if you have a 128mb or better nvidia/ati card. What kind of card are you running?

---

### Post by .Maleficus. on 2006-06-26
I did download the full version from the site, AND the installer, thinking you needed both.  It shouldn't be my graphics card, because I have an nVidia GeForce 6600GT 128mb.  I read through the ReadMe file, and it said you need some sort of Java program to install it.  I don't know what that is, or where to get it, so I might just give up on this game.

Edit: Ahhh, I didn't see the thing about drivers before...  How would I go about installing new drivers?  Where do I get them?  The nVidia website?

---

### Post by catlett on 2006-06-26
Java is easy in Ubuntu (believe it or not) Give me 2 seconds and I'll be back with the commands.

---

### Post by catlett on 2006-06-26
Run these in the terminal.
```
sudo apt-get update
```
```
sudo apt-get install sun-java5-jre sun-java5-plugin
```
Then try the game again. It must be the java because your card is the same if nor better than mine :D 

P.S. You can just cut/paste the commands in the terminal if it makes life easier.

P.S. Didn't see your post but I'll post the commands for the better nvidia drivers.

[COLOR="Red"]For your nvidia drivers enter this[/COLOR] ```
sudo apt-get install nvidia-glx nvidia-kernel-common
``` You'll have to reboot for them to take effect. You'll know they are installed when you restart because there will be a nvidia logo splash page that appears for a couple of seconds before ubuntu starts.

---

### Post by .Maleficus. on 2006-06-26
Thank you very much for the codes, but right after I entered "sudo apt-get update", "Password:" came up, and when I tried typing something, nothing happened.  And seeing as how I don't know what they mean by password, typing something wouldn't have helped anyways.  Could you tell me what that means too?

---

### Post by catlett on 2006-06-26
The password you enter is your user password i.e. the password you log on with. When you enter the password nothing will appear. Not even ****. But it is entering. Just type in your login password and hit enter.

---

### Post by shoot2kill on 2006-06-26
it is ok, just type your main password, in ubuntu, no **** are shown it just stays blank, just keep typing, then press enter


LOL... ^ ^ ^

---

### Post by .Maleficus. on 2006-06-26
Ok, I did what you said (BTW, thank you for the fast replies) and this is what happened.  Did I do it right? because at the bottom it says couldn't find package or something like that.

andy@andy-desktop:~$ sudo apt-get update
Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release [30.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages [4571B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources [1478B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [25.3kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages [37.7kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources [22.1kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4253B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [6359B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Fetched 165kB in 2s (56.6kB/s)
Reading package lists... Done
andy@andy-desktop:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
andy@andy-desktop:~$

I will try updating the nVidia drivers now.

---

### Post by catlett on 2006-06-26
This is going to get a little complicated but it really isn't. Ubuntu has different repositories and you have to make them available to get certain packages. Just take a leap of faith and follow these directions.
Open up the terminal and enter these commands
```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list_backup 
```
```
sudo gedit  /etc/apt/sources.list 
``` The last command will open up a text file. Delete everything on that page and replace it with this next block of text.
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```

Save the file by clicking on save at the top of the window. Then close the window.
Go back to the terminal and enter ```
sudo aptitude update
``` Then re-enter the commands that gave the error about not available.

---

### Post by .Maleficus. on 2006-06-26
Ok, I have Java installed.  Here is the ReadMe on how to install it.  I don't know what they are talking about so it would be great if you could tell me what they mean.

Firstly you need a Java 5 (or higher) JVM installed.  If you currently do not 
have one then you can get it from [http://java.sun.com](http://java.sun.com)

Once you have Java installed you can un-compress this file anywhere on your 
file-system.  Inside the folder you will get a directory stucture like this:

<parentFolder>				-> the folder you extracted to	(eg 'c:/games/')
	|
	<wswBrowser Folder>		-> the wswBrowser folder 
		|
		|-ReadMe.txt		->	This file
		|
		|-wswBrowser.jar	->	The wswBrowser application in jar form
		|
		|-docs/				->	A docs folder holds documentation about the 
		|						program.  (Help / Changelogs etc)
		|
		|-lib/				->	resources used by wswBrowser (graphics etc)

There is one file which you have to currently modify to use wswBrowsers launch 
mechanism.  This is  lib/wswBrowser.properties.  In this text file there is a 
property called 'wswDirectory=/home/alex/warsow'.  You need to change this to 
where you installed warsow on your own machine. 
eg if warsow.exe is found at C:/Program Files/warsow/warsow.exe, then you would 
change this property to : 'wswDirectory=C:/Program Files/warsow'

PLEASE NOTE:  You currently need to use forward slashes on unix and windows 
systems.

You can run this program in a variety of ways.
Either double click the jar file if your machine is set up to launch jar files.
or 'java -jar wswBrowser.jar' In the directory with the jar file in.
I find it easy to create a bash script which changes to the correct directory 
and execs it all in one.  Then i can create a short cut on my desktop which 
launches it easily.


Edit: BTW, I would like to have a special section in my Applications menu for just games like this, (not the ones already installed) so how would I go about making a section for that?  Thanks again for the help!

---

### Post by catlett on 2006-06-26
In the warsaw folder there is another folder called "browser". In that folder is a text file called "wswBrowser.Properties". Double click to open that file. You have to edit that file. It looks like this 
> # wswBrowser properties file.

#

# Default .properties file. Created 10 Feb 2006, by Alex 'Cl1maX' Foreman







#	Here you can change and modify the programs setup.

#

# Program location

#

# wswBrowser needs to know where your warsow executable is.

# For instance on my machine (linux)it resides in '/home/alex/warsow'

# A windows machine maybe similar to 'C:/Games/warsow 

# replace to where ever you put the application. 

[COLOR="Red"]wswDirectory=../[/COLOR]







# Language

#	wswBrowser has multi-Language support.

#	It currently supports :-

#			English, 

#			Dutch, (Thanks KoFFiE)

#			French, (Thanks chtstorm)

#			German, (Thanks patman)

#

# Simply replace with the language of your choice

# Contact me in #warsow on quakenet if you would like to translate it to another

# language.  I'd be more than happy to add it

language=English







# Protocol

#	wswBrowser can select which version of Warsow servers it is looking for.

#	

#	0.072a is Protocol 6

#	0.1 is Protocol 7

protocol=7







# ServerTimeout

#	You can specify a server time out in milli seconds.

# 	After this time out the browser will disregard the server as 'dead'

#	It is a sensible default of 999 miliseconds

#	You wont normally want to change this.  Beaware that sometimes this timeout

#		is not completely honored. (Sometimes servers with higher pings get in)

#		This is due to the Java Scheduling system. No bug, no Damage :) 

serverTimeout=999 The red area (it's not red in the real file I just highlighted it here) is where you are going to put the "path" to the warsaw binary. I don't know your user name in Ubuntu but it is part of your path. 
I'll edit the file as if Maleficus is your Ubuntu name. Replace it with the user name you have in ubu8ntu if it isn't Maleficus.
i> # wswBrowser properties file.

#

# Default .properties file. Created 10 Feb 2006, by Alex 'Cl1maX' Foreman







#	Here you can change and modify the programs setup.

#

# Program location

#

# wswBrowser needs to know where your warsow executable is.

# For instance on my machine (linux)it resides in '/home/alex/warsow'

# A windows machine maybe similar to 'C:/Games/warsow 

# replace to where ever you put the application. 

[COLOR="Red"]wswDirectory=../home/Maleficus/Desktop/warsaw[/COLOR]







# Language

#	wswBrowser has multi-Language support.

#	It currently supports :-

#			English, 

#			Dutch, (Thanks KoFFiE)

#			French, (Thanks chtstorm)

#			German, (Thanks patman)

#

# Simply replace with the language of your choice

# Contact me in #warsow on quakenet if you would like to translate it to another

# language.  I'd be more than happy to add it

language=English







# Protocol

#	wswBrowser can select which version of Warsow servers it is looking for.

#	

#	0.072a is Protocol 6

#	0.1 is Protocol 7

protocol=7







# ServerTimeout

#	You can specify a server time out in milli seconds.

# 	After this time out the browser will disregard the server as 'dead'

#	It is a sensible default of 999 miliseconds

#	You wont normally want to change this.  Beaware that sometimes this timeout

#		is not completely honored. (Sometimes servers with higher pings get in)

#		This is due to the Java Scheduling system. No bug, no Damage :) 

serverTimeout=999

 The only issue I have is the .. (the 2 periods) before the / of /home/Maleficious/Desktop/warsaw. They put the ../ in the text. I don't know if it is needed because there is no .. used in ubuntu for files. A single . makes a file hidden but I don't that is what they wanted to achieve. If this doesn't work then remove the 2 periods ( .. ) before the path.


P.S. I never added a whole section to the menu before but I know you can add entries with "Alacarte Menu Editor" It is under Applications<Accessories. When you open it go to "file". It has an "add new entry option".

---

### Post by .Maleficus. on 2006-06-26
Well, I tried what you said, and the screen still goes black and then back to the desktop.  Might I not have installed Java right?

---

### Post by catlett on 2006-06-26
Did you change the text file /etc/apt/sources.list with the directions from my other post? And then did you run ```
sudo apt-get update 
``````
sudo apt-get install sun-java5-jre sun-java5-plugin
``` After you changed the list?

---

### Post by .Maleficus. on 2006-06-26
Yep, everything looked ok, I went through the questions and such.  Maybe I have the directory in the wswBrowser properties file wrong.  Are you going along with this installation on your computer too?  And if so, did you get the game to run?  I thought I had it right, but who knows.  I'll try some more.

---

### Post by catlett on 2006-06-26
I got it to run right away. Just for the heck of it I downloaded it when I saw your post. All I did was download the "Full" linux version. Right click and "extract here". Then I opened the folder and double clicked on the warsaw file i.e. the blue square.
My screen went blank for a second and then the whole screen was taken up by the game.
The screen has a menu and in the backgroung a demo of the game was running. It is a "shooter" type of game where you see the game from a view of your gun.
I had trouble setting up the character and getting into a game but the game launched and I was interacting with the menu just by double clicking the file.

Have you rebooted since you made all the changes? If you haven't, try it. I know the new drivers won't install until you do, maybe java is the same I don't remember..

---

### Post by .Maleficus. on 2006-06-26
Ok, I'll try rebooting right now.

---

### Post by .Maleficus. on 2006-06-26
Well, I just rebooted, and now nothing happens when I click the blue warsow icon in my warsow folder.  Now I'm really confused.  Also, I downloaded Tremulous (another FPS game) and when I clicked on the icon on my desktop, I get an error message saying it couldn't detect my character coding.  What does that mean?  And when I right click it, there isn't an option to extract it.

---

### Post by catlett on 2006-06-26
For Tremulous the issue is it is trying to open as a text document and it isn't. Righ-click on it ans select "open" it will have a window with options. Select "run". The installer will run.

---

### Post by .Maleficus. on 2006-06-26
The only options it gives me are "Open with Text Editor"" and "Open with another Application..." I don't have a regular "Open" option.  Am I supposed to have a regular "Open" option?

---

### Post by catlett on 2006-06-26
Right click on thye installer file. It will give you a menu. Select the top option "run". This will open another menu with 4 choices. 
```
run in terminel       display      cancel      run
```

Select run.
It will open a terminal and run a bunch of stuff. Just pretty much follow the directions. When it is done, you will have a folder in your home folder called tremulous. Open it and in it will be a blue square called "tremulous.x86". Double click it and the game will run.

---

### Post by .Maleficus. on 2006-06-26
Ughhh....  Now I get the message "No write permission to /usr/local/games".

---

### Post by catlett on 2006-06-26
Did it give you any other options? Is there a place you can put in /home/malfecious? You don't need permissions to write to your home folder.
I went through the installation (thyanks for turning me on to these games by the way) I just kept hitting enter and it bypassed it. I believe it gave me another option.

---

### Post by .Maleficus. on 2006-06-26
Where would I find the other option?  When I hit enter, it gives me the failed write window, then back the the usr/local/games/tremulous window.  I hit all the arrow keys, and it highlighted different things (OK and Cancel).  Is there something wrong with my computer maybe, since I can't run Warsow or Tremulous?

---

### Post by catlett on 2006-06-26
Actually I ran the installer and it stopped when I hit start install or something. Then I ran it again and it had a blue screen in the terminal with that same question. Then I just kept hitting enter and it gave another option. I actually thought the install failed but I looked in my home folder and there was a tremulous folder. I opened the folder and double clicked the tremulous.x86 file and the game launched.

I don't think there is anything wrong with your computer but to troubleshoot, search synaptic package manager for a game and install it. Then run it. Anything installed through synaptic package nmanager will work. If the synapticn game doesn't work then something is wrong.

---

### Post by .Maleficus. on 2006-06-26
This will probably sound like a very dumb question, but, where do I find the game once I installed it?  I installed (I think I did at least) 3ddesktop and some solitare game, but I can't find them.  Also, Tremulous WON'T let me install the game in my home folder, aren't I supposed to be able to put anything in there that I want?

---

### Post by .Maleficus. on 2006-06-26
Hmmm... This is very strange... It seems that whenever I press "Run", nothing happens.  I put in my CD of Unreal Tournament 2004, double clicked the linux installer, clicked "Run", and nothing happend.  This has been happening with the other things I have been trying to install too.

---

### Post by catlett on 2006-06-26
You can access anythping by typing it's name in the terminal and hitting enter ```
3ddesktop
``` I use the Debian menu. It shows everything. After you install it it will be under Applications. Run these commands for the Debian menu
```
sudo apt-get install menu
``````
sudo apt-get install menu-xdg 
``````
killall gnome-panel
``` I don't understand about tremulous. Home is where you have total control. The system is set up as if you are just a user and do not have administrator powers. So you install your apps to home.

---

### Post by .Maleficus. on 2006-06-26
Should I maybe just try to re-install Ubuntu?  I mean, I won't be losing many files, since, well, none are installed :P.  Would I maybe have more luck if I did that?

---

### Post by catlett on 2006-06-26
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) This is the guide I use when I install Dapper. Just do what we have been doing. Cut and paste the commands. 
Actually the list I had you use to replace the /etc/apt/sources.list is the one this guide uses.
So try a reinstal. Change the /etc/apt/sources.list again. Then go through that guide. It will set you up with java, flash, dvd playback, mp3 capability and more.
Then try the games. The install is quick. To run another install and go through that guide will only take an hour.
Ar least then you will know your computer is set up correctly

Good luck

---

### Post by .Maleficus. on 2006-06-26
Alright, I'm going to re-install.  Catlett, thanks again for all the help you've given me today.  Hopefully I will get the programs working this time.

---

### Post by .Maleficus. on 2006-06-26
Ok, I just got done re-installing Ubuntu and downloading updates.  I'm going to redo some of the things I did earlier in this thread, and install other programs fromt the website you gave me.

---

### Post by catlett on 2006-06-27
Good luck. Post if you have any problems. Start a new thread though. That way others that are smarter than me can see it and jump in. 
Stick with it, noone gets there install perfect first shot. When you get the hang of it you'll wonder how you let yourself be confined to the windows world.

See you aropund the forum.

---

