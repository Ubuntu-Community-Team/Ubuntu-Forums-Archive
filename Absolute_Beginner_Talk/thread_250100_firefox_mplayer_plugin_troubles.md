---
title: "firefox mplayer plugin troubles"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by garitd on 2006-09-03
When ever I try to watch a video thats not flash the mplayer does its thing.. it starts the download and everything seems to work fine till it fisnishes.. it gives me this error..

"Error: mplayer execv: No such file or directory"

So.. I dont even know where to begin with this.  I can tell you that Im running a 32bit firefox on a amd64 Ubuntu 6.06 everything else works great!

---

### Post by persev on 2006-09-12
For what it's worth I am having the same problem and I have already tried a lot of "fixes" no of which have worked, so  here is a bump.

---

### Post by garitd on 2006-09-12
ha ha .. yeah.. that actually makes me feel better.  Thanks for the bump :)

---

### Post by persev on 2006-09-13
I am really starting to think it is a Mplayer version problem because I have Elive 5 beta installed on one of my systems and it plays yahoo news flash videos fine but it's Mplayer version is .23 where as Ubuntu's version is .17
at least in reguards to plugins.

---

### Post by Kilz on 2006-09-13
> **persev said:**
> I am really starting to think it is a Mplayer version problem because I have Elive 5 beta installed on one of my systems and it plays yahoo news flash videos fine but it's Mplayer version is .23 where as Ubuntu's version is .17
at least in reguards to plugins.

Are you sure you have mplayer itself installed? I know its possible to install the browser plugins and not the player for some odd reason.

---

### Post by persev on 2006-09-13
> **Kilz said:**
> Are you sure you have mplayer itself installed? I know its possible to install the browser plugins and not the player for some odd reason.

Not only do I have it installed I have reinstalled it, I have also reinstalled the codecs and plugins.  I have also tried Automatix and Easy Ubuntu for codecs and plugins. I do know that the version installed in Elive 5 is 3.23.  If I am unable to resolve this I will have to put Win XP back on this machine to placate my wife, frankly it's getting tiring constantly hearing how "that linux stuff never works for me" and "why don't you just put windows back on it?" despite the fact that her laptop would barely run because of all the spyware and viruses under windows. How my wife manages to find the one thing that "won't work" under linux is beyond me.

I also can't find a deb package for mozilla-mplayer 3.23.

Also after much googling I have found that this issue with yahoo video,etc with the mplayer error is unique to ubuntu, it is apparently also comon to FC4 and FC5 users and others.

---

### Post by Kilz on 2006-09-13
> **persev said:**
> Not only do I have it installed I have reinstalled it, I have also reinstalled the codecs and plugins.  I have also tried Automatix and Easy Ubuntu for codecs and plugins. I do know that the version installed in Elive 5 is 3.23.  If I am unable to resolve this I will have to put Win XP back on this machine to placate my wife, frankly it's getting tiring constantly hearing how "that linux stuff never works for me" and "why don't you just put windows back on it?" despite the fact that her laptop would barely run because of all the spyware and viruses under windows. How my wife manages to find the one thing that "won't work" under linux is beyond me.

I also can't find a deb package for mozilla-mplayer 3.23.

Also after much googling I have found that this issue with yahoo video,etc with the mplayer error is unique to ubuntu, it is apparently also comon to FC4 and FC5 users and others.

I totaly understand the situation, My wife has the only Windows box on my home network because of complaints like that. I no longer clean out the garbage from it as a lesson of "you get what you ask for". Last time it got infected I handed her the restore disk. :mrgreen:
But lets see if we can get this working for you. The error means that it cant find mplayer. Enter these commands in the terminal and paste the results in a reply.

```
ls -l /usr/bin/mplayer
```
also 
```
ls -l /usr/lib/win32
```

---

### Post by persev on 2006-09-13
> **Kilz said:**
> I totaly understand the situation, My wife has the only Windows box on my home network because of complaints like that. I no longer clean out the garbage from it as a lesson of "you get what you ask for". Last time it got infected I handed her the restore disk. :mrgreen:
But lets see if we can get this working for you. The error means that it cant find mplayer. Enter these commands in the terminal and paste the results in a reply.

```
ls -l /usr/bin/mplayer
```
also 
```
ls -l /usr/lib/win32
```

First command gets this output: -rwxr-xr-x 1 root root 7251160 2006-05-15 17:46 /usr/bin/mplayer

Second one gives this: lrwxrwxrwx 1 root root 6 2006-04-19 19:42 /usr/lib/win32 -> codecs

---

### Post by Kilz on 2006-09-13
> **persev said:**
> First command gets this output: -rwxr-xr-x 1 root root 7251160 2006-05-15 17:46 /usr/bin/mplayer

Second one gives this: lrwxrwxrwx 1 root root 6 2006-04-19 19:42 /usr/lib/win32 -> codecs

Im hoping that /usr/lib/win32 -> codecs is a long list of codec files. I noticed you are running 64bit Dapper, Did you use my howto linked in my signature to set it up? If so what was the file name of the script you used. It will tell me the version.

---

### Post by persev on 2006-09-13
> **Kilz said:**
> Im hoping that /usr/lib/win32 -> codecs is a long list of codec files. I noticed you are running 64bit Dapper, Did you use my howto linked in my signature to set it up? If so what was the file name of the script you used. It will tell me the version.

The thread starter is using 64bit Dapper, I am using 32bit and I originally set it up with automatix.

---

### Post by Kilz on 2006-09-13
> **persev said:**
> The thread starter is using 64bit Dapper, I am using 32bit and I originally set it up with automatix.

:oops: 

O well just didnt notice it. Im not sure why its not working for you. Everything looks like its installed. Sadly there is no longer a automatrix section here to ask them if they could help.

---

### Post by persev on 2006-09-13
> **Kilz said:**
> :oops: 

O well just didnt notice it. Im not sure why its not working for you. Everything looks like its installed. Sadly there is no longer a automatrix section here to ask them if they could help.

Well I got it working! Took 3 days but finally success!  Okay here is what I did- first I removed w32codecs, mplayer, mozilla-mplayer, gstreamer0.10-pitfdll via synaptic; then I did "sudo apt-get remove automatix" in a terminal; then installed the latest version of Automatix; finally reinstalled codecs and Swiftfox browser with plugins. 
Now everything works in Swiftfox but if I open Firefox yahoo news videos still won't play in it.  I'm not sure which of these operations did the trick and I not going to undo everything to find out either as long as everything works under Swiftfox.
Thanks for the help though. I am going to try and paste this in other threads with the same problem.

---

### Post by Kilz on 2006-09-14
> **persev said:**
> Well I got it working! Took 3 days but finally success!  Okay here is what I did- first I removed w32codecs, mplayer, mozilla-mplayer, gstreamer0.10-pitfdll via synaptic; then I did "sudo apt-get remove automatix" in a terminal; then installed the latest version of Automatix; finally reinstalled codecs and Swiftfox browser with plugins. 
Now everything works in Swiftfox but if I open Firefox yahoo news videos still won't play in it.  I'm not sure which of these operations did the trick and I not going to undo everything to find out either as long as everything works under Swiftfox.
Thanks for the help though. I am going to try and paste this in other threads with the same problem.

I personaly dont recommend Swiftfox. Its the tivo of browsers. It takes FOSS code, compiles it, then changes the license to forbid you to redistribute it. All for that age old reason GREED, from the advertising and search revenu.

---

