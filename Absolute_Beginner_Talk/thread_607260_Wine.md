---
title: "Wine"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Liliitha on 2007-11-08
I opened Warcraft III on Ubuntu with wine and it goes extremely slow.  Is it just me or does it not support gaming applications well?  Really slow, like mouse arrow moves once every 4 seconds.  : )

---

### Post by taurus on 2007-11-08
What kind of graphic card do you have and have you installed a driver for it?

---

### Post by pissedoffdude on 2007-11-08
> **Liliitha said:**
> I opened Warcraft III on Ubuntu with wine and it goes extremely slow.  Is it just me or does it not support gaming applications well?  Really slow, like mouse arrow moves once every 4 seconds.  : )

Try running it from the command line and add -opengl to the end of it.  Also make sure that you have correctly installed the proper video drivers for your graphics card.

---

### Post by Liliitha on 2007-11-09
Well I am checking the card now but I never installed anything for Ubuntu.  I didn't think it needed it since everything else worked fine, like youtube and gimp.  Do you all think they will not allow wine online because it is a third party program or does blizzard usually allow linux users to play online?  Hmmm.. I clicked the exe on the disc this time and the loading screen for the driver came up then froze.  Do I have a bad wine or can you not install drivers with wine?

---

### Post by Liliitha on 2007-11-09
Alright, after waiting a long time for the installation screen to load in wine the nv setup said it cannot install since none of it's packages match my current card.  The strange thing about this is that it always worked on windows and for some reason the disc stopped working on ubuntu.  Any Ideas?  The error message is > No suitable drivers for your current chip.

---

### Post by pissedoffdude on 2007-11-10
> **Liliitha said:**
> Well I am checking the card now but I never installed anything for Ubuntu.  I didn't think it needed it since everything else worked fine, like youtube and gimp.  Do you all think they will not allow wine online because it is a third party program or does blizzard usually allow linux users to play online?  Hmmm.. I clicked the exe on the disc this time and the loading screen for the driver came up then froze.  Do I have a bad wine or can you not install drivers with wine?

Try going to system>administration>restricted drivers manager and enable any restricted drivers.  If that doesn't work, then you should give envy a shot [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by Liliitha on 2007-11-10
> **pissedoffdude said:**
> Try going to system>administration>restricted drivers manager and enable any restricted drivers.  If that doesn't work, then you should give envy a shot [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

I downloaded envy but I don't know how to start the program... >.<  Is there a way to activate it threw terminal?

---

### Post by Maestro23 on 2007-11-10
> **Liliitha said:**
> I downloaded envy but I don't know how to start the program... >.<  Is there a way to activate it threw terminal?

In terminal:(Must be in the directory you downloaded it to)

> sudo dpkg -i packagename

---

