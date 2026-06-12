---
title: "how to copy a file, and how do you know where do copy it to using the command line?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by babysteps on 2007-04-25
Obviously, I'm newer than new at this. I have taken the plunge and now i'm drowning....

How do I fill in the 'blank', the specifics when the instruction goes something like this:

Now copy the file to /usr/src
Code:

sudo cp /path/to/file/rt2570-1.1.0-b1.tar.gz /usr/src/

I don't know what the 'path' is , nor the 'to', nor the 'file'.
I cannot download the file because I don't have connection (and have been trying for some time now, but the majority of the instruction says to 'download' it...kind of ironic, and sometimes a slap in the face), and so i copy the file from a different computer via memory stick, and the 'rt2570 file is now on the desktop.  

So, i can extract it, but i don't know how to extract it to a certain place, nor where that certain place should be.  

Help?

babysteps

---

### Post by LaRoza on 2007-04-25
I am not sure what you want, are you trying to extract a file to a different directory?

 To uncompress an archive (usually tar.gz) you must use the tar command with the syntax
```

 tar -xvzf <file_name>.

```
To uncompress it to a certain location add 

```

-C newlocation

```

---

### Post by mikewhatever on 2007-04-25
A path to file is where the file is located. For example if test.txt is in you home folder, and your user name is Ubuntu-user, then the path to it would be /home/Ubuntu-user/test.txt.
As to where to copy a file is really up to you or to the how-to you follow.
Suppose you want to copy the said test.txt to /usr/scr. Here is the command.
cp /home/Ubuntu-user/test.txt /usr/scr

---

### Post by steve.horsley on 2007-04-25
If you say the file is on your desktop,
 and let's assume that your user name is babysteps, 
 and the file name is  rt2570-1.1.0-b1.tar.gz
then the path to that file will be: /home/babysteps/Desktop/rt2570-1.1.0-b1.tar.gz
Note the capital-D in Desktop. So the command to copy it to /ust/src would be:
**sudo cp /home/babysteps/Desktop/rt2570-1.1.0-b1.tar.gz /usr/src**

This can be done witht the nautilus file manager of course, but you need one with root permissions - you can get one with the command **gksu nautilus**.

---

### Post by babysteps on 2007-04-26
> **LaRoza said:**
> I am not sure what you want, are you trying to extract a file to a different directory?

 To uncompress an archive (usually tar.gz) you must use the tar command with the syntax
```

 tar -xvzf <file_name>.

```
To uncompress it to a certain location add 

```

-C newlocation

```

Thanks LaRoza for your reply.  I was wondering, if I could extract it to a different directory in one command?  Or does it have to be two separate actions?  Also, are the "tar -xvzf" and the "-C" interchangeable, or how are they different in functions?

---

