---
title: "Ubuntu VGA Driver"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Snitz on 2007-07-18
Hey there, through the crap I was in last night, I finally got Ubuntu to work along with winxp and I don't think I'll be using Windows anymore :D.
But still, I'm facing one problem. Ubuntu didn't detect my VGA driver so I have to know where to download it from. I have it as a .exe extension but I can't install it since ubuntu doesn't support .exe 
So please tell me how can I download my VGA driver?

The name of my driver is: Intel Chipset something :$

---

### Post by sad_iq on 2007-07-18
To find out what's your video card type ```
lspci |grep VGA
``` Won't restricted manager install the driver for you??? I don't have any Intel video card...so can.t really help too much!!!

---

### Post by Snitz on 2007-07-18
The name of the driver is:

Mobile Intel(R) 945GM/GU Express Chipset Family.

Please help me in this so I can switch to Ubuntu for good!

---

### Post by Snitz on 2007-07-18
Oh no, This is the name of the driver.

Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

Now where to get it?

---

### Post by overdrank on 2007-07-18
> **Snitz said:**
> The name of the driver is:

Mobile Intel(R) 945GM/GU Express Chipset Family.

Please help me in this so I can switch to Ubuntu for good!

I have the same chipset and feisty install it right away with the install. You can check your xorg to see which driver is being used.
```
gksudo gedit /etc/X11/xorg.conf
```
Enter that command in the terminal locate under applications, accessories, terminal. Under the device section you should see you intel chipset and driver.

---

### Post by Snitz on 2007-07-18
> **overdrank said:**
> I have the same chipset and feisty install it right away with the install. You can check your xorg to see which driver is being used.
```
gksudo gedit /etc/X11/xorg.conf
```
Enter that command in the terminal locate under applications, accessories, terminal. Under the device section you should see you intel chipset and driver.
The xorg.conf is empty. I don't see any device section.

---

### Post by overdrank on 2007-07-18
> **Snitz said:**
> The xorg.conf is empty. I don't see any device section.

Make sure it is a **X** capital X  it is case sensitive.

---

### Post by Snitz on 2007-07-18
> **overdrank said:**
> Make sure it is a **X** capital X  it is case sensitive.
> Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
It detected it, that's weird, because I cannot use my normal 1280x800 resolution, all I have is 1024x768.

Is this normal?

---

### Post by sad_iq on 2007-07-18
> **overdrank said:**
> You can check your xorg to see which driver is being used.
```
gksudo gedit /etc/X11/xorg.conf
```


 Well easier this way:```
cat < /etc/X11/xorg.conf |grep Driver
```
 Paste the output here. Also ```
glxinfo |grep direct
``` should print(if all is ok):"**direct rendering: Yes**"

---

### Post by Snitz on 2007-07-18
Yes, it pasted this.

direct rendering: Yes

---

### Post by sad_iq on 2007-07-18
> **Snitz said:**
> It detected it, that's weird, because I cannot use my normal 1280x800 resolution, all I have is 1024x768.

Is this normal?
This is how to correct the problem: [http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by Snitz on 2007-07-18
I just want to know why I'm not being able to use the 1280x800 resolution and true colors? Although in the xorg.conf it shows that the resolution exists but it's not accessible through the screen resolution in the system.

---

### Post by sad_iq on 2007-07-18
> **Snitz said:**
> I just want to know why I'm not being able to use the 1280x800 resolution and true colors? Although in the xorg.conf it shows that the resolution exists but it's not accessible through the screen resolution in the system.
Don't remember exactly...but pressing **ALT**+**CTRL**+ **+** (or -) will change your resolution on the fly...try it!!!

---

### Post by Snitz on 2007-07-18
I got it fixed. My screen resolution is now 1280x800. Just a question, is 60HZ good with that resolution or should I need to use with that resolution?

---

### Post by sad_iq on 2007-07-18
That question...I cannot give an answer...sry...but if it works...it should be ok!!!

---

### Post by Snitz on 2007-07-18
Well if anyone can answer me on this, it would be great. Otherwise Ubuntu is running perfectly. I just have to figure out how to run the php server and mysql server. I'll make a post about it now.

---

