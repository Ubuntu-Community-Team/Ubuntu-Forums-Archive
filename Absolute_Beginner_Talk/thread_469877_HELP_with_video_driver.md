---
title: "HELP with video driver"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by mowermanjp on 2007-06-10
Don't know how to install nvidia drivers, can't login as root user, not allowed to edit xorg.conf.
can anyone help a linux newbee?

---

### Post by mikewhatever on 2007-06-10
Get envy [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
or enable the restricted nvidia driver in System>Administration
What version of Ubuntu do you have?

---

### Post by mowermanjp on 2007-06-10
6.10

---

### Post by logos34 on 2007-06-10
> or enable the restricted nvidia driver in System>Administration

not available in 6.10.

Envy may or may not work.

sudo apt-get install envy

What exactly is your status?  Are you running the gui now but poor resolution, or did x server fail to start?

---

### Post by Jimmyfj on 2007-06-10
You don't need to be logged in as root to install your nVidia-driver. Simply go to System/Administration/Restricted Drivers Manager. Enter your root-password and select Enable Driver.

Ubuntu will now download the driver for your system and after a reboot you'll see a icon in the top right corner (looks like a graphics card) Then clikc on the icon and enter your root-password and select Close. Your nVidia-driver shold now be installed and working.

Then go to Programs/ Add/remove and choose the System-group. Scroll down till you find the program Sysinfo and install it.

Run sysinfo and wait for load. Now you'll see a nVidia-point at the bottom in the left side. Clik on nVidia and  at the buttom-right-site you'll se nVidia Display Settings - Click on that and chose your resolution and refresh rate. Save any settings you change and exit.

---

### Post by mowermanjp on 2007-06-10
upgraded to 7.04
new resolution options added but still not able to choose the correct resolution.
i think i need to edit the xorg.conf file but i can only open it in read only format. wont let me save it since i am not the "owner" of the file.
i tried the instructions from jimmy but cant find the sysinfo part of it

best resolution i can choose is 1024x768 and monitor res is 1680x1050 so it is like viewing it at 640x480 on my screen

---

### Post by logos34 on 2007-06-10
> **mowermanjp said:**
> upgraded to 7.04
new resolution options added but still not able to choose the correct resolution.
i think i need to edit the xorg.conf file but i can only open it in read only format. wont let me save it since i am not the "owner" of the file.
i tried the instructions from jimmy but cant find the sysinfo part of it

best resolution i can choose is 1024x768 and monitor res is 1680x1050 so it is like viewing it at 640x480 on my screen

try 
**sudo nvidia-settings**

Set the resolution and refresh there.  Hit apply.  Save configuration to x file.

Then go back and set it as default in sytem>prefs>screen resolution.

To edit xorg:
[B]
gksudo gedit /etc/X11/xorg.conf[/B]

---

### Post by mowermanjp on 2007-06-18
Thank you everybody for the help. Finally got everything working.
Still having trouble with setting resolution default. everytime i start computer i have to use the nvidia control panel to pick the resolution, its never listed in the resolution preference tab. how do i set it to boot with the correct resolution?

---

