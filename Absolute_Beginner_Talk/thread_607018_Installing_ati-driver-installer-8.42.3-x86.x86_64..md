---
title: "Installing ati-driver-installer-8.42.3-x86.x86_64.run"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by xsabrewulf on 2007-11-08
I just downloaded "ati-driver-installer-8.42.3-x86.x86_64.run"

from ATI's webpage.

How am I suppose to install this?

I double click on the icon and I get an error saying:

[B][I]Could not open the file /home/mike/Desktop/ati-d…ler-8.42.3-x86.x86_64.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again[/I][/B]


I uninstalled my old drivers VIA Envy so i would really like these drivers installed.

---

### Post by Maestro23 on 2007-11-08
> **xsabrewulf said:**
> I just downloaded "ati-driver-installer-8.42.3-x86.x86_64.run"

from ATI's webpage.

How am I suppose to install this?

I double click on the icon and I get an error saying:

[B][I]Could not open the file /home/mike/Desktop/ati-d&#8230;ler-8.42.3-x86.x86_64.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again[/I][/B]


I uninstalled my old drivers VIA Envy so i would really like these drivers installed.

Open a terminal and navigate to the directory where the file is. Then

> sudo chmod + x ati-driver-installer-8.42.3-x86.x86_64.run

./ati-driver-installer-8.42.3-x86.x86_64.run

---

### Post by xsabrewulf on 2007-11-08
what does "chmod +" do and mean?

---

### Post by Maestro23 on 2007-11-08
> **xsabrewulf said:**
> what does "chmod +" do and mean?

Changes the permissions on the file to make it executable.

---

### Post by xsabrewulf on 2007-11-08
> **Maestro23 said:**
> sudo chmod + x ati-driver-installer-8.42.3-x86.x86_64.run

./ati-driver-installer-8.42.3-x86.x86_64.run


in the first line do I have to put that "x" in after the "+" sign? because it says "x" no such file name

also, on the second line do I need to put the "." infront of the "/" ?

---

### Post by carlosjuero on 2007-11-08
> **xsabrewulf said:**
> in the first line do I have to put that "x" in after the "+" sign? because it says "x" no such file name

also, on the second line do I need to put the "." infront of the "/" ?
No space between the + and the x
```

chmod +x ./ati-driver-installer-8.42.3-x86.x86_64.run

```

The actual error you got was because Nautilus was trying to open the installer as a text file, which it isn't - when it is executable you can run it and install the drivers.

Easiest way is to install right after you chmod the file by typing ```
./ati-driver-installer-8.42.3-x86.x86_64.run
```
Make sure you are in the same folder as the installer file.

Note: Be sure to uninstall any previous versions of the ATI driver, the uninstall script (if it exists) is located in /usr/share/ati and is called fglrx-uninstall.sh

---

### Post by powertower on 2007-11-08
I have been fighting this driver for a few days. To install it properly you need to follow this tutorial close. Otherwise the fglrx drivers won't take after installation. It will revert to the fglrx driver from the original Ubuntu installation. All of it was done in the terminal. The link is here, make sure you don't get any errors after each step, if you do something is wrong..... Follow method 2 installation...

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way)

Let us know how it worked

POWERTOWER-

---

### Post by atlascomplete on 2007-11-08
When I installed my NVidia driver, it started booting when I typed the entire file path, i.e. "./usr/desktop/NVidia-blah-blah-blah.run" instead of just "./NVidia-blah-blah.run"

Of course, I forget the actual file path.

---

### Post by carlosjuero on 2007-11-08
> **atlascomplete said:**
> When I installed my NVidia driver, it started booting when I typed the entire file path, i.e. "./usr/desktop/NVidia-blah-blah-blah.run" instead of just "./NVidia-blah-blah.run"

Of course, I forget the actual file path.
Well the ./ is for the current folder - if it isn't in the current folder then you can either specify the full path, or change to the folder it is downloaded in.

---

### Post by xsabrewulf on 2007-11-08
> **powertower said:**
> I have been fighting this driver for a few days. To install it properly you need to follow this tutorial close. Otherwise the fglrx drivers won't take after installation. It will revert to the fglrx driver from the original Ubuntu installation. All of it was done in the terminal. The link is here, make sure you don't get any errors after each step, if you do something is wrong..... Follow method 2 installation...

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way)

Let us know how it worked

POWERTOWER-


Wow, that seems like a lot of work and a lot of thing could go wrong. im kinda scared to do all those things...

---

### Post by Maestro23 on 2007-11-08
> **xsabrewulf said:**
> Wow, that seems like a lot of work and a lot of thing could go wrong. im kinda scared to do all those things...

Great link.  I installed my 1st ATI driver that way in Edgy 6.10. :guitar:

---

### Post by powertower on 2007-11-08
/no work involved, no thinking, its a tutorial. Took about 10 minutes for me. I would suggest following it though or you will have problems....

POWERTOWER-

---

### Post by carlosjuero on 2007-11-08
> **xsabrewulf said:**
> Wow, that seems like a lot of work and a lot of thing could go wrong. im kinda scared to do all those things...

If you follow the instructions exactly it is a breeze :)

---

