---
title: "The Nvidia Card From Hell"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by ritterrav on 2007-10-11
Ok, i have recently been given a Nvidia 6200 PCI (not APG or PCI-E) and i cannnot install the damn thing. I have had to reinstall ubuntu 4 (yes FOUR) times because i always end up with the same error, and i cannot reconfigure xserver to get it back to normal so i can even ask for help here. 

So i have my onboard card, (works fine) then i have the nvidia one. I installed fiesty from the livecd using my onboard, then when it was running i used the restricted drivers to enable it. and after i do that, the Xserver wont boot on ANY card, with the nvidia one, ubuntu wont boot passed the third orange bar, and with the onboard card i get this MESSED up error saying something like, the xserver is not configured correctly...

Right now im using my LIVECD to write this... The recovery menu ONLY works with the ONBOARD card, not the nvidia one. 

So can anyone help me? Plz, i just came back from windows and i get this...

---

### Post by dcstar on 2007-10-11
> **ritterrav said:**
> Ok, i have recently been given a Nvidia 6200 PCI (not APG or PCI-E) and i cannnot install the damn thing. I have had to reinstall ubuntu 4 (yes FOUR) times because i always end up with the same error, and i cannot reconfigure xserver to get it back to normal so i can even ask for help here. 
...........

Try telling people the error, or search for it in the forums for a solution.

---

### Post by ritterrav on 2007-10-11
I did, the error with the onboard card is that it says Xserver is not configured correctly, which makes sense because the xserver is configured for the Nvidia card. But ubuntu wont start with the nvidia card.

---

### Post by overdrank on 2007-10-11
> **ritterrav said:**
> Ok, i have recently been given a Nvidia 6200 PCI (not APG or PCI-E) and i cannnot install the damn thing. I have had to reinstall ubuntu 4 (yes FOUR) times because i always end up with the same error, and i cannot reconfigure xserver to get it back to normal so i can even ask for help here. 

So i have my onboard card, (works fine) then i have the nvidia one. I installed fiesty from the livecd using my onboard, then when it was running i used the restricted drivers to enable it. and after i do that, the Xserver wont boot on ANY card, with the nvidia one, ubuntu wont boot passed the third orange bar, and with the onboard card i get this MESSED up error saying something like, the xserver is not configured correctly...

Right now im using my LIVECD to write this... The recovery menu ONLY works with the ONBOARD card, not the nvidia one. 

So can anyone help me? Plz, i just came back from windows and i get this...

HI and it sounds like a conflict between the graphics card and the onboard graphics.

---

### Post by drbob07 on 2007-10-11
First off, try installing using your nVidia card. I had a similair situation on my old computer.

Ubuntu will not load the appropriate drivers for your nVidia card if you don't install with it, and when you attempt to load the right drivers, it will bork your xorg.conf.

So you need to be able to install off of your nVidia card.

The simplest solution would be to disable onboard grahpics in your BIOS, and then just install off your nVidia card, and never use onboard graphics ever again.

---

### Post by ritterrav on 2007-10-11
I disabled my onboard all the time. But i cannot even install ubuntu, with NVIDIA card running.

---

### Post by RomeReactor on 2007-10-11
Hi. Have you tried **sudo dpkg-reconfigure xserver-xorg**? If not, press CTRL+ALT+BACKSPACE; that will leave you in a console. Then, login if you are asked to, and enter the following:
```
sudo /etc/init.d/gdm stop
```
to stop the display; you can't see it at the moment since you're in a console, but it *is* running.

Then:
```
sudo dpkg-reconfigure xserver-xorg
```
When asked which driver to use for the video card, select **nv**. Otherwise, choose the default settings for everything else.

Once that's finished, if you're not sent to your desktop, enter:
```
sudo /etc/init.d/gdm start
```

Also, I would suggest disabling the integrated card in your PC's BIOS before doing all this. Are you certain the Nvidia card works?

EDIT: Sorry, too slow.

---

### Post by dcstar on 2007-10-11
> **ritterrav said:**
> I did, the error with the onboard card is that it says Xserver is not configured correctly, which makes sense because the xserver is configured for the Nvidia card. But ubuntu wont start with the nvidia card.

Old Nvidia cards require the **nvidia-legacy** package, simply set your system up to use the VESA driver (which will work with virtually EVERY video card) using the procedure below, then use Synaptic to install that package.

Then open a terminal and:
```
sudo dpkg-reconfigure xserver-xorg
```
Select the nvidia driver and answer all the other prompts, when finished do:
```
sudo /etc/init.d/gdm restart
```

---

### Post by ritterrav on 2007-10-11
do i have to be using the Card when i type in that stuff in the recovery mode?

---

### Post by dcstar on 2007-10-11
> **ritterrav said:**
> do i have to be using the Card when i type in that stuff in the recovery mode?

It shouldn't matter, but it is preferable to have it plugged in.

You may also have to install the **discover1** &** xresprobe **packages, they assist in detecting your video hardware when you run the reconfigure command.

---

### Post by zero244 on 2007-10-11
Ive been where you are several times. Do some research on how to do basic editing of your xorg.conf file using nano.
By learning to do this you can get your desktop back and not have to reinstall from scratch.
When your system is running ok with the onboard card make a backup of your xorg.conf file so you can restore it.....or edit it with nano.
I have a 6200 agp card that works fine.....so the card should work.
I even run beryl with that card.........its a tad slower than running beryl on a faster card but it does work ok.
If for some reason you cant get the nvidia card to work......check out Gutsy which is going to be released soon.
The main thing is to learn the basics of getting your xserver running again.
One thing you can do sometimes is if your video card is not working correctly.........edit your xorg.conf file with nano at the black hole terminal and put vesa in the driver=section instead of nvidia.
Its possible that the card might be defective.
I haven't used a pci video card for a long time, I am assuming Ubuntu supports pci video cards.
Good Luck.......and dont give up.

---

### Post by ritterrav on 2007-10-11
Ok, i have tried all of your suggestion and to prevail. i know the card works fine because i used it in Windows. Where is the xorg located so i may get to try that?

---

### Post by RomeReactor on 2007-10-11
The file is located in /etc/X11:
```
gksudo gedit /etc/X11/xorg.conf
```

---

