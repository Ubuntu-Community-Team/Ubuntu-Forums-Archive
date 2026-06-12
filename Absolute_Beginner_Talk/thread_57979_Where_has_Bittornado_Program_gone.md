---
title: "Where has Bittornado Program gone?"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by nickpaton on 2005-08-18
Complete newbie - downloaded, installed and updated to latest Kubuntu no probs.

My interest is to use this PC as a bit torrent downloader, using Bittornado program.  Loaded Bittornado using Kynaptic ( i.e right click Bittornado > Install>Commit changes to System> Install etc) and now a green square against Bittornado within Kynaptic. 

Am I right to assume that BT is now fully loaded and ready to go?  If so I cannot find a program symbol anywhere to click onto, to actually use the program i.e. via K Menu > Utilities/Internet or whatever.

I know this is a really basic question, but what have I done wrong or not done?

Many thanks in advance

Nick

---

### Post by TheDude on 2005-08-18
[QUOTE=nickpaton]Complete newbie - downloaded, installed and updated to latest Kubuntu no probs.

My interest is to use this PC as a bit torrent downloader, using Bittornado program.  Loaded Bittornado using Kynaptic ( i.e right click Bittornado > Install>Commit changes to System> Install etc) and now a green square against Bittornado within Kynaptic. 

Am I right to assume that BT is now fully loaded and ready to go?  If so I cannot find a program symbol anywhere to click onto, to actually use the program i.e. via K Menu > Utilities/Internet or whatever.

I know this is a really basic question, but what have I done wrong or not done?

Many thanks in advance

Nick[/QUOTE]

Go in Kynaptic. Search for an uninstall bittorrent. Now bittornado will be your default program for torrent files (just find them on the internet and click to download).

One note, did you do this:?

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Because you must do that to get the newest bittornado. Good luck.

---

### Post by nickpaton on 2005-08-18
I'm not sure if there's a problem with the install.  

From Konsole at nick@kubuntu: ~$  I've tried to run the update as per your post:
first:
sudo............. list_backup >return

It asks for the password which I give, and then immediately returns to the command prompt, i.e nothing appears to actually happen.

I then run:

sudo gedit etc/apt/sources.list  >return

And get 

sudo: gedit: command not found

and returns to nick@kubuntu: ~$

Doing a Find Files/ Folders puts Bittornado in 4 usr directories so the program appears to be loaded, I just cannot find any way of getting to it via K Menu.

I realise this sounds really stupid, but what am I actually doing wrong?
I have successfully installed Thunderbird email client via Kynaptic, but maybe I was just lucky!

Thanks again.

---

### Post by xequence on 2005-08-18
I am not sure about that because I use gnome but... Maybe you have to refresh the panel? Not sure how to do it in KDE though. Also try "Run Application" and type it in. Again, thats in gnome and I dont know about how to do it in KDE.

Also gnome comes with its own bittorent client.

Sorry I cant help more  ](*,)

---

### Post by bored2k on 2005-08-18
1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
* Instead of gedit, use the command kwrite
2a. sudo apt-get install bittornado-gui
or
2b. sudo apt-get install azureus
or
2c. sudo apt-get install bittornado-gui azureus

To execute, look it up on the menu or type (from a "konsole" terminal):
3a. btdownloadgui
or
3b. azureus

---

### Post by nickpaton on 2005-08-19
Many thanks to you all - I've now managed to get the program downloaded and working OK!

The secret for anyone else with similar problems is to not confuse KDE (Kubuntu) with Gnome (Ubuntu) environments.
 :roll:

---

