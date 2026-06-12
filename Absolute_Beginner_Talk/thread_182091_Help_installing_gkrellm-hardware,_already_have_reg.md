---
title: "Help installing gkrellm-hardware, already have regular gkrellm installed &amp; working"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Getwild2 on 2006-05-25
I've downloaded, unzipped and extracted gkrellm-hardware.tar.gz to my /tmp directory.  Now I just have a folder called "Hardware" containing a bunch of items.  

What do I do now?  

I have regular gkrellm installed, setup and working just how I want it.  I then installed lm-sensors found here: [http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors+howto]("http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors+howto")

Can you help?  I know its probably very easy but I've searched and I'm a noob with very little experience.  Everything I've installed has been from command line or Synaptic. 

Thanks SO much in advance!!

---

### Post by bluevoodoo1 on 2006-05-25
Check out this page... 
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

scroll down to...
"4. Installing from source"

---

### Post by Getwild2 on 2006-05-25
[QUOTE=bluevoodoo1]Check out this page... 
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

scroll down to...
"4. Installing from source"[/QUOTE]
So will it overwrite my existing installation?  

Will it keep my settings or should I write them down?

Thanks for the link, that's perfect!!

---

### Post by bluevoodoo1 on 2006-05-25
[QUOTE=Getwild2]So will it overwrite my existing installation?  

Will it keep my settings or should I write them down?

Thanks for the link, that's perfect!![/QUOTE]

I don't know if it will overwrite it or not, but I would definitely make a backup of your settings.

---

### Post by Getwild2 on 2006-05-25
[QUOTE=bluevoodoo1]I don't know if it will overwrite it or not, but I would definitely make a backup of your settings.[/QUOTE]
Alright, I got my settings backed up and I tried to follow the instructions to no avail.

sudo apt-get update
sudo apt-get install build-essential
tar -xvzf gkrellm-hardware.tar.gz
cd Hardware
./configure      [COLOR="Red"]<---------------This directory is not found and I cannot continue[/COLOR]
make
sudo make install 

Any recommendations??  Thanks again!!  :-k

---

### Post by bluevoodoo1 on 2006-05-25
[QUOTE=Getwild2]Alright, I got my settings backed up and I tried to follow the instructions to no avail.

sudo apt-get update
sudo apt-get install build-essential
tar -xvzf gkrellm-hardware.tar.gz
cd Hardware
./configure      [COLOR="Red"]<---------------This directory is not found and I cannot continue[/COLOR]
make
sudo make install 

Any recommendations??  Thanks again!!  :-k[/QUOTE]

nevermind

---

