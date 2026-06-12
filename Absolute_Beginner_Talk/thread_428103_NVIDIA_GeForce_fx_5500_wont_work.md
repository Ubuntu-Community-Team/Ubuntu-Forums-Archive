---
title: "NVIDIA GeForce fx 5500 wont work"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by checksignalcable on 2007-04-30
my geforce 5500 wont work it just goes black when loading x but my geforce mx 440 works?



plz help asap

---

### Post by checksignalcable on 2007-04-30
:guitar: :lolflag: :popcorn: im still waiting lol help is greatly appreciated

---

### Post by checksignalcable on 2007-04-30
im on my linux box right now so i would be verry happy to play my music

---

### Post by andnobodyslept on 2007-04-30
Need more info. Which version Dapper, Edgy, Feisty? Have you tried to install the official NVIDIA Drivers? If so how? Does the genetic driver "nv" work? I have the same chipset and it works great. Just need some more info before anyone can help. No one in the forum is psychic so it helps to be patient.

---

### Post by checksignalcable on 2007-04-30
well i have fiesty fawn and no the standard drivers dont work and i might try the nividi official ones..but i dont know how to do that nad btw im running my nv geforce mx 440 which is perfect but my nice card geforce fx 5500 doesent work with linux

---

### Post by andnobodyslept on 2007-04-30
Post your xorg.conf, that should be a good starting place. As for me, I'm still using edgy, basically just found a thread in the forums on installing the official drivers. It is supposed to be a lot easier in Feisty, don't know yet, will find out when I upgrade.

---

### Post by andnobodyslept on 2007-04-30
Try this thread see if it works
[http://ubuntuforums.org/showthread.php?t=420276]("http://ubuntuforums.org/showthread.php?t=420276")

---

### Post by checksignalcable on 2007-04-30
i tried installing the nivida dirvers and i downloaded the .run file to my sektop and then i opened terminal and did this:[IMG]http://i89.photobucket.com/albums/k232/gucci_1/umm.png[/IMG]

---

### Post by koconnor100 on 2007-04-30
watching closely , since my card is identical to his.... :)

Got mine into 80x600 mode before installing proprietory restriced drivers, and 640x480 after installing. 

Still hoping envy will come to the rescue on this ...

---

### Post by andnobodyslept on 2007-04-30
As I said before still using Edgy so I have yet to try to install the drivers so I don't really know what works or not. But I'm going around the forums and doing some googleing and here is what I am finding. Also did you both update to Feisty or do a clean install?
Here is the "official" way to install the restricted drivers in Feisty
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29")

Also checksingnalcable, try running the .run file as root. Just an idea, but with my limited experience with Linux (<1year) it is the stupid easy stuff that you forget that keeps things from working.

Also it is hard to help you with such little info. At least post your xorg.conf, or your X error log.

---

### Post by killmongo on 2007-04-30
it looks like you are trying to run the program from your home directory while it is located in your Desktop directory...

Just drag the file into the terminal and click paste. And make sure you run using sudo

---

### Post by checksignalcable on 2007-04-30
> **andnobodyslept said:**
> As I said before still using Edgy so I have yet to try to install the drivers so I don't really know what works or not. But I'm going around the forums and doing some googleing and here is what I am finding. Also did you both update to Feisty or do a clean install?
Here is the "official" way to install the restricted drivers in Feisty
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29")

Also checksingnalcable, try running the .run file as root. Just an idea, but with my limited experience with Linux (<1year) it is the stupid easy stuff that you forget that keeps things from working.

Also it is hard to help you with such little info. At least post your xorg.conf, or your X error log.

well i cant really post my xorg file because its now corrupt.i kept googeling and now im getting and xorg error on both cards.i know there is a way to recover it and i did back it up but i dont know how to restore it

so im going to try what you said when i get home but as for now im at school and my pc is unbootable.btw it just gives me the same error as the one i get when trying to run my 5500 with a non corrupt config

and if i knew how to post my error log i would but i cant cause i have no idead where to start:popcorn: :lolflag:

---

### Post by andnobodyslept on 2007-04-30
To get everything back the way it should be, next time you boot up, boot into recovery mode from grub. That way all you'll have to work with is the command line and won't have to worry about the X server being a problem.
Once there do
sudo dpkg-reconfigure xserver-xorg
From there you should be able to reconfigure your xconf so at least you might be able to get something to work. 
I'm at work right now, but am planning on doing a clean install of feisty on my linux box when I get home. I have the FX 5500 chipset and will post any results that get.

---

### Post by andnobodyslept on 2007-04-30
Well I did a clean install, and everything worked perfectly, at least it is video wise. The only problem is I can't turn off my internal speakers and only use the line out. But that is for another day. 
Maybe something else will work for you. I'll keep an eye on this thread to see if I can help.

---

### Post by djqz on 2007-05-01
I have a FX 5500  and just upgraded from edgy to feisty. In order to get the restricted drivers to work I had to do the following..

1. Download the latest nvidia drivers (9755) from the website [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)

2. save to my home folder

3. Stop X by pressing ctrl+alt+F2 logging in and type
```

sudo /etc/init.d/gdm stop
```

4.cd to home folder if you need to and run nvidia installer
```
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

be careful with capital letters - it is case sensitive!!

5. Follow instructions in setup program

6. When it finishes, restart X
```
sudo /etc/init.d/gdm start
```

I swear by this procedure as it has got me out of trouble every time I have upgraded my version of ubuntu!!

Good luck

---

