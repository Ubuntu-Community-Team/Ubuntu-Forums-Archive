---
title: "Need help - Nvidia GLX"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Frost_44 on 2007-08-05
I've tried installing this on Ubuntu various times, and none of them have ever worked.  I keep on coming up with an error, saying something about X configurations and I cannot access my screens and I stay in a black command screen.  I need this driver, however, to have any sort of desktop effects and to boost my resolution.

Can anyone help me with this?  All I'm doing is installing the newest software, and running the command line as noted in the description.  I've tried both restarting and restarting X.  It never works...so I'm wondering if there are any extra steps that I must take.

---

### Post by skymera on 2007-08-05
if you neeed correct nvidia drivers, i found this script,i havent tested but i hope to in a few days.
attached:

---

### Post by dougfractal on 2007-08-05
Please provide more info

lspci -nn
lsb_release -d
uname -r
cat /etc/X11/xorg.conf
grep "(EE)" /var/log/Xorg.0.log.old    # your failed attempt


Testing X  (I'm testing this please feedback)

Save your new xorg.conf in your home folder as ~/xorg.conf.new

```
chmod u+s /usr/X11R6/bin/Xorg    #  add sticky bit to Xorg
```

```
[ctrl+alt+f1]
startx -- :1 -config ./xorg.conf.new
 
#  potential crash if hotswap nv to nvidia, so restart X between goes.
[ctrl+alt+F7]   normal login
[ctrl+alt+F9]   new X session  (check F8)

[ctrl+alt+f2]
DISPLAY=:1 xterm &    # start xterm in case gnome fails
killall startx
sudo /etc/init.d/dgm restart    #  potential crash if hotswap nv to nvidia, so restart X

```
logs for is test at /var/log/Xorg.1.log

If X is good then 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
cd ~
sudo cp ./xorg.conf.new  /etc/X11/xorg.conf
sudo /etc/init.d/dgm restart
```

---

### Post by alienexplorers on 2007-08-05
To load the nvidia drivers try the ENVY script at > [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html).

Just follow the prompts and you should be good to go.

---

### Post by skymera on 2007-08-05
i hosted the envy script on first reply

---

### Post by alienexplorers on 2007-08-05
I know! You just should have given the location of the ENVY script so he could read about it before using it.  I hate it when someone says do so and so and gives no place to get information about the command.

---

### Post by Frost_44 on 2007-08-05
For some reason it did not work...I dled Envy and allowed it to restart my computer.  The same pop up dialogue appeared (all of this is after I reinstalled Ubuntu).  So here I am on my 4th or 5th try with nothing to show for it.  Is there something I must do prior to installing and executing Envy?

---

### Post by alienexplorers on 2007-08-05
I just loaded Ubuntu and ran the ENVY script and it loaded my drivers (glx) with no problems.  I did not have to do anything before hand.

Can you post your exact video card and the output of lspci.

Can you also post your xorg.conf file (cat /etc/X11/xorg.conf)

---

### Post by Frost_44 on 2007-08-05
I did it one more time...and it failed.  However, instead of immediately reinstalling...I tried to use envy again in that dark screen (sorry, I dont know the name).  When installing it through that, it finally worked!  Thank you everyone for all your help, it was GREATLY appreciated.

---

