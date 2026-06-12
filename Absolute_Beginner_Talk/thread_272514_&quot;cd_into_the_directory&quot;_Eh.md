---
title: "&quot;cd into the directory&quot; Eh?"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by gn2 on 2006-10-06
I'm trying to install Wine to see if my favourite VOIP application will work on my Ubuntu Laptop.

Problem is I'm a Terminal-shy point-and-clicker...

Can someone please explain what the @/£% ? line 3 "cd into the directory" means please?
Bearing in mind I haven't a clue about Terminal commands or how it works...:redface: 



To install Windows applications using Wine, follow these instructions:

   1.  Download the Windows application from any source (e.g. download.com). Download the .EXE (executable).
   2.  Place it in a convenient directory (e.g. the desktop, or home folder).
   _3.  Open the terminal, and cd into the directory where the .EXE is located._
   4.  Type wine the-name-of-the-application.extension (e.g. wine realplayer.exe).

---

### Post by Aberrix on 2006-10-06
cd means 'change directory'

so you'll do something like..

cd '/home/user/folder'
(but without the ' marks and the directory you are actually looking for)

that will get you to the directory, just like clicking through folders in a gui.

---

### Post by bswilson on 2006-10-06
This refers to the command **cd**, which literally is an abbreviation for **change directory**.  To use this command, you must be in a terminal window.  When someone says "just cd into the directory", they mean that you want to change the directory you are currently in.

When you open the terminal window, you begin in your home directory, which will be the file path **/home/username**, where "username" is the name you gave to your account.  My username is bswilson, so my home directory file path is **/home/bswilson**.

Does this help?

---

### Post by gn2 on 2006-10-06
Did the "cd" thing, but either nothing happened or it gave an error...

Anyway, got Wine installed but the app I wanted, VoipCheap.exe didn't want to play, sound issues it seems.

Would have posted earlier but forum was down.

Thanks for the help.

---

### Post by Brownedwg89 on 2006-10-06
you might want to beware of caps. linux is case-sensitive.
For Example, when i first tried to run ventrilo in wine i was getting errors that it didnt exist because i was typing "cd ~/c/program files/ventrilo"
instead i should have typed "cd ~/c/Program Files/ventrilo"

also, "~" is short for "/home/*username*"

---

### Post by yellowband on 2006-10-06
hi gn2

its been a while since i've used vmware to run windows in linux, but if wine uses the same principles, you have to remember that it is only a virtual machine which is really running in linux.  Any hardware that is not supported in linux will not work in a virual machine either.  Maybe somebody with more experience could elaborate, but this may be why your software isn't working.

---

### Post by gn2 on 2006-10-06
I have the simpler solution to my woes, which is wait till my credit with existing VOIP package expires, then switch to a Linux friendly one...

I was wanting to use VOIPCheap [www.voipcheap.co.uk](www.voipcheap.co.uk) but it isn't supported in Linux. Can still use it's web interface to call direct from my home landline phone, bizarrely free to USA including mobiles (or is that cell phones?) but 10p/minute  to mobile next door? Weird.

Anyway, none of that terminal stuff for me, if I can't do it with a mouse I lose interest fast.

Horses for courses...

The terminal's days are numbered, the point and click brigade are coming.....

---

### Post by TooRight on 2006-10-06
Hang in there hon... i know it seems crazy, but although I was nervous about the terminal a couple of weeks ago, I am lovingggg it now!!

It's soooo much simpler than the old XP way that I'm used to... amazing how just a couple of lines pasted into it can do soooo much!! :D

---

### Post by gn2 on 2006-10-06
Cutting and pasting prewritten instructions from a guide is fine by me, but actually having to think what I'm doing is asking a bit much...

Haven't needed terminal for much other than to install automatix....
And change screen gamma.

---

### Post by Brownedwg89 on 2006-10-06
stick with it... the terminal becomes your best friend after a while
need to install something? you'll use apt-get for it instead of synaptic

---

### Post by gn2 on 2006-10-06
> **Brownedwg89 said:**
> stick with it... the terminal becomes your best friend after a while
need to install something? you'll use apt-get for it instead of synaptic

Doubt it, I'm just plain lazy.

---

### Post by grte on 2006-10-07
> **gn2 said:**
> Doubt it, I'm just plain lazy.

That's the thing.  If you know what it is you want, apt-get is much faster and easier than synaptic.  It enables laziness.

That's pretty much true of the terminal as a whole, once you learn some commands.

Consider installing, say, rythmbox.  In synaptic, you have to open the program, browse through the various files, or do a direct search (in this case, wait for the search to finish), then right click, select install, hit the apply button, wait for it to install, then click the close button on the status button, then you're done.

With apt, you open the terminal, type sudo apt-get install rhythmbox, and you're done.

---

### Post by gn2 on 2006-10-07
> **grte said:**
> 
With apt, you open the terminal, type sudo apt-get install rhythmbox, and you're done.

Quick isn't always best? (like sex for example)

With Synaptic you can browse through a range of software and try stuff you like the look of.

To install via terminal you have to already know what software you are looking for...

For example in PCLinuxOS VMWare isn't in the repo, so I needed an installer for the downloaded .rpm
I enter ".rpm installer" in a search of Synaptic and I found kPackage Manager, installed it and then used that to install VMWare Server.

Likes the precious Synaptic...

---

### Post by grte on 2006-10-07
> **gn2 said:**
> Quick isn't always best? (like sex for example)

With Synaptic you can browse through a range of software and try stuff you like the look of.

To install via terminal you have to already know what software you are looking for...

For example in PCLinuxOS VMWare isn't in the repo, so I needed an installer for the downloaded .rpm
I enter ".rpm installer" in a search of Synaptic and I found kPackage Manager, installed it and then used that to install VMWare Server.

Likes the precious Synaptic...

You can search with apt, as well.  The command is apt-cache search <term>.

---

### Post by gn2 on 2006-10-07
> **grte said:**
> You can search with apt, as well.  The command is apt-cache search <term>.

Just tried that and it seems to work, but with limited information presented.
It's not the same as browsing through Synaptic, which is a VASTLY better option. 
In my opinion.

Each to their own I suppose.

Please no more attempts to convert me, I'm happy as I am!

---

### Post by picpak on 2006-10-07
An alternative to cd'ing and whatnot is simply opening the folder and opening the .exe file with wine.

I've also found the Add/Remove Programs tool to be more intuitive than Synaptic. My family loves it.

---