### Post by aysiu on 2007-04-26
> **babysteps said:**
> Thanks LaRoza for your reply.  I was wondering, if I could extract it to a different directory in one command?  Or does it have to be two separate actions?  Also, are the "tar -xvzf" and the "-C" interchangeable, or how are they different in functions?
Sure. Here's an example from the Wiki:```
sudo tar xzvf firefox-2.0.0.1.tar.gz -C /opt
```

---

### Post by babysteps on 2007-04-26
> **steve.horsley said:**
> If you say the file is on your desktop,
 and let's assume that your user name is babysteps, 
 and the file name is  rt2570-1.1.0-b1.tar.gz
then the path to that file will be: /home/babysteps/Desktop/rt2570-1.1.0-b1.tar.gz
Note the capital-D in Desktop. So the command to copy it to /ust/src would be:
**sudo cp /home/babysteps/Desktop/rt2570-1.1.0-b1.tar.gz /usr/src**

This can be done witht the nautilus file manager of course, but you need one with root permissions - you can get one with the command **gksu nautilus**.

Thanks Steve.Horsely, and MikeWhatever for your help.  I eventually got to do what I wanted to do.  It's actually interesting how the computer seem to actually give some sort of feedback, sort of nudging me along, giving clues, but not budging until it's exactly right.  For example, if i forget a "/" or a "cd" change directory,   it will just say 'such and such is a directory', and after looking at the message,  eventually I will correct it after a "duh" moment.

Here's a question for you all:  I was wondering about how each version (mine is Breezy which is "abandonned" :( as of 4/13/07) will be supported for 18 months only, and that maybe I should stick to learning the command line, and working at the black screen (CTRL ALT + F1), instead of trying to learn something like gksu nautilus (?) and then having to look for help everywhere pertaining to that?

What are you thoughts and advices on that?

---

### Post by aysiu on 2007-04-26
I would install a GUI. You can still learn the command-line from with the GUI.

---

### Post by b1g4L on 2007-04-26
I agree with aysiu. Install a GUI - it'll give you a chance to use your computer right away and learn in increments about the command line. Trying to work strictly from the command line could get very frustrating, IMO.

---

### Post by babysteps on 2007-04-27
> **b1g4L said:**
> I agree with aysiu. Install a GUI - it'll give you a chance to use your computer right away and learn in increments about the command line. Trying to work strictly from the command line could get very frustrating, IMO.

Aysiu and blg4L,

So, "Graphical User Interfaces" (sorry I have to start learning what the letters stand for otherwise my eyes will gloss over) as in Ubuntu, right? 

 I have to admit when I first booted up my laptop with Ubuntu I fell in love with the look: the font (anyone know the name of the font?), the elegance, simplicity, well roundedness, and yet grounded and centeredness.  I was also just at the end of a phase of being drawn to that color of orange. There's no doubt in the attraction of the graphical representation.  At the same time, I've started to move toward the black/dark blue (painted my room black !) and the need for the simple,  basic, and focussed.  

Well, I can't think of anything better  than what I have now, being able to switch between the black screen and the GUI.

I just hope that the basics will always be functional.  For example, I may havefollowed the instructions incorrectly, but I couldn't use the rpm command to install a file for realplayer.  I don't know how many different basic distributions there are out there, but is it inevitable that users have to choose?  Does a basic langauge exist for any distribution? Or will things eventually evolve and break away?

Am I opening up a can of warms?

---

### Post by aysiu on 2007-04-27
A GUI doesn't have to be the full Ubuntu. You could install Xubuntu (something lighter) or a window manager (something even lighter than Xubuntu) like IceWM or Fluxbox.

As for RealPlayer:
[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

And for RPM and other installation methods:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by babysteps on 2007-04-30
> **aysiu said:**
> A GUI doesn't have to be the full Ubuntu. You could install Xubuntu (something lighter) or a window manager (something even lighter than Xubuntu) like IceWM or Fluxbox.

As for RealPlayer:
[url]https://help.ubuntu.com/community/RealplayerInstallationMethods[/url

And for RPM and other installation methods:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)


Hi Aysiu, thank you for the links.  I found them to be helpful.  I was able to install RealPlayer on the laptop that is able to get online.  At first there were no sound, and then somehow, I hit the space bar instead of clicking to play the video and the sound came on.  
Unforutnately the other laptop (still can't get online, yet) whose realplayer was installed via copied file through memory stick, has so so video, but no sound.

The link about how to install was very helpful, too.  The mystery of the .deb files and how to install them are now solved.  More importantly I now understand what Apt-get is for, and why in the past it hadn't worked for me.  Wish that was made clear, the fact that it will try to get online to get the sources.  

In my still frustrated frame of mind, I want to express the difficulty of having much of the instructions (I am grateful for their existence, don't get me wrong!) take the status of being able to get online for granted.  This catch 22 situation is perhaps the most discouraging aspect for beginners. Is there a way to get all the dependencies in a neat bundle for those who need to install but cannot get online with the particular computer? A particular example is one where I was supposed to get gcc-3.4 installed.  It was hard to find the right package,. and then when i copied the file onto the computer to install, it complains of 4 different things missing: fcc-3.4-base (=3.4.6-5), cpp-3.4 (=3.4.6-5), binutils (>=2.16.1-3) and Libc6 (>-2.3.6-5).  So I go and find those online, but they're not the exact same series of numbers.   I uninstall the Fcc-3.4 first, install these dependencies I listed, re-install gcc-3.4. Thing are OK for a while, then when at the crucial moment of installing the rt2570 driver for the nebulous Belkin USB wireless G, (the one with multiple ids depending on the version) I came close to installing the rt2570.ko file, then it complains of something about the gcc-3.4 line 11 and 12 can't be found....I get this substitute thing going, trying to get it to use gcc-4.0 instead .  I was able to "make", but then at the very last line of what was looking like it was doing well, I get another message about gcc-3.4 something about magic...and I never get to the final stage.  From that point on, the computer acts like a nag, complaining about something every few lines, as it kind of go off into space, looking for I don't know what....

It would be nice to not have that happen.

---

### Post by aysiu on 2007-04-30
Unfortunately, that's one of the biggest weaknesses of Linux, and I don't see it going away--Linux distros are very web-dependent. They tend to assume you have broadband internet and that it's working. Dial-up and wireless can be problematic.

The good news is that Ubuntu includes *build-essential* on the CD, so you can install *make* and all those other compiler goodies without an internet connection: ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

The bad news...
1. Most new users have no idea they need to install *build-essential* in order to *make*
2. Most new users have no idea *build-essential* is on the Ubuntu CD
3. *ndiswrapper* used to be on the CD, but (for some strange reason) the Ubuntu developers took it off for Ubuntu 7.04 (Feisty Fawn)

---

### Post by babysteps on 2007-05-03
> **aysiu said:**
> Unfortunately, that's one of the biggest weaknesses of Linux, and I don't see it going away--Linux distros are very web-dependent. They tend to assume you have broadband internet and that it's working. Dial-up and wireless can be problematic.

The good news is that Ubuntu includes *build-essential* on the CD, so you can install *make* and all those other compiler goodies without an internet connection: ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
``` 

