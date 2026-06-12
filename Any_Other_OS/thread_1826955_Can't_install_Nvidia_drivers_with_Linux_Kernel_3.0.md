---
title: "Can't install Nvidia drivers with Linux Kernel 3.0.1 in Sid"
date: 2011-08-17
forum: Any Other OS
---

### Post by Dlambert on 2011-08-17
Hello, i have Linux Mint Debian Edition 64 Bit and when the update manager said Kernel 3.0.1 was available (mint update) I got excited, so I installed it. When i rebooted It gave soime errors about Nouveu not being installed (which is good) And wouldn't load X (No driver). So i did a terminal login and Navigated to my Folder that contained the Nvidia Driver, and when i type in ```
sudo ./N(tab)
``` nothing happens. I tried typing out the full name, and still no joy. Then i rebooted into 2.32.x and renamed the driver to nv.run, and retried the process, and still nothing happened except a File/folder doesn't exist error. Yes the file is executable.  In order to install the driver on 2.32.x i just used the command, sudo ./N(tab) (no x check) and it ran correctly. What am I doing wrong? Any ideas?

---

### Post by 23dornot23d on 2011-08-17
From what you are saying there are no Nvidia drivers loaded - so lets load some in ......

On later kernels for some reason the Nvidia drivers do not seem to load in straight away ....

you could try 

apt-get install aptitude
aptitude update

(cannot remember for sure if sid has Nvidia-current ..... ( you may need to list what is available )

aptitude install nvidia-current
aptitude install nvidia-settings

aptitude safe-upgrade

also look for the kernel header file ......... for 3.0.1 .......

Post screen shots of each step you take to resolve it ...... dkms files are needed too ....
aptitude safe-upgrade may add everything you need ...... but post a screen shot of what you
see before you do it ....... just to be sure .......

 ( I photograph mine if there is no GUI and post them )

can you get to a desktop with Nouveau .... or just a terminal screen ?

---

### Post by Dlambert on 2011-08-17
I will try, i don't want noveau installed, so i just get a terminal. During boot it says, "No state found for Nvidia HDMI/ Hd audio"

---

### Post by 23dornot23d on 2011-08-17
What graphics card is it and what computer - please ?

---

### Post by Dlambert on 2011-08-17
Well, i try to install the Nvidia driver manually if possible (latest features etc), Nvidia GTS 450, Amd Phenom II x4 OC'D 3.6 Ghz. 4GB of Gskill Ram ddr3 1600. CUSTOM BUILT by me

---

### Post by 23dornot23d on 2011-08-17
The standard drivers should be ok ..... the Nvidia drivers for that card are here though .....
your choice .....

[http://www.nvidia.com/object/linux-display-ia32-260.19.12-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.12-driver.html)

---

### Post by Dlambert on 2011-08-17
I know, re-downloaded this morning, trying right now.

---

### Post by 23dornot23d on 2011-08-17
Have a good look at the text on the screen as it loads in ....... does it say it is missing 
anything ........

Also watch to see if it says ok or a RED [COLOR=Red]**FAIL**[/COLOR] comes up if not ok ...... on the right hand side
of the terminal screen as the driver loads in ...... a picture is worth a thousand words too .

If it comes up Ok .... you should be ok to go .... and may need to create a xorg.conf file ....

---

### Post by Dlambert on 2011-08-17
I got it! A re-download worked! just booted back into an older kernel and copied Driver into downloads folder, then make it executable in the properties menu. Then rebooted into 3.0.1, and logged in and ran,

```
su
``` ENTER PASSWORD

```
cd /home/dlambert/Downloads
```

```
init 3
``` TO KILL X, just in case

```
./N(tab to display full name)
```

And let it do it's thing. The first run gave me an error about noveau, and i let it attempt to mod-probe it out. Then had to reboot and try it again, same steps and the installer ran, then just a blinking cursor, so i rebooted and tried again, and immediately after install for the third time, i was greeted by the Login Screen. Just reboot after that and enjoy!

---

### Post by 23dornot23d on 2011-08-17
Good to go then .... if its ok now - go to top right and mark as solved please ....

glad you have it working now .... ;)

---

### Post by Dlambert on 2011-08-17
Never mind, when i restart the Driver doesn't load, and i have to repeat the process just to see the desktop, and the OpenGL performance is terrible...

---

### Post by Dlambert on 2011-08-17
Also, i wrote another x config file. I think. Will boot later (working outside)

---

### Post by 23dornot23d on 2011-08-17
Ok ... if you had a xorg.conf file that worked ok previously ....... try copying that one .....

I always keep a backup of mine .... as I run a couple of monitors and it just saves me
setting it up each time ...... let me know how it goes ......

Do a screen shot too ...... nvidia-settings should show you something if the driver loaded in ok
post on imageshack - free to use and makes images available fo things like this ..... set it up once
and it comes in useful for loads of things .......... just cut and paste the direct link into
images or links here ,,,,,,,,,,,

Here is where you will find Nvidia-settings ...... if you do not already know .... 

Menu  >> Preferences >> Nvidia X Server Settings .........

---

### Post by Dlambert on 2011-08-17
Thats what i used to reset x Config. (nivida-settings) Give me a bit.

---

### Post by Dlambert on 2011-08-18
I got it finally! Here's how I fixed it:

Booted into recovery mode (via GRUB) To prevent X from loading at all

Entered Root Password

init 3 (to prevent a runlevel error)

I had to then log back in

```
cd /home/dlambert/Downloads
```

Then,
```
sudo ./N(tab)
```

And i entered my password, and the Installation went all the way through, instead of stopping at "Building Kernel Module" 

Reboot and Enjoy, hopefully this will help anyone else that has this problem. :KS:KS:KS:KS:KS

---

