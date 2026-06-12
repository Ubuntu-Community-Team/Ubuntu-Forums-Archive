---
title: "Problem restarting X Server after NVIDIA"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by PJFan on 2008-02-06
Hi everyone, I'm a total Ubuntu noob, so please bear with me.  I've been trying for several hours to get my GeForce 7200 card working.  I'm now at the point where I have Applications --> System Tools --> NVIDIA Xserver Settings.  I also have the box checked for "NVIDIA accelerated graphics driver" under the Restricted Drivers Tab.

When I click on NVIDIA Xserver Settings, it tells me I need to run nvidia-xconfig as root.  I open a terminal window and type:

sudo nvidia-sconfig

I get:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

I understand that I'm then supposed to restart Xserver.  I use:  sudo /etc/int.d/gdm restart.  Then I see the GUI close itself out and I get a black screen where it appears that the computer is going through several checks.  After the fourth check, it just hangs.  If I use ctrl-alt-F1, I can get a new command prompt asking me to enter my username.  After entering user and password, I type:  sudo /etc/int.d/gdm start and it will restart the GUI, but with reduced display settings.  

I can't seem to get the restart phase of this thing to work correctly.  What am I doing wrong? 

Thanks for any help you can provide.

---

### Post by Presto123 on 2008-02-06
I'll tell you what I honestly THINK...If this is a totally new install, I would reinstall the OS and go at it this way so that you will know how to do it the easy way next time.

1. Reinstall of course
2. Update the OS
3. Go into System/Administration/Software Sources and enable all the repos.
4. Go into Add/Remove, click on All Available Applications in the top right corner and type in Nvidia in the search box. The driver you will want will be "NVidia binary X.Org driver". Click on the box to the left, hit apply and after it installs...
5. Go into Restricted Drivers Manager and enable the Nvidia card
6. Reboot

7. Enjoy


I don't have any experience with the issue you are having. If you wish to go at it as you are now, I am unsure how to guide you from where you are, so, give it some time and someone probably can help.

---

### Post by nikoPSK on 2008-02-06
> **Presto123 said:**
> I'll tell you what I honestly THINK...If this is a totally new install, I would reinstall the OS and go at it this way so that you will know how to do it the easy way next time.

1. Reinstall of course
2. Update the OS
3. Go into System/Administration/Software Sources and enable all the repos.
4. Go into Add/Remove, click on All Available Applications in the top right corner and type in Nvidia in the search box. The driver you will want will be "NVidia binary X.Org driver". Click on the box to the left, hit apply and after it installs...
5. Go into Restricted Drivers Manager and enable the Nvidia card
6. Reboot

7. Enjoy


I don't have any experience with the issue you are having. If you wish to go at it as you are now, I am unsure how to guide you from where you are, so, give it some time and someone probably can help.

please, don't. Try reconfiguring xorg first:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Dr Small on 2008-02-06
Yes, please try reconfiguring X first

---

### Post by nikoPSK on 2008-02-06
> **Dr Small said:**
> Yes, please try reconfiguring X first

Although, I wish I knew that before, when My x broke three times in a row and I just kept reinstalling... :|

---

### Post by PJFan on 2008-02-06
Thanks guys.  I reconfigured x.  Now when I use ctrl-alt- backspace, it brings me back to the GUI.  That part now seems to be working.  However, when I run nvidia-xconfig and then do a ctrl-alt-backspace, it still loads with reduced video settings and still tells me I need to run nvidia-xconfig as root.  Am I missing something?  

Also, after the reconfigure, I can no longer use /etc/int.d/gdm restart.  It says:  *sudo: /etc/int.d/gdm: command not found*

Thanks again for any additional guidance.

---

### Post by nikoPSK on 2008-02-06
> **PJFan said:**
> Thanks guys.  I reconfigured x.  Now when I use ctrl-alt- backspace, it brings me back to the GUI.  That part now seems to be working.  However, when I run nvidia-xconfig and then do a ctrl-alt-backspace, it still loads with reduced video settings and still tells me I need to run nvidia-xconfig as root.  Am I missing something?  

Also, after the reconfigure, I can no longer use /etc/int.d/gdm restart.  It says:  *sudo: /etc/int.d/gdm: command not found*

Thanks again for any additional guidance.

try sudo nvidia-xconfig

---

### Post by PJFan on 2008-02-06
Yes, thanks.  I was using

sudo nvidia-xconfig

That part is working as far as I can tell.  But when I reset the system, the new driver isn't taking effect.  I'm seriously considering a reinstall.  I'm not sure what else to do.

---

### Post by nikoPSK on 2008-02-06
> **PJFan said:**
> Yes, thanks.  I was using

sudo nvidia-xconfig

That part is working as far as I can tell.  But when I reset the system, the new driver isn't taking effect.  I'm seriously considering a reinstall.  I'm not sure what else to do.

I guess you could, since the dpkg didn't go so hot...

---

### Post by Dr Small on 2008-02-06
> **PJFan said:**
> Thanks guys.  I reconfigured x.  Now when I use ctrl-alt- backspace, it brings me back to the GUI.  That part now seems to be working.  However, when I run nvidia-xconfig and then do a ctrl-alt-backspace, it still loads with reduced video settings and still tells me I need to run nvidia-xconfig as root.  Am I missing something?  

Also, after the reconfigure, I can no longer use /etc/int.d/gdm restart.  It says:  *sudo: /etc/int.d/gdm: command not found*

Thanks again for any additional guidance.
That should be:
```
sudo /etc/init.d/gdm start
```

---

### Post by mortuk on 2008-02-07
any luck on this?

i am also having a similar problem. I keep getting a random freeze (gutsy) every so often, and heard that latest nvidia drivers fixed it. anyways have installed, run sudo nvidia-xconfig, then restart and X breaks

the only way I can get back to a GUI is to do
```
sudo dpkg-reconfigure xserver-xorg -phigh
startx
```

as the following doesnt work
```
sudo /etc/init.d/gdm start
```
it attempts to start X 3-4 times and then garbles the screen and I think its saying something about low gfx mode, I cant tell as the screen is offset and really garbled

tried going back to a previous xorg.conf but no joy, help!! :P

---

### Post by PmDematagoda on 2008-02-07
How did you install the latest Nvidia drivers?

Also, try doing this:-

1) Open a modules file for editing using:-
```
nano /etc/default/linux-restricted-modules-common
```

2) Edit the "DISABLED_MODULES" line and make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```

3) Save the file and then check if the GUI works.

---

