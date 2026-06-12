---
title: "New Nvidia linux driver 96.43 released jan 29th 08"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by halfhearted on 2008-02-05
The new Nvidia linux driver looks as if it will run the GeForce4 440 Go in my old Dell 840C, however the instructions say " Run "sh NVIDIA-Linux-x86-96.43.05-pkg1.run" from the terminal. If I open a terminal and type "sudo sh NVIDIA-Linux-x86-96.43.05-pkg1.run" it replies that it cannot open the file. What am I doing wrong? Thanks for any help.

---

### Post by Shazaam on 2008-02-05
Where did you download it to? If you downloaded it to your desktop you need to cd (change directory) to the location of the file like this.....
```
cd ~/Desktop
```
Note the capitol d in Desktop. Once you get there in terminal type in-
```
ls
```
This will list everything there. Make sure your driver is in that list. The full version of the original code without the shortcut would be-
```
cd /home/yourusername/Desktop
```
(substitute your username in the above)
Then you can issue the sudo sh command. But you need to stop X from running.
Do a Control+Alt+F1
This will get you to a black login screen. Log in. Type this in....

sudo /etc/init.d/gdm stop

Then cd to the driver and then run it.

---

### Post by halfhearted on 2008-02-05
Thanks very much for that. Now I get the message that "you seem  to be running X" it says that I should close X. How do I do that? And having closed it, how do I open it again? Thanks again.

---

### Post by halfhearted on 2008-02-05
Sorry friend , didn't see the end of your very helpful message. My apologies.

---

### Post by lduplantie on 2008-02-05
I have just upgraded my driver using Envy ( [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) ).
No problems, it upgraded the drivers in a few minutes,

---

### Post by oedha on 2008-02-05
or...you can just install the driver from Add/remove
search for nvidia on all available applications
or envy
or
are you sure sudo /etc/init.d/gdm stop didn't shutdown your X ?

---

### Post by halfhearted on 2008-02-05
Well Shazam, it failed again. This time it said that there was no kernel interface that matched my kernel and that it could look for one if I wished. Sadly it couldn't find one. Then it said that it would attempt to compile one for me, so I agreed, having nothing to lose. Then it said that I was missing something like 'libc header files'. Then it failed. However on the plus side I did manage to get X started again by modifying your command. How do I get the 'libc header files' please?

---

### Post by lduplantie on 2008-02-05
Envy will compile a kernell for your system

---

### Post by Shazaam on 2008-02-05
You need to install build-essential through Synaptic. Then try again.
Yes, Envy works for some people, so does the "Restricted Driver Manager". But that wasn't what the op was asking about.:)

---

### Post by halfhearted on 2008-02-05
Thanks for further advice Shazaam. I went and installed Envy. This is an amazing bit of software. Anyway it did its thing and seemed to go off and install the Nvidia 96.43.01 Linux accelerated graphics driver, which it got from God knows where. I turned off and tirurned on again and ....Nothing. Total blackness - after the initial screens and a couple of drum beats. According to the Dell specs for my old Dell Latitude 840C it runs this card -
 32MB NVIDIA GEFORCE4 440 GO (NV17) VIDEO - Problem is that now I can't see anything. Is there anyway back from this or do I have to completely reinstall again?

---

### Post by Shazaam on 2008-02-05
Since you are back reboot into "Recovery Mode" (hit ESC when Gutsy is booting), go ahead and login at the prompt.
You will have to run this at the prompt after login....
```
sudo dpkg-reconfigure xserver-xorg
```
and choose "nvidia" as the driver. If that doesn't work do it again and choose "vesa" to get back to a gui.

---

### Post by halfhearted on 2008-02-07
Come on you Linux gurus! Better to say "Ubuntu Gurus" I guess. Actually it's quite hard to say "Ubuntu Gurus". Anyway, joking aside, I have fixed the problem so I thought I'd post the solution just in case any other poor souls meet the black screen that the AGP driver generated on my laptop. The solution is to edit xorg.conf. A line has to be added to the Devices section. The line is -

         Option        "UseDisplayDevice"         "DFP" (with appropriate tab spacing)

This solves the problem and allows X to output to the laptop's flat panel. Otherwise you just get output from the D-Sub video out socket.

---

