---
title: "Right-Click with a Macbook"
date: 2008-09-16
forum: Apple Hardware Users
---

### Post by Deadpool on 2008-09-16
I'm having an issue with Ubuntu. I cannot double-click, as ctrl+click is not working properly. I cannot figure out how to set the keyboard to the correct settings, can anyone give me a step-by-step guide?

---

### Post by liquidfunk on 2008-09-16
Have a look here: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by hajk on 2008-09-16
Right- and middle mouse-clicks can be simulated on Apple keyboards and touchpads with various combinations of keys and taps. This can present a problem in some drawing applications (like XFig) where you would need an extra hand to terminate a line... What's needed here is a set of single-key right- and middle mouse-click emulations. These might also come in handy in other situations, as they free up a hand (useful when holding a coffee mug) and prevent accidental clicks when merely doing a two-finger scroll on a touchpad.

It is a simple matter to assign right- and middle mouse-clicks to a some little-used keys, like the right-Alt and right-Command keys on any recent Apple keyboard. It doesn't matter much which keyboard you have specified in your Ubuntu setup, I usually pick the PC104 spec for my Apple Aluminum wireless US keyboard. Now, this is what you should do:

1. Install the "xev" package (if it isn't already installed), then in a terminal give the "xev" command. A little window opens with a small square: put the cursor in that square. Then hit the right-Alt and right-Command keys and watch the output for the keycodes, probably 108 and 134, and write them down. Keycodes do change from time-to-time, though, so check them yourself. Then close the little window by clicking on the X; this terminates xev.

2. Make a little script, like /usr/local/bin/keyboard (you need root privileges for that),```

#!/bin/sh
xmodmap -e "keycode 108 = Pointer_Button3"
xmodmap -e "keycode 134 = Pointer_Button2"
xkbset m
```where you should substitute the keycodes on your keyboard if different from mine. Make this script executable with the command```

sudo chmod a+x /usr/local/bin/keyboard
```

3. Make sure that the "xkbset" package is installed, then find where your keyboard settings can be modified and enable control of the mouse with the keyboard, so that the "xkbset m" command in the script will work.

4. Finally, as user give the command "keyboard", and now those two keys should work as right- and middle mouse-clicks. If this works, then add the command "/usr/local/bin/keyboard" to the startup applications.

N.B. I'm a little vague on where these system settings for keyboard and startup programs are located. That's intentional, as their location has changed several times over the past years. You should look for System settings, or some such...

NN.BB. Usually I add a few more key assignments to the above script, like putting the §/± and `/~ key assignments right```

xmodmap -e "keycode 94 = section plusminus"
xmodmap -e "keycode 49 = grave asciitilde"
```Check these keycodes with xev as above. 

These key-assignments don't interfere with the system settings for the keyboard layout. For example, you can still in the layout specify the left-Alt key as the Compose key (for making accented letters on a US-keyboard); and the left-Command key (usually called left-Windows key...) as Third-level chooser to produce a EuroSign. 

Have fun with your new key assignments!

---

### Post by cyberdork33 on 2008-09-16
good post hajk, I think I will post this one in the FAQ.

---

### Post by niglet101 on 2008-09-16
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by hajk on 2008-09-17
Glad to be of help. 

BTW, the reason I prefer using keys for clicking instead of tapping the touchpad with one or more fingers is a very practical one: just trying to move the cursor (with one finger) or doing a two-finger scroll was forever giving me mouse clicks instead (and driving me mad in the process). I guess I'm heavy-handed when I get absorbed in work... The only touchpad nicety that I allow myself is one-finger vertical scrolling along the right edge of the touchpad.

---

### Post by ulukapata on 2008-09-17
this will explain to you


[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by tp42 on 2009-01-09
Thanks hajk for this helpful post :-)
I tried it on Ubuntu 8.10, Macbook Pro Core2Duo with the your script for the right mouse click and it works. Except of one "not found" message I receive starting the script "keyboard" manually:

> ~$ keyboard
/usr/local/bin/keyboard: 3: xkbset: not found

Although it does work soemthing seems to be not working as supposed?
Perhaps you might have a look at it?
Best regards, 
tp42

---

### Post by hajk on 2009-01-09
You need the "xkbset" package installed for that. This is (was) mentioned in item 3 a bit as an afterthought, I've now given this requirement a bit more prominence. Thanks for the feedback.

---

### Post by bgturk on 2009-04-21
I mapped my right Apple key for right clicking by running the command 

xmodmap -e "keycode 134 = Pointer_Button3" & xkbset m

works for me. 

However, adding this command to System->Preferences->Startup Applications produces no effect. Is something overwriting the effect of this command at log on, or am I doing something wrong?

---

### Post by hajk on 2009-04-21
The & is a separator for two commands, while you can only give a single command in Startup Programs. So, gather those two commands in a script, make it executable, then call that script in Startup Programs.

---

### Post by Alterax on 2009-04-21
Personally, I'm still a fan of using the mac-style CONTROL + Click to get a right-click.  If that is what you would like to do, then here is how to go about it:

Hit ALT-F2 and give this command:  
```
gksudo gedit /etc/default/mouseemu
```
It'll prompt you for a password.

Now just set it up like this:

```

#MID_CLICK="-middle 0 68"         # F10 with no modifier
MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 87"        # F11 with no modifier
RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

```

And once you save, log out, and log back in, control-click will handle your right-click issues.

---

### Post by bgturk on 2009-04-21
Thanks. 
I find it strange that concatenating commands with "&" does not work. 

Rather than writing a shell it is simply possible to create a file ~/.xmodmap with the following content:

> keycode 134 = Pointer_Button3


Then log out and log in, and answer yes to the prompt weather to load the file .xmodmap, and your right apple key will function as a right click.

---

### Post by bgturk on 2009-04-21
> **Alterax said:**
> 
```

#MID_CLICK="-middle 0 68"         # F10 with no modifier
MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 87"        # F11 with no modifier
RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

```

And once you save, log out, and log back in, control-click will handle your right-click issues.

I tried this 
```

#MID_CLICK="-middle 0 87"         # F11 with no modifier
#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 88"        # F12 with no modifier
RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

```
logged out and in, and control-click still doesn't work. Maybe I need to restart?

---

### Post by hyperboloid on 2009-04-21
> **bgturk said:**
> Thanks. 
I find it strange that concatenating commands with "&" does not work. 

Rather than writing a shell it is simply possible to create a file ~/.xmodmap with the following content:



Then log out and log in, and answer yes to the prompt weather to load the file .xmodmap, and your right apple key will function as a right click.

Well, that is confusing!  What the heck is the purpose of the added command "xkbset m" in the original post, then?

---

### Post by cyberdork33 on 2009-04-21
> **Alterax said:**
> Personally, I'm still a fan of using the mac-style CONTROL + Click to get a right-click.  If that is what you would like to do, then here is how to go about it:

Hit ALT-F2 and give this command:  
```
gksudo gedit /etc/default/mouseemu
```It'll prompt you for a password.

Now just set it up like this:

```

#MID_CLICK="-middle 0 68"         # F10 with no modifier
MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 87"        # F11 with no modifier
RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

```And once you save, log out, and log back in, control-click will handle your right-click issues.
That is good to know since several people ask about setting this functionality up. However, it is too bad that it is mouseemu that you need to accomplish things as most Mactel uninstall this because of other conflicts with keyboard keys.

---

### Post by hajk on 2009-04-22
Yes, I know that Ctrl-Click is the default in Mac OS X for getting a right mouse click, but I don't like the fact that it either requires both hands to execute, or a level of dexterity (sinistrality) that gets more difficult the longer I forget to do my finger exercises.:) The method in the OP can be done with one finger.

---

### Post by ruimoura on 2009-04-22
Hi, i've installed Ubuntu 9.04 on my Macbook (3.1) and everything is working just fine (i've followed this - [https://help.ubuntu.com/community/MacBook3-1/Jaunty](https://help.ubuntu.com/community/MacBook3-1/Jaunty)).

The thing is, i'm having a problem with the trackpad. It's not about the second mouse click, or anything, it's about the movement, that is very, very irregular. Sometimes when i drag my finger on the trackpad the speed is ok, and then just stops, and then continues to move very slow, and so on ... 

Any tip on this?

Thanks.

---

### Post by ruimoura on 2009-04-23
Anyone?

:(

---

### Post by sms0611 on 2009-04-23
> **Alterax said:**
> Personally, I'm still a fan of using the mac-style CONTROL + Click to get a right-click.  If that is what you would like to do, then here is how to go about it:

Hit ALT-F2 and give this command:  
```
gksudo gedit /etc/default/mouseemu
```
It'll prompt you for a password.

Now just set it up like this:

```

#MID_CLICK="-middle 0 68"         # F10 with no modifier
MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 87"        # F11 with no modifier
RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

```

And once you save, log out, and log back in, control-click will handle your right-click issues.


This looks really usefull, how would I change it to use the right ctrl key (coz I´m left handed)? Would It be possible to set up to use either ctrl keys?

---

### Post by !@!@! on 2009-06-18
My apologies for the slight grave dig, but I just must say thank you! I don't even own a MacBook and this helped me tremendously. My right click (and left click, but I tap the touchpad) is quite loud (especially when you can't wake people up at night ;)) so I needed an alternative way of right clicking. This worked just fine on my Sony VAIO.

---

### Post by adam1234 on 2009-11-25
Hi all - this is my first post on this forum.

I just recently dual-booted Ubuntu 9.10 with OS X on my MacBook, and I have also been struggling with the right-click issue. 

My laptop is the newer model, with the aluminum unibody (rather than white polycarbonate). This means that my laptop has the newer Touchpad (no buttons, click by pressing anywhere on pad).

Anyway,  I tried a few of the suggestions posted online for how to right-click, but none seemed to work.

That aside, I discovered two different ways to right-click on a MacBook without using any keyboard keys.

Method 1:
If you PRESS the pad with one finger while the other finger is RESTING elsewhere on the pad, you can get a result similar to pressing-and-holding a right mouse button. Unfortunately it is very difficult to navigate to an entry of the right-click menu, since you need to slide your RESTING finger along the pad while keeping your other finger PRESSED in order to keep the menu open.

Method 2:
By simultaneously PRESSING the Touchpad with two fingers, you can get an identical result to a single right-click. I emphasize PRESS, because you actually need two simultaneous "clicks". It took a while to get used to, but now I can't get over how simple it is. Better still, this method has simplified my right-clicking in OS X (no more using "control")! This technique should work with all of the aluminum unibody Mac laptops, but I can't say whether it can be somehow extended to the older generation of laptops.

This post might be very obvious to some of you, but I hadn't found any mention of these methods on any forums. I hope some people will find it helpful.

Adam

---

### Post by dennis123123 on 2009-11-25
You shouldn't need to PRESS anywhere on the touchpad, tap to click works fine.

Running:
$ synclient TapButton1=1
$ synclient TapButton2=3
$ synclient TapButton3=2

Should enable left click with 1 finger tap, right click with 2 fingers, and middle click with 3 fingers.

There is a section in the macbook wiki for the 5,5 pro model touchpad, I suggest giving that a read also.

---

### Post by DnDer on 2010-03-16
> **Alterax said:**
> Personally, I'm still a fan of using the mac-style CONTROL + Click to get a right-click.  If that is what you would like to do, then here is how to go about it:

Hit ALT-F2 and give this command:  
```
gksudo gedit /etc/default/mouseemu
```
It'll prompt you for a password.

Now just set it up like this:

```

#MID_CLICK="-middle 0 68"         # F10 with no modifier
MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 87"        # F11 with no modifier
RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

```

And once you save, log out, and log back in, control-click will handle your right-click issues.

I can now do things like CTRL-C and CTRL-V to copy cut and paste. But I don't get a right-click menu in Firefox, for example, when I attempt to Ctrl+click an image to get the "save image as dialogue."

(I'm on a gen 5, early 08 macbook.)

What have I done wrong or forgotten to do?

---

### Post by damagu on 2010-06-12
I have a Macbook Pro 3,1 and installed Ubuntu 10.04. I tried using your instructions to switch the command and ctrl keys around. I put this in a script:
------------
#!/bin/sh
xmodmap -e "keycode 133 = Control_L"
xmodmap -e "keycode 37 = Super_L"
------------

Even though xev now shows that hitting the command key gives Control_L and hitting the left control key gives Super_L, I still can't copy and paste unless I use the left ctrl key. 

I don't get it. Any help would be appreciated.

---

### Post by hajk on 2010-06-13
You may have to wade through the Gnome settings with 'gconf-editor' for clues.

---

### Post by frafu on 2010-06-13
Hi,

An alternative might be the Simulated secondary click of the accessibility tab of the Mouse control panel. 

The version that currently ships with lucid requires at-spi to run; but running at-spi produces a few bugs, among others, freezes of the desktop because of its incompatibility with gksu.

The good news is that since version 2.31.3 mousetweaks does not require anymore at-spi, that makes its usage more sensible for people that do not want to manually change configuration files of the system. 

To issue a right click, the user only has to push and hold the left mouse button until the pointer has completely changed colour. After releasing the left mouse button, the right click gets automatically issued. 

But as the synthetic right click is preceeded immediately by the real left click, it does not work as expected under some situations: for example, when trying to do a synthetic right click on the link on a web page, the left click preceeding the synthetic right click opens the new page before the synthetic right click opens the contextual menu. 

However, in all the situations were a left click just before the right click does not change the context, the simulated secondary click might be an interesting way to perform a right click. 

Version 2.31.3 of mousetweaks is available in my PPA for lucid (ppa:frafu/ppa); but as the PPA does not produce packages for the Mac (as far as I know) here is the URL with the source tarball:
[http://download.gnome.org/sources/mousetweaks/2.31/](http://download.gnome.org/sources/mousetweaks/2.31/)


Cheers

---

### Post by linuxopjemac on 2010-06-14
This might help
[http://mac.linux.be/content/tuning-ubuntu-macintosh-key-mapping-and-3-mouse-button-emulation-0](http://mac.linux.be/content/tuning-ubuntu-macintosh-key-mapping-and-3-mouse-button-emulation-0)

---

