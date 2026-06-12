---
title: "Black screen on start new video card Radeon .."
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by gottifour on 2008-02-20
Hello all...I have installed 7.10 and everything has been working great thanks to all of your information here. I have upgraded to a Radeon HD 2600 xt video card (AGP) and now when I boot to ubuntu I just get a out of range message and then a black screen. I tried dvi to hdmi and dvi to vga same result. I can boot to recovery mode and get to  root@ubuntu : but I dont know what to do, if anything, from here? Does anyone know what I could try? Thanks in advance......d

---

### Post by luisito on 2008-02-20
After you boot in recovery mode try nano /etc/X11/xorg.conf and look at the configuration in this file. The most important part is where it says Section "Device". A safe option is to set Driver to "vesa", which would disable hardware acceleration but would make it work again. At least you can start like this. 

Actually you do not need to boot in recovery mode. If you boot normally, you can then press Ctrl-Alt-F1 to go to a console. After configuring /etc/X11/xorg.conf, press Ctrl-Alt-F7 to go to graphics mode again and Ctrl-Alt-Backspace to reset X11.

---

### Post by macogw on 2008-02-20
or ```
sudo /etc/init.d/gdm restart
``` after you finish editing xorg.conf and that'll restart X and take you straight back to it.

---

### Post by gottifour on 2008-02-20
Thanks so much for the quick replies...This community is the best I've been around. After I change it to vesa and Ctrl-Alt-F7, it just hangs an "the x server is now diabled. restart GDM when it is configure correctly. 


I wasn't sure were to type this...sudo /etc/init.d/gdm restart...Do I have to get back to the root?...Thanks again

---

### Post by luisito on 2008-02-20
To type "sudo /etc/init.d/gdm restart" you just go back to the console where you edited xorg.conf. You go back there with Ctrl-F1.

You may just reboot if unsure. It won't hurt.

---

### Post by luisito on 2008-02-20
Sorry I meant Ctrl-Alt-F1

---

### Post by gottifour on 2008-02-21
I had to go to work for a little while..I'm back now....

After I edit the xorg.conf I push^x to save and asks me if I want to overwrite xorg.conf anf I type Y. It then tells me permission denied. 

Does it matter that all the settings under  device and device # say nvidia? AM I supposed to change the device # too. 

Sorry for so many questions...My previous card was a nvidia and I was using a nvidia driver..

Thanks again...d

---

### Post by gottifour on 2008-02-21
Does this have anything to do with me having a Radeon HD 2600 xt video card?

---

### Post by gottifour on 2008-02-23
Sorry for the bump but I'm really stuck at this point...

After I edit the xorg.conf I push^x to save and asks me if I want to overwrite xorg.conf anf I type Y. It then tells me permission denied.

---

### Post by mickinator on 2008-02-23
Yes it does have to do with the card, the card is cack for linux, I'm using one at the moment, there are no good drivers for it, im just using vesa at the moment until a nice one is developed, all the fixes Ive found dont really work, so vesa is is, no desktop cube!!!

---

### Post by gottifour on 2008-02-23
Thanks for the response...I wonder if a driver will be available in the future? As of now I cant even get a graphical ubuntu at all. I try to put in the vesa drivers but it wont let me save them..Do you know how to do this?

---

### Post by luisito on 2008-02-23
If your card is a Radeon, then nvidia is a very wrong setting. You might have installed the proprietary drivers of Nvidia instead of ATI.

If you want to be able to save xorg.conf you have to edit it with the command:
sudo nano /etc/X11/xorg.conf

It will ask you for your password. I didn't tell you to use sudo before because I thought you were in a root terminal.

---

### Post by gottifour on 2008-02-23
> **luisito said:**
> If your card is a Radeon, then nvidia is a very wrong setting. You might have installed the proprietary drivers of Nvidia instead of ATI.

If you want to be able to save xorg.conf you have to edit it with the command:
sudo nano /etc/X11/xorg.conf

It will ask you for your password. I didn't tell you to use sudo before because I thought you were in a root terminal.


Thanks for the response...I will try it when I get home....The reason I have the nvida drivers is because I had that card before this one. Will the vesa driver still work with this card even though all the other settings say nvidia? 

Thanks again for the response...

---

### Post by luisito on 2008-02-25
> **gottifour said:**
> Thanks for the response...I will try it when I get home....The reason I have the nvida drivers is because I had that card before this one. Will the vesa driver still work with this card even though all the other settings say nvidia? 


The name of the identifier is irrelevant. The important setting is driver in "Device" section.