### Post by bluevoodoo1 on 2006-05-25
This gkrellm-hardware is a theme?? I downloaded and extracted the gkrellm-hardware found here [http://members.dslextreme.com/users/billw/gkrellm/](http://members.dslextreme.com/users/billw/gkrellm/) and saw that is't just a bunch of images that make up a theme. If this is the case, there is no need to "install" it. If you look inside the "hawrdware folder" what do you see?

Are you mainly trying to get lm-sensors to work? If so, Synaptic is the best choice for that. I'm not quite sure what you're trying to do... lm-sensors or gkrellm.

---

### Post by Getwild2 on 2006-05-25
[QUOTE=bluevoodoo1]This gkrellm-hardware is a theme?? I downloaded and extracted the gkrellm-hardware found here [http://members.dslextreme.com/users/billw/gkrellm/](http://members.dslextreme.com/users/billw/gkrellm/) and saw that is't just a bunch of images that make up a theme. If this is the case, there is no need to "install" it. If you look inside the "hawrdware folder" what do you see?

Are you mainly trying to get lm-sensors to work? If so, Synaptic is the best choice for that. I'm not quite sure what you're trying to do... lm-sensors or gkrellm.[/QUOTE]
I've got lm-sensors working, installed via Synaptic:

[COLOR="Blue"]cstiff@ubuntu:~$ sensors
it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.73 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
VCore 2:   +0.00 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
+3.3V:     +6.53 V  (min =  +8.16 V, max =  +8.16 V)   ALARM
+5V:       +4.89 V  (min =  +6.85 V, max =  +6.85 V)   ALARM
+12V:     +12.03 V  (min = +16.32 V, max = +16.32 V)   ALARM
-12V:     -27.36 V  (min =  +3.93 V, max =  +3.93 V)   ALARM
-5V:      -13.64 V  (min =  +4.03 V, max =  +4.03 V)   ALARM
Stdby:     +4.97 V  (min =  +6.85 V, max =  +6.85 V)   ALARM
VBat:      +3.22 V
fan1:     1875 RPM  (min =    0 RPM, div = 8)
fan2:     2755 RPM  (min =    0 RPM, div = 2)
fan3:        0 RPM  (min =    0 RPM, div = 2)
M/B Temp:    +38°C  (low  =    -1°C, high =    -1°C)   sensor = thermistor
CPU Temp:    +30°C  (low  =    -1°C, high =    -1°C)   sensor = thermistor
Temp3:        -1°C  (low  =    -1°C, high =    -1°C)   sensor = disabled   ALARM[/COLOR]

I'm trying to get gkrellum-hardware installed so it can use sensors to report back to me via GUI.  Right now I have the regular gkrellum which just reports disk space, processes, cpu, network, etc.  

Below is what I see in my Hardware folder once the file is extracted:
[IMG]http://www.lbcflint.org/cjs/images/hardware.JPG[/IMG]

---

### Post by bluevoodoo1 on 2006-05-25
What does the readme say? It says nothing (I just read iT)

Edit: This gkrellm-hardware is a theme. Looking at the main page of [http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html) shows the temps/fans so there's probably a line of code you have to add to the gkrellm config.

edit2: this is probably what you're looking for, though i don't know anything about it.
[http://sourceforge.net/projects/gklmsensors](http://sourceforge.net/projects/gklmsensors)

---

### Post by Getwild2 on 2006-05-25
[QUOTE=bluevoodoo1]What does the readme say?[/QUOTE]
Looks like it IS a theme. 

[COLOR="Red"]"This is a test theme that demos frame overlap and spacer features
new in GKrellM 2.1 and 1.3.

It's not very polished."[/COLOR]

So I went to the Themes portion of gkrellm and it says, "Untar your theme tar files in /home/cstiff/.gkrellm2/themes".  Looks like we're getting there.  I cant find the .gkrellm2/themes folder to copy and paste the Hardware folder into though?!

EDIT:  Okay, so I downloaded gkrellm sensors, I'll probably have to do some playing around with it.  Granted, maybe its the same sensors I got from Synaptic.

---

### Post by bluevoodoo1 on 2006-05-25
[QUOTE=Getwild2]Looks like it IS a theme. 

[COLOR="Red"]"This is a test theme that demos frame overlap and spacer features
new in GKrellM 2.1 and 1.3.

It's not very polished."[/COLOR]

So I went to the Themes portion of gkrellm and it says, "Untar your theme tar files in /home/cstiff/.gkrellm2/themes".  Looks like we're getting there.  I cant find the .gkrellm2/themes folder to copy and paste the Hardware folder into though?![/QUOTE]

Well create the folder in the specified location. Open Nautilus right click to create folder, name it .gkrellm (it will be a hidden folder), then open that folder and create a folder named themes. Put your untarred Hardware folder in there and see how it goes.

Wait, I thought you were trying to get lm-sensors working with it? So you wanted this "theme" all along???

---

### Post by Getwild2 on 2006-05-25
[QUOTE=bluevoodoo1]Well create the folder in the specified location. Open Nautilus right click to create folder, name it .gkrellm (it will be a hidden folder), then open that folder and create a folder named themes. Put your untarred Hardware folder in there and see how it goes.

Wait, I thought you were trying to get lm-sensors working with it? So you wanted this "theme" all along???[/QUOTE]
Yes but I did not realize it was a theme, I guess its easier that it IS a theme.  Lemme try the above and see what happens.  I wonder if the .gkrellm folder is there but I just cant see it.

---

### Post by bluevoodoo1 on 2006-05-25
[QUOTE=Getwild2]Yes but I did not realize it was a theme, I guess its easier that it IS a theme.  Lemme try the above and see what happens.  I wonder if the .gkrellm folder is there but I just cant see it.[/QUOTE]

It might already be there then, Do this first before the above. Hit ctrl+h to see your hidden folders OR from Nautilus View >Show hidden files

---

### Post by Getwild2 on 2006-05-25
Whew, figured it out!  The /.gkrellm/themes directory was hidden, so I showed hidden files, copied and pasted the Hardware folder in there and WHA-LA!  Now I an adjust my sensor settings to my liking.  

Thanks SO MUCH bluevoodoo1 for your help!  I wouldve been still trying to install the thing if you hadnt figured out that it was a theme.  Man, it's much easier as a theme.  

Thanks again, I REALLY appreciate it!  :mrgreen:

---

### Post by bluevoodoo1 on 2006-05-25
[QUOTE=Getwild2]Whew, figured it out!  The /.gkrellm/themes directory was hidden, so I showed hidden files, copied and pasted the Hardware folder in there and WHA-LA!  Now I an adjust my sensor settings to my liking.  

Thanks SO MUCH bluevoodoo1 for your help!  I wouldve been still trying to install the thing if you hadnt figured out that it was a theme.  Man, it's much easier as a theme.  

Thanks again, I REALLY appreciate it!  :mrgreen:[/QUOTE]

:mrgreen:

---

### Post by Getwild2 on 2006-05-25
I thought you might want to see what we accomplished together.  :mrgreen: 

[IMG]http://www.lbcflint.org/cjs/images/monitor.JPG[/IMG]

Now I just have to figure out how to rename the temp1, temp2, fan1 and fan2 to the correct devices.  

Thanks again for all of your help!!  :-D

---

### Post by bluevoodoo1 on 2006-05-25
[QUOTE=Getwild2]I thought you might want to see what we accomplished together.  :mrgreen: 

Now I just have to figure out how to rename the temp1, temp2, fan1 and fan2 to the correct devices.  

Thanks again for all of your help!!  :-D[/QUOTE]

Looks good!

I downloaded it to mess around with it myself. You can change the names of "temp," "fan" etc in with the user-config and/or the sensor-config files in the .gkrellm2 folder. I actually had to copy everything in the sensor-config and paste it into the user-config for the temps/fans to show up, since it wasn't there. The main configuration file is the user-config, so look there first. But after that all I did was replace "temp1" with whatever you want.

```
sensor "BUTT" "it8712-9191-0260/temp1" 10000 0 0 0
``` etc. etc.

You can see it on the screenshot :)

---

### Post by Getwild2 on 2006-05-26
I took your advice and here is my final product.  

[IMG]http://www.lbcflint.org/cjs/images/monitor2.JPG[/IMG]

Thanks again for ALL of your help, you've really shed some light on a few things for me.  8)

---

### Post by bluevoodoo1 on 2006-05-26
:):)

---

