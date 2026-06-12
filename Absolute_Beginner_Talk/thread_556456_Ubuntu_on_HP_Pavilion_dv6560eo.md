---
title: "Ubuntu on HP Pavilion dv6560eo?"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by chny on 2007-09-21
Hi. I tried too install Ubuntu on my dv6560eo, I went well too boot the cd. But when the loading was done my screen went black. Nothing happend, I asked a friend of mine if could by my displaycard but he said that Nivida should work well.. 

Do you guys think  I need too wait until the next release of ubuntu? Maybe that version will support my computer..

Will be glad for any help!




System Model: HP Pavilion dv6500 Notebook PC    
BIOS: PhoenixBIOS 4.0 Release 6.1     
Processor: AMD Turion(tm) 64 X2 Mobile Technology TL-60 (2 CPUs), ~2.0GHz
Memory: 2046MB RAM
Page File: 909MB used, 3403MB available
DirectX Version: DirectX 10
DX Setup Parameters: Not found
DxDiag Version: 6.00.6000.16386 32bit Unicode

Card name: NVIDIA GeForce 8400M GS
Manufacturer: NVIDIA
Chip type: GeForce 8400M GS
DAC type: Integrated RAMDAC
Device Key: Enum\PCI\VEN_10DE&DEV_0427&SUBSYS_30CF103C&REV_A1
Display Memory: 880 MB
Dedicated Memory: 113 MB
Shared Memory: 767 MB

---

### Post by jr.gotti on 2007-09-21
How long was the screen black? Sometimes if you let it sit for awhile it pops up. I had Ubuntu running on a Pavilion not too long ago.

Secondly, what install disk did you use? Did you try the alternate install CD? Maybe that will work a little better for you.

---

### Post by mysticmatrix on 2007-09-21
> **chny said:**
> Hi. I tried too install Ubuntu on my dv6560eo, I went well too boot the cd. But when the loading was done my screen went black. Nothing happend, I asked a friend of mine if could by my displaycard but he said that Nivida should work well.. 

Do you guys think  I need too wait until the next release of ubuntu? Maybe that version will support my computer..

Will be glad for any help!




System Model: HP Pavilion dv6500 Notebook PC    
BIOS: PhoenixBIOS 4.0 Release 6.1     
Processor: AMD Turion(tm) 64 X2 Mobile Technology TL-60 (2 CPUs), ~2.0GHz
Memory: 2046MB RAM
Page File: 909MB used, 3403MB available
DirectX Version: DirectX 10
DX Setup Parameters: Not found
DxDiag Version: 6.00.6000.16386 32bit Unicode

Card name: NVIDIA GeForce 8400M GS
Manufacturer: NVIDIA
Chip type: GeForce 8400M GS
DAC type: Integrated RAMDAC
Device Key: Enum\PCI\VEN_10DE&DEV_0427&SUBSYS_30CF103C&REV_A1
Display Memory: 880 MB
Dedicated Memory: 113 MB
Shared Memory: 767 MB

The problem is with your card. 8400gs was released after Feisty was released, and hence the default open-source nv drivers don't yet support your card. It is fixed in Gutsy.

Now you can either
A) Load gutsy beta, to be released in few days
B) Try alternate install CD(text based), switch to Vesa, and install necessary nvidia drivers.

Don't get afraid if you see second step and don't understand a bit of it. If you are ready to spare some hours, the forums would be glad to get the stuff working.

Cheers

EDIT: Nice display of information. If other people can be as descriptive, we would figure out things faster

---

### Post by chny on 2007-09-21
Thanks for fast response!

I sat back for a while, it was like the computer was not responding, and the "bzzz" sound when your cddrive is working went off.. So I assumed the install window didnt popup because of my displaycard. I am gonna try too burn out a new copy now.. just too see if it works.

---

### Post by Pumalite on 2007-09-21
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by chny on 2007-09-21
> **mysticmatrix said:**
> The problem is with your card. 8400gs was released after Feisty was released, and hence the default open-source nv drivers don't yet support your card. It is fixed in Gutsy.

Now you can either
A) Load gutsy beta, to be released in few days
B) Try alternate install CD(text based), switch to Vesa, and install necessary nvidia drivers.

Don't get afraid if you see second step and don't understand a bit of it. If you are ready to spare some hours, the forums would be glad to get the stuff working.

Cheers

EDIT: Nice display of information. If other people can be as descriptive, we would figure out things faster

Okay im downloading the textbased version now.. will try it and come back too you guys! Thanks:)

---

### Post by chny on 2007-09-21
I have installed Ubuntu with the textbased version. I can boot up ubuntu without problems and I can see the UBuntu loading screen, but right after that my screen still go black. I can go intothe "terminal" but what do I do here? How can I install my displaydrivers in kernel/terminal.. The link you gave me said someting about ENVY can i run it from terminal? If so where do I find the directonary?

Maybe I need too configure my network aswell if I have too download displaydrivers?

---

### Post by chny on 2007-09-21
Does anyone know? :S

---

### Post by mysticmatrix on 2007-09-21
> **chny said:**
> Does anyone know? :S

Sorry for my late reply. As you can boot to text based installer, do this

Once in Command Line, type

```
sudo nano /etc/X11/xorg.conf
```

This will open the text editor, nano

Now you have to edit this line

```
Section "Device"
Identifier "nVidia Corporation NVIDIA Default Card"
Driver "[COLOR="Red"]nv[/COLOR]"
BusID "PCI:1:0:0"
Endsection
```


to 

```
Section "Device"
Identifier "nVidia Corporation NVIDIA Default Card"
Driver "[COLOR="Red"]vesa[/COLOR]"
BusID "PCI:1:0:0"
Endsection
```

After this, save the file and restart your computer. This should land you to graphical interface.
Go ahead and tell the results.

Using Nano: Saving Document <ctrl>+<o>
Exiting <ctrl>+<x>

Nano is quite easy to use and self explainatory.

After that, if you get GUI, try getting your internet working(If it is not automatically working).
After that, we shall proceed

---

### Post by chny on 2007-09-21
Hey, thank you so mutch! :D I think I got this allright now.. I have installed Envy and I can edit Nvidia settings in systemtools.. I guess the installation went well! Thanks again:)

---

### Post by mysticmatrix on 2007-09-22
> **chny said:**
> Hey, thank you so mutch! :D I think I got this allright now.. I have installed Envy and I can edit Nvidia settings in systemtools.. I guess the installation went well! Thanks again:)

No problems...
Mark thread as solved when you think you're fine. It would help other people too.

---

