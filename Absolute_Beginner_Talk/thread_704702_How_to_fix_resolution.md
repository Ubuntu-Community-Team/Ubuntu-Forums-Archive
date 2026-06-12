---
title: "How to fix resolution?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by sanjay135 on 2008-02-22
I just successfully installed Ubuntu 7.10 on my Dell Inspiron e1705 notebook (bought March 2006) and for some reason, the resolution will only display 1600x1200 or less. My screen's default resolution is supposed to be 1920x1200. I've been looking online but the help I've found has all been a bit confusing. I'll continue to look on my own, but some help would be much appreciated.

---

### Post by taurus on 2008-02-22
What graphic card does it have and have you installed any driver for it?

Applications -> Accessories -> Terminal
```
lspci | grep VGA
```

---

### Post by incen on 2008-02-22
Yeah~ check your graphic card first. I had some problem with higher resolution before, too. Mine is Nvidia. Although I could sort of picking up the monitor model in "Screen and Graphic" setting, my Ubuntu just failed to detect both monitors correctly every time. If yours is Nvidia one. Try to go to their website and download the latest driver first. :)

---

### Post by sanjay135 on 2008-02-22
> **taurus said:**
> What graphic card does it have and have you installed any driver for it?

Applications -> Accessories -> Terminal
```
lspci | grep VGA
```
I entered that command and it returned 

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

(After I installed the OS, one of the first things I did was go to the Restricted Drivers Manager and enable my graphics card and wireless card.)

---

### Post by Crooksey on 2008-02-22
```

$ sudo aticonfig --initial

```

Then reboot.

---

### Post by Champagne706 on 2008-02-22
Hi guys !!! I am very new to Linux Ubuntu !! and I'm trying to install my display driver to get max resolution.... I downloaded the new driver for my card from Nvidia.com, but it wont install ! It gives me this error.......

[IMG]http://i24.photobucket.com/albums/c16/Champagne6969/Screenshot.png[/IMG]

I'm not good at all with terminal command yet, and so far Ubuntu has been real easy to understand and fun to use, due to the fact that the GUI is very user friendly compared to other Linux versions such as Debian. :lolflag:

Anyway thanks for the help in advanced ! :)

---

### Post by sanjay135 on 2008-02-23
> **Crooksey said:**
> ```

$ sudo aticonfig --initial

```

Then reboot.
I entered that command and got this message in return.

Found fglrx primary device section
Nothing to do, terminating.

I went ahead and rebooted and I don't believe anything happened. At least, the screen resolution was the same and trying to change it yielded the same dead ends. 

Any other ideas? I really do appreciate the prompt responses.

---

### Post by SpiderGorilla on 2008-02-23
Are you using the Ubuntu install from the ubuntu.com website or are you using the Ubuntu distribution from Dell?

---

### Post by SpiderGorilla on 2008-02-23
> **Champagne706 said:**
> Hi guys !!! I am very new to Linux Ubuntu !! and I'm trying to install my display driver to get max resolution.... I downloaded the new driver for my card from Nvidia.com, but it wont install ! It gives me this error.......

[IMG]http://i24.photobucket.com/albums/c16/Champagne6969/Screenshot.png[/IMG]

I'm not good at all with terminal command yet, and so far Ubuntu has been real easy to understand and fun to use, due to the fact that the GUI is very user friendly compared to other Linux versions such as Debian. :lolflag:

Anyway thanks for the help in advanced ! :)

When you downloaded the file, there should've been some instructions right along-side of it for installation. You need to follow those instructions carefully. Go back to nVidia.com and go through like you're going to download the file again, then you should get those instructions. I'd try to walk you through it, but I'm not sure if there's any changes between versions of the drivers.

---

### Post by sanjay135 on 2008-02-23
> **SpiderGorilla said:**
> Are you using the Ubuntu install from the ubuntu.com website or are you using the Ubuntu distribution from Dell?
I'm using an install from a livecd I have. The computer's nearly 2 years old and I just completed the install the other night.

---

### Post by SpiderGorilla on 2008-02-23
Do you remember where you originally got that LiveCD?

---

### Post by sanjay135 on 2008-02-23
> **SpiderGorilla said:**
> Do you remember where you originally got that LiveCD?
It was part of something called a Linux Identity Set, a small booklet with 32-bit and 64-bit liveDVD's containing Ubuntu 7.10 and the other official versions (Kubuntu, etc.). I bought it because it had really detailed instructions (more so than I had found online) on how to properly partition my hard drive to prepare for Ubuntu because previous attempts would only allow me to do a clean install or partition manually, which I don't have the know-how for.

---

### Post by Champagne706 on 2008-02-23
Hi SpiderGorilla thanks for the response ! I did try to follow the nvidia instructions, and thats the error it gave me ! It tells me to type this in the terminal.... 

sh NVIDIA-Linux-x86-169.09-pkg1.run 

and i get >> sh: Can't open NVIDIA-Linux-x86-169.09-pkg1.run

Please remember I have bad terminal knowledge, I don't know any commands !!!! :-x 

I tried dragging the driver file in the terminal and I get the error the screen shot says that I posted in my first post.