I can't try here, but I wonder if
```
sudo apt-get install xorg-driver-fglrx
```
would install your Radeon drivers right away. In any case, it should not be hard to set up your card correctly once your graphics start working again.

---

### Post by JoshuaRL on 2008-02-25
Also something you could try before manually configuring your xorg.conf is to go into BIOS and make sure the onboard video card is disabled.  Once you've don that try this from the Recovery Mode is:
```

dpkg-reconfigure -phigh xserver-xorg

```
That will try to reconfigure xorg for your video card.  Just yesterday it worked or a video card I had never heard of before (Matros).  So you might as well give that a try.

---

### Post by gottifour on 2008-02-25
Thanks for the responses..I will try both suggestions right now....

---

### Post by gottifour on 2008-02-25
I used ....dpkg-reconfigure -phigh xserver-xorg and that did get the vesa drivers in there , but now I am getting the restart 6 times blue screen error.. It will show the mouse cursor in the middle of the screen and then it goes back to the terminal..

When I try this ....sudo apt-get install xorg-driver-fglrx

it tells me bad command, should I be at root for this?

Thanks again......I feel like we are making progress..:)

---

### Post by luisito on 2008-02-25
> **gottifour said:**
> I used ....dpkg-reconfigure -phigh xserver-xorg and that did get the vesa drivers in there , but now I am getting the restart 6 times blue screen error.. It will show the mouse cursor in the middle of the screen and then it goes back to the terminal..

This is strange. X seems to be starting now but then something goes wrong. I don't know what.

What do you see when you do cat /var/log/Xorg.0.log|grep EE ? What about cat /var/log/Xorg.0.log|grep WW ?

> 
When I try this ....sudo apt-get install xorg-driver-fglrx

it tells me bad command, should I be at root for this?


It's going to ask you for your password to get root privileges. I don't understand why it doesn't work. It should work in any Ubuntu installation.:confused:

---

### Post by gottifour on 2008-03-10
> **mickinator said:**
> Yes it does have to do with the card, the card is cack for linux, I'm using one at the moment, there are no good drivers for it, im just using vesa at the moment until a nice one is developed, all the fixes Ive found dont really work, so vesa is is, no desktop cube!!!


I cant even get into the ubuntu gui....How did you manage that? I now have the vesa drivers in but it still just keeps showing the cursor in the middle of the screen and flashing back to the cmd prompt. It will do that like 6 times and keep cycling. Any idea what it could be? This is a fresh install. I cant even run the live sessions..

---

### Post by gottifour on 2008-03-10
> **luisito said:**
> This is strange. X seems to be starting now but then something goes wrong. I don't know what.

What do you see when you do cat /var/log/Xorg.0.log|grep EE ? What about cat /var/log/Xorg.0.log|grep WW ?



It's going to ask you for your password to get root privileges. I don't understand why it doesn't work. It should work in any Ubuntu installation.:confused:


I am getting (EE) failed to intialize GLX extenstion (compatible nvidia X driver not found)
                    (WW) the directory "user/share/fonts/X11/cyrillic" does not exsist
 
                     (WW) EDID preferred timing clock 154.00mhz exceeds claimed max 150mhz, fixing

Any idea what that means? It seems like I still have some nvidia drivers or settings still in there. This is driving me crazy I should just put my old nvidia card back in but I still play games on steam trough windows and the hd2600 xt is a pretty good card considering im still on a agp slot...thanks for any help...

---

### Post by Google Spider on 2008-03-10
This thing worked to get my gui back when I screwed it by installing the wrong driver:
> 
sudo dpkg-reconfigure -phigh xserver-xorg (press enter)
startx(press enter)

But your prob looks more complex.

---

### Post by forrestcupp on 2008-03-10
Get to your command line and try this to remove the nvidia drivers:
```
sudo apt-get --purge remove nvidia*
```

Then type:
```
sudo dpkg-reconfigure xserver-xorg
```
This time you're doing it without the -phigh, and you're going to manually configure X, choosing the vesa drivers.  If you put the -phigh in there, it will try to detect it on its own and will give you drivers that don't work with the HD 2600 card.  Trust me, I had an HD 2600 until I got fed up and switched to nvidia.

