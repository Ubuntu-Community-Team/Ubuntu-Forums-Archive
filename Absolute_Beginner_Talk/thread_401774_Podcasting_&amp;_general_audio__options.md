---
title: "Podcasting &amp; general audio  options"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by ratbagradio on 2007-04-05
I'm a podcaster who has switched from WinXP to Ubuntu over the past two weeks. I'm very happy with the change and am negotiating a sharp learning curce. However, I need some suggestions as I'm a bit confus3ed as to my immediate options.


SONICSTAGE: This is Sony program for managing uploads and downloads to their range of Mini Disc players. Sony has only in its last release updated the program to work on MAC -- but I recognise that Sonic Stage cannot be run on Ubuntu/Linux:

So that's out of my calculations and I'll need access to a Windows Program to continue to handle my HiMD audio.(More on that later)

I edit with AUDACITY -- and thats' OK as I have incorporated it into my Ubuntu desktop. I podcatch (ie:" download podcasts)with JUICE /LEMON/IPODDER --and thats' OK as that too is now running on Ubuntu.

But I'm having trouble with an audio player as I usually use an iRiver program for that. So which oif the audio players out there can handle all formats and how do I rig it to be my default player?

I have downloaded Amarok but it seems  not to be willing to play WAV and it gives me no play format  options? Is this the case? What other players should I consider for one click play? I'm ken on using one that will also delete the audio from the system if I want. I know the Democracy Video Player does that so I may fall back on that. I'd also appreciate a player with easy sync to device options such as exists with iTunes , iRiver programs and the like.

My"plan" is to keep my second computer on WIN XPP: and run my Sonic Stage on that while networking the two comp[uters to access shared files. I' haven't got around to seeing how to do that yet as I wanted to sort out my software issues.

So am I going about this the right way?

---

### Post by gilforsyth on 2007-04-06
Amarok should play anything you can throw at it.  
First, make sure you have the proper packages downloaded, 
Terminal:
```
sudo apt-get install gxine libxine-extracodecs
```

Then, in Amarok, go to Settings -> Configure Amarok -> Engine -> Output plugin and try selected Xine, if it isn't already selected.  

Amarok will also handle your podcatching with no problem.  
EDIT: Sorry, thought you had an ipod.  You should be able to find the appropriate instuctions for connecting your audio player to Amarok via google or the forums.  If you post what model player you have I can try to run it down for you.

Also, if Amarok does play all the files you want it to, you can configure it to be the default player for each audio type by right clicking on a file and going to properties and setting Amarok as the default player.

---

### Post by ratbagradio on 2007-04-06
Yeah -- I intalled Amarok and it didn't play mp3 format. It asked for it to be installed. That was several long hourse ago whiel I did searches and tried , I guess, about five solutions -- until I got to the one you suggest here. I fsolved it just then before logging onto thsi forum to catch your reply.

I was missing them packages big time ands there was the massively long upgrade in TERMINAL.

[in frustration I also played with Songbird hoping that was a option...]

But now I'm happy but I had to also REBOOT to  get the desktop audio friendly.

As for my Mp3 devices:

I use **iRive**r -- the **T30** and the **ifp 700**. The 700 series is notoriously difficult to sync to but it's a great recorder(with plug in play mic power) -- which also plays. but I'm primarily focused on HiMD which employs  a very separate format to Mp3.

So if you can help me to get my T30 syncable (and I haven't looked at that yet as I've been caught up with chasing the mp3 rainbow) I'd much appreciate it.

---

