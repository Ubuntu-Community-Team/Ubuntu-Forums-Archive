---
title: "mouse delayed"
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by gase07 on 2005-06-14
i am a complete newbie who has never written a command line in my life so i don't know where to begin.  i just installed ubuntu and everything seems to have gone well with the installation except for the mouse.  i've noticed that many others have had problems with their serial mouses but mine is a ps-2.  the system (other then the mouse) seems to work well enough and the computer responds well to my keyboard commands.

i'm under the impression that my problems have something to do with xorg.conf but wouldn't know what to look for or how to fix it. also, how do i log in as the root user?

thanks for the help

---

### Post by Alexander Kirillov on 2005-06-14
[QUOTE=gase07]i am a complete newbie who has never written a command line in my life so i don't know where to begin.  i just installed ubuntu and everything seems to have gone well with the installation except for the mouse.  i've noticed that many others have had problems with their serial mouses but mine is a ps-2.  the system (other then the mouse) seems to work well enough and the computer responds well to my keyboard commands.

i'm under the impression that my problems have something to do with xorg.conf but wouldn't know what to look for or how to fix it. also, how do i log in as the root user?

thanks for the help[/QUOTE]
 

To login as root, select "Root terminal" in system tols menu. If it asks for apssword, enter your password. To get teh menu (if your mouse is not working), use Alt-F1. 

the first thing you should try is 
dpkg-reconfigure xserver-xorg
(from root terminal). This will run teh same detection/cofiguration routine it did at install time - you may try to change something now.

---

### Post by gase07 on 2005-06-15
i ran dpkg-reconfigure xserver-xorg but ended up making more of a mess then i started out with. i just reinstalled ubuntu hoping that the mouse problem would correct itself but it's right back to where i started. the mouse works, just not well. it responds very slowly to my hand motions.

i'm going to try dpkg-reconfigure xserver-xorg again but any other suggestions would be appreciated.

also, i dont' understand how the root password gets set up? i don't recall every choosing it but somehow managed to sign in as the root user. how do i set that up now?

---

### Post by gase07 on 2005-06-15
i just ran dpkg-reconfigure xserver-xorg several times more but nothing seems to have helped. now i have an even bigger problem on my hands. x will not load. i have a good idea of how to fix it (at least through dpkg-reconfigure xserver-xorg) but i can't log in to my root user.

earlier i was able to log in to the root through the root terminal using the same password as my user profile (not root). now that x wil not load i don't know what to enter for my root username and password. nothing works.

i seem to be missing some important piece of information regarding this root login. i've looked around but i must be looking in all the wrong places.

your help would be much appreciated as i am getting increasingly frustrated by the whole thing.

---

### Post by poofyhairguy on 2005-06-16
[QUOTE=gase07]i just ran dpkg-reconfigure xserver-xorg several times more but nothing seems to have helped. now i have an even bigger problem on my hands. x will not load. i have a good idea of how to fix it (at least through dpkg-reconfigure xserver-xorg) but i can't log in to my root user.

earlier i was able to log in to the root through the root terminal using the same password as my user profile (not root). now that x wil not load i don't know what to enter for my root username and password. nothing works.

i seem to be missing some important piece of information regarding this root login. i've looked around but i must be looking in all the wrong places.
[/QUOTE]

Try this:

sudo -s

---

### Post by gase07 on 2005-06-16
that helped out a lot. thanks. i was able to log in to my root and everything is back to how it was before - mouse problems.

i've tried to run dpkg -reconfigure xserver-xorg a few times now but nothing has helped. before i move on i have to ask

1. do i have to reboot the computer before changes i make will take effect?

in regard to the mouse or display problem

2. what should i do to go about fixing it? 

if you need to know my configuration, i'd be happy to share it but you'd have to let me know how to get it. thanks

---

### Post by wylfing on 2005-06-16
This is not particularly a problem I'm good at solving, but I'll try to help. You do not have to reboot for changes to take effect from things like dpkg-reconfigure. However, running that isn't going to solve your mouse responsiveness problems. Here's what I suggest:

1. Do you have the option of ditching PS/2 altogether and getting a USB mouse? USB mice can be had for extremely low amounts of money, so unless you are hooked on your PS/2 mouse this might be a quick fix.

2. What -- exactly -- is the mouse you're trying to use. Is it a screwy no-name mouse? Are you using an adapter?

3. Post the relevant section from your xorg.conf file. It's usually the 2nd "Input Device" section. You should be able to tell which is the one for mouse.

---

### Post by gase07 on 2005-06-16
i would really prefer to keep the mouse i have. no there are no adapters. my mouse is a 

IntelliMouse 1.1A PS/2 Compatible

it's a microsoft mouse with two buttons and a scroll wheel

this is my configuration

