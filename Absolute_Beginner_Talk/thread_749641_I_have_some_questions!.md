---
title: "I have some questions!"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by dragonblade on 2008-04-08
[LIST=1]
[*]Can someone give me a crash course on commands in the terminal and how to install .tar.gz applacations?
[*]I forgot to make it so I could go into GRUB and choose what to boot. How can I turn it on?
[*]How do I install another OS (Like Windows or another Linux distro) to dual-boot it with my Ubuntu?
[*]How do I install the drivers on a driver install disk that was disigned for windows?
[*]How can I make my PC faster? I have an EMachine ETower 466id. Please help! My PC is so slow!
[*]Can someone give me links to get some awesome apps (Useful,Improving,fun,labor saving)?
[/LIST]

---

### Post by R6V2 on 2008-04-08
Well, you can install anything if it's got room, when Installing Linux, it should of already setup GRUB, if you had another OS.

WINE can use windows based Apps to run on Linux.

If your PC is slow...Sucks4U! Get a new one :P

> Can someone give me links to get some awesome (Useful,Improving,fun,labor saving)?

Some awesome..what?

---

### Post by dragonblade on 2008-04-08
apps
some awesome apps

---

### Post by R6V2 on 2008-04-08
Ahh, Linux comes with Alot of great apps! Search around on your Z: drive...or whatever it is, and i'll find you some more on da internet :)

---

### Post by igknighted on 2008-04-08
> **dragonblade said:**
> [LIST=1]
[*]Can someone give me a crash course on commands in the terminal and how to install .tar.gz applacations?
[*]I forgot to make it so I could go into GRUB and choose what to boot. How can I turn it on?
[*]How do I install another OS (Like Windows or another Linux distro) to dual-boot it with my Ubuntu?
[*]How do I install the drivers on a driver install disk that was disigned for windows?
[*]How can I make my PC faster? I have an EMachine ETower 466id. Please help! My PC is so slow!
[*]Can someone give me links to get some awesome apps (Useful,Improving,fun,labor saving)?
[/LIST]

1) right click the *.tar.gz file in your file browser and click extract here.  Then open the readme file inside.  A *.tar.gz file is an archive (think zip file), so every one is different for how to install.  The readme should explain it.

2) 'sudo nano /boot/grub/menu.lst' will get you to the file to edit.  Read the commented lines for the explanation of each line before you change it.

3) Search the wiki, there is a good how-to.  Windows will overwrite the grub bootloader, so you need look up the instructions and have a liveCD handy.

4) Drivers for windows are 99.99% of the time completely unneeded, and 99.99% of the time they are worthless anyways.  There are a few exceptions... what devices did you have in mind?

5) Buy something that isn't an emachines?  Or possibly just add more ram, that often helps.  What are the specs?

6) Way too many to list... I like krita for photo editing, banshee for music, pidgin for chatting, vi for coding/text editing and AWN for an application launcher/dock.  Your mileage may vary with all of these.

---

### Post by cmay on 2008-04-08
terminal crashcourse.

sudo apt-get install some_program

pwd 
print working directory

whereis  some_file
prints out where the some_file you asked for is

find some_file
finds some_file that you wanted

whoami
lets you know who your logged in as

top 
info on stuff like cpu usage

free
memory free and used

man 
asks you what manpage you want ? 

man bash
displays you the man page for bash shell

you can combine two commands also
like echo hi there && sleep 2 && clear && hi again && clear
clear will clear the screen and echo will print message
and sleep will wait for 2 secs before do next thing its the && that combines the commands

and dont use any of the dangerus commands there is a treadh about .
you can do everthing in the shell like play music and print out tekstfiles but you can also 
by accident erase all your harddrives data. 
hoped it helped

---

### Post by aysiu on 2008-04-08
I'm answering these out of order for a reason (the order I'm answering is the order you should approach these issues in):

3. Install Windows first. Back it up. Defragment it. *Then* install Ubuntu or another Linux distro.

2. If you did #3 properly, then Grub should be installed and Windows should have already been added to the boot menu.

