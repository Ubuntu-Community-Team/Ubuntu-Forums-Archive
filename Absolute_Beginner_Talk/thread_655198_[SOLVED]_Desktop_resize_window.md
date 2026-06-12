---
title: "[SOLVED] Desktop resize window"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by JohnPta on 2008-01-01
When

---

### Post by JohnPta on 2008-01-01
Operating system: 7.10
When I have the Visual effects on "Normal" on the desktop, I can not drag the open windows over the workspace nor can I resize the windows or close the windows by clicking the "X" at the right top because the "X" is not available. Is that normal or must I adjust an option somewhere?

---

### Post by RomeReactor on 2008-01-01
Hi. What video card do you have? please open a terminal (Applications->Accessories->Terminal) and run the following:
```
metacity --replace
```

---

### Post by jordanmthomas on 2008-01-01
Do the windows move if you hold alt and click on them to drag them around?

If so, then press alt + F2 and type this:
```
gtk-window-decorator --replace
```

---

### Post by JohnPta on 2008-01-01
> **RomeReactor said:**
> Hi. What video card do you have? please open a terminal (Applications->Accessories->Terminal) and run the following:
```
metacity --replace
```

The Video card is NVIDIA Geforce 6100. 
I did run that command:

Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

This is the answer from the operating system on the screen.

---

### Post by JohnPta on 2008-01-01
> **jordanmthomas said:**
> Do the windows move if you hold alt and click on them to drag them around?

If so, then press alt + F2 and type this:
```
gtk-window-decorator --replace
```

Yes it does Move 
After that I did run that command, without the "[" but nothing happens. I also tried with the "[" the first time I got a help screen. Now nothing anymore.

---

### Post by RomeReactor on 2008-01-01
Try jordanmthomas' suggestion; if that doesn't work, try this in the terminal:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Then press CTRL+ALT+BACKSPACE to restart your display.

---

### Post by JohnPta on 2008-01-01
> **RomeReactor said:**
> Try jordanmthomas' suggestion; if that doesn't work, try this in the terminal:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Then press CTRL+ALT+BACKSPACE to restart your display.

I did run that command in terminal after I have rebooted the computer however nothing happens.

---

### Post by JohnPta on 2008-01-01
> **JohnPta said:**
> I did run that command in terminal after I have rebooted the computer however nothing happens.


Oeps, I think I have a problem, the computer crashes after approximately 10 minutes. Although I have put the Visual effects to basic/none.

I rebooted several times and now the computer doesn't crash anymore but I can still not move the windows under normal settings in visual effects.

---

### Post by RomeReactor on 2008-01-01
As far as I know you shouldn't have problems with your card; the 6000 range of nVidia cards is very well supported in Linux. Let's try to reconfigure your display: close all applications that you have running, then press CTRL+ALT+F1--this will bring you to a black screen with white text. Log in if asked to, then make a backup of your current display configuration:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
This will create a backup called **xorg.conf.backup** in the same directory where your current configuration is. Now let's stop the Gnome display manager:
```
sudo /etc/init.d/gdm stop
```
Now that nothing graphical is running on your system, it's time to reconfigure the display:
```
sudo dpkg-reconfigure xserver-xorg
```
accept all the defaults it prompts you with--except when asked to select a video card driver, select **NVIDIA**; afterwards your display should start automatically. If it doesn't, run:
```
sudo /etc/init.d/gdm start
```
if it still doesn't start, try rebooting:
```
sudo reboot
```

If after all this your display issues aren't solved, and you want to revert to your previous configuration, run this from the terminal:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
and then press CTRL+ALT+BACKSPACE, or reboot.

Hope this helps.

---

### Post by JohnPta on 2008-01-02
> **RomeReactor said:**
> As far as I know you shouldn't have problems with your card; the 6000 range of nVidia cards is very well supported in Linux. Let's try to reconfigure your display: close all applications that you have running, then press CTRL+ALT+F1--this will bring you to a black screen with white text. Log in if asked to, then make a backup of your current display configuration:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
This will create a backup called **xorg.conf.backup** in the same directory where your current configuration is. Now let's stop the Gnome display manager:
```
sudo /etc/init.d/gdm stop
```
Now that nothing graphical is running on your system, it's time to reconfigure the display:
```
sudo dpkg-reconfigure xserver-xorg
```
accept all the defaults it prompts you with--except when asked to select a video card driver, select **NVIDIA**; afterwards your display should start automatically. If it doesn't, run:
```
sudo /etc/init.d/gdm start
```
if it still doesn't start, try rebooting:
```
sudo reboot
```

If after all this your display issues aren't solved, and you want to revert to your previous configuration, run this from the terminal:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
and then press CTRL+ALT+BACKSPACE, or reboot.

Hope this helps.

Thanks it seems to work. I was never prompted however I continued typing in the commands you gave me. 

I am happy to be a member of such a community.

---

### Post by JohnPta on 2008-01-02
> **RomeReactor said:**
> As far as I know you shouldn't have problems with your card; the 6000 range of nVidia cards is very well supported in Linux. Let's try to reconfigure your display: close all applications that you have running, then press CTRL+ALT+F1--this will bring you to a black screen with white text. Log in if asked to, then make a backup of your current display configuration:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
This will create a backup called **xorg.conf.backup** in the same directory where your current configuration is. Now let's stop the Gnome display manager:
```
sudo /etc/init.d/gdm stop
```
Now that nothing graphical is running on your system, it's time to reconfigure the display:
```
sudo dpkg-reconfigure xserver-xorg
```
accept all the defaults it prompts you with--except when asked to select a video card driver, select **NVIDIA**; afterwards your display should start automatically. If it doesn't, run:
```
sudo /etc/init.d/gdm start
```
if it still doesn't start, try rebooting:
```
sudo reboot
```

If after all this your display issues aren't solved, and you want to revert to your previous configuration, run this from the terminal:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
and then press CTRL+ALT+BACKSPACE, or reboot.

Hope this helps.

The display is working correctly now. I was never prompted to do anything but I typed in all the line command you gave me and than I rebooted by pressing the reset button. Because the whole system was hanging. I think I have a defective memory chip or something like that.

---

