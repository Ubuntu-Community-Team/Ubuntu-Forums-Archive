---
title: "cmd line rocks"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by desijays on 2007-07-25
Im sure there are a few of us on this forum and probably others that swear by the terminal to do everything. Although Im not one of those fanatics, Im not much a fan of GUI's though I use it to get the occasional task done. I love the cmd line. Gives full control. I know for those of you that understand what Im talking, won't have a problem agreeing with me. 

What I like about the cmd line binaries is that, usually the binary files are programmed to perform one task well, very very well actually. And using IPC methods ( pipes || shared mems || msg queues ) it is possible to derive any kind of functionality by combining the various binary programs.

There are so many cmd line binaries out there. And listing and categorising the best of the best among them would be good for terminal freaks like me. 

So i was wondering if we can create a thread, listing the  various cmd line binaries that help to perform common functions a normal user would do using a GUI. Besides there are many threads listing GUI apps for linux. A thread listing the cmd line binary apps would be nice.

A category-wise arrangement would suffice, I believe.

The following can be used as a categorical blue print....

Audio Players
Video Players ( is it possible to view movies without loading x? or do i have to use a GUI terminal? )
Browsers ( lynx comes to mind :))
newsreaders
mail clients
games ( rogue ;) )
DVD, CD writers
picture viewers
installation, uninstallation suites ( apt-get, cache, file rock. is there anything better? )
compression ( bzip, gzip. anything else )
encryption

---

### Post by threeonethree on 2007-07-25
auy desi ... ke chakkar

---

### Post by Mornedhel on 2007-07-25
For video : mplayer.

A man page longer than the Silmarilion.

---

### Post by Nekiruhs on 2007-07-25
VLC all the way. just install it and then run ```
vlc -I ncurses
```
And theres text pidgin
```
finch
```
And text based GAIM
```
gaim-text
```
Oh, and Mplayer does indeed need X for video, I dont think Video is possible without X

---

### Post by univremonster on 2007-07-25
> **Mornedhel said:**
> For video : mplayer.

A man page longer than the Silmarilion.

You're right... I couldn't even bring myself to read any of it it's so long... So in that respect I'd say it's more like some Russian literature.

---

### Post by asmoore82 on 2007-07-25
yes, mplayer can use the kernel framebuffer or SDL and play a video without X11

want to checksum a CD and get some GUI-class output while doing it??

```
~ $ dd if=/dev/cdrom | pipemeter | md5sum >cdcheck.md5.txt
```

---

### Post by Mornedhel on 2007-07-25
Heh, SDL is for n00bs, I use the proud warrior's ASCII codec from libcaca.

---

### Post by Dr Small on 2007-07-25
You can use IRSSI for IRC, via the terminal.

---

### Post by Nekiruhs on 2007-07-25
> **asmoore82 said:**
> yes, mplayer can use the kernel framebuffer or SDL and play a video without X11

want to checksum a CD and get some GUI-class output while doing it??

```
~ $ dd if=/dev/cdrom | pipemeter | md5sum >cdcheck.md5.txt
```
And how might one do so? I've tried and it spits out crazy error messages and won't quit.

---

### Post by jvc26 on 2007-07-25
using a combination of screen on several machines I can get all the top/other commands I'm running on a bunch of servers via a simple CTRL+z+N and can change between individual commands I'm running on each of the servers with CTRL + a + N - Seriously, screen is one of the most useful and brilliant things I've found in cli - esp with the use of 1 terminal window to have all my connections, all my commands at my fingertips, and IRSSI always on on one of the servers so I am always able to access IRC, and dropped connections arent a problem. Oh and with detach I can leave my tasks running on a server, log out and come back later and they'll have been running while I was gone!
Il

---

### Post by asmoore82 on 2007-07-25
> **Nekiruhs said:**
> And how might one do so? I've tried and it spits out crazy error messages and won't quit.

the mplayer thing or the CD checksum thing (they weren't supposed to be related)

---

### Post by desijays on 2007-07-25
> **Illuvator said:**
> using a combination of screen on several machines I can get all the top/other commands I'm running on a bunch of servers via a simple CTRL+z+N and can change between individual commands I'm running on each of the servers with CTRL + a + N - Seriously, screen is one of the most useful and brilliant things I've found in cli - esp with the use of 1 terminal window to have all my connections, all my commands at my fingertips, and IRSSI always on on one of the servers so I am always able to access IRC, and dropped connections arent a problem. Oh and with detach I can leave my tasks running on a server, log out and come back later and they'll have been running while I was gone!
Il

What is screen again? So i gather it helps me to create a new sub-terminal within a terminal and i can tie processes to that terminal.

doesn't 'sh' allow me to do that already? or am I mistaken?

---

### Post by jaffamuffin on 2007-07-25
> **desijays said:**
> What is screen again? So i gather it helps me to create a new sub-terminal within a terminal and i can tie processes to that terminal.

doesn't 'sh' allow me to do that already? or am I mistaken?

"Oh and with detach I can leave my tasks running on a server, log out and come back later and they'll have been running while I was gone!"

Please take a few moments to understand the gravitas of this sentence.

---

### Post by desijays on 2007-07-25
> **Nekiruhs said:**
> 
And theres text pidgin
```
finch
```

On the website it says it makes use of libpurple. Do we have to download that and install as well?

---

### Post by desijays on 2007-07-25
> **jaffamuffin said:**
> "Oh and with detach I can leave my tasks running on a server, log out and come back later and they'll have been running while I was gone!"

Please take a few moments to understand the gravitas of this sentence.

missed that. but i get it now. Perhaps its akin to 'sh on crack'.

---

### Post by jaffamuffin on 2007-07-25
> **desijays said:**
> missed that. but i get it now. Perhaps its akin to 'sh on crack'.

Later could be in 6 months or 6 hours. If you are remoting in, and your connection drops, just reconnect and pick up where you left off, I suppose the closest analogy would be terminal VNC client type thing.  But It is a lot more than that, on crack as you say.

---

