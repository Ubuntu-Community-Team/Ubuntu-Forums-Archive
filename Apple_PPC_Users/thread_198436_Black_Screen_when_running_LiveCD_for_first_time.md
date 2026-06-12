---
title: "Black Screen when running LiveCD for first time"
date: 2006-06-17
forum: Apple PPC Users
---

### Post by strikebf on 2006-06-17
Hi. Although this may not be the exactly correct forum, I'm assuming I can get better Mac help here.

I have an old blue-and-white iMac G3, but I've spent the money to add more RAM and update the OS to 10.4.6... I just downloaded Dapper, and burned the ISO to a disk with Disk Utility.

I've booted up the computer through the disk (using the 'c' key), and followed the instructions by hitting return. It goes through the loading process with a status bar, the Ubuntu logo, and all of the things it is doing with 'ok's next to them-- no problems there from what I can see.

The next part is the problem- I get a black screen, and I hear very nice music for about 5 seconds, (most likely an intro to the install?) and then the screen goes black. Pitch black. I've hit keyboard buttons, moved and clicked the mouse... I've ended up doing this several times, and just leaving the computer for an hour or so. 

I once again looked at the yaboot installer, and tried the *live video=ofonly*, yet when I do THAT, once the loading process is done, I get an error message saying that my Xserver graphic stuff isn't messed up, and it asks if I want it to diagnose the problem. All over the screen is the message saying that Ubuntu comes with no warranty, etc. But, I keep typing in 'yes', and 'no', but that doesn't work. I've done that several times, as well.

I've tried some of the other options, 'live-powerpc', 'live-nosplash-powerpc', and I've tried 'live-powerpc video=ofonly', yet I either get a black screen, or an Xserver error (when I do the video code, I get the Xserver error, when I don't change anything, I get a black screen)

I would really like to use Ubuntu, or an Ubuntu deriative--- can anyone please point me in the right direction?

Thanks much,
Ben

---

### Post by daft_ska on 2006-06-17
There is currently a problem with DRI on old b&w G3's that use the rage 128 card.
The quick-fix for the problem, at least for the liveCD, is to hold control and option and then hit F1, this should drop you into a terminal.

At the prompt, type "sudo nano /etc/X11/xorg.conf", without quotes, noting to use the captial X in X11.

find the line that says "load "dri" near the top and put a # in front of it.
Then, hit Control-X, and then hit Y to save, followed by enter.
Next, and this is the part where I may need to be corrected, as my method is way harsh...but I digress.
I personally then do "ps ax | grep X" and the one process that is not "ps ax | grep X" has a number in front of it, typically 4 numbers long, that's the process ID.
Type "sudo kill XXXX" replacing the XXXX's with the process ID, this kicks X in the teeth and makes it reboot. It should reboot you into the logon screen.
Press enter, and you should be good to go!

If you do end up installing Ubuntu, I've posted a solution to get DRI working on older G3's, just do a little searching for my other two posts.
Anyone want to provide the nicer way of restarting X?:rolleyes:

---

### Post by strikebf on 2006-06-17
Erm, I'm still a bit confused, sorry. I got as far as the 'ps ax | grep X' part, but only one process had anything to do with that (from what I could tell), and it said 'grep X'. Should I put that one?

---

### Post by nkbj on 2006-06-17
Try 'sudo killall gdm' followed by 'sudo /etc/init.d/gdm start'.

---

### Post by beanworks on 2006-06-17
There's a parallel thread on this from a week ago ([[mac] Ubuntu 6.06 - iMac G3: Old Problem, New Wrinkle]("http://ubuntuforums.org/showthread.php?t=190131").

I've got a G3 iMac also.  I tried Kubuntu first and had the same problem, then tried Xubuntu (same problem) before I figured it's probably not the Mac.  My question is, would the commands be the same for Kubuntu (and/or Xubuntu)?

Carol

---

### Post by daft_ska on 2006-06-17
Yes, I've used all 3 and it should work on all of them.

---

### Post by strikebf on 2006-06-17
Okay- great. I followed the steps on the other related post, and am now becoming a full-Ubuntu user (I'm too lazy to screw around with Mac partitions to keep OS X-- so I'm deleting it, but keeping the CDs handy), as the installation is 40% complete at the moment.

Thanks much everyone for ALL of your help.

---

