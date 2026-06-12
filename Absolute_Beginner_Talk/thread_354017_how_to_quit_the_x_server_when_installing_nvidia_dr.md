---
title: "how to quit the x server when installing nvidia driver..."
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-02-05
hello.
just a quick question, which may sound stupid, but ive been trying to install the nvidia linux drivers from the nvidia site, now i finally managed to get the driver to run as far as being told that the xserver was running and needed to not be runing when the driver was installing.
so how do i stop the xserver to install that nvidia driver ?
also when your trying to run something like a driver and it says it needs to be run as root, what exactly does that mean ?
cheers

---

### Post by kinematic on 2007-02-05
> /etc/init.d/gdm stop kills the xserver
> /etc/init.d/gdm start after installation brings it back up....then do > startx to get back to the desktop.
when it asks to be run as root it means you need administrator priviliges....in this case it would be > sudo sh NVIDIA-driver-version.run

---

### Post by newbsaucer on 2007-02-05
The problem I run into here is that when I run>  /etc/init.d/gdm stop  I get to a black screen with a prompt. I assumed this was the command prompt. however I can run string after string of commands and nothing happens. No output strings nothing. It just sits there with the cursor mockingly blinking back at me. I can see what I typed and a return carriage. Thats it. 

I try to type in /etc/init.d/gdm start to go back to the GUI but nothing happens.  I have tried the cntrl-alt-f1 and f7 key combinations as well and nothing happens. Sorry to hijack your thread man I just thought I would kick this in here since I hit the same roadblock.

---

### Post by techno-mole on 2007-02-05
no worries, as it happens ive had the black screen, with nothing but the cursor, the only way ive found to get out of it is to reboot, sorry its not more helpful ?
ps-cheers for the help with the x server thing.

---

### Post by steve.horsley on 2007-02-05
**sudo /etc/init.d/gdm stop** should drop you to a black screen with a login prompt. If not, what happens if you do Ctrl-Alt-F1 from the GUI. This should give you a B&W console while leaving the GUI still there on Ctrl-Alt-F7. Can you log in this way? If so, use **sudo /etc/init.d/gdm stop** and other commands from there.

---

### Post by kevinatkins on 2007-02-05
Yes, the black screen is just your standard terminal login. Type your login name, then your password when requested (nb, when typing password, you won't see any feedback on the screen. that's ok - just type password and hit 'return')

you might find it easier to install the nVidia driver using a package, which i think should be available from the multiverse repository. better still, head over to [www.getautomatix.com/](www.getautomatix.com/) and install Automatix - this will allow you to install all softs of useful stuff not included with the stock distribution, and includes the nVidia driver. 

Whichever method you use to install the driver, you will probably need to edit your X server configuration file by hand (nVidia provides instructions). Post back if you get stuck.

---

### Post by bodhi.zazen on 2007-02-05
Although kinematic and steve.horsley and kevinatkins all have given you good advice, 

the best way to install the nvidia driver is with envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I advise the "beta" driver, it is stable for me and an improvement on the stable driver :p

---