Aysiu, I'm going to pick your brain some more.  I'm just curious as I have gotten myself a Linux phrase book and it mentioned the use of the " ; " to mean to execute one command, and upon success, then execute the next one, each separated by the  " ; ".  So, could I do the following?

sudo apt-cdrom add ; sudo apt-get update ; sudo apt-get install build-essnetial


> 
The bad news...
1. Most new users have no idea they need to install *build-essential* in order to *make*
2. Most new users have no idea *build-essential* is on the Ubuntu CD
3. *ndiswrapper* used to be on the CD, but (for some strange reason) the Ubuntu developers took it off for Ubuntu 7.04 (Feisty Fawn)

I followed instructions to install build-essential, but mine came with gcc-4.0, and it totally messed with the gcc-3.4 that I was trying to install for the rt2570 driver.  I wondered if I should have installed gcc-3.4 first?  

I think one thing that makes me feel helpless is not knowing how to back track...short of a re-install of Ubuntu, I don't know how to ensure I'm starting with a clean slate.  Thus, the hard drive gets wiped out time after time while each time I think "this is going to working now..."

IS there a sure way for a clean slate? for back tracking?

Babysteps

---

### Post by aysiu on 2007-05-03
> **babysteps said:**
> Aysiu, I'm going to pick your brain some more.  I'm just curious as I have gotten myself a Linux phrase book and it mentioned the use of the " ; " to mean to execute one command, and upon success, then execute the next one, each separated by the  " ; ".  So, could I do the following?

sudo apt-cdrom add ; sudo apt-get update ; sudo apt-get install build-essnetial I'm not sure, as I've never tried that, but you can do this: ```
sudo apt-cdrom add && sudo apt-get update && sudo apt-get install build-essential
```

> I followed instructions to install build-essential, but mine came with gcc-4.0, and it totally messed with the gcc-3.4 that I was trying to install for the rt2570 driver.  I wondered if I should have installed gcc-3.4 first? I don't know.  

> I think one thing that makes me feel helpless is not knowing how to back track...short of a re-install of Ubuntu, I don't know how to ensure I'm starting with a clean slate.  Thus, the hard drive gets wiped out time after time while each time I think "this is going to working now..."

IS there a sure way for a clean slate? for back tracking? Well, any time you ```
sudo apt-get install *something*
``` you can always ```
sudo apt-get remove *something*
``` to get rid of it or ```
sudo apt-get autoremove *something*
``` to get rid of it and its dependencies. You can find some useful other flags if you type ```
man apt-get
``` or ```
man dpkg
``` And don't forget a lot of this can be done graphically through Synaptic Package Manager (or Adept Package Manager, if you're using Ubuntu).

---

