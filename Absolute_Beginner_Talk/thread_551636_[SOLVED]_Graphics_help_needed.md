---
title: "[SOLVED] Graphics help needed"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by styphon on 2007-09-15
Hi,

I've just installed Ubuntu on my PC in dual boot mode. Did all the updates and set to work getting my graphics working.  I have a wide screen monitor and a GeForce 8800GTX. I ran the restricted drivers and they installed fine. Rebooted and now I get no signal.  I went into the restore option on boot up and pressed ctrl+d when asked to. It came up with something about the graphics card not responding. Now I can't see a thing when I boot up the GUI. Any suggestions for a complete newbie to Linux?

Thanks in advance.

---

### Post by w4ett on 2007-09-15
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

### Post by styphon on 2007-09-15
All I can say is, thank you thank you thank you thank you thank you thank you

The first option for installing the drivers is what gave me the black screen.  The second option worked a charm. Thank you very much :D.

---

### Post by w4ett on 2007-09-15
Great!.....Please mark your thread "Solved"

Good Luck

---

### Post by styphon on 2007-09-15
> **w4ett said:**
> Great!.....Please mark your thread "Solved"

Good Luck

Too late, already done :).

EDIT: OK, editing the title doesn't mark it solved, hmm. Lol, just found the *mark thread solved* option.

---

