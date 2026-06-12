---
title: "Screen resolution"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-07-27
Hi
I'm now into my third day as a Linux (Ubuntu 5.10) user and am on a steep part of the learning curve.
However, I'm still perplexed as to how to adjust the monitor screen resolution.
When I check in System->Preferences->Screen Resolution a total of four options are given the largest of which is 1024*768
But, I want to use 1280*1024
Can anybody help me acheive this?

Thanks
Paul

---

### Post by moma on 2006-07-27
Hello,

Check this guide (print it out or save in a text file)
[http://doc.gwos.org/index.php/ChangeResolution]("http://doc.gwos.org/index.php/ChangeResolution")

Note that 
$ sudo /etc/init.d/gdm stop 
will end the graphical gui and puts the screen in a text modus.
Just login with your user name and perform the commands.

$ sudo dpkg-reconfigure xserver-xorg
Questions concerning screen resolution settings come last.

You may also open your /etc/X11/xorg.conf and check the values:
$ gedit /etc/X11/xorg.conf

```

...
SubSection "Display"
     Depth           24
     Modes           "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
```


// moma
   [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")
---
[COLOR="SandyBrown"]The screen resolution dialog (System->Preferences->Screen Resolution)
should be improved so it can change values in /etc/X11/xorg.conf. 
Further it should be able to install 3D-acceleration (OpenGL) support and have a tab page for XGL/AIGLX settings.
The dialog ist useless misery as it is now![/COLOR]

---

### Post by PingunZ on 2006-07-27
goto console and type ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
select 1280x1024 with SPACEBAR and exit with ENTER.
then reboot or restart X

---

### Post by rck_hitokiri on 2006-07-27
you can try this if you want.... goto console then type
sudo dpkg-reconfigure xserver-xorg.... mostly you can accept until you reach your monitor settings... hope this can help.

---

### Post by PaulFXH on 2006-07-27
Hi
Thanks to verybody for your replies.
Unfortunately, I have not succeeded in getting the screen resolution changed.

Here's what happened:

1) In console mode, I typed sudo dpkg-reconfigure -phigh xserver-xorg
After entering password, error message says that the dpkg-reconfigure command does not exist.

2) In terminal, I typed sudo dpkg-reconfigure xserver-xorg
which leads me into an enormous rigmarole of questions. To the majority of these i just hit the default option except for the resolution where I checked one of the 1280*1024 boxes.
Interestingly, only the three lowest resolution boxes (1024*768 and lower) had asterisks in them -- does this mean that only these options were available?
After rebooting and trying to start Ubuntu, I get an error screen telling me that there has been a fatal server error and no screens were found. I am encouraged to visit [www.wiki.x.org](www.wiki.x.org) to read about the error.
A log file (forget the exact address) provides a little more detail and concludes that "failed to open framebuffer device". It also says that "screens found but none have a usable configuration".

So, essentially, in this condition, Ubuntu was unusable.
To extricate myself from this I re-entered the console, typed sudo dpkg-reconfigure xserver-xorg and proceeded through the Xorg configuration settings. This time, however, I set the screen resolution at 1024*768 and everything returned to normal.

At first glance, therefore, it seems that my computer is unhappy with a resolution higher than 1024*768. Yet, I operate without problems at 1280*1024 when running Windows on the very same machine.

Does this ring any bells with anyone?

Thanks 
Paul

---

### Post by PaulFXH on 2006-07-27
Hi folks
Just to say I solved the problem and my monitor is operating happily in 1280x1024 resolution right now.
I achieved this by following the (very simple) guidelines given by Bluecherry in response to a thread with the very same title as this one but posted 2-3 hours later.
While the posters who replied to my query all recommended making the changes in console mode and going through the whole Xorg reconfiguration rigmarole, the other thread just used sudo gedit /etc/X11/xorg.conf in terminal mode and then text-edited the xorg.conf file.
Paul

---

### Post by tjp.thomas on 2006-07-27
Could you post what you typed to get 1280x1024 to work...?
Found it myself... sorry! Please disregard!

---

### Post by avtolle on 2006-07-27
[http://ubuntuforums.org/showthread.php?t=224129](http://ubuntuforums.org/showthread.php?t=224129) for those who might be interested.

---

