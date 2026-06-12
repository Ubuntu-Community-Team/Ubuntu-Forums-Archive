---
title: "Can't install on G5"
date: 2007-06-01
forum: Apple PPC Users
---

### Post by stylecramper on 2007-06-01
I have a dual 1.8 GHz G5 and bought the Ubuntu 7.04 Alternate CD. I can boot from the CD and get past the black logo screen with progress bar. After that, an error appears: "Failed to start the X server", and I'm shown a text screen that asks if I want to view some output. Whether I choose Yes or No, after that an error message  comes up that says "bcm43xx_microcode5.fw not available or load failed" and this message repeats indefinitely while I am unable to do anything.

The G5 has an ATI Radeon 9600 added to it, but otherwise nothing unusual. Any suggestions would be welcome.

---

### Post by stmiller on 2007-06-01
Hmm. Very weird. The alternative CD does not boot into X; it's a text based installer.  Make sure at the yaboot prompt you are specifying the 64bit install. G5 machines need a 64bit kernel. Press tab at the yaboot menu to see all options. I think you want

install-powerpc64

or something similar to that. Try that boot option, if you haven't already and let me know if that works. I have an identical machine (dual 2Ghz Radeon 9600 AGP) and installed okay with the alternative CD here.

---

### Post by stylecramper on 2007-06-02
> **stmiller said:**
> Hmm. Very weird. The alternative CD does not boot into X; it's a text based installer.  Make sure at the yaboot prompt you are specifying the 64bit install. G5 machines need a 64bit kernel. Press tab at the yaboot menu to see all options. I think you want

install-powerpc64

or something similar to that. 

Good suggestion, thanks. Hitting tab shows the following options:

live
live-powerpc64
live-nosplash
live-nosplash-powerpc64
check
check-powerpc64
driverupdates
driverupdates-powerpc64

Now I'm starting to think they've sent me the wrong disc. The envelope says "Ubuntu 7.04 Alernate CD PPC" but the label on the cd says "Ubuntu 7.04 PPC - Desktop CD".

Just for fun, I tried booting with live-powerpc64 but ended up with exactly the same errors as above.

---

### Post by Auria on 2007-06-02
Seems like you've got the liveCD, not the alternate CD

> Just for fun, I tried booting with live-powerpc64 but ended up with exactly the same errors as above.

Most likely because tis is what it does by default ;)

---

### Post by JD Walsh on 2007-08-29
I think I know this one...

I'm pretty sure you got the Desktop CD, and not the Alternate, but you may still be able to make it work. Just go ahead and boot with it like you have been and let it crash. Then follow the steps I've described below:

First, when it asks if you want to look at the logs, use your arrow keys to highlight

<Cancel>

Then press enter. There's nothing in there that's going to help you. Trust me.

I don't know for sure why your computer is getting hung after you leave those log files, but you should be able to get that to stop by pressing

^C (command-c)

That should end the hung process and you should get some text, ending with a prompt that will look something like

```
ubuntu@ubuntu.com ~$
```

The important part is that dollar sign with (I hope) a blinking underscore. It means that you have control of your machine back, and then you can get around to fixing your problem.

You see, at least one of your problems is the driver for the Radeon card. There is a bug in the 7.04 release where it is trying to read the x86 BIOS on your PPC-based graphics card. There is a very detailed discussion of it at [[SOLVED] xserver wont start after 7.04upgrade PPCG4dual]("http://ubuntuforums.org/showthread.php?t=531002").

Essentially, what you need to do is edit the xorg.conf file. When you get that $ [dollar sign] prompt, type:

```
dpkg-reconfigure -phigh xserver-xorg
nano -w /etc/X11/xorg.conf
```

The second command should open up a window with your X Window configuration file. You can use your arrow keys to scroll down to where it says:

```
Section "Device"
Idenfifier "ATI Technologies, Inc. RV350 AP (Radeon 9600)"

```
or something similar.

Then scroll down to where it says:

```
End Section
```

Make sure you are at the first "End Section" after the Radeon Identifier.

Now, right before where it says "End Section," insert a line that reads:

```
Option "NoInt10" "yes"
```

That will tell it to STOP looking for x86 code! Now, after you have inserted this line, press

^O (command-O)

That SAVES the file! (Don't ask me why...) Then you can exit the editor. (I think that one is command-A, but there should be a list of the key-commands at the bottom of your screen.)

After you have exited the editor, you should be able to start up the desktop by typing

```
startx
```

Once you have things installed, you may have to edit the xorg.conf file on your computer the same way you did above, but after that it should work fine. Let me know...

--JD

---

### Post by JD Walsh on 2007-08-30
Tried out my instructions myself, and I have a few corrections to make:

To break out of that loop after your computer hangs, try pressing

control-option-F1

In order to be able to save your changes to the "xorg.conf" file, you will need to type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo nano -w /etc/X11/xorg.conf
```

Normally when you use "sudo" you need to enter a password, but when running from the live CD you don't. Nonetheless, you still have to use sudo in order to be allowed to save "xorg.conf"

Also, the control key combination to exit the nano editor is

^X (control-x)

Good luck!

--JD

---

