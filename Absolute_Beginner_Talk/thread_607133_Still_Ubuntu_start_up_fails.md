---
title: "Still Ubuntu start up fails"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by binzer on 2007-11-08
Hi,
I've a problem with ubuntu startup. When I startup ubuntu, it doesn't show the login screen, rather the following lines appear:
* starting anac(h)ronistic cron an acron [ok]
* starting deferred excution scheduler atd [ok]
* starting periodic command schedulear crond [ok]
*checking battery state... [ok]
* Running local boot scripts(/etc/rc.local) [ok]
-(a blinking curser)

I rebooted ubuntu manytimes, but the problem persists. Please tell me how I can fix it. I have urgent documents there.

thanks

---

### Post by jfinkels on 2007-11-09
You are looking at the text output from the bootup process. This means that your X server, the program that's in charge of the graphical windowing system, has failed to start for some reason. You are looking at a virtual terminal. You can try to access the graphical display by pressing <Ctrl>+<Alt>+<F7>. If nothing comes up, go back to a virtual terminal by pressing <Ctrl>+<Alt>+[<F1> | <F2> | ... | <F6> ]. Login with your username and password. Type the following:```
startx
```If you get an error, post it back here.

---

### Post by binzer on 2007-11-09
I used <Ctrl>+ <Alt>+<F7> to get the terminal. When I put in the command "startx" it displays "Fatal Server Error" and "No Screens found". I feel that the programe  fails to bootup graphics.

Plz any help? I am now in the terminal and hope it can be fixed!

---

### Post by jfinkels on 2007-11-11
> **binzer said:**
> I used <Ctrl>+ <Alt>+<F7> to get the terminal. When I put in the command "startx" it displays "Fatal Server Error" and "No Screens found". I feel that the programe  fails to bootup graphics.

Plz any help? I am now in the terminal and hope it can be fixed!

At the terminal, type the following command:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will tell Ubuntu to reconfigure your X server for your particular hardware. Do you know what kind of video card you have?

If you have urgent documents, you can boot into the live CD environment and access the data on your disk from there.

---

### Post by yabe on 2007-11-12
hi

i've got the same **** problem:
during the boot the notebook gets stuck at "running local scripts [ok]"
"startx" works, the sudo blabla thing too...but then? 

please help!

(Packard Bell Easy Note E6300 Notebook)

---

### Post by jfinkels on 2007-11-12
Typing startx will start the graphical windowing system. Isn't that what you want? If you want the graphical login manager, you can type:```
sudo /etc/init.d/gdm start
``` and see if that works.

Doing "sudo dpkg-reconfigure -phigh xserver-xorg" automatically reconfigures your X server as Ubuntu sees fit (it should automatically recognize your hardware and determine the best configuration). If the graphical window system still does not work, post back here with the make and model of your video card, and the output from this command:```
cat /etc/X11/xorg.conf
```

---

### Post by hapreet on 2007-11-13
> **jfinkels said:**
> At the terminal, type the following command:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will tell Ubuntu to reconfigure your X server for your particular hardware. Do you know what kind of video card you have?

Sorry to hijack your thread but :KS[COLOR="Red"]jfinkels THANK YOU SO MUCH.[/COLOR]:KS

I am an absolute beginner at ubuntu. Having never used anything but windows my whole life i decided to dive into the deep end and configure ubuntu to load off of an external hard drive. After encountering a variety of problems i managed to make it work when connected to a different computer, but not mine. When i got around this problem through configuring my bios the next hurdle was ubuntu always stopping at:

```

* Running local boot scripts(/etc/rc.local) [ok]
-(a blinking curser)
```

and while this was happening, the screen would flash on and off a few times. Indicating that it was probably a graphics problem. Unfortunately before i realised this i spent time trying to correct tty1...tty6 files as suggested in this [[COLOR="Blue"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=424078&highlight=feisty+boot+problem").

But after no luck i found this thread and simply  opening a virtual terminal (by pressing <Alt> + <F1>) and typing in your code it worked like a charm (the first time it started in black and white then went to ubuntu but i have never encountered that since).

Obviously as you have suggested the installation must have been configured to use the graphical card of my other computer which was different to mine.

Just a word of warning make sure you note there are no spaces in **dkpg-reconfigure** and **xserver-xorg**. (if not, you will encounter error messages about conflicting commands or something. Even when successful there will be a message about some backup but thats a good thing.)

---

### Post by jfinkels on 2007-11-13
> **hapreet said:**
> 
But after no luck i found this thread and simply  opening a virtual terminal (by pressing <Alt> + <F1>) and typing in your code it worked like a charm
X server configuration problems come up a lot when configuring a Linux desktop system on a new computer. This command is sort of a panacea, letting you start with a fresh configuration file, automatically determined from your particular hardware. As with most programs, you can view and edit the configuration file explicitly, and the configuration file for X is located at '/etc/X11/xorg.conf' (make a backup before editing!).

---

