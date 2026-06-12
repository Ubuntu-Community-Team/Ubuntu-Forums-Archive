---
title: "HELP! Can't acess anything!"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by liamwithers on 2007-09-21
Hi, I was just trying to install Enlightment and get it working on my pc from here: [http://ubuntuforums.org/showthread.php?t=54476]("http://ubuntuforums.org/showthread.php?t=54476")

I edited a file which i accessed by doing this: ```
sudo cp /usr/share/gnome/default.session ~/.gnome2/session
sudo gedit ~/.gnome2/session
```

It said to change 1,RestartCommand=gnome-wm --sm-client-id default1 but there wasn't that file, there was 0,RestartCommand=gnome-wm --sm-client-id default0 and 1,RestartCommand=gnome --sm-clientid default 1 (something like that, thinking off the top of my head)

It then said to restart the X server. CTRL+ALT+SPACE, that wouldn't do anything so I logged out because it said once I restarted the X server I had to log back in. Once I logged out and back in I have lost my new toolbar which had everything on it. I had to create a launcher and put in Name: Firefox and Command: Firefox, luckily it worked. 

SOMEBODY PLEASE HELP! I don't even know how to get to the terminal with a short cut to get back to that file and edit it to normal. 

Any help GREATLY appreciated.

---

### Post by yman on 2007-09-21
> **liamwithers said:**
> Hi, I was just trying to install Enlightment and get it working on my pc from here: [http://ubuntuforums.org/showthread.php?t=54476]("http://ubuntuforums.org/showthread.php?t=54476")

I edited a file which i accessed by doing this: ```
sudo cp /usr/share/gnome/default.session ~/.gnome2/session
sudo gedit ~/.gnome2/session
```

It said to change 1,RestartCommand=gnome-wm --sm-client-id default1 but there wasn't that file, there was 0,RestartCommand=gnome-wm --sm-client-id default0 and 1,RestartCommand=gnome --sm-clientid default 1 (something like that, thinking off the top of my head)

It then said to restart the X server. CTRL+ALT+SPACE, that wouldn't do anything so I logged out because it said once I restarted the X server I had to log back in. Once I logged out and back in I have lost my new toolbar which had everything on it. I had to create a launcher and put in Name: Firefox and Command: Firefox, luckily it worked. 

SOMEBODY PLEASE HELP! I don't even know how to get to the terminal with a short cut to get back to that file and edit it to normal. 

Any help GREATLY appreciated.

its Ctrl+Alt+Backspace to restart X.

by the way, you can access a terminal with Ctrl+Alt+F1 (or any other function key, like F2. the terminal you are working in is likely to be accessible with F7). you'll need to log in.

you can also open the main menu in Gnome using Alt+F1. open a window that allows you to execute commands with Alt+F2. you can choose to run them in the terminal then.

---

### Post by jr.gotti on 2007-09-21
When the computers all booted up, hit control alt F2. This will bring you to a console window. Log in like normal, and then enter:

sudo vim ~/.gnome2/session
This will bring you to a text based editor. Edit the file, and then save it.

(To insert text, first press "i"...when your done editing, press escape to get out of insert mode, then press ":" and type in "wq" and hit enter. (This will write the file then quit.)

Then hit Control Alt F7, and restart the Xsession. (Control Alt Backspace)

---

### Post by liamwithers on 2007-09-21
Just so i definitely do it right, please could somebody find the same file and tell me what the line in the file says, its something like 1,RestartCommand=gnome --sm-clientid default 1

---

### Post by jr.gotti on 2007-09-21
> **liamwithers said:**
> Just so i definitely do it right, please could somebody find the same file and tell me what the line in the file says, its something like 1,RestartCommand=gnome --sm-clientid default 1

```

[Default]
num_clients=6
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
2,id=default2
2,Priority=40
2,RestartCommand=nautilus --no-default-window --sm-client-id default2
3,id=default3
3,Priority=60
3,RestartCommand=gnome-cups-icon --sm-client-id default3
4,id=default4
4,Priority=40
4,RestartCommand=gnome-volume-manager --sm-client-id default4
5,id=default5
5,Priority=50
5,RestartCommand=vino-session --sm-client-id default5

```

---

### Post by yman on 2007-09-21
> **liamwithers said:**
> Just so i definitely do it right, please could somebody find the same file and tell me what the line in the file says, its something like 1,RestartCommand=gnome --sm-clientid default 1

this is what it says, in my unaltered file right from the ubuntu 7.04 (feisty fawn) live CD:
```
# This is the default session that is launched if the user doesn't
# already have a session.
# The RestartCommand specifies the command to run from the $PATH.
# The Priority determines the order in which the commands are started
# (with Priority = 0 first) and defaults to 50.
# The id provides a name that is unique within this file and passed to the
# app as the client id which it must use to register with gnome-session.
# The clients must be numbered from 0 to the value of num_clients - 1.

[Default]
num_clients=6
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
2,id=default2
2,Priority=40
2,RestartCommand=nautilus --no-default-window --sm-client-id default2
3,id=default3
3,Priority=60
3,RestartCommand=gnome-cups-icon --sm-client-id default3
4,id=default4
4,Priority=40
4,RestartCommand=gnome-volume-manager --sm-client-id default4
5,id=default5
5,Priority=50
5,RestartCommand=vino-session --sm-client-id default5
```

---

### Post by liamwithers on 2007-09-21
Right. I don't think I have done this right. I got into the file and changed it, then pressed escape like you said, all it done was "beep" out of my pc. Then I pressed the FULL STOP BUTTON, was i supposed to press that? I couldn't decide what it said in your post. Please spell it if isn't fullstop. When i pressed fullstop i realised the second time i tried to do this that it inserted another - (hash/minus whatever it is) So i removed that, and tried pressing hash after escape and it didn't do anything and then i pressed wq and enter to only get another beep. Then pressed CTRL ALT F7 to come back here with no change made. What should I do?

---

### Post by jr.gotti on 2007-09-21
Haha sorry if i wasn't clear. First go back and enter a colon. : <---that thing. Then enter "q!" to quit without saving. Then re-enter the vim command.

Okay...fresh unaltered file. Press the "i" (letter i) key. This will put you in insert mode. Navigate with the arrows...and edit like you would with any other program. When everything is back to normal hit the ESC (escape) key. Then enter another colon ":" , and now enter "wq"

All of this is without the quotations of course. And I know vim is complicated. That's why there's gedit. Unfortunately, you cant run that without an xsession. :P

(For clarification, the colon only puts vim in command mode. So after you enter the colon, don't hit enter until you input the command (wq in this case)

---

### Post by yman on 2007-09-21
> **jr.gotti said:**
> When the computers all booted up, hit control alt F2. This will bring you to a console window. Log in like normal, and then enter:

sudo vim ~/.gnome2/session
This will bring you to a text based editor. Edit the file, and then save it.

(To insert text, first press "i"...when your done editing, press escape to get out of insert mode, then press ":" and type in "wq" and hit enter. (This will write the file then quit.)

Then hit Control Alt F7, and restart the Xsession. (Control Alt Backspace)

if he has any graphical environment, why tell him to use vim? it's more complicated, and the goal here is simply to solve a problem.

EDIT: can you read my mind? i wrote this post while you were writing yours.

---

### Post by jr.gotti on 2007-09-21
> **yman said:**
> if he has any graphical environment, why tell him to use vim? it's more complicated, and the goal here is simply to solve a problem.

I was under the assumption that his graphical display is pretty much fubar'd. And besides...it's nice to learn vim. One day he will need it.

---

### Post by liamwithers on 2007-09-21
arggggghhhhhhhhh.. First go back and enter a colon. : <---that thing. Then enter "q!" to quit without saving. did that, then when i went to do it again i accidently put sessions instead of session and now i cant get to it properly, all i get is a load of ~'s

Going to reboot, be back in 5

---

### Post by jr.gotti on 2007-09-21
> arggggghhhhhhhhh.. First go back and enter a colon. : <---that thing. Then enter "q!" to quit without saving. did that, then when i went to do it again i accidently put sessions instead of session and now i cant get to it properly, all i get is a load of ~'s

Going to reboot, be back in 5

This is where I would tell you that the ~'s mean empty lines, and that a reboot is hardly necessary. But I don't think I got you in time. All you had to do was open the correct file :P

>  EDIT: can you read my mind? i wrote this post while you were writing yours.

:wink: be very afraid...

---

### Post by jw5801 on 2007-09-21
I much prefer nano, it's alot simpler! Anyway, Alt+F2, gedit, will open nice regular text editor so you can fix that file up. That's if you're in tty7 (ctrl+alt+F7), which should be your graphical interface.

---

### Post by liamwithers on 2007-09-21
It told me when I done:

Okay...fresh unaltered file. Press the "i" (letter i) key. This will put you in insert mode. Navigate with the arrows...and edit like you would with any other program. When everything is back to normal hit the ESC (escape) key. Then enter another colon ":" , and now enter "wq"

It said the file name then some random numbers and letters then written. Does that mean its worked?

---

### Post by jr.gotti on 2007-09-21
Try it out and you tell me. :P

Now that I think about it...did you alter the original file before you copied it over? If not, you can just recopy it. lol

---

### Post by jr.gotti on 2007-09-21
> **jw5801 said:**
> I much prefer nano, it's alot simpler! Anyway, Alt+F2, gedit, will open nice regular text editor so you can fix that file up. That's if you're in tty7 (ctrl+alt+F7), which should be your graphical interface.

I have no idea why, but I can't stand nano. For no reason...I just can't. lol

---

### Post by liamwithers on 2007-09-21
Ermm I'm confused, I edited the file for the Enlightenment if thats what you're talking about. How do I test it? Log out and back in? Reboot?

Will reboot anyway just to check.

Please post back though lol because I'm really struggling here, I'm 13 years old lol so I am not too good compared to all the Linux Experts :D

---

### Post by liamwithers on 2007-09-21
Wahoooooo! Got my toolbar back. Thanks a bundle Jr.Gotti :D you've helped loads, can I add you to my friends list?

---

### Post by jr.gotti on 2007-09-21
> **liamwithers said:**
> Wahoooooo! Got my toolbar back. Thanks a bundle Jr.Gotti :D you've helped loads, can I add you to my friends list?

Glad I could help =] and feel free!

---

