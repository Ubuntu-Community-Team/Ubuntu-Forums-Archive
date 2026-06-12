---
title: "Mapping Mouse Buttons"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Literati on 2008-03-13
Hi everyone. I'm trying to fix my mouse using BTNX, but I can't seem to install the darn thing! :D

I'm using this guide:
[http://www.ollisalonen.com/btnx/man/btnx-manual.html#steps](http://www.ollisalonen.com/btnx/man/btnx-manual.html#steps)

I'm currently at "Installing BTNX" (AKA, the very first step :P) 
I've gotten to number four, and this is EXACTLY what my terminal looks like:

matt@Matt:~$ sudo modprobe uinput
matt@Matt:~$ cd /home/matt/Other/btnx-0.4.7
matt@Matt:~/Other/btnx-0.4.7$ make
make: *** No targets specified and no makefile found.  Stop.

So, instead I searched around, and found that I need to run ./configure. So I did, and now I only end up with this error :D

matt@Matt:~/Other/btnx-0.4.7$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables

Does anyone have any idea what's happened? (Also, if you could explain the error, so I don't make it again in the future, I would greatly appreciate it :))

---

### Post by Literati on 2008-03-13
Bump
Please :)

---

### Post by dokdoom on 2008-03-13
Can you explain what problems you are trying to fix on your mouse? Or are you just trying to get the side buttons to work as it would in windows (Just an example.)

---

### Post by Literati on 2008-03-13
> **dokdoom said:**
> Can you explain what problems you are trying to fix on your mouse? Or are you just trying to get the side buttons to work as it would in windows (Just an example.)

I'm trying to get the LEFT HotKey (Thumbbutton) to act as a BACK button. :)

---

### Post by dokdoom on 2008-03-13
I thought so, I remember trying to do this a long time ago. I'm not sure which exact make and model of Mouse you are trying to use but I'll tell you how I set mine up.

Google the exact make of mouse you are using and then xorg.conf. Your google should look like:

mouse_name_type xorg.conf 

You shouldn't need to install anything to get it to work but I can't say for sure. Good luck!

---

### Post by Literati on 2008-03-13
> **dokdoom said:**
> I thought so, I remember trying to do this a long time ago. I'm not sure which exact make and model of Mouse you are trying to use but I'll tell you how I set mine up.

Google the exact make of mouse you are using and then xorg.conf. Your google should look like:

mouse_name_type xorg.conf 

You shouldn't need to install anything to get it to work but I can't say for sure. Good luck!

Is there any way to see what number corresponds to what function on the mouse?

---

### Post by Literati on 2008-03-13
> **Literati said:**
> Is there any way to see what number corresponds to what function on the mouse?

Oh, and I've tried xev, but it just shows up at a blank box with a black outlined square in it :(

So, I'm a big loser and just figured out how XEV works.

I've figured out the numbers of the buttons, but how do I tell it that I want it to act as a back button instead of whatever it does now.

Okay, more specifics:

The button I want to become the BACK button, is mapped as being the same as the Center click button (Scroll Click) or BUTTON 2.
Now what?

---

### Post by Literati on 2008-03-13
Anyone? I'd like to get these buttons working :(

---

### Post by jerrynewt on 2008-03-13
Here is my xorg.conf file that I reconfigured to get the forward and back buttons in firefox to work. Try and see if it works for you.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "Buttons"               "9"
        Option          "ButtonMapping"         "1 2 3 6 7 8 9"

---

