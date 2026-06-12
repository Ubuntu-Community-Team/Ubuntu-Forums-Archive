---
title: "Kernel Module Help"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by Louis_DeVecchis on 2006-05-20
I am trying to install an "Intel Extreme Graphics Controller"
Below is what happens when i run the "install.sh"

```
The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

root@Linux:/home/lou/Desktop/dripkg#
```

The log file states:
```
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/lou/Desktop/dripkg/agpgart-2.0 modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
Makefile.linux:151: *** Cannot find a kernel config file.  Stop.
```

I've tried following the howto on upgrading Kernel but all of the apps required fail during installation because they are "broken packages" or "not installable" can anyone help or is their an alternate means of making my resolution 1024 x 768 instead of 640 x 480?

thx if any one can help

---

### Post by halfvolle melk on 2006-05-20
Hi,
Dunno about hte compiling stuff above, but upping your resolution may rquire to edit your xorg.conf.

Open a terminal: Apps -> Accs -> Terminal.
First back-up:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Then edit xorg.conf. I always use Vi. Using Vi need to press "insert" so you can type stuff. Once you're done press "Esc" and then type ":wq [ENTER]".

Use [www.google.com](www.google.com) and enter the make of your monitor, maybe add "frequency". Here's mine:
[http://www.si87.com/Products/Monitors/17inchmonitor.html](http://www.si87.com/Products/Monitors/17inchmonitor.html)
> Sync Frequency:  	Horizontal: 27.0-86.0kHz, Vertical: 50-160Hz
Write this down.
Now edit xorg.conf:
```
sudo vi /etc/X11/xorg.conf
```
Press "instert".
Note what you've written down and edit accordingly. Again, here's what I have:
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       27-86
        VertRefresh     50-160
```
```
SubSection "Display"
                Depth           24
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
```
Press "Esc" and type ":wq [ENTER]". Make sure to read the entire post before continuing.
Press CTRL+ALT+BACKSPACE. If the log-in screen doesn't appear, type "startx". If that throws you back to a blinking cursor I'm sorry to have caused you the trouble :), do this:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
reboot, and you'll be back at 640x480.
Hope this helps.

---

