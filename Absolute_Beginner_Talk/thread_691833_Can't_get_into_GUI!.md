---
title: "Can't get into GUI!"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by alstroph on 2008-02-09
When I boot I it asks for my username and password in text.. no gui. Then a blue window pops up and says stuff. This is the error report it makes:

/etc/gdm/failsafeXServer: Line 47: [: too many arguments 
Warning: Could not retrieve EDID because get-edid is not installed (1)
: error: this program does not know hot to configure the "10
shared/deafult-x-server doesn't exist" X server
Warning: Could not generate /etc/x11/xorg.conf.failsafe for vesa driver


After that all I get is a command line. I don't want to reformat since I have already downloaded some stuff that would be hard to get back. Is there any way I can just restore everything back to factory settings? What should I do?

---

### Post by KhaaL on 2008-02-09
hmm, did you have a gui before? what happened before that?

have you tried fixing the situation by running **dpkg-reconfigure xserver-xorg -phigh** ?

---

### Post by Ex-windows on 2008-02-09
You could also try using th elive cd and then take a look to see whats going on. 
AS Khaal Mentions try running that commd and and reset everything. Did you run, change, or do anything just prior to this happening??

---

### Post by alstroph on 2008-02-09
Here's what I can remember that I did:

While trying hard to get Beryl working someone recommended that I use Compiz Fusion. I uninstalled Beryl and installed their recommendation. My GUI actually started to perform better for a while, but things messed up again so I figured a restart my machine to try and fix it. When I booted it gave me that error.

I used a program called Envy someone recommended for my driver problem. It seemed to work great.

Here are my specs:

Ubuntu 7.10
Sony Vaio SZ330-P
Pentium Duo Core 2 2.0 Ghz
2 GB DDDR 2
Nvidia Geforce Go 7400 128 MB

---

### Post by fenian on 2008-02-09
First at the command line log in and enter...

> sudo dpkg-reconfigure xserver-xorg

Then reboot with the command...
> 
sudo reboot

If you still have no gui ,at the command line log in and enter...

> sudo apt-get install gdm ubuntu-desktop

---

### Post by alstroph on 2008-02-09
Thanks guys :D. Tried the first suggestion but it turned out to be no good. the second bit of code Fenian posted brought me back. I've never been so happy  to see an 800x600 box in the middle of my screen.

What video drivers should I use before I start going crazy again? :)

---

### Post by overdrank on 2008-02-09
> **alstroph said:**
> Thanks guys :D. Tried the first suggestion but it turned out to be no good. the second bit of code Fenian posted brought me back. I've never been so happy  to see an 800x600 box in the middle of my screen.

What video drivers should I use before I start going crazy again? :)

Hi and have you tried the restricted drivers locate under system, administration. And as mentioned previously you can try Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by alstroph on 2008-02-09
I tried Envy before... but I'm worried they might have been the cause of my problems before. Do you think they could have been?

---

### Post by overdrank on 2008-02-09
> **alstroph said:**
> I tried Envy before... but I'm worried they might have been the cause of my problems before. Do you think they could have been?

Hi and I installed on my son's system last weekend and he has the 7300. I had to use envy to install a older version of the nvidia driver to get his system stable.

---