After doing that, reboot and download [Envy](http://albertomilone.com/nvidia_scripts1.html) to install the latest ATI drivers from their web site.

If you do these things, you should be good to go.

---

### Post by gottifour on 2008-03-11
> **forrestcupp said:**
> Get to your command line and try this to remove the nvidia drivers:
```
sudo apt-get --purge remove nvidia*
```

Then type:
```
sudo dpkg-reconfigure xserver-xorg
```
This time you're doing it without the -phigh, and you're going to manually configure X, choosing the vesa drivers.  If you put the -phigh in there, it will try to detect it on its own and will give you drivers that don't work with the HD 2600 card.  Trust me, I had an HD 2600 until I got fed up and switched to nvidia.

After doing that, reboot and download [Envy](http://albertomilone.com/nvidia_scripts1.html) to install the latest ATI drivers from their web site.

If you do these things, you should be good to go.

Thanks  this got me to a gui..I am trying to install ultimate edition and I have a gui but it looks like it is a low resolution and its kind of hard to read the text. When I try to install the drivers with envy it say my card is compatible and I download them but when I restart it starts giving me the 6 times error again. I can then type startx and it gets me back to this low resolution blurry screen. When I try to change the resolution system-preferences-screen resoulution it will not change...Im kind of confused...does this make any sense to you? Thanks for any help....d

---

### Post by gottifour on 2008-03-12
> **forrestcupp said:**
> Get to your command line and try this to remove the nvidia drivers:
```
sudo apt-get --purge remove nvidia*
```

Then type:
```
sudo dpkg-reconfigure xserver-xorg
```
This time you're doing it without the -phigh, and you're going to manually configure X, choosing the vesa drivers.  If you put the -phigh in there, it will try to detect it on its own and will give you drivers that don't work with the HD 2600 card.  Trust me, I had an HD 2600 until I got fed up and switched to nvidia.

After doing that, reboot and download [Envy](http://albertomilone.com/nvidia_scripts1.html) to install the latest ATI drivers from their web site.

If you do these things, you should be good to go.


Im pretty much fed up with this card..Is there a card you could recommend that is similar to the hd2600? Thanks

---

### Post by forrestcupp on 2008-03-12
> **gottifour said:**
> Im pretty much fed up with this card..Is there a card you could recommend that is similar to the hd2600? Thanks

Well, I got a Geforce 8600 which is comparable to the HD2600.  It runs like a dream.  I had an HD2600 and ditched it because nvidia just works better in Linux.

But there's got to be a way to make it work better than this.  I got my HD2600 working fairly well.  I just had issues running Compiz and OpenGL stuff at the same time.

Can you still get to the Desktop?  If so, try going to System->Administration->Restricted Drivers Manager and see if you can enable the ATI proprietary drivers in there.  It should use the newer drivers you tried to install with Envy.  That's worth a try.  It seems like I may have had to do this after using Envy.  You'll have to restart after enabling in the RDM.

---

### Post by Warmask on 2008-03-18
I'm using Radeon HD 2600 PCI-e.  Conclusion: This card SUCKS under Linux. I've tried this card in multiple distributions and multiple video drivers, it just doesn't work. I love this card under windows, it's a cheap crossfire DX10 card.

My only hope is that eventually there will be an a driver that works for linux.  If anyone finds this driver, or finds a new proprietary release works. plz plz plz post in this forum.  Thank you.

---

### Post by gottifour on 2008-03-18
> **Warmask said:**
> I'm using Radeon HD 2600 PCI-e.  Conclusion: This card SUCKS under Linux. I've tried this card in multiple distributions and multiple video drivers, it just doesn't work. I love this card under windows, it's a cheap crossfire DX10 card.

My only hope is that eventually there will be an a driver that works for linux.  If anyone finds this driver, or finds a new proprietary release works. plz plz plz post in this forum.  Thank you.

I hear ya...I cant get mine to work either..even though mine is agp. I had to go back to a old nvidia card..Ill be waiting for some drivers that will work as well....thanks for all of your previous help guys..

---

### Post by Therion on 2008-03-18
Okay before you two decide to toss your video cards, try this... I had similar issues with my nVidia 8800 and this is what got things straightened out.  This assumes you already have the Restricted Driver installed and enabled in System/Administration/Restricted Drivers Manager.  Double check to make sure the driver is ENABLED there.  If so you're going to manually edit your xorg.conf file as follows:

```
sudo dpkg-reconfigure xserver-xorg
```
Accept all the default settings until you get to the screen where you can choose monitor resolutions.  

Choose three resolutions (no more, no less) that your monitor can use and that are decently high and de-select the ridiculously low ones (like 600 x 480).  Use the arrow keys to move up and down.  Select the resolutions you want to use by putting an " * " in the brackets and remove the " * " from the brackets for resolutions you do NOT want to use.

Remember that the HIGHEST RESOLUTION YOU CHOOSE HERE WILL BE THE NEW DEFAULT RESOLUTION.  Very important!

Save, exit, reboot and pray to whatever heathen deity you worship that this works.  It should.

---

