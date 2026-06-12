---
title: "Joypad Help?  Joy2Key?"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Oracle of Wuffing on 2006-07-24
I have a rather generic 8-button joypad connected to my computer via a joypad/USB adaptor, and it looks like the Device Manager says that everything's okay with that... But I'd like to map my joypad buttons to keyboard input (think:  Flash games that are designed for keyboard controls only).  I found that there's a Linux version of [Joy2Key]("http://interreality.org/~tetron/technology/joy2key/") through Google, but I'm guessing I'm executing the installations for that incorrectly- 'make' just gives me a "command not found" error in Terminal.

So, um, could someone either point me to a better solution/the right way to install this, or point me to the way to get the information I need to give you in order to help me on this, please?

---

### Post by OU812 on 2006-07-24
Please read this. I hope it helps.

[http://www.ubuntuforums.org/showthread.php?t=171822](http://www.ubuntuforums.org/showthread.php?t=171822)

john

---

### Post by Oracle of Wuffing on 2006-07-24
Thanks, that would explain why the command wasn't found. ;) 

However, as tends to happen, I have another problem now... The ./configure went fine.

```
oracleofwuffing@WuffyTank:~/joy2key-1.6.1$ make
 cd . && /bin/sh /home/oracleofwuffing/joy2key-1.6.1/missing --run automake-1.8 --gnu  Makefile
make  all-am
make[1]: Entering directory `/home/oracleofwuffing/joy2key-1.6.1'
 cd . && /bin/sh /home/oracleofwuffing/joy2key-1.6.1/missing --run automake-1.8 --gnu  Makefile
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT joy2key.o -MD -MP -MF ".deps/joy2key.Tpo" -c -o joy2key.o joy2key.c; \
        then mv -f ".deps/joy2key.Tpo" ".deps/joy2key.Po"; else rm -f ".deps/joy2key.Tpo"; exit 1; fi
joy2key.c:90:22: error: X11/Xlib.h: No such file or directory
joy2key.c:91:23: error: X11/Xutil.h: No such file or directory
joy2key.c:92:24: error: X11/keysym.h: No such file or directory
joy2key.c:119: error: syntax error before ‘*’ token
joy2key.c:119: warning: data definition has no type or storage class
joy2key.c:122: error: syntax error before ‘RegisterCloseEvent’
joy2key.c:122: error: syntax error before ‘*’ token
joy2key.c:122: warning: data definition has no type or storage class
joy2key.c:123: error: syntax error before ‘*’ token
joy2key.c: In function ‘process_args’:
joy2key.c:639: warning: assignment makes pointer from integer without a cast
joy2key.c: In function ‘argtokey’:
joy2key.c:734: error: ‘NoSymbol’ undeclared (first use in this function)
joy2key.c:734: error: (Each undeclared identifier is reported only once
joy2key.c:734: error: for each function it appears in.)
joy2key.c: In function ‘sendkey’:
joy2key.c:774: error: syntax error before ‘event’
joy2key.c:785: error: ‘event’ undeclared (first use in this function)
joy2key.c:786: error: ‘KeyPress’ undeclared (first use in this function)
joy2key.c:790: error: ‘True’ undeclared (first use in this function)
joy2key.c:791: error: ‘CurrentTime’ undeclared (first use in this function)
joy2key.c:795: error: ‘KeyRelease’ undeclared (first use in this function)
joy2key.c:796: error: ‘KeyPressMask’ undeclared (first use in this function)
joy2key.c:796: error: ‘KeyReleaseMask’ undeclared (first use in this function)
joy2key.c:798: error: ‘False’ undeclared (first use in this function)
joy2key.c: At top level:
joy2key.c:837: error: syntax error before ‘RegisterCloseEvent’
joy2key.c:837: error: syntax error before ‘*’ token
joy2key.c: In function ‘RegisterCloseEvent’:
joy2key.c:840: error: ‘Window’ undeclared (first use in this function)
joy2key.c:840: error: syntax error before ‘root_return’
joy2key.c:842: error: ‘children_return’ undeclared (first use in this function)
joy2key.c:845: error: ‘disp’ undeclared (first use in this function)
joy2key.c:845: error: ‘win’ undeclared (first use in this function)
joy2key.c:845: error: ‘root_return’ undeclared (first use in this function)
joy2key.c:845: error: ‘parent_return’ undeclared (first use in this function)
joy2key.c:848: error: ‘SubstructureNotifyMask’ undeclared (first use in this function)
joy2key.c: At top level:
joy2key.c:857: error: syntax error before ‘*’ token
joy2key.c: In function ‘CheckIfWindowClosed’:
joy2key.c:861: error: ‘XEvent’ undeclared (first use in this function)
joy2key.c:861: error: syntax error before ‘event’
joy2key.c:864: error: ‘disp’ undeclared (first use in this function)
joy2key.c:864: error: ‘parentwin’ undeclared (first use in this function)
joy2key.c:864: error: ‘SubstructureNotifyMask’ undeclared (first use in this function)
joy2key.c:864: error: ‘event’ undeclared (first use in this function)
joy2key.c:865: error: ‘True’ undeclared (first use in this function)
joy2key.c:866: error: ‘DestroyNotify’ undeclared (first use in this function)
joy2key.c:867: error: ‘win’ undeclared (first use in this function)
make[1]: *** [joy2key.o] Error 1
make[1]: Leaving directory `/home/oracleofwuffing/joy2key-1.6.1'
make: *** [all] Error 2
oracleofwuffing@WuffyTank:~/joy2key-1.6.1$
```

Um... I understand that I need some certain files that I evidently don't have, and I'm guessing that that just screws up the rest of everything from then on.

---

### Post by pcgc1xn on 2006-10-17
Most of the message you have got is just it complaining that you are missing a couple of files:
X11/Xlib.h: No such file or directory
X11/Xutil.h: No such file or directory
X11/keysym.h: No such file or directory

Now where do you get these things?

I found a note (here: [http://packages.ubuntu.com/edgy/x11/joy2key](http://packages.ubuntu.com/edgy/x11/joy2key)
) that says you need these:
debhelper (>= 4.0.0), autotools-dev, libx11-dev, libxt-dev
I installed these things using the GUI tool (can't remember the name at the moment, sorry)

In other cases I have found that googling the filename sometimes tells you what package it is in lets you get one step further before finding the new one needs another package...  Though remember that often all of the files will be in one package - so don't kill yourself looking for one, solve any one, and the others may go away.

Is there a good way to find out what you need?  Probably but I don't know it.

Now because I am actually really good at this, I predict that your next question will be:
"I have installed it, but it complains about not finding /dev/js0"

Ubuntu does not put your joystick there, it is in /dev/input/js0
There is a command line option which lets you specify which device you want to look at - it is pretty clear in the readme.

Do yourself a favour though and check the name of the device I told you, it shows up in the control panel, joystick tester thingie.  You see, I was trying to get this to work until 2am last night, so I am not really on top form at the moment, and anythign I write may or may not be correct.:D 

I will add my next question to the thread.

Having installed and run the program, it sees the joystick and responds, but no other programs do.
What I am trying to do is set the buttons so I can use them to control the music player.  If I set 'Z' to skip to the next track, and I hit 'Z' on the keyboard, it works.  So then I set the buttons on the joystick to 'Z' using joy2key.  When I hit the buttons, I get 'Z's in the terminal I ran it in, but nothing else seems to see them - not amarok, not even if I give focus to Kate I would expect to see 'Z's get entered into my text document.  Nothing, except 'Z's in the terminal.  I get this whether I use the -X, -terminal or -other one (2am remember) options.

I guess that if the joysticks are in a spot where joy2key doesn't normally look for them, the keyboard might be as well.  I know that I can specify the device number for the keyboard, but I don't know what it is.

Any help would be appreciated, thanks

---

### Post by dk5151 on 2006-12-02
I"m having the issue that you predicted, joy2key looking for /dev/js0, but I can't find the command in the readme to fix it.

---

### Post by pcgc1xn on 2006-12-04
Sorry, can't help you, I never ended up getting it to do what I wanted (control Amarok), because I found there was an addin in Amarok to do juat that.

I had a look through the readme & can't find it either.

I found the answer either in the files contained in the package or google - try the homepage or maybe man.  The truth is out there, and I am no genius at this stuff, so others should be able to find it too.

Good luck.

---

### Post by dk5151 on 2006-12-05
Thank you, my quest will continue. I'm using qjoypad for the time being and it's doing the trick.

---

### Post by christhemonkey on 2006-12-05
If its complaining about not being able to find /dev/js0 when its at /dev/input/js0 then you can just make symlink to it.

```
sudo ln -s /dev/input/js0 /dev/js0 
```

---

### Post by rune_kg on 2007-01-13
joy2key -dev /dev/input/js0

Does the trick

Rune Kaagaard
[http://runelyd.dk](http://runelyd.dk)

---

