---
title: "GUI is gone!"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by Sonic132 on 2006-04-21
Ok, here's the story...
I have been trying repeatedly to upgrade to Breezy Badger, but each time a different file is either already upgraded(causing an error), or somesuch. Each time I just removed the file, and got a newer version of the same file. This had worked thus far.

Well, now **xine** started causing me problems. I'm still not entirely sure what it is, but I think it is something to do with the GUI system. You see, I removed that, and was going to reinstall it, but the toolbar crashed so instead. I resetted the computer.

Upon restarting, the computer no longer booted into GUI Ubuntu. Instead, I'm stuck with Terminal linux.

I think I might be able to simply get the updater to replace **xine** and everything should be ok. But I cant recall any of those commands.

Anybody happen to know them, or can anyone offer any other ideas?

---

### Post by PhilOSparta on 2006-04-21
If you feel that a reinstall of xine will fix the problem, since you are at the terminal input,    enter
sudo apt-get install xine

You could possibly start X by typing in the terminal
startx

---

### Post by Sonic132 on 2006-04-21
```
sudo apt-get install xine
E: Couldn't find package xine
```
```
startx
xauth: creating new authority file /home/steven/.serveauth.7895
X: user not authorized to run the X server, aborting.
giving up.
xinit: Connection refused (errno 111): Unable to connect to X server
xinit: No such process (errno 3): Server error.
Couldn't get a file descriptor referring to the console
```

---

### Post by Sonic132 on 2006-04-21
Upon entering this line, **sudo startx** I got this response.
```
Xsession: unable to start X session --- no "home/steven/.xse/
"/home/steven/.Xsession" file, not session managers, no window 
terminal emulators found, aborting.
```

---

### Post by PhilOSparta on 2006-04-21
I did a search for installing xine and found this link.

[http://www.ubuntuforums.org/showthread.php?t=117139&highlight=gxine+install](http://www.ubuntuforums.org/showthread.php?t=117139&highlight=gxine+install)

You may need to check your repositories also.  They are located in
System -> Administration -> Synaptic Package Manager
when you get your X working.

---

### Post by Caligula on 2006-04-21
You coukd always install gnome/KDE/XFce again, but probably there is a simpler solution I just don't know about...

[CODE]sudo apt-get install ubuntu-desktop[CODE]
or of course "kubuntu-desktop"/"xubuntu-desktop"...
That will do the trick... is it says it's already installed, 
and you want to take the risk, you can always remove it and install then.

In the meantime;)
[CODE]sudo apt-get install lynx[CODE]
If you don't have, of course...
(That's what I'm using to write these line's, I'm in the Terminal...:D:D:D

---

### Post by Sonic132 on 2006-04-21
> I did a search for installing xine and found this link.

[http://www.ubuntuforums.org/showthre...=gxine+install](http://www.ubuntuforums.org/showthre...=gxine+install)

You may need to check your repositories also. They are located in
System -> Administration -> Synaptic Package Manager
when you get your X working.
I checked out that link and installed gxine. But it still keeps saying can't find package xine. Also, I cant get the **gedit** command to work in order to edit the sources.list file.
It says:
```
sudo: gedit: command not found
```

> You coukd always install gnome/KDE/XFce again, but probably there is a simpler solution I just don't know about...

```
sudo apt-get install ubuntu-desktop
```
or of course "kubuntu-desktop"/"xubuntu-desktop"...
That will do the trick... is it says it's already installed,
and you want to take the risk, you can always remove it and install then.

In the meantime
```
sudo apt-get install lynx
```
If you don't have, of course...
(That's what I'm using to write these line's, I'm in the Terminal...
OK, I installed lynx. But now how do I run it?

---

### Post by Caligula on 2006-04-21
well... that lynx was quite a joke.. you do know what it is, right?
It's a terminal web browser, so you can surf the internet while you're trying to fix this, on other enviroments "atl+ctrl+F1/F2/F3/F4/F5/F6"(F7 is GUI), like the desktops in GUI. You lauch it by simply typing "lynx"...

But If you do what I said in the other part you should be alright...
Good luck!
Tell us what happened...

---

### Post by Caligula on 2006-04-21
Oh! forgot something...
Gedit is for the GUI, you need to do so:
```
sudo **nano** /etc/apt/sources.list
```... 
good luck!

---

### Post by Caligula on 2006-04-21
But when I think about it...
also when you're in the terminal, it's supposed to say that it can't display gedit, not that command is not found...
But nano should still work, it's got nothing to do with the GUI.

Personally I would go for the ```
sudo apt-get install ubuntu-desktop
```...
makes things simple...

---

### Post by Sonic132 on 2006-04-21
LOL. Interesting program but I want my GUI back.

---

### Post by Caligula on 2006-04-21
[QUOTE=Sonic132]LOL. Interesting program but I want my GUI back.[/QUOTE]
Are you installing ubuntu-desktop again?

Personally I thinks it's the best solution, and there shouldn't
be any problems, with the amout of times I've done it... lol

---

### Post by Sonic132 on 2006-04-21
[QUOTE=Caligula]But when I think about it...
also when you're in the terminal, it's supposed to say that it can't display gedit, not that command is not found...
But nano should still work, it's got nothing to do with the GUI.

Personally I would go for the ```
sudo apt-get install ubuntu-desktop
```...
makes things simple...[/QUOTE]
I kinda wish I was more patient now. Because I didn't see your response until it was too late.
You see I took the old Ubuntu install disc and tried to repartition the linux partition. It failed, and the install failed. So, I restarted again. Now my computer is even more screwed because...the GRUB loader is failing to load the boot menu.
I dont even have a clue what to do now, because I cant boot into Windows to fix the partitioning.

---

### Post by Sonic132 on 2006-04-21
[QUOTE=Caligula]Are you installing ubuntu-desktop again?

Personally I thinks it's the best solution, and there shouldn't
be any problems, with the amout of times I've done it... lol[/QUOTE]
](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by Caligula on 2006-04-21
Yep.. you kinda screwed...
I think that when repartitioning fails it formats the disc, wi=hich mean I really hope you had a backup...

I cant think of anything to do except reinstalling the whole lot, it's not complicated, ask here if you get any problems during installation.

Good luck! hell, you'll need it...
P.S. The most important thing, don't worry, be happy:) in the pat two weeks I've installed the OS about 4 times...It's no a big deal...

---

### Post by howbag on 2006-05-21
If grub doesn't manage to show up (Grub error 21?) you prolly installed the OS on a physical slave disk, and not the master (this was what i did, and got it working after installing on the master)

I really have no clue when things get messy, i just try alot of things... this is what made my install work.
btw. I have the same startx problem aswell.

---

### Post by catlett on 2006-05-21
To get windows booting again you will need a windows install disk or the rescue disk that came with your computer. Boot to the cd and choose recovery. It will lead you to a command line enter```
 fixmbr
``` For Ubuntu it looks like your x winfow system didn't set up properly during upgrade. First tyry and reconfigure x to see if it is a configuration issue ```
sudo dpkg-reconfigure xserver-xorg
``` If that doesn't work you should be able to get everything back by reinstalling the gui with the earlier advice. Just run the command to remove it and then to reinstall. ```
sudo apt-get remove ubuntu-desktop
``````
 sudo apt-get install ubuntu-desktop
```
If you have access to another compouter it might be easier to download a copy of Breezy and upgrade by installing Breezy from the cd instread.

---

