---
title: "turn off tapping on mouse"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by tronnix75 on 2007-10-09
i have ibm t40p laptop and i need to turn off the annoying tapping option, i went into the mouse settings nothing in there?

---

### Post by tronnix75 on 2007-10-09
your telling me no one can anser this

---

### Post by strabes on 2007-10-09
Please [search the forums](http://ubuntuforums.org/search.php?searchid=28534099) before asking a question. This question has been asked many times before. You need to edit your /etc/X11/xorg.conf:```
gksudo gedit /etc/X11/xorg.conf
```Find the section that looks like this:> Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"SHMConfig"	"true"
Endsection
Add the following line on a new line before "Endsection"```
	Option		"MaxTapTime"	"0"
```Save the file and restart your X server using CTRL+ALT+BACKSPACE.

---

### Post by tronnix75 on 2007-10-09
i went to that and added the line it did not work also the line ption "SHMConfig" "true" was not there should i add this..  i want to turn off the tapping completly on the mouse pad that is on my laptop so i dont accidently tap something i dont need to, i want to use the buttons.:)

---

### Post by K5KS on 2007-10-09
Glad this came up...was going to look for this tonight.  I did try this but it failed to Turn Off the Tapping feature.  Here is what the edit looks like.

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"150"

should this turn off the tapping feature?

---

### Post by st33med on 2007-10-09
> **tronnix75 said:**
> i went to that and added the line it did not work also the line ption "SHMConfig" "true" was not there should i add this..  i want to turn off the tapping completly on the mouse pad that is on my laptop so i dont accidently tap something i dont need to, i want to use the buttons.:)

Yes, you should. Also, if you don't want the touchpad to be active while typing follow the bottom link:
[http://ubuntuforums.org/showthread.php?t=271052&highlight=syndaemon]("http://ubuntuforums.org/showthread.php?t=271052&highlight=syndaemon")

---

### Post by tronnix75 on 2007-10-09
so your saying it does not work?:confused:

---

### Post by st33med on 2007-10-09
Assuming that you mean that it will not sense anything, no. That HOWTO will disable the touchpad from running while you are typing, so it does not highlight, move the cursor, etc. while typing.

I am assuming that bumping into the touchpad while typing is annoying you, correct?

---

### Post by Lord Illidan on 2007-10-09
Gutsy has a GUI option to disable the touchpad. It worked for me on this Sony VAIO VGN-FE41E. Perhaps you'd like to upgrade to Gutsy (It's soon going to be released anyway). Could have something to do with Xorg 7.3, not sure.

---

### Post by jordanmthomas on 2007-10-09
```
Section "InputDevice"
    Identifier		"Mouse3"
    Driver		"synaptics"

        Option      "Device"                "/dev/psaux"
    Option      "Protocol"              "auto-dev"
    Option      "LeftEdge"              "120"
    Option      "RightEdge"             "830"
    Option      "TopEdge"               "120"
    Option      "BottomEdge"            "560"  # comment out this entire line to disable horizontal scroll/click ability
    Option      "FingerLow"             "14"
    Option      "FingerHigh"            "15"
    Option      "EmulateMidButtonTime"  "70"
    Option      "VertScrollDelta"       "20"
    Option      "HorizScrollDelta"      "0"
    Option      "MaxTapTime"            "0"    # 0 disables tap-to-click, set it to 100 to re-enable
    Option      "MinSpeed"              "0.3"
    Option      "MaxSpeed"              "0.75"
    Option      "AccelFactor"           "0.015"
    Option      "EdgeMotionMinSpeed"    "200"
    Option      "EdgeMotionMaxSpeed"    "200"
    Option      "UpDownScrolling"       "1"
    Option      "LeftRightScrolling"    "0"
    Option      "CircularScrolling"     "0"

#Option		"SendCoreEvents"	"true"
#    Option		"Device"		"/dev/psaux"
#    Option		"Protocol"		"auto-dev"
#    Option		"HorizScrollDelta"	"0"
    Option		"SHMConfig"		"on"
    # For ALPS TouchPads
#    Option		"MaxSpeed"		"0.7"
#    Option		"MinSpeed"		"0.18"
#    Option		"AccelFactor"		"0.08"
#    Option		"TopEdge"		"120"
#    Option		"LeftEdge"		"120"
#    Option		"BottomEdge"		"830"
#    Option		"RightEdge"		"650"
#   Option		"FingerLow"		"25"
#    Option		"FingerHigh"		"30"
    # Do you keep moving the mouse while typing? Try this trick.
    #synclient TouchpadOff=1 disable your synaptics touchpad
    #synclient TouchpadOff=0 enable your synaptics touchpad
EndSection

```
My section for my synaptics touchpad (well it's an alps touchpad, but whatever)
The only way it will click is if I use the buttons.  Scrolling works as expected.
don't worry about shmemconfig being set to true unless you want to turn tapping on / off at will.

---

### Post by tashmooclam on 2007-10-09
Hello Tronix, my touchpad drove me crazy also. It was overly sensitive and made my laptop almost useless.
My first answer is: The new version of Ubuntu (7.1) coming out in several days will have a control under system>preferences. I would upgrade to that if you can stand waiting for it.
OR:
There are two small programs that can be used to adjust the touchpad. 
One is called "gsynaptics" and the other "qsynaptics". After one of these is downloaded, then the other instructions given above are necessary. It was very confusing and I can't recall how I actually was able to do it. I went to a borders bookstore and found instructions in an expensive book "ubuntu hacks" and some folks here helped me also. A very annoying experience.
OR: Belkin tiny optical mouse, $14. Give it away after installing 7.1

---

### Post by tronnix75 on 2007-10-09
> **st33med said:**
> Yes, you should. Also, if you don't want the touchpad to be active while typing follow the bottom link:
[http://ubuntuforums.org/showthread.php?t=271052&highlight=syndaemon]("http://ubuntuforums.org/showthread.php?t=271052&highlight=syndaemon")

I tried this and now i cant load into the X server, i deleted the synaptic touchpad entry and restarted now all i get is a command line please help:(

---

### Post by Lord Illidan on 2007-10-09
I would have upgraded if I were you. Ironically, with Gutsy, you would have at least made it to failsafe.

Try this command :  sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by tronnix75 on 2007-10-09
> **tashmooclam said:**
> Hello Tronix, my touchpad drove me crazy also. It was overly sensitive and made my laptop almost useless.
My first answer is: The new version of Ubuntu (7.1) coming out in several days will have a control under system>preferences. I would upgrade to that if you can stand waiting for it.
OR:
There are two small programs that can be used to adjust the touchpad. 
One is called "gsynaptics" and the other "qsynaptics". After one of these is downloaded, then the other instructions given above are necessary. It was very confusing and I can't recall how I actually was able to do it. I went to a borders bookstore and found instructions in an expensive book "ubuntu hacks" and some folks here helped me also. A very annoying experience.
OR: Belkin tiny optical mouse, $14. Give it away after installing 7.1

i need help Getting the GUI back cna you help:(

---

### Post by Ripfox on 2007-10-09
Did sudo dpkg-reconfigure -phigh xserver-xorg do it?

I swear there is a GUI tool that works right away with 7.04, I installed it on my GFs lappy...for the touchpad problem anyways.

---

### Post by tronnix75 on 2007-10-09
> **ripfox said:**
> Did sudo dpkg-reconfigure -phigh xserver-xorg do it?

I swear there is a GUI tool that works right away with 7.04, I installed it on my GFs lappy...for the touchpad problem anyways.

how do i upgrade to the latest?

---

### Post by st33med on 2007-10-09
Did you back up the files as it said? If you did, do:
```
sudo cp /etc/X11/xorg.conf_synbackup /etc/X11/xorg.conf 
```
on your computer.

---

### Post by tronnix75 on 2007-10-09
> **st33med said:**
> Did you back up the files as it said? If you did, do:
```
sudo cp /etc/X11/xorg.conf_synbackup /etc/X11/xorg.conf 
```
on your computer.

i did not run that command

---

### Post by st33med on 2007-10-09
Also, those spaces are tabs in xorg.conf, don't hit the space bar.

---

### Post by st33med on 2007-10-09
:( This is going to be hard...

Could you please type up the Xorg exactly as it is here? You just have to type up that synaptics Input Device, that is all.

---

### Post by tronnix75 on 2007-10-09
> **st33med said:**
> :( This is going to be hard...

Could you please type up the Xorg exactly as it is here? You just have to type up that synaptics Input Device, that is all.

when i try and type back in the "synaptics mousepad" back in it says error, this is the command i do at the prompt remember i am in the CLI not the GUI i can not get into the GUI.

i login as me and password, then i type in vi /etc/X11/xorg.conf and i go to the where i need to put in the synaptics entry and it will not let me it says error how do i put this back in?:confused:

---

### Post by Lord Illidan on 2007-10-10
Just type in this command. It will give you a new /etc/X11/xorg.conf
sudo dpkg-reconfigure -phigh xserver-xorg

Then, you can go back to the GUI, and upgrade from there.

---

### Post by tronnix75 on 2007-10-10
I did this command, restarted and then the resolution comes up smaller, i selected VESA and then the highest resolution but it is like 480x360 i think how can i fix this?:(

---

### Post by GhostHunter on 2007-11-12
i have the same problem with tapping, and i tried what u suggested, and it wont let me save the changes or over wright the whole file with an edited one, it says i dont have permission even tho i am in an admin account, wont let me log into root at logon screen, hope u can help me with this!  thanks

---

### Post by jordanmthomas on 2007-11-12
To edit the file, type this in a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```

BEFORE YOU DO THIS, do this 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
to make a backup in case you screw up.

I would suggest looking into gsynaptics instead of my method, however, as it's simpler.

Also, you seem a little confused about the concept (or lack thereof) of the root account in Ubuntu, so I'm going to give you a link that I think you should read:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by GhostHunter on 2007-11-12
thanks you so much for your help, everything went perfectly!
love this forum, such a fast reply, thanks community!

---

