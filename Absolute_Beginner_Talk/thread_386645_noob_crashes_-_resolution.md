---
title: "noob crashes - resolution"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Vandorius on 2007-03-17
Ok guys i just installed ubuntu but crashed x server mins after. it was my mistake.
i wanted to make resolution from 1024 to 1280x1024 so i searched the forum. Ok i opened terminal and tiped something i cant remember now. Then it asked me if i want vga with bunch of other stuff then in next window it asked me what resolution i want i choose 1280 but then when i restarted x my ubuntu wont start! dammit! :P 

What can i do. Will reinstalling ubuntu be the best solution for a linux noob like me?

---

### Post by taurus on 2007-03-17
Boot into recovery mode from GRUB menu and reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
```
Choose **vesa** as a driver for your graphic card.  When done, reboot.

```
shutdown -r now
```
Now, you need to install a driver for your graphic card and what is it anyway?

---

### Post by Vandorius on 2007-03-17
Thanks for the quick reply mate. i just chose a lame way to repair this with formating!

The next time i try switching the resolution i choose vesa and then 1280x1024?
Is this correct?

i have radeon 9600 graph card do i need to install drivers when im done installing ubuntu again?

---

### Post by DaveyG on 2007-03-17
> **Vandorius said:**
> Thanks for the quick reply mate. i just chose a lame way to repair this with formating!

The next time i try switching the resolution i choose vesa and then 1280x1024?
Is this correct?

i have radeon 9600 graph card do i need to install drivers when im done installing ubuntu again?


does the screen appear to be a too small or too big for the monitor?

Did you edit Xorg.conf?

---

### Post by Sanchopinky on 2007-03-17
I have the same problem right now, my recommended settings are 1280x1024 but the maximum option is 800x600. What do I have to do to get my resolution fixed..? It's a little annoying everything appears too big for the screen.

---

### Post by taurus on 2007-03-17
> **Sanchopinky said:**
> I have the same problem right now, my recommended settings are 1280x1024 but the maximum option is 800x600. What do I have to do to get my resolution fixed..? It's a little annoying everything appears too big for the screen.

Try to install a driver for your graphic card before you increase the resolution for your monitor.

---

### Post by Sanchopinky on 2007-03-17
It says I need to install it as the super user.. how do I switch?

---

### Post by DaveyG on 2007-03-17
Take a look at this thread i posted a few days ago and see if it helps..

[http://ubuntuforums.org/showthread.php?t=384986](http://ubuntuforums.org/showthread.php?t=384986)

---

### Post by taurus on 2007-03-17
> **Sanchopinky said:**
> It says I need to install it as the super user.. how do I switch?

What graphic card do you have on your machine?

---

### Post by Sanchopinky on 2007-03-17
Davey when I ran the program I got this:

[[IMG]http://img379.imageshack.us/img379/6036/screenshotkr4.th.png[/IMG]](http://img379.imageshack.us/my.php?image=screenshotkr4.png)

It didn't really do anything.. 


Btw I am using ATI Xpress 200 series

---

### Post by taurus on 2007-03-17
> **Sanchopinky said:**
> Davey when I ran the program I got this:

[[IMG]http://img379.imageshack.us/img379/6036/screenshotkr4.th.png[/IMG]](http://img379.imageshack.us/my.php?image=screenshotkr4.png)

It didn't really do anything.. 


Btw I am using ATI Xpress 200 series

And that's why I asked which graphic card do you have because his link is for Intel graphic controller.  Since you have an ATI, you can't use "i810" or "915resolution".  Therefore, you need to remove the 915resolution if you just installed it.

Hope this guide helps with your ATI card.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by DaveyG on 2007-03-17
> **taurus said:**
> And that's why I asked which graphic card do you have because his link is for Intel graphic controller.  Since you have an ATI, you can't use "i810" or "915resolution".  Therefore, you need to remove the 915resolution if you just installed it.

Hope this guide helps with your ATI card.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

Sorry... i should of waited until i knew wich card he has :(..

but i installed it and got an error also.. restarted and it was all fine.

---

### Post by Sanchopinky on 2007-03-17
You guys rock! Thanks a lot guys.

---

### Post by Vandorius on 2007-03-17
Ok guys this is how far i got with this.

I have ATI radeon 9600 to fix the resolution to 1280x1024 i installed this 915resolution_0.5.2-4ubuntu1_i386.deb now the resolution is good but runs very very slow.

Please help me out i just installed Ubuntu few hrs ago i just wanna set this graphic card straight. 

I dont even know how to uninstall the package if it isnt right :( 

complete linux noob here

---

### Post by taurus on 2007-03-17
You cannot use 915resolution if you have an ATI card.  Look at the link from my post #11 for instructions on how to install an ATI driver for your card.

If you need to remove 915resolution, run these two command at the prompt.

Applications -> Accessories -> Terminal
```
sudo aptitude remove 915resolution
sudo aptitude update
```

---

### Post by Vandorius on 2007-03-17
Ok it looks like i ve unistaled thiss package. Now what do i do for ATI card ive followed lthe link to ATI card drivers but there isnt anz guide how to install it. Its just a guide to install nvidia there. 

And the drivers link just sazs deb and some link beside.....what do i do with this

Thanks for helping me

---

### Post by taurus on 2007-03-17
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Fiberkneip on 2007-03-17
Hello... My first post on this forum!

I also have a ATI card (x800) and have a resolution "problem". I just installed 
Ubuntu a few hours ago and its the first time I have even touched linux. But it all 
went smooth until I was to change the resolution. I have a normal CRT screen wich I
normaly run in 1152x864, but I only get 1024x768. I had that little ATI issue when
booting up, but this forum helped me along. How do we use those "deb http://www.xxx...." type links? Trying to get the ATI driver...

And thanks... 

This community is the most supportive I have ever seen :)

---

### Post by BillGod on 2007-03-17
I have seen this several times before.  The usual cause of X crashing after changing xorg.conf file is the refresh rates.  Make sure under /etc/X11/xorg.conf you moniter settings are correct.

If you cant boot into gnome hit esc during GRUB bootup and select the safe mode kernel (can't remember off the top of my head what its actually called)

sudo gedit /etc/X11/xorg.conf


Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection


then under your Section "Screen" make sure your default depth is 24.

under 
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

you can always change "1280x1024" to "1280x1024_60" that sets your default refresh rate.  I would start at like 50 and go up by 10's and see what works best.  

I hope this helps.

---

