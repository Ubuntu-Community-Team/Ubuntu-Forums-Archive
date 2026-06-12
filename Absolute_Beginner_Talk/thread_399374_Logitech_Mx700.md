---
title: "Logitech Mx700"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-04-02
Hello every one.

I have been searching for a way to get my Logitech Mx700 Mouse to work properly. By work properly I mean have the two side buttons work.

I found a few posts on the subject, one went into pretty decent detail and I thought I followed them well but when I restarted my computer I got an error asking if I wanted to check this or that. I had no clue what it was but after clicking yes a couple of times I got to a Black screen I could type on.

[Didnt get this one right.]("http://ubuntuforums.org/showthread.php?t=65471&highlight=mx700")

But I found a few setting people have that they say work for them, maybe some one can tell me wich one is better?

and maybe step by step how to implement it?

The first one was


Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

The second is 

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Dev Name" "Logitech USB Receiver"
    Option         "Dev Phys" "0000:00:02.0-1/input0"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "10"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7 "
    Option         "Resolution" "800"
EndSection 

Thanks for any information on this topic. For some reason ( completely uneducated guess) the second one here looks like what I want. just wish I knew how to load it in.

Last time I tried to follow directions I screwed up badly some were and had to reinstall Ubuntu :confused:

---

### Post by Sabar on 2007-04-02
can I do this?

Applications > Accessories > Terminal

Then Paste in;

cat /proc/bus/input/devices

After that Paste in;

sudo gedit /etc/X11/xorg.conf

enter password

Find inside the new window that opens;

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Highlight > right click > cut

Then go to my above post highlight the second configuration 

Right Click > Copy

Go back to xorg.conf (/etc/X11) - gedit 

paste in were the old one was.

> Click save at top of xorg.conf (/etc/X11) - gedit screen,  then restart.  This just worked for me!

How do I save it? Just click the save button on the top? Should my Mouse start magically working now? Is there something else I need to do?

Does anybody think this will work? Like I said last thing I tried I screwed something up BAD

Thanks guys.
Sabar

---

### Post by gjtoth on 2007-04-02
> **Sabar said:**
> can I do this?

Applications > Accessories > Terminal

Then Paste in;

cat /proc/bus/input/devices

After that Paste in;

sudo gedit /etc/X11/xorg.conf

enter password

Find inside the new window that opens;

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Highlight > right click > cut

Then go to my above post highlight the second configuration 

Right Click > Copy

Go back to xorg.conf (/etc/X11) - gedit 

paste in were the old one was.

How do I save it? Just click the save button on the top? Should my Mouse start magically working now? Is there something else I need to do?

Does anybody think this will work? Like I said last thing I tried I screwed something up BAD

Thanks guys.
Sabar

The only thing that I had to edit was the xorg.conf file.  BTW, the second set of instructions in your first post is the one that works for me.  You'll need to reboot for it to take effect.

---

### Post by Sabar on 2007-04-02
YES!!

My Mx700 mouse is now working!! Well at least the two side buttons for forward and back are working.

Thank you very much for the response!

For anybody who reads this post at a later date, all I did was what I listed in my second post.

Clicked on save at the top of the screen then restarted my computer.

GOOD LUCK!!
Sabar

---

### Post by lucaspr on 2007-04-02
Just a little contribution (and a hidden question).. :)

For X to restart: Just press CTRL-ALT-BACKSPACE.  Works for the NVIDIA/ATI-drivers, don't know for sure.....

---

### Post by Stoffer on 2007-04-19
This worked great for me in terms of forward and back buttons, but my up & down fast scroll buttons still don't work.

---

### Post by w3stfa11 on 2007-04-19
I remember MX700 working (the two side buttons) on 6.10, but it doesn't seem to work out of the box on 7.04. :(

---

### Post by rekon on 2007-05-29
Awesome. Thanks Sabar, your second configuration worked like charm after I edited the "Dev Phys" option to my own needs. Only thing that I have problems with is my UP scroll button, but I never use it much anyways because I typically read websites top to bottom :p. 

Thank you to all the members that contribute to this website!

---

