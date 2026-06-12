---
title: "lost my desktop when trying 'desktop  effects'"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by granny6989 on 2007-04-09
tried to start the desktop effects from the taskbar, and it whites out my screen. Somehow it is now set to default, so that when I start xwindows, it whites out and i can't get anywhere. I can restart and get to the login page, but can only run the terminal mode, otherwise i'm back to the desktop blizzard. The mouse is there and moves around, but all other graphics are missing and i can't tell what's going on. Any info on where to look in my settings and what setup file to change to get my desktop back would be greatly appreciated. Thanks.

S*

ps- running feisty on i686 w/ nvidia mx4000 if that matters

:confused:

---

### Post by terdon on 2007-04-09
The easiest way to get a working desktop back is:```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo rm /etc/X11/xorg.conf

```
Then log out and log back in. This will copy your X configuration file to /etc/X11/xorg.conf.old and the next time you log in, a new one will be generated. You can also try posting the xorg.conf file in case we can figure out whats went wrong in the first place.

---

### Post by granny6989 on 2007-04-09
tried that, didn't change anything. It acts like it's going to load up and then goes to the blanked out white screen with the working mouse pointer still.....


trying to figure out how to get a printout or attachment of the xorg.conf now.

---

### Post by granny6989 on 2007-04-09
at this point i can print a hard copy but can't figure out how to save  to a disk or upload  the info.... i am pretty new to linux, and with the terminal only i am very limited in my abilities, sorry. if you can give me a tip on how to get that info out to a floppy or a cd from the terminal prompt it would be a great help.

S*

---

### Post by floke on 2007-04-09
If you can get to a terminal you can try this:

sudo dpkg-reconfigure -phigh xserver-xorg

This will reset your X settings

Hope this helps

* EDIT * BTW - use the space bar to select your resolution when prompted (you'll see what I mean)

---

### Post by granny6989 on 2007-04-09
so i've tried that also, but it stays the same.

When I log back in, it shows the loading bar briefly, then blanks out to all white with a working mouse pointer. If I move around the screen, it reacts like there is some desktop environment there, but with it all white, it's impossible to guess where anything would be.

This all started by going to the system/preferences pulldown and choosing the 'enable desktop effects'. I would assume that if it worked, it would pop up a window asking if you wanted to keep these settings, something like that... I think that I may have accidentally hit that button,  while mousing around on the white screen. With that in mind, is there a way to change that setting back in terminal mode. I am able to log back out to the login screen and boot to there  (with graphics), but once i log into xwindows, i'm the polarbear in the snowstorm again.........

S*

---

### Post by terdon on 2007-04-09
I don't know what "enable desktop effects ", I don't have that option in the dropdows (what version of ubuntu are you using by the way?). However, your problem sounds like you are running beryl. Beryl is a flashy desktop environment. I use it and it's great, but the white screen thing is a known bug. 

So, lets check if you are running beryl. When you get to the white screen, hold down the Alt Ctrl and F1 keys (once you are finished with the text mode hold down Alt and F7 to get back to the graphical world) . This will take you to text mode. Once there, login with your normal username/password. Then do```
ps aux | grep beryl[\CODE]
also try [CODE]ps aux | grep Xgl
```

If neither of these commands returns anything, this is not a beryl problem and we go to plan B. If you do get something post it, and I'll see if I can help.

Now, plan B. I assume you have a working winblows or whatever system alongside your linux. If this is the case you can redirect output from commands to a file you can access under windows and that way you can post it here. So, ```

cp /etc/X11/xorg.conf > /media/windows/C/Documents\ and\ Settings/username/Desktop/xorg.txt

```

This assumes that your windows C drive is mounted under /media/windows/C/, if not change accordingly. Do NOT remove the "\" before each space in Documents and Settings, they are needed. Finally replace "username" with your windows username. 

Now, this command will copy your xserver settings file to your windows desktop and save it as xorg.txt. Then you can boot into windows and post this file so we can have a look. 

Finally also try this:[CODE]
ps aux > temp.txt
cp temp.txt /media/windows/C/Documents\ and\ Settings/username/Desktop/ps.txt[CODE]

This will generate a list of all running processes and save it in your windows desktop. Post that list and I might be able to find anything running that should not be there and then walk you through killing it.

---

### Post by granny6989 on 2007-04-09
tried that stuff also, but don't know if it's beryl system or not... I am using the new Feisty 7  beta release, which has some type of integrated graphics effects package. It's in the pull down menus, and when i first tried it, it whited out but then you could escape back to normal desktop. Last try i was  mousing around on the white screen drawing circles  and what not to see if it would pop on, and i think that mayhap i hit some kind of confirm, which locked me into snowstorm mode. ANYWAYS, the good thing is that this is my only operating system,  so no windows transfer out, etc. Everything is actually working if I start in terminal safe mode, but i don't  know how to save to disk or anything or i would do that. if i could get my config info to a disk i could transfer it online with this fine macintosh machine that i'm typing on now. so that's my dilemma...

---

### Post by terdon on 2007-04-09
OK, did some googling and I think that the desktop effects of feisty are compiz (compiz is a project closely related to beryl, I won't go into the details since it is kinda controversial). Anyway, check out this thread and see if any of it helps.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/89741](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/89741)

---

### Post by marcus2004 on 2007-04-19
I thought that I would post here as I found out how to get out of the white screen.
Hold down Alt Ctrl and F1 keys and then Alt and F7 and then Alt Ctrl F1 again (at least I had to do it twice) and then it takes you into text log in. Log and then type:
```
ps -A
```
This will give you a list of programs with their PIDs
Find Compiz.real 
then type:
```
kill -9 (pid of compiz)
```

Then Alt F7 again and then go to System -> Preferances -> and Desktop Effects and disable the desktop effect.

---

### Post by TheTux on 2007-04-19
I'm still downloading Feisty. But I think if you disable the composite extension in xorg.conf the desktop effect will also be disabled. comment the following lines

```

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

hope that will help.

---

### Post by Steve Thornton on 2007-04-22
> **terdon said:**
> The easiest way to get a working desktop back is:```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo rm /etc/X11/xorg.conf

```
Then log out and log back in. This will copy your X configuration file to /etc/X11/xorg.conf.old and the next time you log in, a new one will be generated. You can also try posting the xorg.conf file in case we can figure out whats went wrong in the first place.
That helped me get things back - thanks

---

### Post by gantengx on 2007-04-23
i have the same problem too. i'm using nvidia geforce 5200fx, ubuntu feisty fawn and i got white screen.

i even tried to delete my user name, remove the username folder from home, and create it again still the same problem.

but if i create another user it works normally. anyone know how to fix it? thanks a lot

---

### Post by gantengx on 2007-04-23
oh found the solution already. restart the computer... geez....

---

