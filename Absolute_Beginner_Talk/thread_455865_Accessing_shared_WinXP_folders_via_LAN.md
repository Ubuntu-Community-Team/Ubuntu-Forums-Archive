---
title: "Accessing shared WinXP folders via LAN"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by wink on 2007-05-27
While I am an "oldie" (don't even ask how old), as far as Ubuntu goes I am one of the newest noobies, so please bear with me. 

Background:
I have sucessfully installed Feisty on two computers, one a desktop, the other a laptop and also managed to network them. The third PC on the network still runs Windows XP SP2.There are folders on the Windows machine containing music and graphics files I would like to be able to access. These folders have been set up to be shared. 

Problem: 
I can go to the Network - File Browser and the Windows Network does show up. Yet when I right-click and try to open that network, I see the location bar change to "smb:///" and no matter what I add (computer name, path to the shared folders), the result is always an error message.

What am I missing (besides a few thousand brain cells)?

---

### Post by hakimaki on 2007-05-27
When I networked my XP box, all I did was Setup Network or something like that (its been a while, sorry)  via control panel.  Give it a name, reboot, and it should come up under your windows network.

---

### Post by Alterax on 2007-05-27
Ah, you're gonna love this one.  I tried using the terminal for the longest with arcane mount commands, just to find out that the great people at Ubuntu made this easier.

Go to Places (on the bar up top), Network, Windows Network, whatever your network is called (default is MSHOME), your computer, click the share name, then it'll ask for your windows logon and password.

That's it; gotta love 'em for making it so easy.

--Alterax

---

### Post by hakimaki on 2007-05-27
To make myself clearer.  Alterax you are 100% correct, but my point was that he must first create a network on his windows box before it will be recognized through linux.  I can see where I wasn't clear enough initially.

---

### Post by wink on 2007-05-27
> **Alterax said:**
> Ah, you're gonna love this one.  I tried using the terminal for the longest with arcane mount commands, just to find out that the great people at Ubuntu made this easier.
--Alterax

If you ask me that was simply too easy. No wonder I couldn't figure it out. ;)
Many thanks.

Hakimaki: Thanks for the clarification but the Win network did exist having been setup a few years ago.

---

### Post by wataboutbob on 2007-05-27
Does using the actual name of the XP pc help. For example on my network, I can open any Nautilus window, and type smb://computer_name and it'll connect to my desktop with the same name.

---