### Post by Bondrake on 2007-07-08
Just FYI, with my MX700 the following worked perfectly on a fresh install of 7.04 (just change the Identifier line to whatever you have listed in your ServerLayout section, by default "CorePointer"):

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option      "Protocol" "ExplorerPS/2"
    Option      "Device" "/dev/psaux
    Option      "ZAxisMapping"  "4 5"
    Option	"ButtonMapping" "1 2 3 6 7 "
    Option	"Resolution" "800"
    Option      "Buttons" "7"
EndSection

---

### Post by PhenixRising on 2007-07-25
> **Bondrake said:**
> Just FYI, with my MX700 the following worked perfectly on a fresh install of 7.04 (just change the Identifier line to whatever you have listed in your ServerLayout section, by default "CorePointer"):

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option      "Protocol" "ExplorerPS/2"
    Option      "Device" "/dev/psaux
    Option      "ZAxisMapping"  "4 5"
    Option	"ButtonMapping" "1 2 3 6 7 "
    Option	"Resolution" "800"
    Option      "Buttons" "7"
EndSection

Thanks so much for that post Bondrake and Sabar thank you for the easy step by step.  I've only had Ubuntu for a day and I'm new to it and lost.  You both really helped me.  Thanks!

---

### Post by phrogman on 2007-07-28
I'm going to have to second PhenixRising on this one.  Thanks Sabar and Bondrake!  I've just started trying out Ubuntu and the learning curve is pretty steep.  The frustration of not having my convenient and second nature forward and back buttons was kiling me!

---

### Post by fiatguy85 on 2007-07-29
Both of these solutions seem to work fine, except for the up scroll button also functioning as a back button simultaneously.  Has anyone figured out how to fix this?

---

### Post by fiatguy85 on 2007-07-29
> **fiatguy85 said:**
> Both of these solutions seem to work fine, except for the up scroll button also functioning as a back button simultaneously.  Has anyone figured out how to fix this?

Figured out my own solution.  Used this guide:  [http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894) with modifications to the button numbers, and now each button does one function.

---

### Post by Sabar on 2007-07-29
A while ago I tried to install my MX700 mouse a different way that I found.  What can I say, Curiosity killed the cat. But what ended up happening was me crashing my system and not being able to get it working again. fortunately it was on a new install of feisty, due to me crashing on an earlier oops 

One thing of many many I have yet to figure out how to do is make a back up of feisty. I don't feel to bad about this, considering I never knew how to do it on windows either. 

But I was reading the link that fiatguy85 has here and I came to this;

> 3. Editing the xorg.conf file

First, let's back it up in case you mess anything up:

Code:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak


I want to learn how to back up feisty and I am guessing if I post sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak into the terminal it would do just this, BUT could some one out there please explain this process a little better? 

Like my first question is where is this back up being saved to? to what extent is my system being backed up? everything on this particular partition? ok so I crash it and I see the screen that comes up saying there is no warrenty on UBUNTU then how do I reload this back up? how do I get to it? as far as I can see there is now way to work on it from a live CD. 

Does anybody see what I cam talking about? this is why a beginner like me went and wrote this original post. because I  know what it is like to start out here, because I am starting out yet.

One thing for people to keep in mind when writing guides for UBUNTU, as great as they are, please remember there are allot of us that are trying this out for the very first time everyday, please assume we Know NOTHING! one of the first things I was trying to get help with said to go to the terminal ..... at the time my thought was ahh what's a terminal? 

anyway glad this post helped a few people. and if I got off topic here was my question of the day

> Like my first question is where is this back up being saved to? to what extent is my system being backed up? everything on this particular partition? ok so I crash it and I see the screen that comes up saying there is no warrenty on UBUNTU then how do I reload this back up? how do I get to it? as far as I can see there is now way to work on it from a live CD. 

---

### Post by fiatguy85 on 2007-07-29
> **Sabar said:**
> Like my first question is where is this back up being saved to? to what extent is my system being backed up? everything on this particular partition? ok so I crash it and I see the screen that comes up saying there is no warrenty on UBUNTU then how do I reload this back up? how do I get to it? as far as I can see there is now way to work on it from a live CD.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Sorry if I oversimplify but here is what this line is doing:
sudo - carry out command as root user
cp - copy file
first path - file to copy
second path - file destination

