---
title: "Custom buttons"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by detroit/zero on 2007-04-12
Hi,

This is sort of a programming/scripting/command line question all in one. I think.

I'm a noob to all this, and there's some actions I take regularly that I'd like to automate.

The first one is simple. I know how to make a button for a panel and make it execute a command, but I can't figure out the command itself. I play Yahoo Pool a few times a week, and when I go to the games area I change my screen resolution to 1024x768 (from 1600x1200) in System>Preferences>Screen Resolution, and slow down my mouse pointer motion from System>Preferences>Mouse. Can I make a single panel button that will toggle the two states?

The second is a similar issue: I have a DSL internet connection. Rather than leaving it active 24/7, I disable my ethernet card at night before bed via System>Administration>Networking interface and reactivate it when next I use the computer. Can I make a "toggle switch" for that  as well?

I realize it may be more of an advanced question that might require more thought than most people want to put into it, but it can't hurt to ask. Even if all you care to do is point me towards some reference material or manuals I'd appreciate it.

Thanks...

---

### Post by FuriousLettuce on 2007-04-12
I don't know about the resolution question, but to disable the ethernet card do
```

sudo ifconfig eth0 down

```
and to reenable it
```

sudo ifconfig eth0 up

```

If you want, you could make an alias for this (google bash alias) so that all you would have to type is 'net-up' or 'net-down' (or whatever you want to call the command).

---

### Post by detroit/zero on 2007-04-12
Thanks for the quick reply. 

I should have been clearer on that one. I did know about the eth0 up/down command, but what's getting me is making a button that toggles, rather than typing it out in command line.  I'm thinking that for both problems, whatever button I create will have to point to a small script or something with an IF/THEN of the device state - IF eth0 is on, THEN turn it off; IF the screen resolution/mouse speed is this THEN change it to the other preset state.

I don't know if it's that easy or I'm a victim of wishful thinking. Is this something that can be done from a command line? Or, am I going to have to give myself a crash-course in Python or something similar to accomplish this?

Any thoughts?

---

### Post by rsambuca on 2007-04-12
It's not a toggle, but you could just make a button for on, and a button for off.

---

### Post by detroit/zero on 2007-04-12
right. i realize that. but that would be the easy way out.

---

### Post by FuriousLettuce on 2007-04-13
Youi'd have to write a bash script which checks the status of eth0 (whether it's up or down) and toggles the status accordingly. Whilst you were at it, you'd probably want to add ifconfig to /etc/sudoers using the visudo command, so that you weren't asked for your password each time - if you're not sure how to use visudo, simply google it

---

### Post by detroit/zero on 2007-04-13
thanks for the tip.. i'll let you know how it goes and post my findings.

---

### Post by FuriousLettuce on 2007-04-13
MAJOR EDIT: Much easier to simply right click on the network-manager icon on your panel and untick 'enable networking'. lol, you don't need all the stuff below.

Hey! The way to do it is this:

Open a terminal and type 
```
nano .netstatus.sh
```
This will open nano with a file called '.netstatus.sh' in your home directory (the initial full stop designates the file as hidden so you don't see the script every time you open your home directory). Paste the following into the terminal (either ctrl+shift+v or right click -> paste)
```
#!/bin/bash

if [ "$(ifconfig | grep -c eth0)" != 0 ]; then
        sudo ifconfig eth0 down
else
        sudo ifconfig eth0 up
fi
```
To save the file, press ctrl and x together, type y then press enter. Next, we have to make the file executable. In the terminal, type
```
chmod +x ./.netstatus.sh
``` 

To test it, type
```
sudo ifconfig eth0 down
```
This will set your interface to go down - either attempt to access the internet, or simply type ifconfig - if you can't access the net / ifconfig lists no entry for eth0 then the interface is down. Next, to test the script itself, type
```
./.netstatus.sh
```
Do the same as before (check the net / ifconfig), but this time you should be able to access the net / ifconfig will list an entry for eth0.

Now that we know it works, we want to be able to run the command without needing our password. In the terminal, type
```
sudo visudo
```
This will open up /etc/sudoers for editing. Add the following line at the bottom
```
username ALL=NOPASSWD: /sbin/ifconfig
```
where username is your username. Once again, save the file by pressing ctrl and x together, typing y and then pressing enter. This means that you no longer have to enter a password if you enter sudo ifconfig.

Finally, we want to turn it into a button, so right click on the panel at the top of the screen (on a blank bit - the panel is the thing that has the applications, places menus etc on it), and choose 'Add to Panel'. Choose 'Custom Application Launcher' at the top of the box. Next, change the drop-down menu from 'Application' to 'Application in Terminal'. The name can be anything - I just called it 'toggle eth0'. In the command bit, put
```
/home/username/.netstatus.sh
```
where username is your username. The comment can be anything - I put 'Toggle the eth0 interface up or down'. Click OK, and you should have a new icon on your panel. Push it, and the net should go down, push it again, and it should come back up!

Shout me if you need any help / there are any problems.

---

### Post by rsambuca on 2007-04-13
Nice job!

---

### Post by detroit/zero on 2007-04-13
No kidding! Awe inspiring, to say the least.

I went step by step and it works like a charm. Once complete, I gave it the netspeed_applet icon and now there's a little ethernet card sitting on my panel to toggle the connection on or off.

While I was actually hoping for just a couple pointers so I could learn the basic technique for myself, I'm not quite finished yet. I know the screen resolution and mouse speeds can be changed from command line as well, so I'm going to do some research and try to adapt the script to change those settings.

Good job! Thanks again!

---

### Post by lacerda_sch on 2007-06-17
Hey there!

Wish I would have seen this howto earlier, would have saved me 2 hours of work. I have just written a script to toggle resolutions and screen backlight (this makes sense if I'm connected to the projector). Is there a smart way to detect current screen resolution? That would make it even more beautiful. :)

The script:

> 
#!/bin/bash

grep -q 0 /usr/local/bin/moviemode-current

if [ $? = 0 ]; then 
	xrandr -s 1
	sudo radeontool light off	
	echo 1 > /usr/local/bin/moviemode-current
else
	xrandr -s 0
	sudo radeontool light on
	echo 0 > /usr/local/bin/moviemode-current
fi

an excerpt from the sudoers file (radeontool needs sudo rights):

> %users ALL = NOPASSWD: /usr/sbin/radeontool


---

