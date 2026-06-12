---
title: "Registry equivalence?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by mjitkop on 2007-04-24
Windows uses the registry to keep track of configurations of the OS itself and programs. Is there an equivalent to the Windows registry in Linux? If not, how does Linix do it? Profile files?

---

### Post by hanzomon4 on 2007-04-24
Sort of....

In gnome you have gconf-editor that lets you edit settings but most programs handle settings on their own also. What is it that you wish to change?

And yes your program settings are in your home dir but hidden, just go to view and click show hidden.

---

### Post by christhemonkey on 2007-04-24
For gnome programs there is an equivalent:
gconf
Though not all programs use it.

Much configuration of programs and the operating system is done in config files in /etc/

---

### Post by alanphil on 2007-04-24
Program configuration information will be in your /home directory. If you view hidden files in the /home directory you will see hidden files and directories (they start with a "." period). These contain your preference settings for each program, and the general desktop environment settings. 

I believe the "apt-get" process also must track what programs you have installed, but I don't know the details on what file contains that information. This would be a list of installed files, so the update process knows to tell you when there is a new version of Firefox, for example.

Alan

---

### Post by Rui Pais on 2007-04-24
> **mjitkop said:**
> Windows uses the registry to keep track of configurations of the OS itself and programs. Is there an equivalent to the Windows registry in Linux? If not, how does Linix do it? Profile files?

the closestis:
.<files> under /home/<username>/ for per user configuration apps.

and
/etc/* for system/administrator apps.

---

### Post by mjitkop on 2007-04-24
Thank you all for your replies. :)

I thought of asking this question because I read an article this morning on how to speed up Windows by cleaning up the registrty, for example. I also have a program called Tuneup Utilities on my PC with XP that does that by removing unused registry entries. 

I have no intentions of changing anything in Ubuntu right now. I was just wondering if Ubuntu can become sluggish like Windows does over time as programs get installed and uninstalled and stuff like that.

---

### Post by stimpack on 2007-04-24
It is surprising all the crap that slows Windows down... Yes your Linux can also be slowed down, but not generally by useless crap, just stuff you need, but if you need enough, ofc it be slower.

Registries = Bad Practice, expected of Windows, Im very disappointed to hear you also have this in Gnome. To empower the user, applications should be as self contained as possible. Breaking things because moving a program breaks a registry entry, tut tut, thats windows!.

---

### Post by Rui Pais on 2007-04-24
> **mjitkop said:**
> Thank you all for your replies. :)

I thought of asking this question because I read an article this morning on how to speed up Windows by cleaning up the registrty, for example. I also have a program called Tuneup Utilities on my PC with XP that does that by removing unused registry entries. 

I have no intentions of changing anything in Ubuntu right now. I was just wondering if Ubuntu can become sluggish like Windows does over time as programs get installed and uninstalled and stuff like that.
the registry is a single file, compressed but still huge, that its decompressed and read, all!!, at beginning of windows boot, no matter if you need or not *all* apps, no matter if it's impossible anyone use *all* apps and need all configs. Just bad design.

At linux you won't get any slowdown cause conf files will be read as needed by apps. Exception may be the gtk/gnome hidden files that tends to grow with use and time... but still not harmful as registry.

---

### Post by micfreedom on 2007-04-24
[COLOR="Blue"]> **stimpack said:**
> It is surprising all the crap that slows Windows down... Yes your Linux can also be slowed down, but not generally by useless crap, just stuff you need, but if you need enough, ofc it be slower.

Registries = Bad Practice, expected of Windows, Im very disappointed to hear you also have this in Gnome. To empower the user, applications should be as self contained as possible. Breaking things because moving a program breaks a registry entry, tut tut, thats windows!.

I am new to this forum and not very techie (although i'd like to learn and feel that ubuntu may be the right opportunity for me).
I am using Windows XP (yeah, I know, I know) at the moment, waiting for an extra Hard Disk Drive to put my work in this, then switch to Ubuntu.
I wondered how the switch over of programs operates. Do I transfer the programs I use from the extra disk drive one by one, and see that each work.
I have some wallpaper from Webshots and use Webshots to activate my wallpaper, containing some of my artistic (!) photos. Can I use Webshots on Ubuntu? How would you transfer that kind of program?
As a general question would be?
How to transfer  "programs that are used in Windows XP" to Ubuntu? Will they work? How to test this?
Is there a jargon that Microsoft uses and Ubuntu does/doesn't?[/COLOR] 
Sorry to put this to you like this, I thought your question and answer looked very similar to what I wondered about.

---

### Post by Rui Pais on 2007-04-24
Linux is a different OS.

You can only run Windows native executables under an emulator (like wine) and vice-versa.

As an example if you use Firefox at Windows you maybe will use firefox under linux but need to install The linux version (it's installed by default)

But Linux distros, on opposite of Windows, install tones of apps, and you will have even more available to install by package manager. All free. :)

---

