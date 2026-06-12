---
title: "Enable 3D acceleration"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by catsmasher on 2007-03-01
Hello All,
 First post and total n00b to Ubuntu. I have updated the proper packages (I think) but I cannot enable 3D rendering. I have an nVidia 7950GT gpu. Please help me. Thanks.

---

### Post by igknighted on 2007-03-01
If you are using the standard kernel (and you are if you didnt explicitly change it) try and install a package called nvidia-glx.  If you have already done this, run the command nvidia-xconfig in a terminal.  Then hit ctrl+alt+backspc to restart X and go back to the login screen.  If you see an nvidia splash screen after your screen goes blank, it is working.

EDIT: The nvidia-xconfig may need to be run with sudo (ie, sudo nvidia-xconfig) in order to write to the system files.

---

### Post by catsmasher on 2007-03-01
It says command not found.  This is very frustrating.

---

### Post by ickyfeet on 2007-03-01
Download Envy from [here]("http://albertomilone.com/nvidia_scripts1.html") and follow the instructions.  It's very easy to use and very straight forward.  It takes care of all the packages and whatnot.

---

### Post by catsmasher on 2007-03-01
Okay, I can QUICKLY see that Ubuntu and Linux in general is much, MUCH to stinking complicated to use as an everday OS. I cannot even find ENVY after I installed it. I guess that's why we pay hundreds of dollars for MS......it actually works.
There is no nvidia-xconfig to be found. I still cannot enable 3D rendering.

---

### Post by click4851 on 2007-03-01
if your still interested, you could try Automatix, its available for download using synaptic. I believe the nvidia driver is one of the many things it can install for you. Ubuntu isn't easy, I wouldn't say hard, but different.

---

### Post by igknighted on 2007-03-01
> **catsmasher said:**
> Okay, I can QUICKLY see that Ubuntu and Linux in general is much, MUCH to stinking complicated to use as an everday OS. I cannot even find ENVY after I installed it. I guess that's why we pay hundreds of dollars for MS......it actually works.
There is no nvidia-xconfig to be found. I still cannot enable 3D rendering.

Perhaps.  If you had ever tried to install windows from scratch you might disagree.  Open synaptic and install the package called 'nvidia-glx'.  This is the driver.  Once it installs (or if it has already been installed), open a terminal and type: "gksudo gedit /etc/X11/xorg.conf" (without the quotes).  Find a section that looks roughly like this:
```
Section "Device"
    Identifier  "NVIDIA 6600 GT"
    Driver      "nv"
    BusID      "1:0:0"
EndSection
```

Your will have a different vid card (maybe a bus ID, who knows what else).  The important thing is it will say Section "Device".  There will be a line that says Driver "nv".  Change the "nv" to "nvidia".  Then ctrl+alt+backspc to restart X and it should be good to go.  If it kills your X, you didn't install the drivers beforehand.  If this happens, type: 'sudo nano /etc/X11/xorg.conf' to open a console text editor, edit that same line back to "nv" and then reboot.  Don't change anything else in there, as it could wreck your system.

---

### Post by catsmasher on 2007-03-01
I get an error that says GNOMEUI-warning: while connecting to session manager, the application was rejected.

---

### Post by igknighted on 2007-03-01
> **catsmasher said:**
> I get an error that says GNOMEUI-warning: while connecting to session manager, the application was rejected.

What command brought up this warning?

---

### Post by catsmasher on 2007-03-01
> **igknighted said:**
> What command brought up this warning?

This one "gksudo gedit /etc/X11/xorg.conf"

---

### Post by igknighted on 2007-03-01
Oh, thats just a debug output.  It's normal.  Did the text editor open so you could edit the file?  If it didn't, try "sudo nano /etc/X11/xorg.conf" to open a simple editor in the terminal.

---

### Post by jml on 2007-03-01
I don't know what people told you what to expect with Ubuntu, but it is definitely not the same as Windows.  That's why most of us use it.  If you are willing to take the time to learn the a bit about it, I think you will be rewarded by a pretty satisfying experience.  Getting 3D graphics working can be a challenge.  But if you really want to learn something, there is no need to vent, just ask another question.  If that is not acceptable to you, then maybe you are right and Windows is a better choice for you.

---

### Post by catsmasher on 2007-03-01
I reinstalled Ubuntu as I had obviously messed things up good somewhere. I then did all the updates. Then I used Synaptic to install the nvidia drivers. I followed igknighteds suggestion. Afterward I opened a terminal and typed: "glxinfo|grep rendering" and it confirmed direct rendering was enabled. 
Thanks for the help. Got a bit frustrated, got used to windows simplicity. Haven't done much command line stuff in years. 
It'll take time to get used to, I'm sure it will grow on me, once I learn the ins and outs.

---

### Post by catsmasher on 2007-03-02
One more question.....or maybe two. Is there any way to access settings for the graphics card? Also, I tried wine to install a windows based program. It showed errors in the terminal, but seemed to install fine. However, I cannot find the program....???? Is there a good comprehensive tutorial on installing and using Wine? I did a search, but it seems there are things that I need prior to installing Wine, which are referred to rather vaguely.

---

### Post by jolger on 2007-03-06
wine is used to emulate windoze programs, if you succesfully installed something on wine it will be placed in ~/.wine/drive_c/program files (something like that, (i think, but am not sure, the ~ stands for /home/user :P) the .wine is a hidden directory) go there and look for your program, then you can run it using:

> wine "application"

replace "application" with the program you installed.

also you should check out the wine config

> winecfg

where you can choose wether to emulate a whole desktop or not (if yes, note that theres no task bar ;)).

if you're experiencing sound problems you should check the "audio" tab there, and select the oss driver thingy...

if you're still having sound problems i dont know what to do :P

[COLOR="Red"]NOTE:[/COLOR] make sure that there is no other sound driver selected than the OSS one.

the desktop emulating option is found in the "graphics" tab or something like that...

/jolger

---

### Post by old_geekster on 2007-03-06
> **catsmasher said:**
> Okay, I can QUICKLY see that Ubuntu and Linux in general is much, MUCH to stinking complicated to use as an everday OS. I cannot even find ENVY after I installed it. I guess that's why we pay hundreds of dollars for MS......it actually works.
There is no nvidia-xconfig to be found. I still cannot enable 3D rendering.
Not to be rude or condescending, but it definitely takes an attitude of optimism to learn Linux or anything new.  I am not saying it is easy, but patience is a must.  I have no doubt that you didn't learn Windows over-night.  We forget this, however.

Here are some links that I feel will help you, if you are determined to use Linux/Ubuntu in particular:

[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers)

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Hopefully, these will help you get started on the right foot.

Remember the old saying, "You can't teach an old dog new tricks"?  Well, I'm here to tell you this is not true.

I am 61 years old.  I have only been using Edgy for about three weeks.  Has it been easy? In a word "NO"!:confused:  Actually, I have reinstalled it 11 or 12 times.  However, I want to use it and I will learn.:) 

Have patience and you will be using it with ease in no time at all.

Good luck.

p.s.  I have learned to over-clock my rig in the past year, also.

---

