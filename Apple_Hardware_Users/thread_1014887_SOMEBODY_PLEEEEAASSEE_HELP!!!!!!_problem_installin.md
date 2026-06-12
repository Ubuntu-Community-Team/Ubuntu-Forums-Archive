---
title: "SOMEBODY PLEEEEAASSEE HELP!!!!!! problem installing hardware sensors monitor"
date: 2008-12-18
forum: Apple Hardware Users
---

### Post by mongrel boy on 2008-12-18
I really could use help here! I have a macbook pro 1.1 and previously was runnung Hardy on it. However I just spent 5 months living in Europe and left my macbook back here in the U.K.
Having returned I decided to put Intrepid on as its the latest version.
I have everything running fine and how i want apart from one crucial thing: Temperatures and Fan Speed.
I've been using the info from here:[COLOR="Red"]https://help.ubuntu.com/community/MacBookPro1-1_1-2/Intrepid#Temperatures%20&%20Fan%20Speed
[/COLOR]
It should be noted that i'm not an experienced computer person! I learned a lot wen i installed hardy and i sorted out vlc flickering and ammount of desktops etc. but something i dont understand is 
firstly,when told to:
add this to /etc/rc.local :

modprobe coretemp
sensors -s

I don't think im quite sure how. I know this may seem silly but can any1 break that down for me into a pure "How to" format?? That wud be great! I've been going into terminal and typing: "/etc/rc. local"
then hitting return then typing "modprobe coretemp sensors -s" then hitting return again. Is that correct?

second problem: the instructions say to right click the main panel menu and add Hardware Sensors Monitor to the pannel.
The thing thats really frustrated me is that Hardware Sensors Monitor ISNT THERE AT ALL!!!

Can someone please help me see where im going wrong? Im scared to run my macbook pro for long as it seems hot. Dunno if this is any help but Im not dual booting. I bought my macbook pro second hand and the harddisk was failing so replaced it and installed ubuntu due to nightmare finding mac OS disc that would work! Is that a problem? I like ubuntu loads and i just want to know my fans are doing what they should and that my CPU temp and HD temp are cool so to speak!
Any help would be great. Many thanks, Kieran

---

### Post by mkvnmtr on 2008-12-18
I am not sure about your machine because mine is older but I think you have to down load the sensors and some other things to start with. Did your tutorial tell you what you need to download?

---

### Post by hyperboloid on 2008-12-18
> **mongrel boy said:**
> I really could use help here! I have a macbook pro 1.1 and previously was runnung Hardy on it. However I just spent 5 months living in Europe and left my macbook back here in the U.K.
Having returned I decided to put Intrepid on as its the latest version.
I have everything running fine and how i want apart from one crucial thing: Temperatures and Fan Speed.
I've been using the info from here:[COLOR="Red"]https://help.ubuntu.com/community/MacBookPro1-1_1-2/Intrepid#Temperatures%20&%20Fan%20Speed
[/COLOR]
It should be noted that i'm not an experienced computer person! I learned a lot wen i installed hardy and i sorted out vlc flickering and ammount of desktops etc. but something i dont understand is 
firstly,when told to:
add this to /etc/rc.local :

modprobe coretemp
sensors -s

I don't think im quite sure how. I know this may seem silly but can any1 break that down for me into a pure "How to" format?? That wud be great! I've been going into terminal and typing: "/etc/rc. local"
then hitting return then typing "modprobe coretemp sensors -s" then hitting return again. Is that correct?

No. You have to open up the file /etc/rc.local in an **editor**, for instance by typing 
```
sudo gedit /etc/rc.local
```
at the command line in a terminal. (There is no space after the "rc.") Once you are in the editor, you can add the lines to the file, save, and quit. You may need to reboot for the changes to take effect. 

> **mongrel boy said:**
> second problem: the instructions say to right click the main panel menu and add Hardware Sensors Monitor to the pannel.
The thing thats really frustrated me is that Hardware Sensors Monitor ISNT THERE AT ALL!!!
Try right clicking on a blank part of the panel, instead of on the menu, and select "Add to Panel". If that does not find it, then check that the package "sensors-applet" is installed (use System -> Administration -> Synaptic Package Manager and search for "sensors-applet". (I'm not sure that's the right package, but it may be what you want.)

---

### Post by ske1fr on 2008-12-18
1.  When you read the instruction to add something to /etc/rc.local it means you need to open the file rc.local in the /etc directory using an editor like nano, and add the lines at the bottom of the file, finally saving the file.  Typing the commands in a terminal window can only work for the length of your current session.  Adding them to the rc.local file means they'll be run everytime you start the computer up.

2.  Did you run that command right above the instruction about Right-clicking before you tried the right-clicking?  If the sensors are not installed, you're not going to be able to add them...

---

### Post by mongrel boy on 2008-12-18
Wow, I didnt expect so much help so fast!! Thanks guys. Atually just after I wrote my post it appeard in the menu.(TYPICAL) I have followed your instructions and edited the file and saved and restarted. All is well.

My new problem is the manual fan speed setting (next on the page i mentioned, just after the CPU temperature section. Can anyone tell me what is applesmc and how do I install it?
Secondly (I know I'm probably coming across as stupid) Can anyone give me a step by step for the following:
-----------------------------------------------------------
(Quote from page) "Copy the files to your home dir: fan_speed1 , fan_speed2 , fan_speed3

And to execute: gksu bash ~/fan_speed1 (...2 or 3)"  
-----------------------------------------------------------

Once I have that done I'll be a happy man!! Thanks a lot for the help, it's cool you all took the time!! Kieran

---

### Post by hyperboloid on 2008-12-18
On my system (a MBP) I can increase the fan speed manually by typing:
```
echo 4000 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
echo 4000 | sudo tee /sys/devices/platform/applesmc.768/fan2_min
```
in a terminal. To reset fans back to the usual speed (2000) one does:
```
echo 2000 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
echo 2000 | sudo tee /sys/devices/platform/applesmc.768/fan2_min
```

Your system is different, so dunno if this works for you. Maybe you only have one fan, for instance.

---

### Post by hyperboloid on 2008-12-18
> **mongrel boy said:**
> Can anyone tell me what is applesmc and how do I install it?
See [https://wiki.ubuntu.com/MactelSupportTeam/PPA]("https://wiki.ubuntu.com/MactelSupportTeam/PPA"); perhaps you want the package "applesmc-dkms" there. 

> **mongrel boy said:**
> Secondly (I know I'm probably coming across as stupid) Can anyone give me a step by step for the following:
-----------------------------------------------------------
(Quote from page) "Copy the files to your home dir: fan_speed1 , fan_speed2 , fan_speed3

And to execute: gksu bash ~/fan_speed1 (...2 or 3)"  
-----------------------------------------------------------

Just save the files, and move them to you home folder. To execute the commands, type them in a terminal.

---

### Post by mongrel boy on 2008-12-18
Thanks a lot every1! got it all sorted now. My fans were running at 1000 RPM!
I've banged them up to 4000 now and im seeing nice cool thermomitors across the board. Really appreciate you guys taking the time to help a simpleton such as myself. That's why I like Ubuntu

---