Here is the link to nvidas driver instructions if anyone wants to take a crack at it :confused:

 
[http://www.nvidia.com/object/linux_display_ia32_169.09.html]("http://www.nvidia.com/object/linux_display_ia32_169.09.html")

Thanks guys !!!! Its much appreciated !!

---

### Post by sanjay135 on 2008-02-24
Does anyone think this might be worth a try? Or might it screw things up further?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0")

---

### Post by Champagne706 on 2008-02-24
Anyone ?? :guitar:

---

### Post by Champagne706 on 2008-02-26
Bump !!Hi SpiderGorilla thanks for the response ! I did try to follow the nvidia instructions, and thats the error it gave me ! It tells me to type this in the terminal....

sh NVIDIA-Linux-x86-169.09-pkg1.run

and i get >> sh: Can't open NVIDIA-Linux-x86-169.09-pkg1.run

Please remember I have bad terminal knowledge, I don't know any commands !!!!

I tried dragging the driver file in the terminal and I get the error the screen shot says that I posted in my first post.

Here is the link to nvidas driver instructions if anyone wants to take a crack at it


[http://www.nvidia.com/object/linux_d...32_169.09.html](http://www.nvidia.com/object/linux_d...32_169.09.html)

Thanks guys !!!! Its much appreciated !!
__________________

---

### Post by confused57 on 2008-02-26
> **Champagne706 said:**
> Bump !!Hi SpiderGorilla thanks for the response ! I did try to follow the nvidia instructions, and thats the error it gave me ! It tells me to type this in the terminal....

sh NVIDIA-Linux-x86-169.09-pkg1.run

and i get >> sh: Can't open NVIDIA-Linux-x86-169.09-pkg1.run

Please remember I have bad terminal knowledge, I don't know any commands !!!!

I tried dragging the driver file in the terminal and I get the error the screen shot says that I posted in my first post.

Here is the link to nvidas driver instructions if anyone wants to take a crack at it


[http://www.nvidia.com/object/linux_d...32_169.09.html](http://www.nvidia.com/object/linux_d...32_169.09.html)

Thanks guys !!!! Its much appreciated !!
__________________

Move the Nvidia driver to your home directory...then "Ctrl+Alt+F1" to get to a console...login...then try installing in the console:
```
sudo /etc/init.d/gdm stop
sh NVIDIA-Linux-x86-169.09-pkg1.run
```

May not work, but worth a try...if it does, then:
```
sudo /etc/init.d/gdm start
```

---

### Post by fahadrather on 2008-02-26
go to system>administration>screen and graphics change your monitor from custom to any of the options you want....see if it works...worked for me!!

---

### Post by fahadrather on 2008-02-26
> **fahadrather said:**
> go to system>administration>screen and graphics change your monitor from custom to any of the options you want....see if it works...worked for me!!

restart the computer..

---

### Post by sanjay135 on 2008-02-26
> **fahadrather said:**
> restart the computer..
I've actually tried that many times already, but it keeps asking me for a driver file, which I don't know how to get.

---

### Post by oedha on 2008-02-26
have you done :==> sudo dpkg-reconfigure -phigh xserver-xorg
from terminal ?
what if you change the resolution manually in xorg.conf
sudo gedit /etc/X11/xorg.conf
find under screen section

---

### Post by sanjay135 on 2008-02-27
> **oedha said:**
> have you done :==> sudo dpkg-reconfigure -phigh xserver-xorg
from terminal ?
what if you change the resolution manually in xorg.conf
sudo gedit /etc/X11/xorg.conf
find under screen section
I'm a complete beginner when it comes to Linux and the command line. Could you explain what those do and how I should use them in more detail? I don't want to get in over my head, but I'm willing to learn.

---

### Post by sanjay135 on 2008-02-27
> **oedha said:**
> have you done :==> sudo dpkg-reconfigure -phigh xserver-xorg
from terminal ?
what if you change the resolution manually in xorg.conf
sudo gedit /etc/X11/xorg.conf
find under screen section
Based on the second command you gave me, I looked in my etc file and found my xorg.conf file. Here are some the parts that I think are relevent to my case:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200"
	EndSubSection
EndSection

Do you want me to change the "1600x1200" to "1920x1200"? That's what I'm trying to do with my screen resolution.

---

### Post by sanjay135 on 2008-02-27
> **oedha said:**
> have you done :==> sudo dpkg-reconfigure -phigh xserver-xorg
from terminal ?
what if you change the resolution manually in xorg.conf
sudo gedit /etc/X11/xorg.conf
find under screen section
So I decided to bite the bullet and try it. I entered the command, selected VESA, and then selected all the resolutions that were available to me in Windows. I rebooted and nothing changed. I also tried inserting "1920x1200" in front of "1600x1200" (I looked online and that's what they say to do) and saved and rebooted and again nothing changed. Am I doing it wrong or is my case just particularly diffiicult?

---

### Post by sanjay135 on 2008-02-27
IT WORKS!!! Sweet. Apparently my ATI restricted driver was turned off, so I turned it back on. That alone didn't do it, but then I ran the reconfigure xserver command and made sure 1920x1200 was checked and it worked! 

Thanks to everyone who responded to my pleas!

---

