---
title: "Ubuntu doesn't work! HELP!"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Muphin Man on 2007-01-29
I am a COMPLETE noob to Ubuntu and I want it so badly but for some reason when I try ANY version of it (Xubuntu, Kubuntu) it comes up with the same thing.

First, the screen does what it's supposed to, goes to the loading screen with the bar and the title of the OS. Then it goes to a black screen with the little underscore blinking. Not too unusual. Then it goes to a weird multicolored screen with question marks and stuff as a border and the error box says "Cannot start Xserver".

What the heck is that supposed to mean?! I press OK and it lists all this stuff that "went wrong" I guess. Then the screen goes black until I reboot the computer.

Please help me, I've looked everywhere for information but nothing is working!

Thanks guys I know you'll help me out,

Muphin Man

---

### Post by mikewhatever on 2007-01-29
Post your PC specs: graphic card, and whatever else.

---

### Post by Zzl1xndd on 2007-01-29
we need a little more info. your computers specs and such. Also is this from an install or the live CDs?

---

### Post by Muphin Man on 2007-01-29
eMachine T2042
Intel Celron Processor 2.00GHz
384 MB of RAM
Nvidia GeForce FX 5700 LE 128 MB Graphics Card
37.8 GB Hard Drive

This is from an Install I think... I downloaded the ISOs and burned them.

---

### Post by Zzl1xndd on 2007-01-29
I had a the same kind of issue with and eMachine when trying to install Kubuntu on it everything seemed to go fine but then it would just hang. The only thing that worked for me was using the Alternate install CDs.

If it was the standard ISO then it was the live CDs. Dont know why but eMachine  dont seem to like the live CDs at all.

---

### Post by Muphin Man on 2007-01-29
What's the difference between the alternate and the one you just download? Also, where can I get the alternate CD?

---

### Post by Zzl1xndd on 2007-01-29
> **Muphin Man said:**
> What's the difference between the alternate and the one you just download? Also, where can I get the alternate CD?

the standard one is a live CD with an install option after it is running (just incase you havn't used a live CD that is one that runs off the CD without writing to your hard drive). The Alternate CDs are simply an installer CD much like the Windows ones (with no try before you install option). as for the alternate CDs and where to get them what version do you want to use. I would suggest the Gnome versions. Or did you want KDE  or Xubuntu?

---

### Post by Frank Golden on 2007-01-29
> **tweakedenigma said:**
> I had a the same kind of issue with and eMachine when trying to install Kubuntu on it everything seemed to go fine but then it would just hang. The only thing that worked for me was using the Alternate install CDs.

If it was the standard ISO then it was the live CDs. Dont know why but eMachine  dont seem to like the live CDs at all.Do you know if you installed or are you running the LiveCD.
If you are running the live CD Ubuntu runs off of the CD and system memory, not installing itself to the HardDrive.
It is a method of trying Ubuntu without actually installing it on your drive.

An install is just that Ubuntu is installed on your HDD and you don't need the CD to run it.

Xserver is your GUI server (xorg). From the error message there is some piece of hardware
not configured properly, not detected properly or not supported with your present configuration. Xorg uses a configuration file called /etc/X11/xorg.conf to setup your mouse,
video card and other input/output devices at boot.
You can from the command line (black screen) edit xorg.conf to try to get past the error.
The command used after you get the black screen and login is

```
sudo dpkg-reconfigure xserver-xorg
```

This will open up a graphical interface to help you configure xorg.
My guess is your graphic card is at issue. Try setting the card driver setting to vesa.

---

### Post by Muphin Man on 2007-01-29
I don't think that I entirely understand what the difference is between Gnome and KDE and Xubuntu is. Aren't they all just different versions of Linux? Or do they build off of Linux OSs like Ubuntu?

I'm trying to try Ubuntu before I install it so that I know what it's like. I already tried using that command to reconfigure, but I don't think I set it to vesa. I assumed that since the drivers are named after their companies that I should choose the "nv" one. I'll try the vesa one instead.

---

### Post by Zzl1xndd on 2007-01-29
> **Muphin Man said:**
> I don't think that I entirely understand what the difference is between Gnome and KDE and Xubuntu is. Aren't they all just different versions of Linux? Or do they build off of Linux OSs like Ubuntu?

They are Desktop environments. This will make a bi g difference in how the desktop looks and works.

the Left is KDE and the right Gnome

---

### Post by Frank Golden on 2007-01-29
> **Muphin Man said:**
> I don't think that I entirely understand what the difference is between Gnome and KDE and Xubuntu is. Aren't they all just different versions of Linux? Or do they build off of Linux OSs like Ubuntu?

I'm trying to try Ubuntu before I install it so that I know what it's like. I already tried using that command to reconfigure, but I don't think I set it to vesa. I assumed that since the drivers are named after their companies that I should choose the "nv" one. I'll try the vesa one instead.
Vesa is a basic driver that usually works when the regular mfg. drivers don't.

---

### Post by Muphin Man on 2007-01-29
Hmm, well I tried that command and using the driver you recommended but when you get to the end of the config, it just puts your cursor on the bottom of the screen expecting you to type a command. What command saves your preferences? Above the blank command space it warns you about overwriting the origional Xserver preferences, so I think it wants you to save.

Anyways, I tried doing startx anyways to see what would happen and it came up with this:

```
(EE) I810 (0): Cannot read V_BIOS
(EE) I810 (0): VBE initializations failed.
(EE) Screen(s) found, but non have a usable configuration.

Fatal Screen error
no screens found
```

Then it gives me space to type another command...

Vicious cycle!

PS I would definately want GNOME if I had to choose between that and KDE. Where do I get the Alternate CD?

---

### Post by dannyboy79 on 2007-04-05
if you're using nano, you need to hit control x, if you made changes then it'll say do you want to save the file, if you click "y", then it'll ask if you want to save the file as the same name, then I just hit enter again. if you're using vi I am not sure as I tried vi once and it was very different from normal text editors but my understanding is that it is very powerful and a great editor I just don't know how to use it.

---

### Post by Mowcius on 2007-04-05
You sound to be having the same problems i have been having apart from your computer sounds much better than mine.

what do you set your screen res to in the graphical ubuntu start menu?

When you were asked to chose the options for the monitor (when you are in the Xserver setup) what did you put?

---