Section "InputDevice"
        Identifier         "Configured Mouse"
        Driver              "mouse"
        Option             "CorePointer"
        Option             "Device"                       "/dev/input/mice"
        Option             "Protocol"                    "ImPS/2"
        Option             "Emulate3Buttons"      "true"
        Option             "2AxisMapping"            "4 5"
End Section

hope this helps; if anyone feels that they should see my video settings or anything else, let me know. thanks for the help.

---

### Post by wylfing on 2005-06-17
That looks right. The ImPS/2 driver is specifically for the Intellimouse, so this to me says it's the mouse hardware that's got a problem. I'm betting your mouse has a few miles on it. Does it work fine in another OS?

You could try changing ImPS/2 to just PS/2 and see what happens. You'll have to restart X, which you can do by pressing Ctrl-Alt-Backspace.

---

### Post by gase07 on 2005-06-17
the mouse and computer are a few years old but the windows operating system i have running on another partition works just fine with the mouse.

tweaking my xorg file sounds like it's worth a shot but i can't make changes in the gui editor and i can't figure out how to open and edit files in the root terminal window. if you could fill me in on how to do that or point me in the right direction for information, i'd appreciate it.

by the way, the driver windows uses for my mouse i think is msmouse.vxd if that helps.

---

### Post by jrobcet on 2005-06-17
This is not correct:```
Option             "2AxisMapping"            "4 5"
```It should be:```
Option             "ZAxisMapping"            "4 5"
```Or perhaps it is just a typo??

---

### Post by gase07 on 2005-06-17
yeah, sorry, just a typo. 

so how would i go about changing ImPS/2 to just PS/2?

thanks

---

### Post by Alexander Kirillov on 2005-06-18
[QUOTE=gase07]yeah, sorry, just a typo. 

so how would i go about changing ImPS/2 to just PS/2?

thanks[/QUOTE]
 1. make backup of the file: 
 cp xorg.conf xorg.conf.backup
2. In terminal window, open the file in nano editor:
 nano xorg.conf

The editor is pretty much self-explanatory (poissible commands are listed at the bottom of the screen; ^ stands for Ctrl, so exit is Ctrl-x)

---

### Post by gase07 on 2005-06-18
thanks for the help, i was able to change the configuration but nothing seemed to help. changed ImPS/2 to PS/2 and it was just the same. then to Microsoft and the computer didn't like that so i changed it back. then, out of curiousity i changed /dev/input/mice to ttyS0 and the computer really hated that, so i changed it back. so i'm back to where i started, with the mouse responding very slowly to my movements, but have certainly learned a lot along the way.

1.  if i make a copy of a file before changing it, do i revert back to the orgional file by typing, for example  "cp xorg.conf.backup xorg.conf".

2.  can you think of, or help me to locate, the names of other drivers that i could try in place of "ImPS/2".

any other thoughts or suggestions would be appreciated, thanks.

---

### Post by gase07 on 2005-06-21
i've tried a variety of settings in the xorg.conf file. i tried anything from changing the identifier to "Mouse1" and "Mouse0", to changing the location of my input device (both "/dev/input/mice" and "/dev/psaux" have the same problem), to changing the protocol from ImPS/2 to ExplorerPS/2 and PS/2 and Intellimouse, and i tried messing with the ZAxisMapping and Emulate3Buttons options.

all this and i still have a mouse that works (all the buttons work fine) but the pointer responds very slowly to my hand movements. the computer, other then the mouse, seems to work fine. i can navigate with the keyboard and the keyboard responds immediately to my actions.

so now what? could there be something wrong with my video settings or some other settings? or is this definately a mouse problem? how do i fix it? can i fix it? please help  ](*,)

---

### Post by wylfing on 2005-06-23
Messing with lines other than the one containing imPS/2 aren't going to help. Have you tried simply increasing the motion speed of the cursor? Go to the main menu > System > Preferences > Mouse. Click the Motion tab. Slide the acceleration and sensitivity over to the right and see if things improve.

---

### Post by Alexander Kirillov on 2005-06-24
[QUOTE=gase07]i've tried a variety of settings in the xorg.conf file. i tried anything from changing the identifier to "Mouse1" and "Mouse0", to changing the location of my input device (both "/dev/input/mice" and "/dev/psaux" have the same problem), to changing the protocol from ImPS/2 to ExplorerPS/2 and PS/2 and Intellimouse, and i tried messing with the ZAxisMapping and Emulate3Buttons options.

all this and i still have a mouse that works (all the buttons work fine) but the pointer responds very slowly to my hand movements. the computer, other then the mouse, seems to work fine. i can navigate with the keyboard and the keyboard responds immediately to my actions.

so now what? could there be something wrong with my video settings or some other settings? or is this definately a mouse problem? how do i fix it? can i fix it? please help  ](*,)[/QUOTE]
 I hate to sya that, but if nothign helps, your easiest way out may be just buying a new mouse. It is not all that expensive, and given that your existing mouse is several years old, it may make sense...

---

