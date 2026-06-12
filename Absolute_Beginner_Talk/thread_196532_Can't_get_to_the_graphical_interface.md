---
title: "Can't get to the graphical interface"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by Woody71 on 2006-06-14
I did a complete install of ubuntu but its only taking me to a DOS type command.  What did I do wrong?  I made the CD like the instructions told me and followed the on screen instructions.  Please help...I really don't want to go back to windows.

---

### Post by tronica on 2006-06-14
what happends when you type startx at the prompt.

---

### Post by aysiu on 2006-06-14
I don't know why this happens, but every now and then... it does. I've never had it happen to me, but I've seen other users in this situation.

When you say "a DOS type command," do you mean that you see this once you log in? ```
woody@ubuntu:~$
```

If so, try these commands: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
``` When you enter the third command, answer the questions as best you can. If you don't know the answer, go with the default.

---

### Post by Woody71 on 2006-06-14
Thx guys.  I'm not at that machine right now but when I get home from work I'll give those a shot.  I'm such a noob!:rolleyes:

---

### Post by Woody71 on 2006-06-14
Ok, I'm getting a message that 'startx' is "command not found."  and the list of commands results in:
"Couldn't find any package whos name or description matched "ubuntu-desktop"
"No packages will be installed, upgraded or removed."
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded"
"Need to get 0B of archives.  After unpacking 0B will be used."

I'm stumped and really WANT to use this seemingly innovative OS.  Can SOMEONE please help me?  :confused:

---

### Post by aysiu on 2006-06-14
Can you try these commands, then? ```
wget -c http://www.psychocats.net/ubuntu/sources.list
sudo chown root:root sources.list
sudo cp /etc/apt/sources.list /etc/apt/sources.list_empty
sudo cp sources.list /etc/apt/sources.list
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by Woody71 on 2006-06-14
Does it matter that I"m not connected to the net?

---

### Post by aysiu on 2006-06-14
Yes! It definitely matters.

Hm. What CDs do you have on you--Desktop or Alternate...? Or Both?

---

### Post by Woody71 on 2006-06-14
[QUOTE=aysiu]Yes! It definitely matters.

Hm. What CDs do you have on you--Desktop or Alternate...? Or Both?[/QUOTE]


I have the desktop version

---

### Post by givré on 2006-06-14
Are you sure you don't have the server CD.
If it is
- download a desktop CD, or an alternate one to reinstall it
- OR try to connect to the net and do what aysiu said

---

### Post by aysiu on 2006-06-14
That's really weird... and unfortunate.

Weird because the Desktop CD doesn't have an option to install without the desktop (whereas the Alternate CD does).

Unfortunate, because the Desktop CD's repository is quite small, and I don't believe it includes *ubuntu-desktop*.

Why doesn't your internet work? Is it wireless? Dial-up?

---

### Post by Woody71 on 2006-06-14
It is the deskop version and how do I connect to the net since I've elected to do the complete install and erased my hard drive as per the options given in the set up?  I can start again from jump street but I have a sneaking suspicion that I'll get the same result.  The download said it'd be a complete install...

---

### Post by Woody71 on 2006-06-14
Aysiu I agree and my connection method prior to the install was wireless but I could just as easily plug into my ethernet card.  Thoughts?

---

### Post by aysiu on 2006-06-14
When you use the Desktop CD as a live CD, is there an internet connection?

Again, are you using ethernet, wireless, dial-up? What kind of internet connection do you have? Usually ethernet is detected automatically. Wireless and dial-up you sometimes have to configure.

---

### Post by Woody71 on 2006-06-14
I'll have to connect to the ethernet when I get home.  More to come.

---

### Post by ascherjim on 2006-06-15
Aysiu: I had the same problem as Woody71, and your detailed instructions worked perfectly for me.  Many thanks.  I was beginning to despair at being able to achieve a graphical interface, and was seriously considering a return to Fedora.  Installing the desktop was quite an impressive action to observe.  I believe it took longer than the actual initial installation from CD -- and perhaps it was in substance the same.  Anyway, such critically helpful and timely contributions to the forum such as yours are most valuable.  Keep up the good work.

---

### Post by nitricacid on 2006-06-15
What I would suggest is that you use the 'Alternate' Image of Dapper.

When you get to the  X server does it come up with a gray box explaing why x server has failed to load?

I can't believe no one asked: what kind of grahics card are you using?
That is usually one of the main reasons why xserver fails to show a GUI/desktop (like gnome)

Get back to me on these questions and maybe we can help you further. :)

---

### Post by givré on 2006-06-15
[QUOTE=nitricacid]
I can't believe no one asked: what kind of grahics card are you using?
That is usually one of the main reasons why xserver fails to show a GUI/desktop (like gnome)[/QUOTE]
You're right but is problem is a bit different :
```
Ok, I'm getting a message that 'startx' is "command not found." and the list of commands results in:
"Couldn't find any package whos name or description matched "ubuntu-desktop"
```
If he don't have startx, he don't have xorg, so no gnome or whatever.
What he just need is to install ubuntu-desktop.

---

### Post by nitricacid on 2006-06-15
i usually just use ```
sudo X
``` and that shows any any errors I have. 
Some reason when I used ```
sudo startx
``` it never did anything.

---

### Post by givré on 2006-06-15
> Ok, I'm getting a message that **'startx' is "command not found** ;)

---

### Post by nitricacid on 2006-06-17
You might want to try and just reinstall everything fresh.
Unless someone knows how to install the 'startx' command alone.

---

### Post by givré on 2006-06-17
starttx come from xinit, wich is a dependency of gdm and x-window-core, so i'm quite sure that if you don't have startx, you will not be able to have a graphical interface at all.

---

### Post by givré on 2006-06-17
starttx come from xinit, wich is a dependency of gdm and x-window-core, so i'm quite sure that if you don't have startx, you will not be able to have a graphical interface at all.
So of course the best think is a reinstall, or installing the ubuntu-desktop meta package

---

### Post by raptros-v76 on 2006-06-17
ok. if X fails to start, like that, if startx doesnt do anything but give errors, then you need reinstall X
```
 sudo aptitude install xserver-xorg
```
this has happened to several others, and when they did this, X worked again.

---

### Post by raptros-v76 on 2006-06-17
[QUOTE=givré]starttx come from xinit, wich is a dependency of gdm and x-window-core, so i'm quite sure that if you don't have startx, you will not be able to have a graphical interface at all.
So of course the best think is a reinstall, or installing the ubuntu-desktop meta package[/QUOTE]
the best choice is reinstalling X with aptitude. ubuntu-desktop is probably still there, its xserver-xorg that is missing.

---

