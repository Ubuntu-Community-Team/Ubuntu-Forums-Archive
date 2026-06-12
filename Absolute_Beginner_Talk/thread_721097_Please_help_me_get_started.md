---
title: "Please help me get started"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by TaintedBllack on 2008-03-11
I have just installed Ubuntu and need help to set up a few things. I tried reading through the forums and tutorials I found but there was so many different options I didn't know what was the best way to do it and was scared I would mess things up.

A list of the things I need help setting up:

1. (SOLVED) Run the java browser based game RuneScape.
2. Install and configure synergy. To use my desktop (Ubuntu) keyboard/mouse for my laptop (win xp).
3. Be able to share files between the two computers.
4. (SOLVED)  Be able to watch videos on youtube using firefox.
5. (SOLVED) Set up a good bittorent client.
6. (SOLVED) Configure amarok to load my music library from my 2nd hard drive. (I tried making links to home but every time I restart they dissapear.. leaving my music library empty in amarok.)


If you help me I will make a promise to help other members in the same way you helped me  once I get a better understanding of everything.

---

### Post by NullHead on 2008-03-11
> **TaintedBllack said:**
> I have just installed Ubuntu and need help to set up a few things. I tried reading through the forums and tutorials I found but there was so many different options I didn't know what was the best way to do it and was scared I would mess things up.

A list of the things I need help setting up:

1. Run the java browser based game RuneScape.
2. Install and configure synergy. To use my desktop (Ubuntu) keyboard/mouse for my laptop (win xp).
3. Be able to share files between the two computers.
4. Be able to watch videos on youtube using firefox.
5. Set up a good bittorent client.
6. Configure amarok to load my music library from my 2nd hard drive. (I tried making links to home but every time I restart they dissapear.. leaving my music library empty in amarok.)


If you help me I will make a promise to help other members in the same way you helped me  once I get a better understanding of everything.

For problem 4 and 5 you can do the following from a terminal: 
```
sudo apt-get install flashplugin-nonfree transmission
```

Copy and past that command into your terminal window and it will install Adobe Flash player(for firefox) and it'll install transmission bit-torrent client. 

I hope it helps you get a head start
NullHead

---

### Post by TaintedBllack on 2008-03-11
Thank you very much Null it worked great. :)

---

### Post by buried on 2008-03-11
1) Download Wine and use Firefox 2 or Install Java 6 manually.
4) Best choice to watch youtube is use Wine and Firefox 2 
```
sudo apt-get install wine
``` or Symnaptic Pacakage Manager.

---

### Post by kesman on 2008-03-11
WHAT? Wine and firefox for youtube? I don't recommend this at all.
If you already got youtube working in firefox, you could move to installing java.
There's a great guide in ubuntuguide.org :
> 
Ubuntu automatically installs plug-ins required to browse a site in Firefox. But if you want to install plug-ins run the following in Terminal:

For Java plug-in:

```
sudo apt-get install sun-java6-plugin
```

that's about it.

---

### Post by TaintedBllack on 2008-03-11
I installed Java but when I try to run the game it says I still need to install missing plugins. Any help?

---

### Post by kesman on 2008-03-11
in firefox type about:plugins in the address-line and check that Java plugin is listed in there.
If not, try running
```

sudo update-alternatives --config java

```

to see a list of java-version that are ready to use. Select the appropriate version and restart your browser.

---

### Post by TaintedBllack on 2008-03-11
> **kesman said:**
> in firefox type about:plugins in the address-line and check that Java plugin is listed in there.
If not, try running
```

sudo update-alternatives --config java

```

to see a list of java-version that are ready to use. Select the appropriate version and restart your browser.

It did not list any java plugins when I checked. I ran that command, selected sun java, and restarted my browser... still not showing any java plugin for firefox.

---

### Post by kesman on 2008-03-11
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre

Try these, may help

---

### Post by TaintedBllack on 2008-03-11
> **kesman said:**
> sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre

Try these, may help


EDIT: NVM I just solved the problem.. needed to uninstall the other java

---

### Post by kesman on 2008-03-11
You can right-click it in the normal file browser too, but in terminal you can use
```

sudo chmod 777 filename

```

---

### Post by TaintedBllack on 2008-03-11
> **kesman said:**
> You can right-click it in the normal file browser too, but in terminal you can use
```

sudo chmod 777 filename

```

HMM.. I tried doing it from the terminal but I am not exactly sure of the correct path. So then I tried the folder itself and it says I don't have permission to change the permissions.

---

### Post by Paqman on 2008-03-11
> **TaintedBllack said:**
> 
1. Run the java browser based game RuneScape.

For future reference, the package ubuntu-restricted-extras will install and set up Flash, Java, codecs and all sorts of useful little things in one step.
> 
2. Install and configure synergy. To use my desktop (Ubuntu) keyboard/mouse for my laptop (win xp).

Sorry, never used Synergy
> 
3. Be able to share files between the two computers.

The normal way most people achieve this is to install Samba. There's tons of info already on these forums about that. It can be a bit fiddly though.
> 
6. Configure amarok to load my music library from my 2nd hard drive. (I tried making links to home but every time I restart they dissapear.. leaving my music library empty in amarok.)

Is you second drive internal? If so, just make sure your permissions are set properly and you should have no problem pointing Amarok at your collection. You tunes don't have to be in your /home for Amarok to index them.
> 
If you help me I will make a promise to help other members in the same way you helped me  once I get a better understanding of everything.
That's the idea! Nice one!

---

### Post by Paqman on 2008-03-11
> **TaintedBllack said:**
> HMM.. I tried doing it from the terminal but I am not exactly sure of the correct path. So then I tried the folder itself and it says I don't have permission to change the permissions.

That's because Nautilus (the file browser) isn't running as root.

Two solutions:
[LIST]
[*]Find out the correct path (from Nautilus?) and use sudo in the terminal
[*]OR open Nautilus as root using the command "sudo nautilus". Make sure you close it and go back to regular Nautilus when you're done.
[/LIST]

Either way will let you change permissions.

---

### Post by LeAstrale on 2008-03-11
with amarok you can set it to automatically check for new music in the places you like.. just point it to your external disc under settings and press update collection or rescan collection.

/Astral-1

---

### Post by TaintedBllack on 2008-03-11
You have all been extraordinary helpful. :-D

I tried using nautilus as root but my other drives and partitions are not showing. How can I get them to show up so that I can change the file permissions. I would also really appreciate it if some one could direct me to some more information about partitions as I don't really understand them very well.

---

### Post by NullHead on 2008-03-11
A partition as in the way your drive is setup or the way Ubuntu reads them? 

Did you ever get java figured out? If not I need to ask if your running a x86_64(AKA 64bit) based install of Ubuntu?

---

### Post by TaintedBllack on 2008-03-12
> **NullHead said:**
> A partition as in the way your drive is setup or the way Ubuntu reads them? 

Did you ever get java figured out? If not I need to ask if your running a x86_64(AKA 64bit) based install of Ubuntu?

No I have not got java working properly yet.. Still having to load the game using unsigned java which prevents me from taking part in a lot of the best content of the game due to excessive lag and loading times.

I am not running 64bit

---

### Post by Sukarn on 2008-03-12
> **TaintedBllack said:**
> You have all been extraordinary helpful. :-D


This is the ubuntu forums. Get used to it... :)

By default, Ubuntu mounts partitions in "/media". To go to it, open up nautilus, and select File System from the left side. This will bring you to root (/) and now you can go to the directory media which should contain one directory for each of your partitions.

---

