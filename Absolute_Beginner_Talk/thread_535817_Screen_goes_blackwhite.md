---
title: "Screen goes black/white"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Canadaboy on 2007-08-27
When I am in Ubuntu after a while the screen goes white and I have to reset...

Any explanations/solutions?

---

### Post by wireddad on 2007-08-27
Completely black and completely white?
 
Mine goes black and white sometimes when certain program is "thinking" under Beryl.

---

### Post by amneziac on 2007-08-27
maybe u need to update your graphics card or sometimes when u just get ubuntu setup, it might be a bit sketchy but it eventually fixes itself

---

### Post by Canadaboy on 2007-08-28
> **amneziac said:**
> maybe u need to update your graphics card or sometimes when u just get ubuntu setup, it might be a bit sketchy but it eventually fixes itself

I think you are right because I did get some new updates for compiz :popcorn:

---

### Post by Canadaboy on 2007-08-28
The updates did not help... I had to reset 10 times in a 2 hour period..

---

### Post by Hobo Joe on 2007-08-28
What is your graphics card and what drivers are you using?

---

### Post by Canadaboy on 2007-08-30
ATI XPRESS 200 (intergrated)

And I got some driver that I dont know (how do I check)

---

### Post by Canadaboy on 2007-11-09
](*,)

This is my second time trying to get Ubuntu + Compiz and then getting the white screen of death.

I tried this in 7.04/7.10

I install Ubuntu, get the restricted drivers for my ATI Radeon Xpress 1100

[-X and then compiz and after a while, white screen!

I tried to do the xorg thing in safe mode but it screwed me :(

I can't find the official drivers on the ATI site and Ubuntu always chooses the wrong one!

:guitar:

---

### Post by meanburrito920 on 2007-11-09
I'm not sure if this is just an ATI driver problem. I get this problem when i log out or switch users and I use nVidia. I still havent found a solution, but I have heard changing the refresh rate of  the monitor helps.

---

### Post by Canadaboy on 2007-11-09
I don't know if this helps but the WSOD occurs at random times, not during special effects.
Like when talking to someone on Pidgin or searching Google images.

---

### Post by Canadaboy on 2007-11-09
This is my second time trying to get Ubuntu + Compiz and then getting the white screen of death.

I tried this in 7.04/7.10

I install Ubuntu, get the restricted drivers for my **ATI Radeon Xpress 1100**

I did this through **Envy**!

[-X and then I got compiz and after a few minutes of talking on Pidgin, WHITE SCREEN!

I tried to do the xorg-config thing in safe mode but it screwed me :(

**I cannot even login because it keeps on going back to the login.**
(I login.... tries to load... back to login... tried to load... back to login.)

I can't find the official drivers on the ATI site and Ubuntu always chooses the wrong one!

:guitar:

---

### Post by Yellow Pasque on 2007-11-10
OK, try:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f
```
and see if that works,

---

### Post by Canadaboy on 2007-11-11
The first line of code said I had the latest version installed.

The second line of code said it found something that was not initialled.

Never the less I can login now.

Lets hope I dont get the WSOD :lolflag:=D>\\:D/

THANK YOU

---

### Post by walleye0406 on 2007-11-20
I have the same  card in my laptop it has worked fine for me, untill i installed java then it had the white screen. Interesting thing is though, the cube still works, and i can tell that every thing else is working. It is almost like the white screen just covers everything except the mouse. does anyone have a solution to this?

---

### Post by Inxsible on 2007-11-20
> **meanburrito920 said:**
> I'm not sure if this is just an ATI driver problem. I get this problem when i log out or switch users and I use nVidia. I still havent found a solution, but I have heard changing the refresh rate of  the monitor helps.
I use NVidia too. I have three users on my computer. Two of them use compiz (A & B). The third one (C) i just created and so it doesnt have compiz enabled.

This is what I have noted:

 i) if i go from A to B or vice versa, I do NOT get the white screen.
ii) If I go from A to C or B to C or vice versa, I get a white screen and the only solution is a hard reset.

I haven't tested this out thoroughly, since I just started doing this last night. Will do some more tonight !

---

### Post by Paul820 on 2007-11-20
I have the same card in my laptop and it works fine with compiz-fusion but i had to install **xserver-xgl** by th advice of one of the threads in this forum. I can't remember where the thread was but you could try that to see if it works for you.

---

### Post by Inxsible on 2007-11-20
> **Paul820 said:**
> I have the same card in my laptop and it works fine with compiz-fusion but i had to install **xserver-xgl** by th advice of one of the threads in this forum. I can't remember where the thread was but you could try that to see if it works for you.I am not sure if it will help, but you can install xgl by
```
sudo aptitude install xserver-xgl
```

---

### Post by Bablefish on 2007-11-20
There was this wiki I followed to get the ATI card on my NC6000 laptop working. Let me tell you I got the biggest fright of my life when I next used my laptop and found that I crashed Xserver. I concider myself lucky that after a quick search of this forum I found a command that would let me reconfigure Xserver, and I did manage to get my laptop working once again. But right now I am thinking twice before I even think of installing that driver again.

---

### Post by rfruth on 2007-12-11
Hardware problem, memtest run okay :confused:

---

### Post by spiderbatdad on 2007-12-11
So... you are dual booting. Did you defrag windows prior to your install of linux? Have you tried ```
sudo dpkg-reconfigure -a
```

---

### Post by wormser on 2007-12-11
I just skimmed your post and did not see what type of video card you have.  It sounds like it crashes when you enable it.  Post the line with your video card.

```
lspci
```

---

### Post by rsambuca on 2007-12-11
Have you run the mem test overnight?  Try that first, get some sleep, calm down, and report back the results!

---

### Post by Canadaboy on 2007-12-11
```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

00:19.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge

00:1b.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 50)

00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)

00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)

00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)

