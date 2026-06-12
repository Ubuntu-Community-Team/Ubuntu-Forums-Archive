---
title: "[SOLVED] Wrong screen resolution has stopped the OS!"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by lordfkiller on 2007-09-11
I used sudo dpkg-reconfigure xserver-xorg , chose my graphic card manufacturer(ATI), and put a star before all resolutions but 1280*800. I am using this resolution in Windows XP. But after pressing CRTL+ALT+BkSp, I can no more see anything but a blue and white page.
I can type in my username... and password, and I hear the sound of wrong password error, but nothing understandable is shown.

Thanks for any help.

---

### Post by w4ett on 2007-09-11
Ok...lets get you back to your desktop.......

From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Blue"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop.

Now lets confirm what video card you have....from the terminal type:
```

lspci
```

Copy and paste the result here so we can have a look.

Good Luck.

---

### Post by lordfkiller on 2007-09-12
Thanks for your help. The problem was solved!
Last time I had selected an incorrect resolution. I selected ATI and 1280*800 and everything was okay!

Although the problem is solved, following is the result of lspci for my graphics card:

 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

Once again, thanks for your help.

---

