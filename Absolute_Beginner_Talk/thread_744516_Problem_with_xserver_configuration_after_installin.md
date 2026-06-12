---
title: "Problem with xserver configuration after installing NVIDIA Drivers from ubuntu."
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by lase on 2008-04-03
Okay, I've followed the steps up to the point where I do dpkg-reconfigure xserver-xorg.

I get through most of the configuration until it comes to the bit selection, I select 24 bits and this is what happens

```
xserver xorg postinst warning: overwriting possibly custom-configured file
```


What should I do <.<

Help needed ASAP XD

---

### Post by bodhi.zazen on 2008-04-03
That is not really a problem or error, just notification the the command worked and wrote a new xorg.conf

log out and at the log-in screen re-start X with ctrl-alt-backspace

FYI, you can also use nvidia settings :

```
gksu nvidia-settings
```

If you like the changes, click the save button.

---

### Post by lase on 2008-04-03
Okay,

I can't log out to the login screen because XServer fails to start after installing the drivers, therefore I only have access to the terminal....

When I try to press control alt backspace, nothing happens.

I get an error when trying to use gksu nvidia-settings saying something about GTK display and not being able to set it.


Any ideas?

---

### Post by lase on 2008-04-03
A quick note, it's referring to theres no usable screen configured.......

---

### Post by bodhi.zazen on 2008-04-03
Ouch, sounds like the configuration did not work.

Re-run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

(The -phigh flag selects defaults for most everything)

And try restarting X with

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

If that fails, you can try 

```
sudo nvidia-xconfig
```

And again, re-start X

If that fails, go back to dpkg-reconfigure -phigh xserver-xorg and this time select teh vesa driver.

Again, re-start X

nvidia-settings will not run without X (it will run with the vesa driver)

---

### Post by lase on 2008-04-03
:(

Still not working, the sudo nvidia-xconfig command only makes a back up of the xorg.conf....?

As far as the sudo dpkg-reconfigure -phigh xserver-xorg, it does the postinst warning after I select the display size :(

Any more ideas?

I do know it should work because I've had it configured before but I forget how I went about it XD

---

### Post by bodhi.zazen on 2008-04-03
Unless those commands print an error message the re-write or re-configure X. Those "warnings" and "back-up" messages are not errors or failures.

After running the commands did you try to re-start X ?

Again, if all else fails go with the vesa driver and use nvidia-settings from within X

---

### Post by forrestcupp on 2008-04-03
Boot to your recovery console and type
```
dpkg-reconfigure xserver-xorg
```
without the '-phigh' (In recovery mode, you're root, so you don't need sudo).  This will allow you to go through the steps and choose the **Vesa** drivers.  Then when you're done with that, type
```
sudo apt-get --purge remove nvidia*
```
To remove everything that has to do with nvidia so you can start with a clean slate.  Then to exit root and get to your desktop, type
```
exit
```

When you get to your desktop, either install the nvidia drivers by using System->Administration->Restricted Drivers Manager, or if that doesn't work, install [Envy](http://www.albertomilone.com/nvidia_scripts1.html) and let it automatically download and install the latest drivers for you.

From then on, use **nvidia-settings** to set your video settings.

---

### Post by lase on 2008-04-03
It's STILL failing to start x server :(

Any ideas?

I can't access ANY GUI.

NOTE: I'm using the VESA Drivers.

IT's STILL FAILING TO START X SERVER...

---

### Post by bodhi.zazen on 2008-04-03
what is the error message you get when you enter the command 

```
X
```

That should start a grey screen with a large black X that moves with the mouse. Exit with Ctrl-Alt-Backspace and post any errors here.

---

### Post by lase on 2008-04-03
I just looked at the error log, the new problems lies in the mouse...

Its sayin theres no Core Pointer...

How can I fix that?

---

### Post by lase on 2008-04-03
Okay, I got to the point where I can look at the gray screen with the mouse cursor,

One problem, mouse doesn't move and it doesn't start up any further :(

I'm using a USB mouse so what type of mouse should I select?

---

### Post by bodhi.zazen on 2008-04-03
Do you have a replacement mouse or can you confirm that the mouse is working (test it with another operating system, check for loose of frayed connections / cables).

---

### Post by lase on 2008-04-03
Yes, It works, I just don't know what setting to use in reconfigure xserver-xorg for the USB mouse.

---

### Post by bodhi.zazen on 2008-04-03
Well, that gest back to the -phigh flag

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Will select the standard default for your mouse. If that fails, you will have to manually try several options ...

---

### Post by lase on 2008-04-03
YAY!

MOUSE WORKS!!! :D :D :D

Okay, I'll install Envy tomorrow and get going from there :D

---

### Post by jecker on 2008-04-09
Please post the /var/log/Xorg.0.log log..

---

### Post by bodhi.zazen on 2008-04-09
> **lase said:**
> YAY!

MOUSE WORKS!!! :D :D :D

Okay, I'll install Envy tomorrow and get going from there :D

Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help ...

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

