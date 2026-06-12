---
title: "Need help with Ubuntu on G3 iMacs in classroom"
date: 2007-01-31
forum: Apple PPC Users
---

### Post by ScooterDMan on 2007-01-31
I am a high school English teacher. Someone donated about 15 G3 iMacs, and I am trying to get them set up to use as a writing lab.

They are all 350mhz processors, range in memory from 64mb-256mb and run Mac OS9.2.  My experience with Ubuntu is limited. I've played with its desktop environment, but have never worked in the command line. From what I've googled online (and read here), these G3 installations can be tricky. So far, I have managed to install Ubuntu 5.10. The login screen comes up, I type in my usrname and password, the pretty music comes on, and then BLACKNESS.

If there's a fix that someone can patiently explain (remember: I know nothing), I would really appreciate it. If not, can you recommend another Linux distro that might make for an easier install. ALL these computers need to do is run the latest versions of Firefox (We can use Google Docs for word processing). 

I have tried installing Xubuntu with the Live CD, but it also goes black after a while.

Any guidance would be great. I'd hate to see these machines go to waste.

---

### Post by linear on 2007-01-31
[COLOR=SeaGreen][COLOR=Black]Sorry, but you will have to delve into the command line.

The installer does not set up the file "xorg.conf" correctly for the iMac G3. The usual fix, after you get to the blank screen, is to drop to a shell prompt (command line) and edit xorg.conf.

To do this:

After booting is complete,
1. press ctrl-option-F1 (should give you a command prompt, may take a couple of tries)
2. type: **sudo nano /etc/X11/xorg.conf** (return) - note that the file name and path are case-sensitive
3. Find and modify "HorizSync" to 58-62 and "VertRefresh" to 75-117. Both are in the "Monitors" section.
4. Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo killall -HUP gdm (return) to restart Gnome

By all reports, you'll need Xubuntu for the low memory iMacs, and I'm not sure that 64MB will cut it there either.

[/COLOR]   [/COLOR]

---

### Post by ScooterDMan on 2007-01-31
Hey, thanks a lot. I think I am making some progress here. I was able to get in there and make the first modifications you suggested, concerning the Horiz and Vert display settings.

I think I may be messing up the DRI, however. Where exactly do I put the #? Before the word "Load"?

Should it look like this:
 #Load      "dri"

or

Load         "#dri"


Or something different?

When I execute the killall -HUP gdm I get the intro music, and a maroon screen instead of a black one. Seems like progress to me!

---

### Post by grazie on 2007-01-31
There really isn't that much choice of linux distros for PPC machines and for easy installation, there's only Ubuntu . You're having problems installing with the Live CD on low spec machines as you need at least 128M RAM, although 256M speeds things up considerablely. To get round this problem, there's an alternate install CD which doesn't use a GUI installer, hence doesn't require as much memory. I'd recommend sticking with Xubuntu for all, but that's your choice. However, as linear says, only 64M of RAM may be pushing it a bit, but it only costs a bit of time to try it. The 64M machines may still be OK to use if you then install and use Fluxbox or similar instead of XFCE.

---

### Post by ScooterDMan on 2007-01-31
This machine that I am trying to perform this initial install on has 256mb of RAM, so that shouldn't be a problem. I just need to figure out how to get beyond the login screen.

---

### Post by grazie on 2007-01-31
I'm afraid you've lost me now. There is no login screen on the Live CD. Do you mean you still can't boot the Live CD? Is so, this nearly always is due to having a bad disk. The issue is probably discussed in many places, but I posted on [this thread]("http://www.ubuntuforums.org/showthread.php?t=346180") recently.

---

### Post by ScooterDMan on 2007-01-31
I was able to install Ubuntu using the iso I burned on a CD. It took about an hour for it to unpackage and install all the files.

Once that was done, an Ubuntu login screen came up. I put in the usr name and password i had set up during the install. After I hit enter, I get a maroon backround and a white pointer.

I have followed the instructions Linear provided above, but I am not sure if I disabled the DRI successfully, because I am unsure as to exactly how I should edit the module — Where exactly do I put the number sign?

---

### Post by ScooterDMan on 2007-01-31
I think I see the source of your confusion now. I am talking about Ubuntu 5.10 here. I only mentioned the Xubuntu Live CD in my first post because I had tried using it to no avail on a different computer earlier today.

If you think I should abandon this Ubuntu install and know a surefire way to get Xubuntu working on this G3 iMac, by all means let me know. I need to get these machines functional in any way I can.

---

### Post by Auria on 2007-01-31
> Once that was done, an Ubuntu login screen came up. I put in the usr name and password i had set up during the install. After I hit enter, I get a maroon backround and a white pointer.


Plain maroon, or do you see the default wallpaper?

---

### Post by ScooterDMan on 2007-01-31
just plain maroon. no wallpaper.

---

### Post by linear on 2007-01-31
> **ScooterDMan said:**
> Should it look like this:
 #Load      "dri"

Yes, like that.

---

### Post by ScooterDMan on 2007-01-31
Thanks for the help, LInear. Even after following the instructions you gave me, and disabling the DRI correctly, I couldn't get past the maroon screen.

Fortunately, I took the advice from someone else in this thread and downloaded the Alternate version of Xubuntu. The install went perfectly, and I am responding from that system now. 

Now that I have this machine up and running, I am eager to see if I will have the same sucess with the slower machines in my classroom tomorrow.

Thanks for the help, Linear. I learned a whole lot by following your instructions today. Hadn't touched a Linux command line before!

---

### Post by 3rdalbum on 2007-02-01
Glad that you installed Xubuntu successfully.

The probable reason why you got the maroon screen with Breezy was because of the "date bug" - that version of Ubuntu won't log in if the date is set too far in the past (i.e. the PRAM battery has run out and the computer hasn't been supplied with power).

For the machines with less memory, it might pay to use the Breezy version of Xubuntu - you install normal Breezy first, then delete Gnome and Gnome's programs and run the command:

```
sudo apt-get install xubuntu-desktop
```

If you run into the date bug again, here's the command to run in the terminal before you try logging in to Gnome:

```
sudo date -u 020116552007
```

That will set the system clock to the current date and time as of 16:55, Feburary 1st 2007.

---

### Post by bodycoach2 on 2007-02-01
It looks like you've found the "trick" to installing Xubuntu on a G3 lower than 500 MHz

[LIST=1]
[*]Download the Xubuntu 6.06.1 ALTERNATE install CD
[*]Burn it at the slowest rate possible
[*]Be patient while loading
[*]Make sure the ethernet cable is plugged in. Makes the setup much easier.
[/LIST]

6.06, 6.10 don't work well on older G3's for some reason. So far, only the 6.06.1 works right. I'm looking forward to the Fluxbuntu PPC version.

If it's going to be a writing lab, you might consider using Synaptic to install some of the Typing Tutor packages. 

My girlfriend uses Ubuntu. She thinks "command line" is an audio animatronic show at Epcot's "Wonders of Life". She's never opened the termimal.

> **ScooterDMan said:**
> Thanks for the help, LInear. Even after following the instructions you gave me, and disabling the DRI correctly, I couldn't get past the maroon screen.

Fortunately, I took the advice from someone else in this thread and downloaded the Alternate version of Xubuntu. The install went perfectly, and I am responding from that system now. 

Now that I have this machine up and running, I am eager to see if I will have the same sucess with the slower machines in my classroom tomorrow.

Thanks for the help, Linear. I learned a whole lot by following your instructions today. Hadn't touched a Linux command line before!

---

