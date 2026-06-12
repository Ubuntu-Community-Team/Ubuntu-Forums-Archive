---
title: "Need help swapping in ATI Radeon 7000 video card"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by SlappyPappy on 2008-04-14
A friend gave me an ATI Radeon PCI video card and I'd like to swap it for the nVidia Riva TNT2 that I'm currently using. I'm guessing that I can't just physically swap them and expect to get back to my GUI desktop with the ATI card. 

Do I have to download drivers or is there a way to get back up into the GUI part with at least Generic drivers?

Can someone walk me through or point me to a Howto so I can get up and running with the ATI card?

Thanks for the help.

---

### Post by anewguy on 2008-04-14
I can give you 1 type of answer:

(1) with your existing TNT2 card installed, download "Envy" and install it

(2) swap you cards

(3) power up Ubuntu - if you don't get a GUI or are unable to read it, do ctrl-alt-F1 to switch to a terminal Window and run Envy in terminal mode via "sudo envy -t".  If your GUI is available, just run Envy from you desktop.  Envy will install the appropriate driver for you.

That's the way I had to do it switching from a TNT2 card to an newer nvidia card.  I'm sure there are other ways as well - I'm just passing along what worked for me.

Good Luck!  :)

---

### Post by forrestcupp on 2008-04-14
Don't install nvidia drivers with Envy if you are going to put an ATI card in.  Here's what you need to do.  

Shut down your computer and swap cards.  Then boot to your recovery mode.  If you have proprietary/restricted nvidia drivers installed, type this
```
apt-get --purge remove nvidia*
```

Then type
```
dpkg-reconfigure xserver-xorg
```
To reconfigure X.  When you go through the process, choose the Vesa drivers to guarantee that you will be able to boot to the desktop.  Then reboot.  After you get back to the desktop, you can then worry about getting the right drivers for your ATI.  If it is newer than a Radeon 9800, I suggest using [Envy](http://www.albertomilone.com/nvidia_scripts1.html) to automatically install the latest drivers for you.

---

### Post by james_xxx on 2008-04-14
For older ATI cards like a Radeon 7000 or 9000, you will want to just use the native open source drivers. They are actually quite good, in my opinion. 

You could just go into you /etc/X11/xorg.conf, and under the Device section, you will want to replace "nv" with "ati".  After that, you should be able to power down, install your ATI card, reboot and have X functioning. If not, run 'sudo dpkg-reconfigure xserver-xorg', and you should be good to go.

---

### Post by SlappyPappy on 2008-04-14
Thanks for the help lads. I'm now up and running and wow, there are a lot of screen effects that I wasn't seeing before. It's like installing a whole new OS.

I basically went with what Jimmy boy was saying as he seemed to have the card I'm using on lock.

---

### Post by krash182 on 2008-05-28
if your running 8.04 dont do it.  it is not supported and the drivers will not recognize it.  you will have to remove it.

---

