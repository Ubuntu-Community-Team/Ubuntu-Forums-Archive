---
title: "Can't play DVD."
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Lou_zer on 2008-01-27
[FONT="Century Gothic"][SIZE="2"]I can't play my DVDs.
When I try to play it, it gives me an error message.
It says to install the neccesary plugins.

Anybody wanna help?
Please & thank you.[/SIZE][/FONT]

---

### Post by emarkd on 2008-01-27
The easiest way to get that going is to install VLC media player.  Click on System > Administration > Synaptic and search for VLC

---

### Post by Bluestick on 2008-01-27
i have the exact same problem gives me a ERROR mssg when trying to play DVD...
 and i do have "VLC" installed....  ive tried diff DVD players nothing works!
 this sucks!

---

### Post by wolfen69 on 2008-01-27
this page [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) will tell you how.

---

### Post by Perfect Storm on 2008-01-27
Do you have all the codecs and libdvdcss2 installed?

Go to System tab ---> Administration ---> Software Sources.

Enable Main, universe, restricted and multiverse. 
Also go to 3rd party and enable partner.

Close Software Sources.

Next open the terminal as you need medibuntu (non-free codecs etc.)

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then it's set up.

codecs etc. installation via terminal (or you can seravh for them in synaptic)
```
sudo aptitude install non-free-codecs ubuntu-restricted-extras libdvdcss2
```


If you're using Totem it would be good idea to use totem-xine instead
```
sudo aptitude install totem-xine
```


Personally I use VLC for DVDs and media files on my computer and mplayer for media via the browser.

---

### Post by emarkd on 2008-01-27
Are you actually using VLC to play the disk?  You have to start VLC from the menu, then select File > Open Disk... in order to play it.

If that still doesn't work, did you try this?:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability)

---

### Post by Bluestick on 2008-01-27
I did everything u guys said and it says

 "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

 i belive i just installed libdvdcss .... hmmm..

---

### Post by emarkd on 2008-01-27
That software is up to version 2 now.  Try installing libdvdcss2.  Maybe that'll get it working...

---

### Post by bwtranch on 2008-01-27
Go back to Synaptic and make sure all your repositories are enabled. Then make sure to Update. Then, in a terminal run:

sudo apt-get update
sudo apt-get upgrade

This will fix the problem.

---

### Post by Lou_zer on 2008-01-27
I'm new to this.
Haha.
Can you put it in a term that I will understand?

---

### Post by emarkd on 2008-01-27
Click on System > Administration > Synaptic.  Then, click on Settings, Repositories and make sure all the boxes are checked except maybe the source code box, and save it.

From the main Synaptic screen, click Reload to reload your cache with the new repositories enabled.  Then you can use the search function to find whatever you're looking for.

---

### Post by bwtranch on 2008-01-27
Yeah sure no prob just didn't know how much you knew.  It's really easy (when you know how, lol)

First, go to System -> Administration -> Synaptic Package Manager, then under (after entering your password) go to Settings -> Repositories and check them all through the tabs. This will enable everything. Even some things that might be a little risky. I'm guessing you probably don't care about that. Now, hit reload.Good now we have all the repositories enabled.

Go to Applications -> Accesories ->Terminal
A terminal window will open and enter the following commands:

sudo apt-get update

and hit enter

after that is done put in:

sudo apt-get upgrade

and that will take a while because you have just upgraded your system. Now you are a pirate and the FBI is looking for you:) No, I'm just kidding. Maybe

---

