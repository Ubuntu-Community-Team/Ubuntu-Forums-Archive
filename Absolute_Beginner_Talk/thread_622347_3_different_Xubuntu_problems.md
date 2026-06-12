---
title: "3 different Xubuntu problems"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by tenbbs on 2007-11-24
Machine is an HP laptop, AMD64-3700+ cpu.
OS is Xubuntu 7.10 x86 Desktop, installed... this morning.

#1 - When I plug in headphones, built in speakers do not turn off. Please see post here
[http://ubuntuforums.org/showthread.php?t=622170](http://ubuntuforums.org/showthread.php?t=622170)

#2 - Using ndiswrapper for my broadcomm wireless card, or a cat5 cable, responses to internet requests are very VERY delayed, but once they start transferring data, that seems to go on at a reasonable speed. Other machines on the network, and this one when booting Windows, do not have the same problems.
See post here (2nd one down)
[http://ubuntuforums.org/showthread.php?t=523602](http://ubuntuforums.org/showthread.php?t=523602)

#3 - How do I get a control panel for the touchpad on this thing? I installed gsynaptics, added the appropriate line in /etc/x11/xorg.conf but I still don't see a Synaptics control panel anywhere in the Settings or System folders of the "applications" menu. I keep moving the cursor accidentally when I type, and I keep double-clicking inadvertantly. I have GOT to turn off "tap-to-click" if I'm going to get any work done.

Thx for the help in advance,

-HelicopterJay

---

### Post by gn2 on 2007-11-24
Open up the casing, disconnect the touchpad and use a mouse?

---

### Post by Daveski on 2007-11-24
> **tenbbs said:**
> 
#2 - Using ndiswrapper for my broadcomm wireless card, or a cat5 cable, responses to internet requests are very VERY delayed, but once they start transferring data, that seems to go on at a reasonable speed. Other machines on the network, and this one when booting Windows, do not have the same problems.
See post here (2nd one down)
[http://ubuntuforums.org/showthread.php?t=523602](http://ubuntuforums.org/showthread.php?t=523602)


Could be IPv6. Try typing about:config in Firefox address bar. Search for **network.dns.disableIPv6** and turn it on. This can make a big difference on networks that do not have IPv6 support.

---

### Post by Luigi239 on 2007-11-24
For the trackpad, did you try restarting X? (ctrl, alt, backspase) I believe when I had that issue it worked for me.

---

### Post by tenbbs on 2007-11-25
1 of 3 solved: For the network speed. It was definitely IPV6 slowing down the DNS lookups. I used both the net.dns.disableipv6 in Firefox, as well as a Community Document that explained how to disable (blacklist) IPV6. Results so far have been great, and if I run into the problem again I know that it's likely an IPV6 issue. Thanks for the help on that.

2 of 3 solved: For the touchpad control, this one was odd, but I went into xfce's Appfinder in Accessories, and put in "gsyn" and searched, and sure enough it returned a result for "Touchpad" which I could open and turn off tapping, as well as adjust scrolling and various other adjustments. It seems after the reboot it rejected my changes, but I believe that's a documented and fixable issue that happens to a lot of people. 

I am a little puzzled as to why gsynaptics has obviously installed itself on the machine, and it works, but it never dropped an icon or a link anywhere in the GUI. I chose gsynaptics over qsynaptics because I believe the "q" varient was intended for KDE, and I've read that XFCE is much more related to Gnome and has nothing to do with KDE.

3 of 3 Outstanding: The method on which to disable the internal laptop speakers when headphones are plugged in is still a mystery to me. I'm going to continue searching for an answer, and will continue to monitor this thread to see if anyone can steer me in the right direction.

Thank you for all of the help so far,

-HelicopterJay

---

### Post by ugm6hr on 2007-11-25
> **tenbbs said:**
> 2 of 3 solved: For the touchpad control, this one was odd, but I went into xfce's Appfinder in Accessories, and put in "gsyn" and searched, and sure enough it returned a result for "Touchpad" which I could open and turn off tapping, as well as adjust scrolling and various other adjustments. It seems after the reboot it rejected my changes, but I believe that's a documented and fixable issue that happens to a lot of people. 

I am a little puzzled as to why gsynaptics has obviously installed itself on the machine, and it works, but it never dropped an icon or a link anywhere in the GUI. I chose gsynaptics over qsynaptics because I believe the "q" varient was intended for KDE, and I've read that XFCE is much more related to Gnome and has nothing to do with KDE.

If you want greater control, you can use syndaemon (and maintain the tap-to-click function) or manually edit xorg (and either edit double-tap settings or turn off tapping permanently):

Some useful entries from me:
[http://ubuntuforums.org/showpost.php?p=3136787&postcount=8](http://ubuntuforums.org/showpost.php?p=3136787&postcount=8)
Shows how to temporarily turn off the Touchpad tapping for 1 second if you are typing - would this solve your problem?

If not - [http://ubuntuforums.org/showpost.php?p=3105368&postcount=2](http://ubuntuforums.org/showpost.php?p=3105368&postcount=2)
Has a link & details for configuring the Touchpad fully - the setting you want is probably something like (maybe try different values for "0"):
```
Option "MaxTapTime" "0"
```

If it is the double tap issue that prevents you from using the syndaemon solution - you can also manually control Tap and DoubleTap times.  You can also edit the amount of pressure required to detect a touch.  Feel free to experiment (after backing up xorg).  Ctrl-Alt-Bksp will resart X to try out new settings.

> 3 of 3 Outstanding: The method on which to disable the internal laptop speakers when headphones are plugged in is still a mystery to me. I'm going to continue searching for an answer, and will continue to monitor this thread to see if anyone can steer me in the right direction.
I think there is no easy way to detect when headphones are plugged in in Ubuntu, so this is the standard.  My laptop behaves the same way - if you find the solution, let me know too!

---

### Post by tenbbs on 2007-11-25
> **ugm6hr said:**
> 
I think there is no easy way to detect when headphones are plugged in in Ubuntu, so this is the standard.  My laptop behaves the same way - if you find the solution, let me know too!

Aww rat farts!!

Maybe I can disable the speakers in the BIOS or something. Hmm...

Thanks for the other info!

-HelicopterJay

---

