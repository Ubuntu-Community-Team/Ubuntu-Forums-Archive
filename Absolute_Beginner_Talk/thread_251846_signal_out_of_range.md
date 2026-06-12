---
title: "signal out of range"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Buttons Malone on 2006-09-06
ok, im pretty new too this linux, really want to learn, tried suse 9 for a while, didnt like it, but now i downloaded ubuntu, to try it out, and when i start my computer up, it goes to the setup scree n, and i click on the start or install ubuntu, and it runs through the little setup screen, checking everything or whatever its supposed to do. I think everything is going fine until it finishes loading then when it goes to start, my monitor automatically goes out of signal range and i've tried changing my settings in windows, and still nothing, do I need to just update my video driver, or am i not doing something i am suppossed to? Please Help. I have a geforce fx 5200 agp with an athlon xp 2000+(1.67Mhz), 1 gb ram, you got the idea i hope. so please help? thank you anyone and everyone who can help me....

---

### Post by bodhi.zazen on 2006-09-06
Can you get to the CLI (Command Line Interface) or are you stuck at a black terminal?

To get to a CLI Ctrl-alt-F1

Should see a log in prompt.

If you can get to the CLI you will have to reconfigure X:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then type:
```
sudo gdm
```

Only problem: I do not know the user name or password of the desktop CD..... LOL

---

### Post by Russty of Oz on 2006-09-06
I have had the same problem in the past.  I too am using a fx 5200 but it is not the card that is the problem, it seems to be with the monitor.  I assume you are using an LCD screen?  When I boot into Ubuntu, I will ALWAYS get the signal out of range message while Ubuntu boots up, but when it has finished the screen comes back on and the login screen appears.  This has only been happening since Dapper, Breezy didn't have this problem with my screen.  And it doesn't happen with a friends laptop, so it is only some LCD screens that do this. So you just need to be patient while booting.  

Now, if yours is staying on signal out of range, reboot into windows, then what I found is that when you boot the Live CD, go into the screen resolution settings BEFORE YOU INSTALL UBUNTU.  For example, my resolution is 1280x1024 but it is at 75Hz, now all I have to do is change the 75Hz to 60Hz and then click the install icon.  Then when it installs it "should" be OK.  Also, if that does work for you, then after installing the nvidia drivers or anything else to do with your graphics, always check the resolution settings BEFORE you reboot or shutdown!  I have been caught out quite a few times by the settings changing.

Good Luck :) 

Russty.

---

### Post by Buttons Malone on 2006-09-07
thanks for the input, i tried using the codes and it told me gdm is already running and just aborted, then i tried waiting patiently (30 min) and still nothing neither of those things worked. i also checked my refresh rate and it was at 60hz. so i am lost and confused. if anyone has any other ideas i would greatly appreciate it. Thank You.

---

### Post by bodhi.zazen on 2006-09-07
> **Buttons Malone said:**
> thanks for the input, i tried using the codes and it told me gdm is already running and just aborted, then i tried waiting patiently (30 min) and still nothing neither of those things worked. i also checked my refresh rate and it was at 60hz. so i am lost and confused. if anyone has any other ideas i would greatly appreciate it. Thank You.

If you re-configured X without errors
```
sudo /etc/rc.d/gdm stop
sudo gdm
```

If you got error messages with configuration of X, re-post.

---

### Post by Buttons Malone on 2006-09-08
well this is my last shot at this live cd. before i give up on it. so here is the situation. i typed in the x reconfiguration and this it what it tells me: xserver-xorg postinst warning: overwriting possibly customised configuration file; backup in /etc/x11/xorg conf.20060908093651 
 then i typed in sudo gdm and it says it is already running: aborting
 then i typed in sudo /etc/rc.d/gdm stop and it says command not found. so if anyone can help me i would greatly appreciate it, before i give up on this cd. Thank You. and Please Help. at the bootup screen should i be choosing to start or install ubuntu or should i try it in safe graphics mode.

---

