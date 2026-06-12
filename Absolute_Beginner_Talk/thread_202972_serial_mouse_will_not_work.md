---
title: "serial mouse will not work"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by h2oclick on 2006-06-24
I am using the live cd only becuase i cannot navigate using the serial mouse to the install icon. 

i have tryed going into console and i did something that asked me if it was a ps/2 mouse or an explorer 1.... i tryed both but still no luck...

i only have 1 serial port... its a pentium2 333mhz... piece of crap but if i get mouse to work on it it'll be used for good use once again :P

thanks for reading, hopefuly you can help


Franc

---

### Post by GTvulse on 2006-06-24
On a console do:

sudo modprobe -v sermouse

then check the output with "dmesg | tail" to find out what device file was assigned to it. Nevertheless, you can always point X to /dev/input/mice and set it up as serial in xorg.conf (using "sudo dpkg-reconfigure xserver-xorg").

It is strange that udev doesn't detect the mouse if plugged when you cold start the machine, but you can work around that replacing psmouse by sermouse in /etc/modules with the help of your favorite text editor. Hint: if using a graphical text editor, say mousepad (I wouldn't use anything different to xubuntu with a p2), use "gksudo mousepad", else you'll screwup .ICEauthority ownership tags and will come back whining for help trying to get back into your account. :-) If you use a console editor you can use sudo, it is perfectly safe in a console.

---

### Post by IYY on 2006-06-24
I also have a serial mouse, and just yesterday I got it working. Ctrl+Alt+F1 to go to console mode. You need to edit the file /etc/X11/xorg.conf and go to the mouse section. Change the device to

/dev/ttyS0 (it might be ttyS1 or 2, depending on your serial port). 

Change the protocol to "Microsoft"

and then restart the X server.

If you need more detailed instructions, just ask.

---

### Post by h2oclick on 2006-06-24
i am complete nuub guyys... i dont really understyand that last post

---

### Post by IYY on 2006-06-24
Alright, here it is in more detail:

To go to console mode, press the keys **Ctrl+Alt+F1**. 

Type the following:

```
sudo nano /etc/X11/xorg.conf
```

Nano is a text editor, and xorg.conf is a plain text file that contains various configuration settings for the graphics in Ubuntu, including monitor, video card, mouse and keyboard.

Go down to the mouse section, and edit the Device and Protocol lines so that they read:

```
Option "Device" "/dev/ttyS0"
Option "Protocol" "Microsoft"
```

(if you later see that the mouse still doesn't work, try ttyS1 or 2, and also try the protocol "Auto").

Save the file (Ctrl+O) and exit the text editor (Ctrl+X).

**Ctrl+Alt+F7** to go back to the graphical mode. **Ctrl+Alt+Backspace** to kill the graphics server. It should come up again, and the mouse should work.

---

### Post by h2oclick on 2006-06-24
hehe... how do i save and exit....

---

### Post by h2oclick on 2006-06-24
Nevermind

---

### Post by h2oclick on 2006-06-24
thanks a lot guys

---

### Post by h2oclick on 2006-06-24
they should have that explanation on the ubuntu FAQ. it took 2 seconds and it was a really easy fix.

---

### Post by IYY on 2006-06-24
I agree, but it's a very rare issue nowdays. It's nearly impossible to find a serial mouse anywhere, and even Pentium 133 machines usually have PS/2 ports. Of course, there are rare exceptions like us.

---

### Post by redcharlie on 2006-06-25
Yes, this fixed the problem!

simply changing the device from "/dev/input/mice" to "/dev/ttyS0" and the protocol from "ExplorerPS/2" to "Microsoft", hitting ctl-alt-backspace, and I'm mousing again!

Many thanx!

One of the great things about linux is that you can run it on old hardware.  I'm trying to get a fileserver/webserver running on an Epox MVP3c-M/AMD K6500.  No ps2 or usb anything.

I agree with h2oclick, this tip should be in the FAQ.  Even though I don't really need an xserver for this machine (besides vnc) it's good to have a mouse should you need it.

---

### Post by redcharlie on 2006-07-01
addendum:
I've got a MS wheelmouse, so changing the protocol from "Microsoft" to "IntelliMouse" in xorg.cong got the wheel/3rd button working.

---

### Post by SoftGround on 2006-07-03
Just had the same problem when demoing the Live CD on a relatives old Win98 computer.  Mouse had died, so old Win95 serial mouse had been pressed into service.

This information needs to be easily available as people are interested in Ubuntu to put it on old hardware.  Would be even better if nuuby people didn't need to go to the console straight away, most would just think it didn't work and give up.:( 

Thanks for the info though

SG

---

### Post by rodrigo666 on 2007-01-04
I just want to say thanks, this thread really helped me.

---

