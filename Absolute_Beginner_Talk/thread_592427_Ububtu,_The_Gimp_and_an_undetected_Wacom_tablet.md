---
title: "Ububtu, The Gimp and an undetected Wacom tablet"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Michael Fearon on 2007-10-26
Hey all,

I'm having a problem with my wacom tablet, it's a CTE-630 (Sapphire). I'm running Ubuntu Gusty which appears to have read the tablet fine i.e. I can move the cursor with out touching the tablet. However when I try to use Gimp (version 2.4.0-rc3, the one installed with Gutsy by default) and make the required changes in Preferences > Input devices, it refuses to acknowledge my device. Returning the message 'No extended input devices'.

Having scoured the internet and not finding anyone with quite the same problem I was hoping someone could help me here.

Thanks for your time.

PS The subject line should have read Ubuntu (Hope the Ubuntu god's aren't angry with me!!! :)

---

### Post by mcallenSchmee on 2007-10-26
Sometimes you have to restart X to get a tablet working, try ctrl+alt+backspace. That might not be the problem in your case though.

---

### Post by Michael Fearon on 2007-10-27
I've tried restarting after configuring the correct files. Still no change. :(
Perhaps this is a problem with Gimp rather than Ubuntu? Reading through the threads on this forum it would appear that other people have had the same 'no extended devices' message from Gimp. Though as I stated I don't appear to have a problem with Ubuntu recognizing my tablet as mouse.

Going to try a Gimp forum and ask there. (Though if anyone has an answer please post. I'm stumped!

---

### Post by CitricAcid on 2007-10-30
I have similar problem. My wacom used to work fine on feisty. Now on gutsy there's only pen position read fine but no pressure sensitivity. Restarting X doesn't fix the issue.
Tablet works but it is not seen by gimp: "No extended input devices".
Help, please.

---

### Post by Destinatus on 2007-10-30
Also having this problem, I already have all the inputs for the tablet in my xorg.conf file and I've tried restarting X several times, keep getting the same error as everyone else in this thread.

---

### Post by andrevanzuydam on 2008-04-17
Hi Everyone

I would like to confirm if all of you are using desktop effects, it seems that the default GIMP does not have support for the tablets in this mode of X.

It apparently needs to be compiled with a GTK library with xinput support.  I am busy trying to get this working and will post here again if I get it right!

To disable the desktop effects and be able to use your tablets in GIMP simply create a file in your home folder as follows 

~/.config/xserver-xgl/disable

Restart X and then see if you can use the tablet in GIMP - remember to set it to screen or window as by default it is disabled.

This will work provided you have followed the HOWTO in installing your tablet.  I was fortunate to have a non-standard graphics driver and therefore did not have desktop effects installed before I began with the tablet.

I noticed the tablet did not detect in GIMP after enabling desktop effects and so started to find out why.

---

### Post by andguent on 2008-04-26
> **andrevanzuydam said:**
> I would like to confirm if all of you are using desktop effects, it seems that the default GIMP does not have support for the tablets in this mode of X.

+1

I have the same exact issue here. I didn't have pressure sensitivity working and didn't know why. Doing the following fixed the pressure sensitivity and disabled effects. Good to know.

```
touch ~/.config/xserver-xgl/disable
Ctrl+Alt+Backspace
```

I'm using the basic Bamboo (MTE-450) and running a fresh upgrade to Hardy from Gutsy.

---