00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)

00:1d.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller

00:1e.0 ISA bridge: ALi Corporation PCI to LPC Controller (rev 31)

00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]

00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c7)

00:1f.1 RAID bus controller: ALi Corporation ULi 5287 SATA (rev 02)

01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]

02:10.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

```
thats what comes up when i typed lspci, my gfx card is in my sig now
and also right now my gfx card isnt enabled but im still getting wsod
and how do I run memtest?

---

### Post by rsambuca on 2007-12-11
You can get to the memtest from the grub menu when you boot up.

---

### Post by Lvcoyote on 2007-12-11
Memtest86 is a utility for testing memory. download it & run it.
If your using the onboard video on your motherboard, try a cheap add on card.
Download a hard drive diagnostic tool available from most hardware manufacturers web sites.  Run it.

---

### Post by sloggerkhan on 2007-12-11
He has radeon xpress integrated graphics? I know people used to have a lot of trouble with them.
However, something I'm curious about:
does ctrl-alt-f4 or other f-keys take you to a terminal when it white screens?
And does it whitescreen before installing fglrx, or after?

---

### Post by Threbus5 on 2007-12-12
Hi,

I read in a couple posts that ATI video cards had problems with Ubuntu.
I do not know that from personal experience just what I read.

Had you considered another video card? (A cheap one.)
If a cheap replacement video card works, great. If it works no better then you at least minimized the cost.

Good luck

---

### Post by RajivNair on 2007-12-12
Hi,

  How did you install your ATI drivers .. did you use the restricted drivers manager by any chance .. the Ubuntu repository doesn't provide a newer version of fglrx ... so its advisable tht you reinstall Ubuntu once again and instead of using the  restricted drivers manager .. install the drivers using [Envy]("http://albertomilone.com/nvidia_scripts1.html") ... its a neat little script for installing your graphics and also it gets the latest drivers and configures the xorg for you ...

Regards,
Rajiv Nair

---

### Post by Teknyk on 2007-12-12
Wait, I have a Radeon Xpress 200 also and all I had to do was enable it in restricted drivers manager.

Granted this gave me issues after an upgrade from Feisty to Gutsy but I think that's because I had been mucking around with it while I had Feisty.

I did do a complete reinstall of Gutsy (mainly to wipe my XP partition) and once I did that I just used the restricted driver manager.

---

### Post by khurrum1990 on 2007-12-12
Ok, tell us in detail what ur hardware configuration is. Tell us everything u know about every hardware connected to ur machine. Ur vga card for example whether its agp or pci express, etc.

---

### Post by Canadaboy on 2007-12-12
This should be all the info bout my GFX card

[http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118_14603_14612%5E14615,00.html](http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118_14603_14612%5E14615,00.html)

---

### Post by Canadaboy on 2007-12-12
ok well first of all i didnt even enable my graphics card at all when i got the white screen of death after multiple reinstallations. So when i reinstalled feisty, i didnt do anything that would enable gfx, i didnt go into restricted drivers manager or used envy (i used envy before and still got wsod as well as when i enabled it in restricted drivers when i was using gutsy) so i believe that its more than the graphics card here.

---

### Post by Canadaboy on 2007-12-14
i just finished the memtest and there were no error:confused:

---

### Post by khurrum1990 on 2007-12-15
> **Canadaboy said:**
> i just finished the memtest and there were no error:confused:
I am sorry that u r having problems. Why not try Kubuntu or Xubuntu 7.10, if u r ok with the desktop environment. If u don't like them then try Linux Mint 4.0. Its based on Ubuntu 7.10 and is pretty much the same, but some people told me that Linux Mint 4.0 works perfectly for them whereas Ubuntu 7.10 doesn't. You could try another distro all together. Seriously though try Linux Mint 4.0, its based on the latest Ubuntu 7.10.

---

