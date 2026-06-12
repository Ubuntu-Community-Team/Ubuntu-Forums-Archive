---
title: "Can't fix Xserver"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by marenum on 2008-03-08
I can't get my monitor to stop saying "out of range" after I log in. I have reconfigured the Xserver to my monitor's settings and it hasn't helped. Do I admit defeat and just reinstall the whole system? I really don't want to loose everything but I'm starting to think this is hopeless!:(

---

### Post by kwacka on 2008-03-08
Open a new desktop with ctrl-alt-F2 , login using your username & password and type  'sudo dpkg-reconfigure xserver-xorg' 

Allow this to select your settings.

Now type 'sudo shutdown -r now' to reboot - hopefully you'll be up and running.

---

### Post by unutbu on 2008-03-08
Please post the output to
```

lshw -C display
cat /etc/X11/xorg.conf

```

---

### Post by herbster on 2008-03-08
May want to mention which video card you're using.

---

### Post by marenum on 2008-03-08
My video card is a XFX GeForce 8600GT. 

I can't really post output because I have no idea how to do it using only the command line. I can really only use my mac for the internet right now.

If you tell me what you're looking for in that output I can type it out though. Thanks.

---

### Post by marenum on 2008-03-08
lshw -version     came out

B.02.10

Is that helpful?

---

### Post by herbster on 2008-03-08
Sure you have the Nvidia driver installed?

```
sudo apt-get install nvidia-glx-new
```

---

### Post by unutbu on 2008-03-08
Marenum,
I'm a bit confused by your situation.

1) You say the monitor says "out of range" after logging in. Does that mean you see the BIOS start up screen, the ubuntu logo and orange bar, and the orange login screen? Are you saying the problem only occurs after you log in?

2) When the monitor says "out of range" is it a message superimposed on a normal GNOME desktop, or has the screen gone black, with only that message displayed? What happens if you press CTRL-ALT-F2 as kwacka suggested? Do you get a virtual (text) console where you can log in and get to a command line?

3) Does your monitor have a On-screen menu with an "Information" screen which tells you the resolution, horizontal frequency, vertical frequency and pixel clock? If so, what are they? 

Please note: I've read that trying to operate a monitor at horizontal and/or vertical frequencies that are beyond its specifications can damage the monitor, so I'd try to get to a virtual console by typing CTRL-ALT-F2 right away. I'm surprised you can see a terminal window while the monitor complains "out of range". I thought monitors just went black in this situation...

3) Have you tried booting from the Live CD? What happens then? Do you get a working system or does the monitor still complain about "out of range"?

---

### Post by marenum on 2008-03-09
unutbu,

everything is normal until after I log in. The loading screen shows up, login is normal, but then instead of taking me to my desktop it give me a black screen that says out of range. 

crtl+alt+f2 brings up a command line.

My monitor's resolution:1680x1050  Vertical Refresh Rate: 56 ~ 76 Hz  Horizontal Frequency: 31 ~ 81kHz

I'm currently burning a new live cd because i gave my old one to a friend... I'm not sure how to boot from it though, thanks.

---

### Post by herbster on 2008-03-09
It's almost definitely an issue with your /etc/X11/xorg.conf. If you can type out the Device (nvidia) Monitor and Screen sections we may be able to diagnose it.

---

### Post by marenum on 2008-03-09
How can I get that information?

---

### Post by herbster on 2008-03-09
Boot in, get to login screen and hit CTRL+ALT+F2 (or F3, F4, F5, F6 :)) and do:

```
sudo nano /etc/X11/xorg.conf
```

Scroll down to those sections and type back here.

---

### Post by unutbu on 2008-03-09
Get thee to a command line.
Type
```

cat /etc/X11/xorg.conf | less

```

The command 'cat' tells the machine to start spitting out the contents of the file '/etc/X11/xorg.conf'. The pipe symbol '|' tells the machine that the text being spewed out by cat should be piped to another program, 'less'. 'less' is a pager program -- it takes text and breaks it into page-sized blocks. Pressing space scrolls you down one page. Pressing 'b' sends you back one page. The up/down arrow keys lets to move one line at a time.

Look for any paragraph that begins with
```

Section "Monitor"

```
or
```

Section "Device"

```
or
```

Section "Screen"

```

Post each of these paragraphs (everything you see until 'EndSection').

---

### Post by marenum on 2008-03-09
sudo nano /etc/X11/xorg.conf  yielded a menu but I couldn't find any text. 

cat /etc/X11/xorg.conf | less   gave me  "/etc/X11/xorg.conf: No such file or directory 

I'm wondering if I somehow deleted my xorg.conf???

---

### Post by herbster on 2008-03-09
There you go. You need to run kwacka's command earlier in the thread:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by marenum on 2008-03-09
I went through the whole process, but I'm still getting the out of range error. The problem seems to be with the display.

---

### Post by unutbu on 2008-03-09
Try
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

If you wish to confirm that the /etc/X11/xorg.conf file exists, 
do 
```

ls /etc/X11/xorg.conf

```
To which the machine should reply
```

/etc/X11/xorg.conf

```

---

### Post by marenum on 2008-03-10
ls /etc/X11/xorg.conf  comes back as "ls /etc/X11/xorg.conf: No such file or directory"

Can I boot from the cd to change the /etc/X11/xorg.conf??? If I choose to reinstall ubuntu will that solve the problem or simply carry it over into the new installation?

---

### Post by herbster on 2008-03-10
Have you run the command unutbu has posted? the dpkg-reconfigure command?

---

