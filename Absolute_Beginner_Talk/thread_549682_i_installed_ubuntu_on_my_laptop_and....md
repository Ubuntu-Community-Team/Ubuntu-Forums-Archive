---
title: "i installed ubuntu on my laptop and..."
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2007-09-12
I just installed ubuntu on my laptop and when it boots its just a black screen and nothing is happening.

---

### Post by medvezhonok on 2007-09-12
What video card do you have?  I had this problem with my ATI Mobility Radeon X1400, and I found a solution here: [http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194")

If that doesn't fix it, can you boot into recovery mode?  This will display more information about what's going on, and if it's a problem with the system booting, it should stop printing wherever it hangs, helping you pinpoint the problem.

---

### Post by zetsumei on 2007-09-12
it's a nvidia card, i had formatted vista off of it.

---

### Post by w4ett on 2007-09-13
Try this:

From the grub  menu (You will have to press the <esc> key after your post screen) boot into recovery mode.

From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Blue"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This SHOULD get you to a GUI desktop. then go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by hyper_ch on 2007-09-13
If you run feisty, then you should not be required to use envy...

---

### Post by w4ett on 2007-09-13
Further to my pervious post, there are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Good Luck

---

### Post by zetsumei on 2007-09-13
> **w4ett said:**
> Try this:

From the grub  menu (You will have to press the <esc> key after your post screen) boot into recovery mode.

From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Blue"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This SHOULD get you to a GUI desktop. then go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

What if that doesn't work?  I'm trying it now.

---

### Post by bigken on 2007-09-13
well if it dont you could try the alernate cd

it would also help if we knew the make and model of your laptop
and which version of ubuntu you have installed

---

### Post by zetsumei on 2007-09-13
I did the sudo dpkg-reconfigure -phigh xserver-xorg and it just said that it made a backup and then gave me the prompt again.  So I ran startx and it worked in recovery mode, so I restarted thinking it'd run again in regular mode, and it's still giving me a black screen right after the load screen.  There's a BIOS Bug #81 that flashes at the top, if that's important or something.  I can't ctrl+alt+backspace, f1, f2, etc.  nothing on this screen.  And I can't get internet access from my wired cable in recovery mode.  This is a dv6000 hp laptop and I used the alternate cd as I couldn't get the livecd to boot.  And this is a fresh install, wiped out all vista things.

---

### Post by w4ett on 2007-09-13
Here's a list of results of that particular bios bug:

[http://us.cypherbios.org/index.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=BIOS+Bug+%2381#1084](http://us.cypherbios.org/index.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=BIOS+Bug+%2381#1084)

---

### Post by zetsumei on 2007-09-13
I've spent my whole night trying to get the GUI running in normal mode, anymore ideas?  What w4ett said to do, it just made a backup and didn't do nothing.  Didn't ask me to input drivers, etc.  But startx works fine in recovery mode, just not normal mode.  Also, why wouldn't it let me use the livecd with noacpi, etc....?

---

### Post by w4ett on 2007-09-13
So it won't boot when using the vesa driver?  I know your frustration level is growing, but we're trying to help.

---

