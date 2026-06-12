---
title: "Mouse Buttons"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Hypoxiacion on 2007-03-12
Hello Everyone,

I migrated from windows some time ago and loving ubuntu! I have just one problem i just can't seem to find a solution for, what i'am after is to find a way to bind one of my side buttons on my Logitech mx1000 to a key, like so when I press the side button I want it to simulate pressing a certain key on the keyboard. The reason for this is for my games, I like to use the side button for quick weapon switching. 

I could quite easily bind a button in setpoint on windows but have looked long and hard to find a way to do this in linux, I have read all the tutorials based on setting up the mx1000 but they all seem to tell you howto setup the extra buttons for firefox.

I have posted these screenshots to give you an idea of what im trying to achieve.

I hope somebody has a solution because this really would make my ubuntu setup complete!

Many Thanks

[[IMG]http://img61.imageshack.us/img61/5810/setpointci9.th.jpg[/IMG]](http://img61.imageshack.us/my.php?image=setpointci9.jpg)

[[IMG]http://img261.imageshack.us/img261/788/utkg7.th.jpg[/IMG]](http://img261.imageshack.us/my.php?image=utkg7.jpg)

---

### Post by leethaksor on 2007-03-15
Hi,

I have the exact same problem, only I would like to go a bit further. I would like to have different button configurations depending on what application is in focus and receiving the button event. So I would have global settings which would be used always except when the foreground application has its own specific configuration.

Microsoft Intellimouse Explorer drivers have this functionality and this is one of the reasons why I haven't yet completely made the switch to Linux.

In windoze I have defined the small thumb button to be the "close" event so I can close all windows and applications by pressing it. Then in firefox for example I defined that button to be "ctrl-w" keystroke to only close the current tab. This is what I would like to accomplish in ubuntu too.

I have always preferred Microsoft mouses over Logitech because of their softer touch. The buttons are lighter to press and don't click loudly. 

Cheers

---

### Post by gurgle on 2007-03-20
I would like to know how to do this as well. Having one of the buttons be a "close" button would be great. I would love to do this for games as well. 

Thanks.

---

### Post by Smuve on 2007-03-20
I think I might be able to help you guys out.  I have Logitech G5 and I use this method to assign the tilt scroll wheel to 'Forward' and 'Back.'  Try it, once you do, you won't be able to live without it. 

I have this labeled as the short version because it tells me exactly what I need to do quickly with little or no explanation.  However, it should be pretty easy to follow.  I've added a few comments to help out a little where necessary.

This will give you control over your mouse buttons.  How creative you get with it us up to you.

All credit should be given to: [http://aarongyes.com/guides/mx1000](http://aarongyes.com/guides/mx1000)
This is where I extracted and adapted my personal guide from.  If you would like a more detailed explanation, please click the link.

INSTALL EVDEV
```
sudo aptitude install xserver-xorg-input-evdev
```

GATHER REQUIRED INFO
```
cat /proc/bus/input/devices
```
Confirm name = Logitech USB Gaming Mouse  
My G5 is called "Logitech USB Gaming Mouse."  Find out exactly what yours is called and write it down, you'll need it later.
From now on, wherever my instructions say Logitech USB Gaming Mouse, insert the name of your mouse from this step.

FIND EVENT #
```
ls /dev/input/
```
Make sure event9 is not taken for the next step

SET EVENT RULE
```
gksudo gedit /etc/udev/rules.d/19-local.rules
```
Paste copied line into file
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Gaming Mouse", NAME="input/event9"
```
Save

ADD NEW MOUSE SECTION TO XORG
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```

Find mouse section and replace with:

```
Section 	"InputDevice" 
	Identifier 	"Logitech USB Gaming Mouse"
	Driver 	"evdev" 
	Option 	"Device" 				"/dev/input/event9"
EndSection
```

Enter this in the ServerLayout section:

	```
InputDevice "Logitech USB Gaming Mouse" 	"CorePointer"
```

Save and Reboot (need to reboot for udev rule to take effect)

CONFIGURE MOUSE
```
sudo aptitude install xvkbd
sudo aptitude install xbindkeys
xev

gedit ~/.xbindkeysrc
```

Use xev to figure out what each of your mouse buttons are assigned to.

For my G5:
# Optional:
# Logitech USB Gaming Mouse
# b:1 left click
# b:2 scroll wheel click
# b:3 right click
# b:4 scroll wheel up
# b:5 scroll wheel down
# b:6 scroll wheel tilt right
# b:7 scroll wheel tilt left
# b:8 thumb button

To assign my scroll wheel to Forward and Back, I enter the following lines:
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]"" 
m:0x0 + b:6 
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]"" 
m:0x0 + b:7
```
***Right and Left at the end of the lines above should both have the first letter capitalized.  Apparently this is a common bug in the forums.  Thanks to jfcervera for pointing that out.

Save

Start xbindkeys
```
xbindkeys
```

Test in Nautilus or web browser.

ADD TO STARTUP (if everything is working)
System > Preferences > Sessions >TAB Startup Programs
Add 
```
xbindkeys
```

---

### Post by gurgle on 2007-03-20
^^ thanks for the help. It would be nice to have a GUI for this, all of these steps seem too long for the average person.

---

### Post by Smuve on 2007-03-20
You should see the long version.

---

### Post by jfcervera on 2007-04-07
Thanks Smuve,

Very useful post, I noticed though that Left and Right should have the first letter in  upper case. I'm sure you wrote it like that, but it seems that any letter after a bracket gets shown in lower case in the forum .... weird

---

### Post by Smuve on 2007-04-07
@jfcervera:  You are correct thanks for pointing that out.  I just added a note to the post.  Even when I go to edit, the post shows capital letters.

---

### Post by wataboutbob on 2007-04-11
Thanks Smuve for this neat post. 

The scroll wheel tilt buttons worked perfectly. But I'm wondering if you know how I can set the thumb button (b:eight) as middle-click.... I use that for auto-scrolling and also as a way to close tabs in firefox.

EDIT:

Interesting... I use to be able to click the left and right button together to spin the beryl cube. Now thats missing. I can still do it with the built-in touchpad buttons, but not through the G5.

---

### Post by wataboutbob on 2007-04-11
okay... using xmodmap, I've managed to reassign button 8 as middle click (button 2)... for the current session alone.

Can someone advice me how I can get this to be run/assigned everytime I restart the computer.

EDIT: RESOLVED!

Finally! Followed Smuve's easy advice on enabling and setting up the scroll-wheel tilt keys for forward and back under Firefox and Nautilus. After that, mapped the thumb key as middle-click. Added xmodmap to startup sessions. Simple when I think about it.... my Ubuntu installation is complete. :D

---

### Post by Smuve on 2007-04-11
Yes, I've been using the forward and back emulation for a while now.  I recently added Ctrl+W to my thumb button per post #2 in this thread.  Now my G5 is even more efficient.  I love it!

Too bad the G5 doesn't have a task switcher button.  That would be money to set as Ctrl+Alt+Right.  The desktop cube would spin like a merry-go-round on crack with beryl!

---

### Post by StargateGamingGeek on 2007-04-28
This is all well and good but what if you want the tilt wheel on the G5 to function as side-scrolling, with b:8 (the thumb button) as back? I never use forward and this would be more useful.

---