This is simply making a copy of your xorg.conf file.  This file is the configuration file for the xserver, which controls the basics of how the graphical user interface of the linux system functions.  It is important to always back this up, in case you make a change that will not work in the file, because then you will be unable to load the graphical interface.  If this occurs, you can boot the kernel with [Recovery Mode] at the end of it to get a command line and simply copy the improperly functioning xorg file, should you want to keep it, and restore the backup (so it is a good idea to have this next part written down).  This would go something like this:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-logi
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

Which is actually in that guide further down.  mv functions much the same as cp, except that it is a cut-paste instead of a copy paste.  It is good practice to back up important configuration files in this manner before changing them, especially when they may render your system unusable.  Many people include this as a step in their guides.  

As for completely backing up Ubuntu onto a liveCD, I would imagine there is a way.  I know there are guides for customizing LiveCDs, but I am not sure how system specific they can get.  I haven't really looked in to this topic too much I don't guess.  Hope this was somewhat helpful.

---

### Post by PhenixRising on 2007-07-31
[QUOTE=fiatguy85;3101183]```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Sorry if I oversimplify but here is what this line is doing:
sudo - carry out command as root user
cp - copy file
first path - file to copy
second path - file destination

This is simply making a copy of your xorg.conf file.  This file is the configuration file for the xserver, which controls the basics of how the graphical user interface of the linux system functions.  It is important to always back this up, in case you make a change that will not work in the file, because then you will be unable to load the graphical interface.  If this occurs, you can boot the kernel with [Recovery Mode] at the end of it to get a command line and simply copy the improperly functioning xorg file, should you want to keep it, and restore the backup (so it is a good idea to have this next part written down).  This would go something like this:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-logi
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```[QUOTE]

You are awesome!  I made a mistake while fixing the ATI bug(?) and had to reinstall ubuntu.  After that reinstall I backed up the xorg.confg immediately and started to install my mouse then some updates.  I had to restart the comp for the mouse functions to take effect BUT I made another mistake and would have had to re-install Ubuntu if it wasn't for Sabar's question and your answer.  Thanks!

---

### Post by rpalmertree on 2007-08-05
*UPDATE* Its fixed. :), and I am a moron, its what I get for trying half a dozen things to get it working and not clean each thing up after it didn't work. I had a script still running on login that was overriding the config in the xorg file, so all is well.  Also thanks for the thread it has helped out alot!

*****FIXED*****
Ok, So i've followed this guide and when I edited my xorg.conf file it didn't crash xserver when it rebooted (woohoo!)

But i'm still have the same problem as before, my back forward buttons are causing the page to scroll up and down, but when looking at the output of xev it shows the thumb buttons are regestered as 4 & 5.

When I click the middle mouse button and scroll up it shows button 6.

So I guess my question is at this point do any of you have any ideas how to get the back forward working?

Here is my xorg file.

Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "Protocol" "ExplorerPS/2"
        Option "Dev Name" "Logitech USB Receiver"
        Option "Dev Phys" "0000:00:02.0-6/input0"
        Option "Device" "/dev/input/mice"
        Option "Buttons" "10"
        Option "ZAxisMapping" "4 5"
        Option "ButtonMapping" "1 2 3 6 7 "
        Option "Resolution" "800"
EndSection

I think the thumb buttons are behaving differently because the scroll acts almost like a page up/down, where the thumb buttons act like a single arrow hit.

thanks for any help.
************FIXED***************

---

### Post by mych on 2007-08-30
I notice there's a number of people having problems with this mx700 so I just though I'd post to say I had used the second method described in Sabar's post and all buttons work fine; forward, backward, scrollwheel, middleclick aswell as the scroll up and down buttons.

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "Protocol" "ExplorerPS/2"
Option "Dev Name" "Logitech USB Receiver"
Option "Dev Phys" "0000:00:02.0-1/input0"
Option "Device" "/dev/input/mice"
Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7 "
Option "Resolution" "800"
EndSection

---

### Post by Sabar on 2007-12-23
Just tried this in gutsy and it seemed to work. woo hoo

---