5. Try IceWM or Fluxbox. I have a guide to IceWM: [http://www.psychocats.net/ubuntu/icewm](http://www.psychocats.net/ubuntu/icewm)

4. You don't, unless they're wireless drivers. What's not working?

1. .tar.gz applications should be a last resort for a beginning user. Use the package manager instead: [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

6. Try [http://www.linuxappfinder.com](http://www.linuxappfinder.com) or just browse Synaptic Package Manager. If you don't know what Synaptic is, read #1.

---

### Post by t0p on 2008-04-08
> **dragonblade said:**
> [LIST=1]
[*]Can someone give me a crash course on commands in the terminal and how to install .tar.gz applacations?
[/LIST]

Check the link in my sig for a "cheat sheet" of Linux commands.

---

### Post by Fixman on 2008-04-08
> **dragonblade said:**
> [LIST=1]
[*]Can someone give me a crash course on commands in the terminal and how to install .tar.gz applacations?
[*]I forgot to make it so I could go into GRUB and choose what to boot. How can I turn it on?
[*]How do I install another OS (Like Windows or another Linux distro) to dual-boot it with my Ubuntu?
[*]How do I install the drivers on a driver install disk that was disigned for windows?
[*]How can I make my PC faster? I have an EMachine ETower 466id. Please help! My PC is so slow!
[*]Can someone give me links to get some awesome apps (Useful,Improving,fun,labor saving)?
[/LIST]

1) right click->extract here, then yuo must see a "INSTALL" file, throught the procedure generally is
```

./configure
make
make clean
sudo make install

```

2 and 3) [http://www.acpmag.com.au/node/5162/](http://www.acpmag.com.au/node/5162/)

4) You don't need any drivers, if the computer is giving you any error, just say what error is.

6) applications->add-remove, or system->administration->synaptic

EDIT: dammit, late! I must be quicker!

---

### Post by dragonblade on 2008-04-08
I just used widows as an example.
Really I just want to know about other Linux distros.

---

### Post by motoperpetuo on 2008-04-08
> **dragonblade said:**
> [LIST=1]
[*]How can I make my PC faster? I have an EMachine ETower 466id. Please help! My PC is so slow!
[*]Can someone give me links to get some awesome apps (Useful,Improving,fun,labor saving)?
[/LIST]

as far as making your PC faster, you could try xubuntu instead of ubuntu. it uses a lighter-weight desktop environment called xfce instead of gnome, which regular ubuntu uses. until recently, i had xubuntu installed on my six-year-old sony vaio (P4 1.2ghz, 256mb RAM) and it ran really, really well. if you really want to go light, try puppy linux. there's also something called fluxubuntu that's supposed to be even lighter than xubuntu, but i haven't tried it.

as far as useful apps, you can find almost anything you need in synaptic. just fire it up, type in some keywords, and go to town. note that if you can't find something on the menus after installing it, you'll probably have to press alt+F2 and type in the name of the app.

also, if i were you, i'd post these questions as different threads, or better yet, find threads that are already discussing these topics. the answers would probably be a lot easier to follow.

---

### Post by aysiu on 2008-04-08
> **dragonblade said:**
> I just used widows as an example.
Really I just want to know about other Linux distros.
Well, they operate quite differently, though.

Windows needs to be installed first, because it is selfish and doesn't want to recognize other operating systems.

If you install another Linux distro, it'll usually recognize Ubuntu and add Ubuntu to its own Grub boot menu.

---

### Post by dragonblade on 2008-04-08
> **R6V2 said:**
> Well, you can install anything if it's got room, when Installing Linux, it should of already setup GRUB, if you had another OS.

WINE can use windows based Apps to run on Linux.

If your PC is slow...Sucks4U! Get a new one :P



Some awesome..what?
...whats Wine?

---

