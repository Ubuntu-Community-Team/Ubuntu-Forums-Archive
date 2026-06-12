---
title: "Please help me to find &amp; alter xorg.conf"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by backflip on 2008-02-28
I downloaded gsynaptics so that I could adjust my touchpad, it doesn't scroll. When I tried to run it I was told  'GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics'
I would appreciate a step by step response as I haven't a clue where that file is, or how to amend it as required.
Thanks.

---

### Post by neurostu on 2008-02-28
xorg.conf is a system file that doesn't show up to the regular user. To access it you must be root or have root privledges.

This is really easy, just type sudo

This is how I backup and then edit my xorg.conf
```

sudo cp /etc/X11/xorg.conf /ect/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

```

The first line will copy xorg.conf into xorg.conf.backup then the second line will open it in gedit so you can edit it!

good luck!

---

### Post by backflip on 2008-02-28
Thanks for your quick reply. I managed to open up xorg.conf and I thought all I would need to do was change the value of SHMConfig to 'true,' but in what appears to be the relevant section (mouse) all I  can see is
 Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

What do I do next?
Thanks

---

### Post by docusn on 2008-02-28
I tried this also, and receive this error message "cp: missing destination file operand after `/etc/x11.xorg.conf.backup'
Try `cp --help' for more information."

Any ideas why I can't get to the file to make a backup?

---

### Post by neurostu on 2008-02-28
Do you have the synaptics driver installed? To find out type:
```
 aptitude search synaptics 
```
Ther should be an entry that looks like 
```
 i   xserver-xorg-input-synaptics    - Synaptics TouchPad driver for X.Org ... 
```
that little "i" to the left of the name says that I have it installed. If you have a v or a p then you don't have it installed.

To install it type
```

sudo apt-get install xserver-xorg-input-synaptics

```

Then reboot. If your trackpad isn't working try adding a synaptics section to your xorg.conf.

Here is the section of my xorg.conf that is for the trackpad.  You can just paste it into your xorg.conf after the section for the mouse
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection
```

---

### Post by neurostu on 2008-02-28
What is the exact command you are typing to make a back up?
```

sudo cp source.txt destination.txt

Sudo - Run as root
CP - copy
source.txt - the source file
destination - copy to or create this file

```

To backup your xorg.conf you need to type:
```

sudo cp /ect/X11/xorg.conf /etc/X11/xorg.conf.bkp

```
Actually where you save the 2nd file doesn't really matter, you can name it whatever you want too.  You could type this to backup your xorg.conf
```

sudo cp /etc/X11/xorg.conf /home/<yourUserName>/xorg.RandomName.chickenFace

```

---

### Post by bbqsandwich on 2008-02-28
> **neurostu said:**
> 
This is how I backup and then edit my xorg.conf
```

sudo cp /etc/X11/xorg.conf /ect/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

```


I just wanted to be nitpicky & point out that if you are copying and pasting from this original reply, I think the ETC directory in the first line is misspelled ECT... so it should be

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

No hard feelings I hope; just trying to be helpful :)

---

### Post by docusn on 2008-02-28
Thanks neurostu, that worked. 

New question - the xorg.conf file is empty - at least I get an empty folder opened. Is that the default setup for the xorg.conf file (ie empty) until I put something in it?

---

### Post by docusn on 2008-02-28
> No hard feelings I hope; just trying to be helpful :)

None taken bbqsandwich I can use all the help I can get!

---

### Post by backflip on 2008-02-28
Thanks neurostu,
I checked that I do have the driver installed, then I pasted the entry from your xorg file into mine, rebooted, but no joy. When I go to System/Preference/Touchpad I still get the same message that I need to  set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics.
Cheers.

---

### Post by neurostu on 2008-02-28
docsun: ha ha ha, thanks, I missed that typo.

This may seem trivial, but have you checked, System->Preferences->Mouse, then the touchpad tab?

Also you might want to try to find out who told you to add  SHMConfig true and ask them to let you have a copy of their xorg.conf

---

### Post by backflip on 2008-02-28
I checked out 'mouse' to see if it had any options but there is none.
Having to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics is a system message, I didn't get it from anyone. When I go to System/Preference/Touchpad and click on that a box appears which  tells me gsynaptics can't inialize because I need to set SHMConfig 'true' in xorg.conf or XF86Config.
What is XF86Config, and is it that which needs amending?
Thanks for your help, I much appreciate it.

---

### Post by neurostu on 2008-02-28
You might want to check out this thread. I didn't read much of it but it might have some answers...

[http://ubuntuforums.org/showthread.php?p=975421](http://ubuntuforums.org/showthread.php?p=975421)

---

### Post by backflip on 2008-02-28
I copied the relevant section from one of the posters xorg file in the link you provided, but that didn't work either.
Thanks for you time and assistance. Not being able to scroll with my touchpad is the only thing not working, so it isn't too bad.
Cheers.

---

### Post by backflip on 2008-02-28
When I run 'aptitude search synaptics' I get the following. Do I need anything else there to be active.
james@james-desktop:~$  aptitude search synaptics
i   gsynaptics                      - configuration tool for Synaptics touchpad 
p   ksynaptics                      - Synaptics TouchPad configuration tool for 
p   libsynaptics-dev                - library to access the synaptics touch pad 
p   libsynaptics0                   - library to access the synaptics touch pad 
p   qsynaptics                      - Synaptic TouchPad configuration tool      
p   xfree86-driver-synaptics        - Synaptics TouchPad driver for X.Org/XFree8
v   xorg-driver-synaptics           -                                           
i   xserver-xorg-input-synaptics    - Synaptics TouchPad driver for X.Org server
james@james-desktop:~$

---

### Post by neurostu on 2008-02-28
one thing you might tree is to UNINSTALL gsynaptics and then install xfree86-driver-synaptics

---

### Post by neurostu on 2008-02-28
I tried install gsynaptics and I was getting the same error you were when I tried to run it. However my trackpad was working great before I installed it.

---

### Post by neurostu on 2008-02-28
and when I installed the xFree86 i got scrolling to work

---

### Post by backflip on 2008-02-28
I uninstalled gsynaptics and it took other stuff with it, now I can't login !!
I rebooted and got as far as the Ubuntu symbol and running bar along the bottom, then it suddenly switched to text and asked me my login and password, i did that but it is still in text mode. How do i sort that.
I'm on another computer now to post this.
Thanks

---

### Post by neurostu on 2008-02-28
Oh my... I'm really sorry abou that. Try logging in and see what happens when you type 
startx, also resinstall gsynpatics "sudo apt-get install gsynaptics" then try startx

---

### Post by dstew on 2008-02-28
I think it is unwise to directly edit your xorg.conf unless you know exactly what you are doing. Even a single typo can create an unbootable xserver, which is what you probably have now.

To restore you xserver, from the command line enter```
sudo dpkg-reconfigure xserver-xorg
```Answer the questions the best you can. Choose the resolution you actually use for the maximum. After you are finished, enter **startx** and you should get your desktop back.

What you probably should have done in the past is to reconfigure the xserver after you installed the gsynaptics package. You might have been given a menu choice to enable that function, and the reconfiguration program would have put it into xorg.conf without any errors.

---

### Post by backflip on 2008-02-28
Many thanks, but that is far too complicated for me. I will probably just reinstall from scratch.
:(

---

### Post by backflip on 2008-02-28
I've actually opened another thread specific to the login fault. Thanks

---

### Post by neurostu on 2008-02-28
Did you backup your xorg.conf? If you did try using your backup.
```

sudo cp /<dirofbackup>/xorg.conf.backup /etc/X11/xorg.conf

```

---

