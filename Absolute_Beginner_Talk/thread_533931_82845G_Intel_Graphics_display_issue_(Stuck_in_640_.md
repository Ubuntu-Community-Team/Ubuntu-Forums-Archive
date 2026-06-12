---
title: "82845G Intel Graphics display issue (Stuck in 640 x 480)"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by noiseordinance on 2007-08-24
Hey there. I'm new to Ubuntu. I wanted to get familiar with Linux after being native to PC and Mac my whole life. I was told this is the OS to use for a PC-savy-yet-Linux-newby.

I have an issue that many have reported: the 82845G Intel Graphics display issue. (Not being able to select anything besides 640x480 resolution)

The issue is usually resolved by setting Video memory in BIOS from 1MB to 8MB (which I've done) and then visiting this page: [http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html) and installing the driver.

My problem is that I have no idea how to install stuff on Linux, "sudo" this and "sudo" that... All I know how to do is run executables. I'm really interested in getting this installed so that I can learn what "sudo" even means but I can't even install the program because the bottom half on the install screens are cut off due to my resolution, so all I can do is run the program off the CD with 4" bars around all sides of my 640x480 display.

I'm begging anyone for laymen's help on installing the Intel driver on my laptop. I don't know how to access the terminal, I don't know any UNIX commands and everything I find out there refers to "simply doing this" and "simply doing that" but nothing is simple for me yet since I don't know the first thing about Linux.

Any help would be incredibly awesome. Maybe someone can check out the Intel page and tell me which of the three drivers I should use and maybe how to use / install it?

Thanks so much!

Sean 

(PS - I'm using Ubuntu 7.04, everything seems to work great, PCMCIA wireless card, USB, audio, touchpad, the works!... Oh, and my laptop is a Dell Inspiron 1100)

---

### Post by anewguy on 2007-08-24
When you see command lines, like the things that start with "sudo", you need to be in a terminal window.  To get to that window:

click "Applications", scroll down to "Accessories", then over to  and click on "Terminal".


The commands you see with "sudo" in front are commands that require what is called in LInux super-user privileges.  This super-user has access to more directories and files than a standard user.

When you enter a "sudo" command for the first time in any given terminal session, it will ask for a password - just enter your normal password.:)

As a side note to the programmers out there - please either check the running resolution and adjust your screens accordingly at run time, or make them for the lowest resolution.  Since the introduction of Feisty Fawn, it seems the default screen resolution for even the LiveCD has been reduced, yet all the screens that ask any questions continue to be for higher resolution - hence things are off the screen.  When I installed 7.04 I had to get rid of the top and bottom bars and still could BARELY get to the top of some response buttons.  I know in Windows we could always check the window size at run time and adjust our programs accordingly at run time.

---

### Post by noiseordinance on 2007-08-24
Which of the three drivers should I attempt to use? There's a Mesa driver and 2 others...

Thanks by the way. :)

---

### Post by anewguy on 2007-08-24
Forgot to ask - when you get to the log on screen, hold down ctrl alt and F2 and see if you get a log on message.  If so - is the screen distorted for it as well?

---

### Post by anewguy on 2007-08-24
Let me do some digging on your choices and get back to you.

---

### Post by noiseordinance on 2007-08-24
Thank you so much... I'm at work right now but as soon as I get home, I'll do as you mentioned and let you know if I get any errors...

Thanks!!

---

### Post by anewguy on 2007-08-24
I've been searching through the forums for info and found a few things for you to check:

[http://www.geocities.com/stomljen/]("http://www.geocities.com/stomljen/")

[http://www.bani.com.br/index.php/2007/01/26/hi-i810-modesetting-goodbye-915resolution/]("http://www.bani.com.br/index.php/2007/01/26/hi-i810-modesetting-goodbye-915resolution/")

[http://ubuntuforums.org/showthread.php?t=94452&highlight=845g+graphics]("http://ubuntuforums.org/showthread.php?t=94452&highlight=845g+graphics")  - pay attention to the information on the 3rd page posted by Bodhi.Zazen

[http://timothyli.wordpress.com/2006/10/25/ubuntu-laptop-experience-dell-inspiron-1100/]("http://timothyli.wordpress.com/2006/10/25/ubuntu-laptop-experience-dell-inspiron-1100/")  - this one includes instructions on being able to see the options on the screen when installing.


I'm sure there are a lot more, but I would try the last 2 first as they seem to be exact solutions on your laptop.

Good luck, and post back if you need more help and/or you get it working!:)

---

### Post by noiseordinance on 2007-08-24
Ok, so I got Ubuntu installed per the last link that you provided (holding ALT + Left click to move the window around) and now i'm trying to paste in the new xorg.conf file. I copied the old one to my desktop and when I try to place anything within the /etc/x11/ folder, it says I do not have permission. Any pointers??

Thanks!

---

### Post by anewguy on 2007-08-24
You  have to have "super user" privileges to do that.  If you are merely copying a file with a "cp " statement, just prefix it with "sudo "  i.e.:

sudo cp myxorg.conf /etc/X11/xorg.conf

If you are using an editor, you need to invoke the editor with super user as well:

sudo gedit /etc/X11/xorg.conf

then you should be able to cut/paste/save

Let me know if you have more questions - we'll get you there yet!:)

---

### Post by noiseordinance on 2007-08-24
Sweet! I got it up and running! Looks very nice. Similar to Mac. Seems pretty fast too, much faster than when it was running on CD, lol. It boots about as fast as my tweaked out XP install I had on it prior.

Thank you so much for your help!!

Is it normal to be getting a "Keyring password" prompt every time I reboot?

---

### Post by anewguy on 2007-08-24
Yes, you get the keyring thing because of the wireless network requiring a key - when you first enter it it is stored on a "keyring".  When you come back later it will ask for the keyring password so it can get the wireless password.  Tired of that?  I believe there is something called "PAM" that will manage that for you in such a way that if your log on password and the password to the key ring are the same, it won't ask anymore.  I haven't done this yet (just been too lazy I guess).  If you search this forum or do a yahoo search for "ubuntu keyring pam" I think you'll find that information.

Glad it's working for you!:)

---

### Post by jordanmthomas on 2007-08-24
It's probably not too big of a deal, but you shouldn't use sudo when launching graphical applications because permissions *can* get screwed up.  Instead, you should use **gksudo** when you're launching a program like gedit.  You can read up a little on it here:  [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

You may be getting that prompt because you used sudo instead of gksudo (but don't quote me on that ;)  )

Try this to get rid of your (maybe permissions-fouled keyrings)
```
sudo rm -r ~/.gnome2/keyrings
```

**edit** Oops, it appears it's normal.  :lolflag:
Still, the point about gksudo is something you should look into and be aware of.

---

### Post by anewguy on 2007-08-24
Thanks for the info.  I've never had a problem with sudo.  Of course, I have root access enabled in the gdm conf file and a valid password, so if I ever get stuck, I can get "unstuck" fairly quick.

---

### Post by noiseordinance on 2007-08-24
I was asking me to setup the keyring password (which happens to be admin password) even using the Live CD. When I first installed, it wanted me to set a keyring password and ever since, every time I reboot, I get this:

[B]Enter password for default keyring to unlock

The application 'nm-applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked[/B]

Once I enter the password, I don't get prompted for it again until reboot, but I haven't done much more than surf the net and run the update program... (Of which I installed all updates...)

Does that help at all?

---

### Post by jordanmthomas on 2007-08-24
According to anewguy it's because it wants to protect the key for your wireless connection.  Any time it needs to read the key and it hasn't been authorized for a while it will ask to make sure it's cool with you to use the key.
(I just use MAC address filters and leave it open, seeing as I'm a lazy man)

Try reading this so you can make it leave you alone.  The thread's a year old, but I think it should still work.
[http://ubuntuforums.org/showthread.php?t=192281](http://ubuntuforums.org/showthread.php?t=192281)

---

### Post by jordanmthomas on 2007-08-24
One of the more recent posts in that thread says to do this:
> I wrote this script:

#!/bin/sh
exec echo -n "MyKeyringPassword" | /usr/lib/libpam-keyring/pam-keyring-tool -u -s

and added it to the session Startup Programs. Obviously it relies on being run after gnome-keyring-daemon starts but before nm-applet, but that seems to happen automagically for me.

So I don't need to enter a password at all any more! I know, I know, very lax security. ...

You still need the libpam-keyring package for pam-keyring-tool. 

---

### Post by anewguy on 2007-08-25
> **jordanmthomas said:**
> According to anewguy it's because it wants to protect the key for your wireless connection.  Any time it needs to read the key and it hasn't been authorized for a while it will ask to make sure it's cool with you to use the key.
(I just use MAC address filters and leave it open, seeing as I'm a lazy man)

Try reading this so you can make it leave you alone.  The thread's a year old, but I think it should still work.
[http://ubuntuforums.org/showthread.php?t=192281](http://ubuntuforums.org/showthread.php?t=192281)

Thanks for the link - I knew there was more than one out there on pam.d, but didn't do the search this time.  The link is appeciated for everyone else reading this thread.

Here's the deal with the keyring:

Your wireless network is using either a WEP or WPA key.  You would have had to set this up when you installed your wireless gateway/router etc..  In order for your PC to logon to that network, it requires that key each time.  What the keyring is doing is "hiding" that key from you so you don't have to remember the network key.  Network Manger is trying to log you on to that network each time you restart your PC, so it asks for the keyring password so that it can look up the network key.  With a single network this may seems useless, but you don't want to have to memorize your network key - a keyring password you provide is easier to remember.  Now if you have access to more than 1 network and each requires a network key, the keyring will remember those keys for you and you need to remember is a single password to the keyring.

As I mentioned in a previous post on this thread, PAM can automate the process for you so that if your log on password and your keyring password are the same, it won't ever ask for the keyring password.  The above post by jordanmthomas is a link to one such set of instructions for PAM.:)

---

### Post by noiseordinance on 2007-08-25
I read pretty much all ten pages of the forum post related to the error I'm getting. I did pretty much everything, installing all the PAM files and whatnot. The one thing I haven't done is:

[I]"Several people have asked how to get this to work with autologin. Making the same change to /etc/pam.d/gdm-autologin as to /etc/pam.d/gdm described at the start of the thread sort of works, but you do get asked for a password at login, so it isn't really automatic any more.

Instead I wrote this script:

#!/bin/sh
exec echo -n "MyKeyringPassword" | /usr/lib/libpam-keyring/pam-keyring-tool -u -s

and added it to the session Startup Programs. Obviously it relies on being run after gnome-keyring-daemon starts but before nm-applet, but that seems to happen automagically for me.

So I don't need to enter a password at all any more! I know, I know, very lax security. But people who don't use gdm autologin might also find this method useful, because it means you can use separate passwords for logging in and for the keyring. And the script could probably be refined so as not to reveal the password in plain text.

You still need the libpam-keyring package for pam-keyring-tool. And I had to look at the source to find out how to use it. There's probably a way of doing the same thing using the dbus interface so you don't need libpam-keyring."[/I]

Does this mean I need to go into the Sessions manager, add a new startup program and type "#!/bin/sh
exec echo -n "MyKeyringPassword" | /usr/lib/libpam-keyring/pam-keyring-tool -u -s" as the command?

Thanks!

(PS - Ubuntu seems freaking awesome, all the UI modifications and whatnot, I love it!)

---

### Post by jordanmthomas on 2007-08-25
Here's what to do for that part:
```
gksudo gedit /usr/local/bin/pamfix
```
paste in that script
```

#!/bin/sh
exec echo -n "MyKeyringPassword" | /usr/lib/libpam-keyring/pam-keyring-tool -u -s

```
save it and close it.  (Make sure to put your password in place of MyKeyringPassword)
Then, type
```
sudo chmod +x /usr/local/bin/pamfix
```
then, in the session properties add a new entry that runs /usr/local/bin/pamfix

It seemed as though this was an alternate solution to the one the thread starts with, but I suppose it couldn't hurt to have both in place.

---

### Post by noiseordinance on 2007-08-25
Thanks a ton to both of you. I now have a fully functional Linux Dell laptop in full 1024x768 and auto-enabled wireless connectivity. So far I'm in love with this new O/S. Transparent toolbars? That's something you have to pay for (StyleXP) on the XP platform. I can't believe all the software this thing comes with.

I'm going to be pursuing a bachelor in IT and getting all the typical certifications and someone told me that of his certs, his Linux certs were his most valuable so I figured "what the heck, I need to get acquainted." There are still some things that need to be ironed out before Linux can grab a more sizable share of the home user marketplace but Ubuntu is a great start. (I can't tell you how frustrated I was installing Red Hat about  6 or 7 years ago) 

Anyways, thanks again guys... I'm sure I'll be hitting this forum up frequently! :)

---

### Post by noiseordinance on 2007-08-25
I'm noticing that 1/3 of the time when starting Ubuntu, I get no display and I have to hard power down. Basically, I'll turn it on, I get past the BIOS prompt. Then I get the Ubuntu loading screen and shortly after loading, my screen goes black instead of going to my desktop (I have it set to auto-login). I have tried waiting and waiting but am forced to hard power down. I'll even hear the Ubuntu login music while the screen is black so I know the system isn't froze. Just no display. And when I turn it on, it'll keep doing the same thing until I hit esc during the GRUB text right after BIOS and manually choosing the Ubuntu kernal (it doesn't matter which one I choose, since they all work). This gets me back to being able to load my desktop but after turning the system off and coming back to it later, I get no display once again...

Does this seem weird?

---

### Post by jordanmthomas on 2007-08-25
It does seem weird.  When it crashes like this are you trying to resume from a suspend or a hibernation?  

Also, you may want to try editing your /boot/grub/menu.lst and finding the line that says default (some number)  and make it say default 0

---

### Post by noiseordinance on 2007-08-25
Is the the text you're referring to?:

[i]## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0[/i]

Also, this isn't after hibernation or anything. I haven't tried using that yet. It's when I shut the computer down completely, walk away for a while, and then turn it back on.

---

### Post by jordanmthomas on 2007-08-25
Yes, that's the number.  It's already the right one.  :|

Is there any chance you BIOS has an option to set the amount of RAM your graphics takes up?  Mine doesn't, so I am really glad I never have problems like this.  :)

The only other thing I can think of is maybe you should try the intel driver instead of the i810 driver (which is what you use, correct?)  To do this edit /etc/X11/xorg.conf and search for i810.  Find the line that looks like
```
Driver "i810"
```
and change i810 to intel.  If it still doesn't work, you are able to specify the amount of VRAM in xorg.conf I believe.

Hopefully that will work, but I can't promise anything.

---

### Post by noiseordinance on 2007-08-25
I changed it to intel and upon reboot, I get a blue screen while Ubuntu is loading:

*"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"*

---

### Post by isaacj87 on 2007-08-25
For fiesty users...all you have to do to get the keyring to stop asking you for a password is do this.

Open up Terminal and type:
```

sudo apt-get install libpam-keyring

```

Then cd to the right directory and open the gdm file...
```

cd /etc/pam.d
gksudo gedit gdm

```

then at the bottom of the file add this line:
```

@include common-pamkeyring

```

So it should like this:
```

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password
@include common-pamkeyring

```

Save close and it'll never bother you again. **There is one thing about doing it this way. Hopefully you set your keyring password to the* same* password you use to log in. They HAVE to be the same in order for this to work. Or it won't. I promise!!**

---

### Post by isaacj87 on 2007-08-25
> **noiseordinance said:**
> I changed it to intel and upon reboot, I get a blue screen while Ubuntu is loading:

*"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"*

You broke your computer forever... Just kidding...I've had this happen (I have an intel card to i915). Just use your LiveCD...**don't reinstall**...just open up terminal and edit your existing xorg.conf file and change it back the "i810"

---

### Post by noiseordinance on 2007-08-25
I'm kinda lost. I boot with the live CD and type in "gkedit gedit /etc/X11/xorg.conf" and it loads the file, but it's already set to "i810" as if it were referencing the CD and not the xorg.conf on my hard drive...

Any pointers?

---

### Post by isaacj87 on 2007-08-25
Sorry, I should of been more specific...

I can't see it right now, but you have to CD into your hard drive to edit the existing xorg.conf. 
In the panel go to Places->Computer and right click on "Filesystem"...it should have it's location in there. Then you can "cd" to it...
For example,
```

cd media0

```

Unfortunately, I can't see what you're seeing because I'm not booting off the live CD...so you can't really quote me on all of this! I'm pretty sure I'm right though.

---

### Post by noiseordinance on 2007-08-25
Am I supposed to boot Ubuntu from the CD or choose one of the other 6 options during boot?

---

### Post by jordanmthomas on 2007-08-25
boot your normal system and once the blue screen comes up hit ctrl - alt - f1
log in here
type
```
sudo nano /etc/X11/xorg.conf
```
use your arrow keys to navigate and change intel back to i810

When you're done, hit ctrl - x to quit, press y to answer yes to the question it asks.

**edit** sorry I didn't make sure the intel driver supported your card.  It is a simple fix though.

---

### Post by noiseordinance on 2007-08-25
Oops nevermind, you replied... I'll try.

---

### Post by isaacj87 on 2007-08-25
> **jordanmthomas said:**
> boot your normal system and once the blue screen comes up hit ctrl - alt - f1
log in here
type
```
sudo nano /etc/X11/xorg.conf
```
use your arrow keys to navigate and change intel back to i810

When you're done, hit ctrl - x to quit, press y to answer yes to the question it asks.

**edit** sorry I didn't make sure the intel driver supported your card.  It is a simple fix though.

Wow! I didn't know you could do it this way...it's alot easier than having to boot off the liveCD first.

---

### Post by noiseordinance on 2007-08-25
Sweet. Well I'm back up and running again, though of course after shutting the system down and then returning 30 minutes later, it goes to the black screen instead of my desktop once again. What was the about possibly tweaking the VRAM settings?

Thanks!

---

### Post by jordanmthomas on 2007-08-25
In the device section for your card (the same section with the i810 line in it, add this:
```
VideoRam 32768
```

Here's an example of what it should look like:
```
Section "Device"
    Identifier  "my card"
    Driver      "i810" # do not remove vesa
    VideoRam 32768
    Option "XAANoOffscreenPixmaps"
    Option "BusType" "PCI"
    Option "ColorTiling" "on"
    Option "EnablePageFlip" "on"
EndSection

```

Of course, my options may be different than yours (not exact same card, so just look at the VideoRam lines to see *where* to put it.)

---

### Post by noiseordinance on 2007-08-26
I changed it as mentioned and upon bootup, went to blackscreen. I hard power down and hit esc at the GRUB menu and select the first kernel option and it boots fine. This is pretty odd. Any other pointers? I'm beginning to feel XP-bound since Ubuntu won't run on my Abit AB9-Pro Dual Core system... D'oh!!!

---

### Post by jordanmthomas on 2007-08-26
I have another idea, but, as usual, I am not sure if it will work or not.  

In your /boot/grub/menu.lst find the line with your kernel.  Here's mine from ArchLinux (yours will look different, but it's the same layout)
```
# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
[COLOR="Red"]kernel /boot/vmlinuz26 root=/dev/sda1 ro [COLOR="Blue"]vga=869[/COLOR][/COLOR]
initrd /boot/kernel26.img

```

Find your section that's like this one.  You will probably have several blocks similar to this, but you should be ok to just edit the first one.  On the line that starts with **kernel** add the text
```
vga=792
``` to the end of it.

This will make your "real" terminals have a resolution of 1024x768 and will maybe make your system allocate more memory to your graphics card so you can run X without it crashing.  That's what I'm hoping anyway.  

If for some reason you can't boot after you do this, you'll still be able to fix it.  In the case it doesn't boot at all after you do this, just hit esc at your grub menu and press e on the first line.  Then, select the kernel line and press e to edit the kernel line that shows up and take off the vga=791.  Hit esc and then b to boot it.  Once booted, you can edit your menu.lst again and take it off.



Did you ever check to see if you can allocate memory to your card in your BIOS (too lazy to read back)?

And the last, final suggestion I have is to maybe look into 815/915 resolution.  A quick forum search for 815resolution or 915resolution should bring up info about it.  I don't have any experience with it so I won't tell you how to use it (and in fact I'm not sure if your card is supported, so check that first as well)

One last question I have is while the screen is stuck at the black screen, does Ctrl - Alt - F1 do anything?

Good luck.

---

### Post by noiseordinance on 2007-08-26
Adding that line still gives me the problem. Defining the resolution doesn't seem to hinder me at all but it doesn't correct the problem either. It almost seems like this thing restarts just fine, but doing a full shutdown creates the problem. I tried pressing ctrl + alt + F1 after Ubuntu was loaded while the screen was black but it didn't do anything, just stayed black. I originally went into my BIOS and set the Video Memory from 1MB to 8MB while I was battling the whole 640x480 display issue, so that's where it's set right now.

Well, thanks for all your help. I really appreciate the support you've provided me. There seems to be some very kind folks floatin' around here on this forum!

---

### Post by isaacj87 on 2007-08-26
Just asking. But did you try installing 915resolution?

That's all I had to do to correct my resolution problem. Here's description of what it does:

> 
resolution modification tool for Intel graphic chipset
915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the **845G**,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server.

915resolution's modifications of the BIOS are transient.
There is no risk of permanent modification of the BIOS.
This also means that 915resolution must be run every time the
computer boots in order for its changes to take effect.
If you want to automatically set the resolution on each boot
and before X is launched, see /usr/share/doc/915resolution/README.Debian
for information about configuring the provided initscript.

 Homepage: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)


---

### Post by LingLing1337 on 2007-08-26
Too lazy to read all pages, but have you tried "dpkg-reconfigure xserver-xorg" in the command line ?

---

### Post by noiseordinance on 2007-08-27
LingLing, when I place that in terminal, it says I need to run the command as root....

Isaac, I don't know what to do with the file once downloaded. :(

Gah! lol

---

### Post by noiseordinance on 2007-08-27
Come to think of it...I don't know the first thing to do on that 915resolution page... I suck!

---

### Post by jordanmthomas on 2007-08-27
[https://help.ubuntu.com/community/FixVideoResolutionHowto#head-8b0ad82432ba5f582395ffe40cfa454adaba2068](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-8b0ad82432ba5f582395ffe40cfa454adaba2068)
This might get you started.

---

### Post by noiseordinance on 2007-08-29
Hey there. It's  hard for me to get online during the work week but I'm back again trying to conquer this thing. I went to the link as mentioned, and I typed:

sudo apt-get install 915resolution

It installed. Then afterwards I typed:

sudo 915resolution -l

It listed my display modes:

Chipset: 845G
BIOS: TYPE 2
Mode Table Offset: $C0000 + $38a
Mode Table Entries: 18

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

I'd like to  use mode 54 or mode 45 (I'm pretty sure my card used 32bit in XP Pro, but I'd be happy with 16bit as that's what it's currently set at in Ubuntu). Problem is the tutorial doesn't seem to tell me how to enable this thing, or I'm just plain stupid. LOL, do you know what I'm supposed to do next?

Thanks so much... I'm feeling humbled by technology.

---

### Post by jordanmthomas on 2007-08-29
```
gksudo gedit /etc/default/915resolution
```
It should look like this:
```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE  or set to 'MODE=auto'
#
MODE=[COLOR="Red"]41[/COLOR]
#
# and set resolutions for the mode.
XRESO=2400
YRESO=1600
```
The 41 you should change to the mode you want to not have available (like 41 or something).
and XRESO should be 1024
and YRESO should be 768.

So, your file should look something like this:
```
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE  or set to 'MODE=auto'
#
MODE=[COLOR="Red"]41[/COLOR]
#
# and set resolutions for the mode.
XRESO=[COLOR="Red"]1024[/COLOR]
YRESO=[COLOR="Red"]768[/COLOR]
```

---

### Post by noiseordinance on 2007-08-30
Well, I did the 915resolution fix. It's still acting up. I'd have the say this is the most sporadic issue I've ever seen. My display always works on restarting the computer. However, my display works less than half the time after a full shutdown / boot up. It's as if there's some sort of randomized script during bootup, though I know that isn't possible. An IT feller for my company who's pretty Unix / Linux savy said it sounds like the default configuration is telling my LCD screen to use a refresh rate that's causing my screen to simply not work. Obviously, whatever kernel option 1 is in the GRUB menu is 100% accurate, as selecting option one has worked every single time.

Hopefully the issue is fixed in the release of Hardy Heron, though that's a looooong ways off. :(   

For the record, I've never had a single screen issue during my laptops ventures with XP.

---

### Post by TeaSwigger on 2007-08-30
Hello,

Hope you enjoy the heck out of your ubuntu, it's awesome. Microsoft takes billions for windows and here's ubuntu offering a serious alternative for nothing... I also really enjoy the freedom to be able to see and control what you're putting on your own computer, as it should be IMH.

Anyway I come bearing links which might possibly be of some relevance.

[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

And hasn't the i915 been superceeded? Maybe I'm confusing it. I ought to remember the specifics, having done something with replacing graphics driver a few days back, but I guess it hit another drain bramage area.

---

### Post by jordanmthomas on 2007-08-30
You've definitely got me stumped.  Maybe you could go on #ubuntu and ask there.  Have you listened to that fart smeller...errr smart feller to see if maybe your xorg.conf has some kind of weird refresh rates set (but I don't see how it would work sometimes but not others in this case)?  

In my head I'm still convinced it has to do with your VRAM but I don't really know what to do about it.  

I'll probably get shot in the face for suggesting this, but maybe you could consider another distro?  

Anyway, good luck to you.  Unless you have something else to add (you've given plenty of information, I'm not chastising you or anything) I'm stumped and I think I might have to throw in my towel.  Anyone else have any ideas?

---

### Post by jordanmthomas on 2007-08-30
> And hasn't the i915 been superceeded? Maybe I'm confusing it. I ought to remember the specifics, having done something with replacing graphics driver a few days back, but I guess it hit another drain bramage area.
Yes, the i810 driver is being replaced by the intel driver.  However, the intel driver doesn't support the OP's card it seems.

---

### Post by jordanmthomas on 2007-08-30
On the plus side, you don't really have to reboot Linux too often.:lolflag:

---

### Post by TeaSwigger on 2007-08-30
Oh! Just recalled it was xserver-xorg-video-intel v2:1.9.94-1ubuntu4, In the backports repository.

> **jordanmthomas said:**
> Yes, the i810 driver is being replaced by the intel driver.  However, the intel driver doesn't support the OP's card it seems.

Thanks for jostling the memory. Would this new version from backports work where the old one didn't? I've no idea. If not, too bad about the card, sheez.

---

### Post by noiseordinance on 2007-08-30
> **TeaSwigger said:**
> Hello,

Hope you enjoy the heck out of your ubuntu, it's awesome. Microsoft takes billions for windows and here's ubuntu offering a serious alternative for nothing... I also really enjoy the freedom to be able to see and control what you're putting on your own computer, as it should be IMH.

Anyway I come bearing links which might possibly be of some relevance.

[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

And hasn't the i915 been superceeded? Maybe I'm confusing it. I ought to remember the specifics, having done something with replacing graphics driver a few days back, but I guess it hit another drain bramage area.

Don't take this the wrong way, but I AM trying to enjoy the heck out of my Ubuntu. LOL.

Anyways, I went to the link, [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) and noticed their mention of installing the updated Intel driver. I know previously in this thread I had attempted to switch from i810 to Intel but just for fun, I tried downloading the Intel drive per that link by typing sudo apt-get install xserver-xorg-video-intel and changing i810 to Intel once again. Of course, upon reboot I was getting an error that X Server couldn't start so I CTRL + ALT + F1 and then did gksudo gedit /etc/X11/xorg.conf and switched Intel back to i810. Upon restart it still tells me that X Server can't start. I read the errors in the log and it's a repeated error saying something to the effect of not being able to buffer and render, and then saying "Is there enough VRAM?" This error occurs about ten times in the error log.

---

### Post by anewguy on 2007-08-30
Hi, I'm no expert or anything like that, but if you don't mind I'll toss in a couple of ideas.

I seem to remember reading other threads about some Intel GPU's that you may need to:

- put something along the lines of    Option  "nodirectrendering"  "true"   in the device section of xorg.conf that defines your video controller

- also something about specifying the video memory and the correct setting to use in your BIOS as well in xorg.conf.

I wish I could give you more specifics.  Perhaps you have already tried these things.  Maybe it will ring a bell with someone and they'll say "what he meant was......".  Maybe you'll have to dig around on some of the post for some of the other Intel gpu's - like the 945(?) I think is something I've seen mentioned.

Also, I can't remember if you ever said what the horizontal freq and vert refresh rates are set at in the monitor section of your xorg.conf file.  Maybe you could post those here as well.

Anyway, I'll quit rambling now.  Good luck to you!:)

---

### Post by TeaSwigger on 2007-08-31
> **noiseordinance said:**
> Don't take this the wrong way, but I AM trying to enjoy the heck out of my Ubuntu. LOL.

Anyways, I went to the link, [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) and noticed their mention of installing the updated Intel driver. I know previously in this thread I had attempted to switch from i810 to Intel but just for fun, I tried downloading the Intel drive per that link by typing sudo apt-get install xserver-xorg-video-intel and changing i810 to Intel once again. Of course, upon reboot I was getting an error that X Server couldn't start so I CTRL + ALT + F1 and then did gksudo gedit /etc/X11/xorg.conf and switched Intel back to i810. Upon restart it still tells me that X Server can't start. I read the errors in the log and it's a repeated error saying something to the effect of not being able to buffer and render, and then saying "Is there enough VRAM?" This error occurs about ten times in the error log.

Gosh did you get your ubuntu working again? When I first changed i810 to Intel in that file I had an error, but when I changed Intel to intel, note the lower-case i, it worked next boot. But I also changed something else I can't seem to remember what. Jeez I feel bad for suggesting the link :( but it really did work here. Wish I knew more about it. If you haven't already, can you try to boot into recovery mode and restore a backup copy of xorg.conf - hopefully you made a copy before editing? Or you can use recovery mode and edit it back from the command line? At the prompt, 'nano /etc/X11/xorg.conf'.

---

### Post by noiseordinance on 2007-09-02
Thanks for all the help folks. I ended up switching to PCLinuxOS which works great for now. I feel that Ubuntu seemed more stable as not so much as a single program shut down whilst using simple things like Firefox and media player. I've had Firefox shut down unexpectidly as well as the configuration utility in PCLinuxOS. That's hardly a gripe but considering it's a fresh install, it gives me a slightly eerie feeling. I'll attempt to switch back to Ubuntu once the new version comes out which, hopefully, will attempt to fix my issue.

---

### Post by jordanmthomas on 2007-09-02
Sorry you couldn't get your issue sorted out.  But I am glad you decided to stay with Linux.  There's nothing wrong with / to be ashamed of for switching either.  Use whatever works best for you, I say.  Ubuntu doesn't cut it for me, so I don't use it.  

My firefox crashes a lot lately too, every time it brings up a save dialog box.  I'm not sure of the cause, and it's pretty much a "deal-breaker" so I use something that suits my needs better.  

I know you're probably tired of all the annoyances you've been through while trying to fix your X.  Since your PCLinuxOS X works, if you're ever bored you should try using its xorg.conf on Ubuntu and see if it might help any.  (If I was you, I probably would just say forget it, but just keep it in mind in case you ever have problems again.)

---

### Post by anewguy on 2007-09-03
There is also a possibility that, when using the old driver, it wasn't always restarting X upon startup.  There is a post out here by user "tarek" about getting his laptop over to Ubuntu.  He had to fight hibernation issues which sound suspiciously like yours.  It involved putting a line in somewhere to force X to restart.  There are a lot of things to read through in the post, but you'll eventually get to the places where he explains what he did to fix this type of problem.  Please see:

[http://ubuntuforums.org/showthread.php?t=499960]("http://ubuntuforums.org/showthread.php?t=499960")

:)

---

