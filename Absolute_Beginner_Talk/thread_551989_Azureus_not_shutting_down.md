---
title: "Azureus not shutting down"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by marx2k on 2007-09-15
Azureus will be running fine, but any time I would like to shut it down, the window does shut down but the process remains.  And I am talking about going to File/Quit, not just closing the window with the "X" in the upper right to minimize it to terminal.  I have to manually sigkill the process every time.  It doesn't really cause any harm to the system or any torrents I have going on when I do shut it down that way but it is a pain.  Also, it doesn't seem to be automatically updating itself through the CVS Autoupdater, though I think that's because it's unable to shut itself down.

Even when the window is shut down and it's supposed to be totally shut down, it's still doing transfers but just has no head.

Aggravating, and Im wondering if anyone else is having similar issues or knows of any fixes?  

I mean, it's not that I have to shut it down constantly or anything, but there is an update every day or 2 days and I have to manually do it now.

---

### Post by Digitallysick on 2007-09-15
I had constant azureus problems, random crashes, lock ups, etc, although this doesn't fix the problem, i suggest ktorrent, its really fast, and works better than azureus did for me try it, you wont go back

---

### Post by nonewmsgs on 2007-09-15
if you open it in a commandline like this

```

asureus

```

whenever you close that cli box, the program dissapears.

---

### Post by st33med on 2007-09-15
You could always do this:
```
sudo killall azureus
```

---

### Post by marx2k on 2007-09-15
Well the main issue isn't HOW to kill it, but the fact that it's not shutting down of its own volition.

Because killing it any other way than quitting it from it's own menu MAY screw the downloads up

---

### Post by nonewmsgs on 2007-09-15
i think it's actually a java bug.

---

### Post by marx2k on 2007-09-17
Yeah, it seems to be... but I am wondering if anyone else has the same behavior or if it's just me

---

### Post by misfitpierce on 2007-09-17
Azureus I only ran when I used automatix on last install and it ran fine but azureus takes too much resource for a download program... Deluge or Transmission <--- my pref. are better and lighter. Deluge carries all the +'s of azureus but runs lighter without java junk.

---

### Post by marx2k on 2007-09-18
I would rather use any torrent download program besides Azureus, but Azureus has one plugin I can't live without.  The plugin is AutoSpeed which pings either a set IP or IP's of the people closest to you in the download swarm and adjusts your upload rate based on the ping reply speed from your peers.  This keeps the upload rate as high as it can be on my router without pinging out my internet connection and sets it dynamically every X seconds.

No other linux based (or even Windows based) torrent download suite seems to offer that which keeps me tied to Azureus.

---

### Post by Ram Crammer on 2007-11-07
I had been using Deluge 0.5.0  but thought I'd try Asureus, since so many people are using it.  After screwing around for half an hour, trying to get it to work, I found a link to install a fix for the Java Run Time Environment.  I Installed that, but then the Ubuntu installer complained saying the older version of Asureus was better supported on Ubuntu.   Well, I decided to try  the newest version of Asureus, despite the dire warning.  The latest Asureus  wouldn't start, and gave the same Java Run Time error  message in terminal.  So, I installed the older version.  Now Asureus runs, but I could never get the NAT errors to go away.  

My router (a slick 2-Wire 700HG) does not support or require reassigning port IDs (the router does it automagically), so what the hell are you supposed to do then?  But that was just one of many problems I encountered while trying to decipher the cluttered and illogical Asureus interface and overly complex configuration wizard and options.  So, I decided to go back and download the very latest version of Deluge (v.0.5.6.2),   and Man, does it rock!!!  All the features I had wanted for months has now been implemented, and my downloads are now much faster.  You can select the files for download in bunches, and tag the entire bunch at once, with various priorities, including "don't download this file".  The Deluge interface is beautiful and logical.  Deluge is sooo much easier to set up, and use than any other client I've seen.  No fuss, no frustration.  From download to up-n-running  took all of about 2 minutes, and never a bit of trouble.  To all you Asureus sufferers out there, wake up!  Deluge blows Asureus out of the water. 

So, the moral is, don't download the earlier version of Deluge from the repositories, and don't bother with Asureus.  You can install and master Deluge v.0.5.6.2 in minutes.  It does everything you need without having to take a Masters level course in bit-torrent technology.  Get it here:  [http://deluge-torrent.org/about]("http://deluge-torrent.org/about")  The Deb installer for the Ubuntu version worked flawlessly on my 32 bit machine.  There is an installer for  64 bit systems also.  You can buy me a bear next time we meet :)

---

### Post by Perfect Storm on 2007-11-07
My vote goes aswell to Deluge, but if you're dieing for Azureus I made a howto/guide, just make sure to uninstall the previous azureus: [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

---

