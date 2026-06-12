---
title: "Need alittle help..."
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by linux-loser on 2007-10-16
sorry if this is the wrong place in the forums for this post but im completely new to linux, ubuntu and this forum so i dont really know it yet.   ive also posted this in 2 other places on the forum, hope thats ok...

im haveing troubles updating ubuntu fiesty 7.04 64 bit. my system is: 
3800+ amd 64
8600GT graphics card ( i know now that its unsupported, ill explain)
1GB RAM

i got the os up and running, fully installed. I installed envy for my graphics card (far as i know thats the only stable way to get my 8600 gt to work). set my resolution to 1680x1050. saved the nvidia settings and restarted the system as it asked. for some reason or another my monitor turns off for about 2 mins during the boot up process. when the monitor turns back on the os starts up right after. the problem comes now. the os starts up. and i hit update, to get the system fully updated was 115 updates to be installed. i installed them and restarted the computer, but now the monitor is off and has been for about an hour. 

is it supposed to do that? my big problem is i cant see if its doing anything, if its loading or asking for my password or what. or maybe its not doing anything at all and something is wrong i dont know. 

please help, this is the 4th time ive tried, but this is the logest ive let it sit, just hoping that its loading the new updated settings and will come back to life soon but no way for me to know. 

sorry for the long message, any help would be great. 

thanks for your time.

---

### Post by PmDematagoda on 2007-10-16
Start up Ubuntu in Recovery Mode and see what the error is, if there isn't any error try this command:-

```
startx
```

If you don't get a GUI, press Alt+F2 to bring you back to the terminal where you can see any errors trying to start it, post those errors if there are any.

---

### Post by Seisen on 2007-10-16
If it updated your kernel most likely you will have to reinstall the Nvidia drivers to get X to work again.

---

### Post by PmDematagoda on 2007-10-16
> **Seisen said:**
> If it updated your kernel most likely you will have to reinstall the Nvidia drivers to get X to work again.

Yep, that is what my suspicions are, but it is better if we clarify if it is indeed X-server that is having the problem.

---

### Post by linux-loser on 2007-10-16
> **PmDematagoda said:**
> Start up Ubuntu in Recovery Mode and see what the error is, if there isn't any error try this command:-

```
startx
```

If you don't get a GUI, press Alt+F2 to bring you back to the terminal where you can see any errors trying to start it, post those errors if there are any.

im sorry i dont how to start the recovery mode.  do i use the disk for that?

---

### Post by twiceasworn on 2007-10-16
To boot into recovery mode hit ESC as the computer is booting up, even if you can't see anything, just hit ESC until the Grub menu comes up.  You will see some entries for kernels and one will have (recovery mode) next to it.  This will boot you to single use mode, so you will have a root prompt.  Once you get to a terminal I would check /var/log and check Xorg.0.log and see why X isn't starting up.  I would also check /var/log/messages.  Like people have said previously, you will probably need to reinstall the nvidia driver.

---

### Post by PmDematagoda on 2007-10-16
No, it is found in the boot loader, when you start your computer up, you get a menu where you can select Ubuntu, Ubuntu(Recovery Mode) and the Memory Test, select the Ubuntu(Recovery Mode) option and start it.

---

### Post by twiceasworn on 2007-10-16
> **PmDematagoda said:**
> No, it is found in the boot loader, when you start your computer up, you get a menu where you can select Ubuntu, Ubuntu(Recovery Mode) and the Memory Test, select the Ubuntu(Recovery Mode) option and start it.

Well he says he can't see anything while the computer is booting, so the boot loader probably isn't coming up.  Not to mention if Ubuntu is the only thing on the box, there is no boot loader it just auto boots, or tries to at least.

---

### Post by PmDematagoda on 2007-10-16
> **twiceasworn said:**
> Well he says he can't see anything while the computer is booting, so the boot loader probably isn't coming up.  Not to mention if Ubuntu is the only thing on the box, there is no boot loader it just auto boots, or tries to at least.

Really? Thanks for the heads up twiceasworn:).

---

### Post by linux-loser on 2007-10-16
ok i tried 
/var/log and it said "bash: /var/log: is a directory

xorg.o.log "command not found"
i tried with a zero and the letter o came up with command not found for both

/var/log/messages "permission denied"

i havent tried startx just yet.  going to try it now.

---

### Post by twiceasworn on 2007-10-16
What you need to do is this.  Navigate to the log directory with 

```
cd /var/log
```

Now you want to parse the log so you can browse through it.  Most likely you are only interested in the last lines of it, since those are the most recent entries.  Typically I use tail for this.  Tail spits out the last part of a file to the console so you can read it.  I typically do a 
```

tail -n20 messages
```

The -n20 gives you the last 20 lines, if you want to view more, up the number.

Do the same thing for the Xorg.0.log.

Also, if you want to try and have xorg reconfigure itself automatically you can do a 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Or if you want to answer all the questions it has, leave out the -phigh.

---

### Post by linux-loser on 2007-10-16
ok i tried startx and it pretty much told me what you guys were thinking i think.  

fatal: could not open '/lib/modules/2.6.20-16-generic/volatile/nvidia.ko': no such file or directory

(EE)Nvidia(0): failed to load the nvidia kernal module!
(EE)Nvidia(0): ***aborting***
(EE)screen(s) found, but none have usable configuration

no screens found fatal IO error 104

so i guess the question is now how do i get back to Envy to reinstall my nvidia drivers?

oh also looking to the future, if i wanted to get a KDE kernal like Kubuntu would i have to do all this again?

---

### Post by twiceasworn on 2007-10-16
I am not sure if this will work for a nvidia card, but this happened to me with my ATI card and I fixed it by doing this.

```
sudo dpkg-reconfigure xserver-xorg
```

When it asks you to pick a driver, pick the vesa driver.

Obviously this driver is not what you want to use, but it will allow you to boot to a GUI so you can reinstall the correct nvidia driver.

---

### Post by linux-loser on 2007-10-16
ok, i picked the versa driver and chose my resolution 1680x1050 (that will work with the versa driver or should i go smaller?)

but now im stuck at the resolution screen,  it wants me to type something in.  what to do?

---

### Post by twiceasworn on 2007-10-16
Well I know for a fact that 1280 X 1024 works, so try that.  Like i said, this will only be used for maybe 5 minutes until you can get the nvidia driver installed.  Also, if you don't know what to put, just hit enter.

---

### Post by linux-loser on 2007-10-16
ok i went through the entire configuration but again its asking about backing a fileup.

says "xserver-xorg postinst warning: overwriting  possibly-customised configuration file; backup in /etc/x11/xorg.conf.20071016124041"


what do i put in?  its not letting me move on from here.

---

### Post by twiceasworn on 2007-10-16
If you hit enter it should just finish it up.  Then you can try to start gdm by doing

```
sudo /etc/init.d/gdm restart
```

And hope it works.

---

### Post by linux-loser on 2007-10-16
yes!!! thank you thank you thank you.

it works, i didnt have to start all over again.  you are the best!

---