### Post by aysiu on 2008-04-08
> **dragonblade said:**
> ...whats Wine?
Wine is a compatibility layer that allows you to run *some* native Windows programs in Linux, but I wouldn't count on it. Your best bet is to find a native Linux application:
[http://www.linuxappfinder.com](http://www.linuxappfinder.com) will help you.

---

### Post by dragonblade on 2008-04-08
What about running Nero 6?
Or do I have to find a Linux equivalent?

---

### Post by Fixman on 2008-04-08
> **dragonblade said:**
> What about running Nero 6?
Or do I have to find a Linux equivalent?

Theres a nero for Linux, but its not free. The best programs for replacing nero are K3B and DeVeDe (both are in applications->add-remove).

---

### Post by dragonblade on 2008-04-08
Ok.
What are the features that make them different?
Whats the UI like?

---

### Post by aysiu on 2008-04-08
> **dragonblade said:**
> Ok.
What are the features that make them different?
Whats the UI like?
The UI's fine. You can see screenshots of K3B here:
[http://k3b.plainblack.com/screenshots](http://k3b.plainblack.com/screenshots)

Just use it. It's very rare that someone finds a feature in Nero they need that K3B doesn't offer.

---

### Post by dragonblade on 2008-04-08
Ok

---

### Post by dragonblade on 2008-04-08
Can K3b copy/burn DVD movies?

---

### Post by aysiu on 2008-04-08
> **dragonblade said:**
> Can K3b copy/burn DVD movies?
I've heard K9Copy or DVD:Rip might be better for that, but I don't have a DVD burner, so I can't weigh in personally.

---

### Post by dragonblade on 2008-04-08
Ok.

---

### Post by Fixman on 2008-04-08
> **dragonblade said:**
> Can K3b copy/burn DVD movies?

Hey! that is illegal!

Nah, Im just joking, but yes, you can.

Also, you can make a faster faster faster and easier easier way that is:
```

Put the DVD to be copied on the track
A icon of the DVD hould appear on the desktop
right click the icon->copy disc (this may take a while)
Select "ISO image", and select some easy to find place (like the desktop or your home folder)
A new ISO file should appear (looks like a CD inside a case)
Remove the DVD, and place the DVD to copy
Double click the ISO file, select "Write" (This may take another while)
You are done!

```

---

### Post by dragonblade on 2008-04-08
Ubuntu will only recognize my external drive since I pluged it in.
I need both the internal and external to copy.

---

### Post by Fixman on 2008-04-08
> **dragonblade said:**
> Ubuntu will only recognize my external drive since I pluged it in.
I need both the internal and external to copy.

You can plug in both and both will be recognized, or just make an ISO as I explained you, unplug and plug the external drive, and burn the ISO.

---

### Post by dragonblade on 2008-04-08
One is internal, the other is external.
The internal one worked before I plugged in the external drive

---

### Post by dragonblade on 2008-04-08
> **Fixman said:**
> Hey! that is illegal!

Nah, Im just joking, but yes, you can.

Also, you can make a faster faster faster and easier easier way that is:
```

Put the DVD to be copied on the track
A icon of the DVD hould appear on the desktop
right click the icon->copy disc (this may take a while)
Select "ISO image", and select some easy to find place (like the desktop or your home folder)
A new ISO file should appear (looks like a CD inside a case)
Remove the DVD, and place the DVD to copy
Double click the ISO file, select "Write" (This may take another while)
You are done!

```
An icon for the DVD dosen't appear.

---

### Post by dragonblade on 2008-04-08
I can't even watch the DVD.
I get an error that says "Can not read from resource"

---

### Post by dragonblade on 2008-04-08
Is anyone here other then me?
Or did this thread die before it finished?

---

### Post by maniac_X on 2008-04-08
> **dragonblade said:**
> [LIST=1]
[*]How can I make my PC faster? I have an EMachine ETower 466id. Please help! My PC is so slow!
[/LIST]

This slowness, unfortunately, is kind of dependant on the hardware that is included in your EMachine. EMachines, in the past, has been notorious for including the barest of minimums of harware to get thier systems running. That's one of the reasons they were able to sell units so cheaply. Also inherent in past EMachine boxes was a severe lack of upgradability options. This usually meant another computer purchase.

You didn't mention any hardware specs for your EMachine. Posting those might give a clue to your "slow" issues with your computer. Even a modern Linux distribution might be slow if the hardware just isn't upto the task.

edit: I found these specs on the web. Hopefully yours is a bit more modern.
[http://www.epinions.com/cmhd-Desktops-All-eMachines_etower_466id/display_~full_specs](http://www.epinions.com/cmhd-Desktops-All-eMachines_etower_466id/display_~full_specs)

---

### Post by cmay on 2008-04-09
you could try debian or a littel distro called damn small linux.
i have a really old computer that can not run windows me that good but its no problem whit
running debian on it.
there is some distros out there designet to run on old hardware.
however ubuntu on a new or newish computer might be the better since its so userfreindley and pretty good updated all the time. 
there is also a lot of users of ubuntu coming along so its a good choice.
not that a debian user will feel that alone.
you could keep the old computer and try some other distros for that and get a new one for ubuntu.

---

