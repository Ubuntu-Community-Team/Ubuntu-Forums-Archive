---
title: "Running Ubuntu as a Live CD?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by whitedragon551 on 2008-02-25
OK I requested a 32-bit and a 64-bit Ubuntu CD from them and they shipped free. When I put them in it loads everything up. A few things have some errors. Should it just boot straight to a desktop or what? I have never used it before so I dont know.

When I put the CD in each thing loads and it will say OK next to it. There are I think 3 things that get errors next to them and cant be loading It goes through a graphical progress bar thats orange and moves from left to right and back again. After that it just goes to a black screen and nothing shows up. 

Im using a Windows Vista 32-bit laptop with 2Gbs RAM, 120Gb HD, and a GeForce Go 6150 video card with 394Mb of shared VRAM.

I tried downloading the .iso and burned it with Alcohol 120% and check for errors with that and I got the same result as the CD's that I requested.

---

### Post by NightwishFan on 2008-02-25
You should come to a screen with an option that says "Start or Install Ubuntu". If that does not boot to a desktop use the "Safe graphics mode" option below it.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by whitedragon551 on 2008-02-25
I got to that screen and I selected install/run as live CD. Then it goes through the list of things to load and the uvcvideo fails and some micro thing fails. After that it comes to a black screen.

---

### Post by sayakb on 2008-02-25
> **whitedragon551 said:**
> I got to that screen and I selected install/run as live CD. Then it goes through the list of things to load and the uvcvideo fails and some micro thing fails. After that it comes to a black screen.

Well, you should go for the Text mode installation then. It is a bit different from the Live session installation, but you should hardly face any prominent problem.

---

### Post by oldb0y on 2008-02-25
Try the "safe graphics mode".

---

### Post by whitedragon551 on 2008-02-25
Im going to do the safe graphics mode real quick and see what happens. Also is it possible to dual boot Ubuntu and Vista without deleting the Vista partition or installing them in a certain order?

---

### Post by oldb0y on 2008-02-25
A dual-boot is possible, yes. Just google for some good guides.

---

### Post by Duck2006 on 2008-02-25
> **whitedragon551 said:**
> Im going to do the safe graphics mode real quick and see what happens. Also is it possible to dual boot Ubuntu and Vista without deleting the Vista partition or installing them in a certain order?

If it works ok for you. Make some room from within vista, the do the install on the space you made with your vista partitioning.

---

### Post by NightwishFan on 2008-02-25
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by meindian523 on 2008-02-25
+1.Use the Vista partitioner to modify Vista partitions to avoid loss of data.

---

### Post by whitedragon551 on 2008-02-25
It doesnt work in Safe Graphics mode either. What do I do now? Or is it not possible for me to use Ubuntu with my chipset due to incompatibility?

---

### Post by Duck2006 on 2008-02-25
Do a text base install. That is a alternate desktop CD.

---

### Post by whitedragon551 on 2008-02-25
Since Im having troubles running Ubuntu from the CD will it have troubles running after a text based install?

Also is there a tutorial or something to install Ubuntu from a text based CD?

---

### Post by meindian523 on 2008-02-25
provided you are sure your hardware will work with Ubuntu.Ask around for people with similar configurations.Otherwise look to other distros.

---

### Post by Duck2006 on 2008-02-25
> **whitedragon551 said:**
> Since Im having troubles running Ubuntu from the CD will it have troubles running after a text based install?

Also is there a tutorial or something to install Ubuntu from a text based CD?

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

That will give you a text base install.

> meindian523  	
Re: Running Ubuntu as a Live CD?
provided you are sure your hardware will work with Ubuntu.Ask around for people with similar configurations.Otherwise look to other distros.

This mite be good to do as well.

---

### Post by whitedragon551 on 2008-02-25
Is there a list of hardware thats compatible with Ubuntu?

---

### Post by Duck2006 on 2008-02-25
Yes there is, as to where not sure, but if i find it i let you know, if not some one will.

---

### Post by meindian523 on 2008-02-25
Guess this is what you want:

[http://ubuntuhcl.org/index](http://ubuntuhcl.org/index)

and maybe this too

[http://ubuntuforums.org/archive/index.php/t-2457.html](http://ubuntuforums.org/archive/index.php/t-2457.html)

Google is a friend dear.

---

### Post by Duck2006 on 2008-02-25
And here to.

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by whitedragon551 on 2008-02-25
I didnt find my laptop on the list at all. Its a HP Pavilion DV6258SE or a DV6000 series. Maybe its not compatible.

---

### Post by Duck2006 on 2008-02-25
> **whitedragon551 said:**
> I didnt find my laptop on the list at all. Its a HP Pavilion DV6258SE or a DV6000 series. Maybe its not compatible.

You have to look at the hard ware that is in the lap top or desk top. Not the brand of computer.

---

### Post by whitedragon551 on 2008-02-25
I got it to boot fine without doing it in the graphics safe mode thing. All I did was type in boot acpi=off and it worked fine.

Now I know the UVCVideo problem I was having is related to a USB webcam, which is very possible. I have a webcam built into my laptop. The BCM43xx BCM43xx.microcode is a problem with the wireless adapter in my laptop. Its a Broadcom 802.11b/g WLAN. So I cant use the internet with Ubuntu unless there is a driver for the wireless adapter out there. Anyone know where I can find one?

---

### Post by chriswyatt on 2008-02-25
Open up a terminal and type:

```
lspci
```

Then you'll get a list of all the hardware on your PC, look for your Broadcom Wireless Adaptor and get the model numbere e.g. BCM4306.  Armed with that knowledge you could look for an online guide to see if it's compatible.

---

### Post by whitedragon551 on 2008-02-26
I did that and it said BCM94311MCG in the device manager. So now I need a driver for that so I can use the internet in Ubuntu and I also need a driver for my NVIDIA GeForce Go 6150.

Also how do you set the boot configuration to have Vista as the default. I tried the savedefault and I tried changing the number to 5 in the defaults, but everything still defaults to Ubuntu as the main operating system.

---

### Post by meindian523 on 2008-02-26
Grub counts from zero,so if your Vista entry is no 5 in the list,you need to have ```
default 4
```

---

### Post by whitedragon551 on 2008-02-26
Where do I put the default 4 at?

---

### Post by Duck2006 on 2008-02-26
In your menu.lst file change

default         0

default         4

---

### Post by Het Irv on 2008-02-26
> **whitedragon551 said:**
> I got it to boot fine without doing it in the graphics safe mode thing. All I did was type in boot acpi=off and it worked fine.

Now I know the UVCVideo problem I was having is related to a USB webcam, which is very possible. I have a webcam built into my laptop. The BCM43xx BCM43xx.microcode is a problem with the wireless adapter in my laptop. Its a Broadcom 802.11b/g WLAN. So I cant use the internet with Ubuntu unless there is a driver for the wireless adapter out there. Anyone know where I can find one?


You shouldn't have any problems running the restricted drivers for the wireless.  I have a HP Compaq 6720s, and the only problem I have had was getting Compiz to run correctly.  That problem was fixed by a line of code.

---

### Post by whitedragon551 on 2008-02-26
It doesnt say default 0 anywhere. Also I tried running the restricted drivers for WLAN and it turned on and then back off. I dont actually use my own wireless router. Its connected to a hotspot so I dont have the option of hooking up with an ethernet cable.

---

### Post by whitedragon551 on 2008-02-26
I just got it to boot into Vista as a default. Now all I need to do is figure out how to connect to the internet in Ubuntu. The restricted drivers wont work and the WLAN connection thing that is in the top bar as default disappeared. How do I get it back?

---

