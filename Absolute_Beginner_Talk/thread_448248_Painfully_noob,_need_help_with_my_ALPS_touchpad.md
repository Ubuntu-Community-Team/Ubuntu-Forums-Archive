---
title: "Painfully noob, need help with my ALPS touchpad"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by VitaminBB on 2007-05-18
Hey gang, first things first, I love Ubuntu, I used corel linux WAY back in the day and only for a few months, ubuntu really looks like its come into its own and im psyched.

Now the steps I have taken I have fixed my wireless connection but I am having serious problems with my ALPS touchpad (and I did check and it is an ALPS touchpad on my sony vaio).

I have read lots about getting the touchpad working and found a cool step by step setup (_[http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide/3](http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide/3)_) HOWEVER the guide says I need to ... (**And then tell Xorg to load the synaptics driver, to do so, go to the Section "Module" and add the following line if it is not already present:**).

Now what does going to the section "module" even mean ?! 

I am painfully noob and I cant find a "SIMPLE" guide to installing this ...

Telling me to go to the section module when I have no clue what that means doesnt help me.


I am hoping some benevolent person here can help me.

Thanks ahead of time.

-VBB

---

### Post by seshomaru samma on 2007-05-18
The link your following is not very newbie friendly
replace their command :
```
sudo vi /etc/X11/xorg.conf
```
with this:
```
sudo gedit /etc/X11/xorg.conf
```
it will open the xorg.conf file (which is located in the /etc/X11 direcory) with the Gedit editor (a more friendly editor than vi)
in that file look for a section that says "Section "InputDevice""
copy paste the following line if it is not already present:
```
Load    "synaptics"
```

then copy paste this to the end of the file
> Section "InputDevice"
Driver "synaptics"
Identifier "touchpad"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "130"
Option "RightEdge" "840"
Option "TopEdge" "130"
Option "BottomEdge" "640"
Option "FingerLow" "7"
Option "FingerHigh" "8"
Option "MaxTapTime" "180"
Option "MaxTapMove" "110"
Option "EmulateMidButtonTime" "75"
Option "VertScrollDelta" "20"
Option "HorizScrollDelta" "20"
Option "MinSpeed" "0.25"
Option "MaxSpeed" "0.50"
Option "AccelFactor" "0.030"
Option "EdgeMotionMinSpeed" "200"
Option "EdgeMotionMaxSpeed" "200"
Option "UpDownScrolling" "1"
Option "CircularScrolling" "1"
Option "CircScrollDelta" "0.1"
Option "CircScrollTrigger" "2"
Option "SHMConfig" "on"
 
#always usefull
Option "Emulate3Buttons" "on"
EndSection

then look for a line that says "Section - Server Layout"
and copy paste this line right below it
> InputDevice "touchpad" "AlwaysCore"

press CTRL+S to save (or better click on  the save icon in Gedit , but not 'save as')

press CTRL-ALT-BACSPACE which will restart your graphic session 
and if the guide is correct your touchpad will work...

---

### Post by VitaminBB on 2007-05-18
That tip at the beginning is great, now when I have the file open I added the line that says "load synaptics" but I noticed I already have a section that talks about synaptic touchpad, it says the following ...

[B]Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection[/B]

Obviously its not the same thing as the the recommended paste but do I need to delete this first before entering the other data or can I still safely paste the other information to the end of the file?

---

### Post by VitaminBB on 2007-05-18
Also I should add, my touchpad "works" but I want to change its settings and I cant see how thats possible.

If the touchpad is working is it possible to find the gui so I can edit the touchpad behaviour ?

---

### Post by wataboutbob on 2007-05-19
If your touchpad is working, are you trying to get the virtual scroll wheels and virtual right click to work as in Windows? 

If that's the objective, kindly note the experience of a friend of mine. Same pointing device as yours - Alps - on a Toshiba laptop. The above solution didn't work for him and only crashed the xorg. So before you try it, I suggest you make a backup of the xorg.conf file.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

FYI, the virtual scroll and rightclick works on my laptop out of the box but I still can't adjust their sensitivity or are size for example.

---

### Post by VitaminBB on 2007-05-19
Actually I just want to edit how my touchpad scrolls and other options.

I have seen Gsynaptics and was hoping there was a GUI I could access ([http://qsynaptics.sourceforge.net/ss.html](http://qsynaptics.sourceforge.net/ss.html)).

Is there no gui I can access to change settings?

---

### Post by wataboutbob on 2007-05-19
Have you tried System >  Preferences > Mouse

Does it help? Again, it has nothing for virtual anything, but you can change mouse acceleration, double click timeout... but nothing like qsynaptics....

So do you have virtual anything with your ALPS pointing device? If you do, do you remember how you enabled it, as my mate would dearly love that feature.

---

### Post by VitaminBB on 2007-05-19
Ya I have played with the mouse settings but there is nothing in there about changing scroll speed etc.

I just want to be able to have a gui that lets me change my scroll speed.

I dont even know what u mean by virtual stuff ?

---

### Post by seshomaru samma on 2007-05-19
If you like that GUI application that you linked to , why don't you just install that?
probably just:
```
sudo aptitude install gsynaptics
```

---

### Post by VitaminBB on 2007-05-19
Good call Sesho...

I dont know if it worked though, I cant find an icon to run the program under "Preferences" or "Administration" and I think there might be an error in installing qsynaptics ...

This is what terminal said...

[B]sudo aptitude install gsynaptics
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

What am I doing wrong?

---

### Post by seshomaru samma on 2007-05-19
It probably means that you have a couple of applications using apt-get at the same time (for example -synapic is open , or you are installing updates).
To be on the safe side -close all applications except the terminal
If you still get the same error - reboot and run the command again (you could use the terminal to hunt down those applications and kill them ,but a reboot will probably be easier at this stage)

if you still get the error after a reboot - then we are talking of a problem of a different magnitude


(also I'm assuming that you enabled the extra repostories, like this:You can add extra repositories using the Software Sources application(in Synaptic), which can be found in the menu: System -> Administration -> Software Sources. Check the repositories you think you will need (main, universe, restricted, multiverse).

---

### Post by VitaminBB on 2007-05-19
EUREKA !!!!

Your my new best friend Sesho, ill take a bullet for u man :)

Cheers !

Works great now.

---

### Post by seshomaru samma on 2007-05-19
glad it helped

may i suggest these three links
[one]("http://monkeyblog.org/ubuntu/installing/")
[two]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")
[three]("http://www.psychocats.net/ubuntu/index.php")

i think they are very helpful

---

