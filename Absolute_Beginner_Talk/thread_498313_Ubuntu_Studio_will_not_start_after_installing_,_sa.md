---
title: "Ubuntu Studio will not start after installing , says X server had a problem"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-07-11
I installed ubuntu studio an a Dell Inspiron 1300 (widescreen 1280*800). 
at the end of the installation process it asked me to choose the resolutions accepted by the x server, there were three resolutions checked ( i believe, 1024*728; 800*600; 640*480 - not sure about the last one) . I also checked 1280*800. so , there were four before i continued.

after the setup was completed , i restarted and it said the x server cannot be started . i tried editing the xorg.conf file , but , can you believe it, it was at first empty and shortly after the text of an error appeared and i could edit it, as if that was the xorg.conf.

then i exited and from that point it prints out every couple of seconds this message:

[ 530.214000] bcm43xx: Microcode "bcm43xx_microcode5.fw" not available or load failed

there's a different number every time this appears .. i mean [ 530.214000] the numbers there change.
what can i do to get the system started?

thanks

---

### Post by sab0403 on 2007-07-11
The number is a timecode, it's normal that it would change.

Other than that, could you post your xorg.conf file? You can get it by typing```
sudo nano /etc/X11/xorg.conf
```Can you get a command line?

---

### Post by sab0403 on 2007-07-11
Also it seems (by some quick googling) that the bmc43xx is a network driver, not something related to video.

Let me check how to remove it and I'll be back.

---

### Post by panti19 on 2007-07-11
thanks for the reply,

well, i cannot type the whole xorg.conf file since it's a long one :P

but, i can see that the "Generic Video Card" has a vesa driver, so i don't see why it doesn't start.

that network card must be to blame..
still it says the x server has the problem after the loading screen

---

### Post by panti19 on 2007-07-11
also in the "screen" section, there are the 4 resolutions i picked.

---

### Post by sab0403 on 2007-07-11
Ok, try booting to the command line. Get to the GRUB menu (if Ubuntu's your only OS installed, you'll have to press <Esc> when asked), and then choose the "recovery" option (or something similar). Do you have a floppy available? You could try copying the xorg.conf file to a floppy and then posting it here...

Perhaps also doing:```
sudo dpkg-reconfigure xorg-xserver
```This *should* give you the generic X interface... just choose the default option at every point and you should be set.

---

### Post by panti19 on 2007-07-11
i don't have a floppy :(


i did dpkg-reconfigure xorg-xserver
and this appeared:

Package 'xorg-xserver' is not installed and no info is available.
Use dpkg --info (= dpkg......
and dpkg --contents...
/use/sbin/dpkg-reconfigure: xorg-xserver is not installed
:confused:

---

### Post by sab0403 on 2007-07-11
hmm. Try flipping it - instead of xorg-xserver, xserver-xorg.

I can't seem to remember which one it is... :oops:

---

### Post by stepan2 on 2007-07-11
it is xserver-xorg

---

### Post by brennydoogles on 2007-07-11
> **sab0403 said:**
> hmm. Try flipping it - instead of xorg-xserver, xserver-xorg.

I can't seem to remember which one it is... :oops:

It is the second ;OP . The bcmxx driver is for broadcom wireless cards (I'm assuming it's a laptop) and it is very buggy. There are several threads on the forum for it, with [ this]("http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306") seeming to be the best one so far. Just make sure you have the same card, and then you should be good to go!!

---

### Post by shaft350x on 2007-07-15
I'm experiencing the same problem as the OP.  Bad X-server, and also have a laptop with the infamous broadcom issue.  I've looked through the x-server log and I don't recall seeing where it was hanging up, but I'm not really all that savvy when it comes to this.  I'll try to get in to the x-server and see if I can't make some changes like suggested.

---

### Post by Pocadotty on 2007-07-15
shaft350x

chances are your problem is with restricted kernel modules.

when you boot your computer choose via grub the generic kernel.

you should be able to boot into ubuntu that way, but your likely going to want the Low-latency kernel, otherwise why use Ubuntustudio?

1. bring up Synaptic package manager.  System->Administration->Synaptic package manager.

2. search "restricted kernel" to narrow down packages

3. add the "linux-restricted-modules-lowlatency" package.

What that will do is enable the lowlatency kernel to use restricted (non-open source/GPL) kernel modules (aka. "drivers").

Your problem happened to me when I installed Ubuntustudio, because of my NVIDIA video card.  the above stuff fixed it.  Its the same procedure regardless of whatever restricted modules you are doing.


I hope this fixes your problem... sorry I couldn't give you a terminal command... im a GUI kind of guy

cheers,
:guitar:

---

### Post by shaft350x on 2007-07-15
I followed the instructions above and I am happy to report I am now posting from Ubuntu Studio!

Thanks!

---

### Post by oiduts on 2007-07-31
I'm having the same problem on my Compaq Presaio R4115 laptop, and I'm unable to boot into the generic kernal either.

I need line commands.

Can you help? (please)

---

