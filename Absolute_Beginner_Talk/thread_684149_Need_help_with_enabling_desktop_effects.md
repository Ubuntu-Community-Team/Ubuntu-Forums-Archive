---
title: "Need help with enabling desktop effects"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-01-31
Ubuntu 7.10
Compiz fusion
Intel 945 Graphic Card with Intel - Experimental modesetting driver

2 days ago my system was fine, Compiz worked and everything, so I know that it can work.

Then I tried to install a graphic card driver that should work better (i810 driver so that no blue fields anymore appear when effects are applied to certain windows, etc), which resulted in a blank screen after re-booting. After going back to the original driver (Intel - Experimental modestting driver which worked before) I am now unable to enable "custom" effects in System>Preferences>Appearance>Visual Effects. Whenever I try to set it to anything but "none" I get the message "Desktop effects can not be enabled".

I read a lot of threads on this Forum, but none helped, i tried out a whole lot, like
 - reinstalling Compiz, Emerald etc
 - change session to xclient script during login (recommended by somebody to me earlier)
 - trying it without and with xserver-xgl
 - run "sudo dpkg-reconfigure xserver-xorg" to try different setting

I admit I don't understand the effect of these commands, but the have been suggested to me in my earlier post or the situation of the person they were suggested to seemed reasonably close to mine to give it a try.

So, here I am  after a lot of time spent to set my system back to where it once was. I am sure that if I can just enable the "custom" Visual effects it all will run nicely

Here some print out:

When I run compiz

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

Tell me if you need more information

Thanks
Andreas

---

### Post by oedha on 2008-01-31
sudo apt-get update
sudo apt-get install python-compizconfig

i am running on intel 915GM and we have the same output.....but compiz fine...even for additional plugins
for me : xgl is for ATI card and maybe nvidia too

~E~

---

### Post by Djalmahal on 2008-01-31
No, no change after installing python-compizconfig

It's weird, it all worked 2 days before,...
Andreas

---

### Post by oedha on 2008-01-31
mmm.... iam not sure i can help...but i'll try
open synaptic......remove xserver-xgl
then
open console ( ctrl+alt+F2 ), login...and type 
sudo dpkg-reconfigure xserver-xorg
see the options there and payy attention on display
then : sudo /etc/init.d/gdm restart
if it's hang :==> sudo reboot

~E~

---

### Post by ubuntu-freak on 2008-01-31
Why switch to the old "i810" driver? The "intel" one has replaced it. That's how I got xv video playback working with compiz enabled in debian.

Try
 
**sudo dpkg-reconfigure -phigh xserver-xorg**
 
Nathan

---

### Post by oedha on 2008-01-31
your not supposed to use i810.......the experimental one should.
~E~

---

### Post by Djalmahal on 2008-01-31
Ok, nothing changed, the reconfiguring of xserver-xorg didn't change anything, I did that before already, tried with different settings it just doesn't seem to produce an effect.

I hope you guys don't run out of suggestions, ;-)

Andreas

---

### Post by Djalmahal on 2008-01-31
Concerning the i810:

i read it in several post and some issues with video windows turning blue while certain effects were applied as well as problems with Google Earth made me think that there is a better driver.

Experimental driver didn't sound like the final word either, if I get Compiz running agagin I swear I won't mess with my video settings
Andreas

---

### Post by oedha on 2008-01-31
when you did sudo dpkg-reconfigure xserver-xorg, did you change anything ? 
and have you done sudo dpkg-reconfigure -phigh xserver-xorg ? just like #5 said ?

~E~

---

### Post by Djalmahal on 2008-01-31
Yeah, as I said, i tried some variations (whatever seemed to make sense without wanting to stretch it too far), already before you suggested it, to no effeCT.

When I run "sudo dpkg-reconfigure -phigh xserver-xorg" I get the line

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080131204652

Does that mean anything bad? Do you want a "print out" of those files?

Andreas

---

### Post by oedha on 2008-01-31
i did this to my friend with pclos.......
can you open terminal
then type :==> ls -l /etc/X11  <-- see the filename and the date
how many files started with xorg did you have.....
here is the way ( your own risk )
i replace the xorg.conf with the xorg when that computer is ok

wanna do this ?
~E~

---

### Post by antisocialist on 2008-02-01
not hte best way out, but my idea is to reinstall ubuntu ;p

---

### Post by ubuntu-freak on 2008-02-01
> **Djalmahal said:**
> Yeah, as I said, i tried some variations (whatever seemed to make sense without wanting to stretch it too far), already before you suggested it, to no effeCT.

When I run "sudo dpkg-reconfigure -phigh xserver-xorg" I get the line

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080131204652

Does that mean anything bad? Do you want a "print out" of those files?

Andreas

 
It should be okay overwriting as you're using an intel chip and open source drivers. When it asks you which driver you want to use, change it from "i810" on the reconfigure screen to "intel". 
 
Nathan 
 
Edit: If you are on a laptop, make a copy of your xorg incase it doesn't put the synaptic touchpad settings back. Happened to me in debian.

---

