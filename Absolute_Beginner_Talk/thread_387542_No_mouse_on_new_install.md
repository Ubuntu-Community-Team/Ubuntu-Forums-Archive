---
title: "No mouse on new install"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2007-03-18
New install of ubuntu  6.1 on older pc. Mouse pointer just stays in the middle of the screen.
Ocasionaly there is an error popup that says something like "There was an error starting the GNOME Settings Daemon" also "Some things, such as themes, sounds, or background settings may not work correctly"
I can close the error window with cr but the mouse stays in the center and I can't get any other buttons to work.

The motherboard is a pcchips m748lmrt with 290meg ram and slot1 p2 400mhz. Mouse is standard ps1 mouse on com port. Hard drive is just an old maxtor 4.3g I had laying around.
Had a hell of a time trying to install with no mouse. Never had any problems with the mouse with win95,win98 or XP. Go figure!
So if anyone has seen this and could help me out that would be great. Then I can move forward to more fun problems. Which I know will follow.
Thanks

---

### Post by oilchangeguy on 2007-03-18
given your rigs specs you'd probably be better off trying xubuntu. and you list the mouse as a ps1? do you mean ps2? or are you using a serial port mouse?

---

### Post by linuxjerk on 2007-03-18
Yes it is a serial ps1 mouse on a com port. Why shouldn't it work? Installing 6.1 is a nightmare.
Now I understand why linux has no chance against windows. So many bugs. 
I can't even get past the mouse problem to enjoy all the other fun bugs I've heard about!!!!!:lolflag: 
I do have it working now on a p4 system with a ps2 mouse but what the heck?????
Linux is a joke. No wonder Bill is making all those billions :popcorn: 

Help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by annda on 2007-03-18
please try not to offend people before asking them for help.

it is really an old and annoying bug.

if you are using COM1 port, the solution is:

(you will have to use the command line. bring up the terminal by hitting ALT+F2 and entering xterm as the command).

in the terminal, type the following line to back up the file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then: 

```
sudo gedit /etc/X11/xorg.conf
```

find the mouse section and change the device and protocol options to this:

Option "Device" "/dev/ttyS0"
Option "Protocol" "Microsoft"

ps. i found this by searching the forums for "serial mouse"

---

### Post by linuxjerk on 2007-03-18
I'm not trying to offend anyone. I'm just stating problems with linux that need to be addressed before it can even come close to competing with windows. Sad but true.

Thanks annda for some really helpful info. As soon as I can figure how to implement
it I will post back on the results.
I did search for mouse problems before I posted but I guess I didn't expect to have
the serial mouse ignored.
thanks

---

### Post by linuxjerk on 2007-03-18
Why does ubunto ignore serial mice?????????

---

### Post by oilchangeguy on 2007-03-18
you have to remember most of the computers that used serial mice have long been replaced or died. windows does just for backward compatability.

---

### Post by annda on 2007-03-18
ubuntu does NOT ignore serial mice. the newer linux kernels just do not auto-detect them. some distributions have included their patches to do that. others have not - users have to include them into their configurations. after that, the mice work.

---

### Post by linuxjerk on 2007-03-18
ok, I saved the xorg.conf file. Then I ran the gedit program. Now can you tell me how to get from the terminal to the edit program without a mouse?
It's probably some control characters or something. I don't even know how to terminate
the terminal. Help!

---

### Post by annda on 2007-03-18
switching between windows: ALT+TAB
terminating the command in the terminal: CTRL+c
killing the terminal: CTRL+d

hope this will help. post for more assistance.

---

### Post by DaveyG on 2007-03-18
im not being rude or anything but it pisses me off when people say stuff about linux, its your computers fault!

sad but true

do you have any drivers for your mouse?.

---

### Post by linuxjerk on 2007-03-18
Well alt+tab doesn't change from the terminal to the editor window no matter how many times I do it.
ctrl+D will kill the terminal and the editor as well.
ctrl+C doesn't stop command of the terminal.

I am so clueless about this stuff it's not funny. I am in a failsafe terminal in what I thin is a GNOME window??

When I start the system instead of logging in first I click alt+t to get options. Then change session to failsafe terminal. From there I start the editor no problem. Just can't do anything from that point.
Any more suggestions?
Thanks

---

### Post by annda on 2007-03-18
ok, you might have to do so more semi-advanced linux command-line stuff. sorry it has be so difficult, but i suppose 1 in 1000 users has to go through this in the beginning.

instead of gedit (a graphical editor) type nano. if you are in the failsafe mode, you don't even need to use sudo. so:
nano /etc/X11/xorg.conf
 after modifying the file go CTRL+o to save changes and CTRL+x to quit the editor.

---

### Post by linuxjerk on 2007-03-18
ok, I ran the nano thing. I was able to edit the file. Then I did ctrl+o and then the filename to save apeared. It says to press enter to save. When I press enter it says permission denied??
As far as I know I am root and I am logged in. What the heck?

---

### Post by linuxjerk on 2007-03-18
There are some things at the bottom that say things like. To files, mac format, prepend, dos format, append, backup file ???????

---

### Post by oilchangeguy on 2007-03-18
given the specs of your computer it's gotta have a ps2 plug for a mouse. why make life so hard, go to your local goodwill, salvation army store and buy a ps2 mouse for 2.00. and give up on the serial mouse.

---

### Post by linuxjerk on 2007-03-18
Believe it or not I'm learning something here. And no there isn't a ps2 plug.

---

### Post by oilchangeguy on 2007-03-18
a pent 2 with no ps2 plug????????? does it also run an AT form factor key board? as far as learning something, great. but this computer running 6.10 is going to be slow.

---

### Post by annda on 2007-03-18
if you do  not have permissions to do something, prepend sudo to terminal commands and gksudo to GUI programs - sorry, i must have confused failsafe with recovery mode.

also, getting a new mouse IS easy, but solving the problem - even if in numerous steps - is much BETTER. a couple of weeks later you will be a regular linux user not afraid of the command line to perform some tasks faster and more accurately.

and even if you never use the command line ever again, you will know that you can. this is a good feeling and it can even cancel out the frustration of a not working mouse.

---

### Post by linuxjerk on 2007-03-18
Absolutely fantastic, it works!!!  :guitar: :popcorn: :lolflag: 
You were right I needed to do it in the recovery terminal.
Thank you very much annda you were a life saver.:KS

---

### Post by annda on 2007-03-18
i'm glad you got it working. hopefully the ubuntu experience will be nicer for you than the beginning.

---

