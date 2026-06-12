---
title: "solution for 8400GS = wait for 7.10 ?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by ubunoobie on 2007-10-03
Hi everyone,

I am having trouble getting the driver for my video card to work... I have searched around quite a bit already for a possible solution, and the closest I have come to finding anything like my problem is here:
[http://ubuntuforums.org/showthread.php?t=562076](http://ubuntuforums.org/showthread.php?t=562076)
As it is suggested in that thread, should I wait until 7.10 comes out in a few weeks? Or is there actually a way to get my card to work now? I have 7.04 installed. My card GPU is nVidia GeForce 8400GS.

p.s. Envy doesn't work for me :( Perhaps there is a way to manually install all the necessary dependencies, driver, ect and configure my card without using Envy?

If someone could help me with this, it would be wonderful! I'm quite a bit of a noob still :)

---

### Post by drf_av on 2007-10-03
Same card as yours, I'm using Gutsy and it works flawlessly. The best solution would be waiting a couplee of weeks, you can play around the beta in the meanwhile!

---

### Post by ubunoobie on 2007-10-03
> **drf_av said:**
> Same card as yours, I'm using Gutsy and it works flawlessly. The best solution would be waiting a couplee of weeks, you can play around the beta in the meanwhile!

Hi, thanks for responding... so what did you have to do to get your card to work in Gutsy? Was it recognized? Did you have to run envy?

I wouldn't mind upgrading now to beta... I just want to make sure I it's a good idea before I go ahead.

---

### Post by ubunoobie on 2007-10-03
Oh man... I think I might be screwed now. I tried to do some commands I saw in another thread and now I can't get back to my desktop, I'm getting a major error message that end with "...no devices found" and "no screens found"

This is what I did. I used synaptic to install "nvidia-glx-new" then I ran "sudo nvidia-glx-config enable" and logged out to restart the graphical x server...

That's when the error message came

What can I do :confused:

---

### Post by w4ett on 2007-10-03
From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

---

### Post by ubunoobie on 2007-10-03
> **w4ett said:**
> From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

Ok thank you very much! I think I selected the wrong resolution however... not a big deal right now though. I'm just glad to have my desktop back.

So do you have any ideas as to what I can do with my vid card problem?

---

### Post by w4ett on 2007-10-03
There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by ubunoobie on 2007-10-03
> **w4ett said:**
> There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

Yea, I've tried envy previously and it didn't work... and it still is giving me an error when I tried to use it now. I don't know what to do next...

I just built this rig, and I refuse to go back to windows!

---

### Post by w4ett on 2007-10-03
Try running Envy in Recovery mode/CLI....remove the old install attempt and then reinstall.

---

### Post by ubunoobie on 2007-10-04
bump.

anyone have any thoughts on this?

---

### Post by om1 on 2007-10-04
if you are brave and want to try the beta
```
update-manager -d
```

it will take you a little while but it works....
all of my drivers worked without ne setup needed.... except to enable restricted drivers... witch is just checking a check box.... that is including bcm4318 wireless 
i havent had any issues so far but i know some people have... if you do try it _[COLOR="Red"]backup all data first[/COLOR]_ then just run the command then set back and wait :popcorn:8).... on dsl bout an hour to an hour and half depending on speed of computer and dsl connection

if i can be of ne help feel free to pm me

---

### Post by ubunoobie on 2007-10-04
> **om1 said:**
> if you are brave and want to try the beta
```
update-manager -d
```

it will take you a little while but it works....
all of my drivers worked without ne setup needed.... except to enable restricted drivers... witch is just checking a check box.... that is including bcm4318 wireless 
i havent had any issues so far but i know some people have... if you do try it _[COLOR="Red"]backup all data first[/COLOR]_ then just run the command then set back and wait :popcorn:8).... on dsl bout an hour to an hour and half depending on speed of computer and dsl connection

if i can be of ne help feel free to pm me

Thanks! So, all I have to do, to go from 7.04 to 7.10, is run that command?

---

### Post by om1 on 2007-10-04
it will make the 7.10 beta version appear in the update manager so you can update to it...

the actual release will be released in two weeks....
but sounds like the beta would be a step up from what you have now

---

