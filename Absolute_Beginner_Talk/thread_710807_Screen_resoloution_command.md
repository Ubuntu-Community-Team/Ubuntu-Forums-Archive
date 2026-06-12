---
title: "Screen resoloution command"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by White_Sabre on 2008-02-28
Is there a commad for 1440x990 resolution?

---

### Post by taurus on 2008-02-28
See if you can log in with your username and password after pressing <Ctrl><Alt>F2.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Restart X with <Ctrl><Alt>Backspace.

What kind of video card and monitor do you have anyway?

---

### Post by White_Sabre on 2008-02-28
> **taurus said:**
> See if you can log in with your username and password after pressing <Ctrl><Alt>F2.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Restart X with <Ctrl><Alt>Backspace.

What kind of video card and monitor do you have anyway?

I have a Nvidia something and I have a 19" HP w1907 monitor

Whichdriver fo I choose?

---

### Post by Journeyman on 2008-02-28
"nv" is the nvidia drivers (unless you have the restricted driver installed, then it would be "nvidia")

---

### Post by White_Sabre on 2008-02-28
Ok theres no 1440x900 option?

---

### Post by taurus on 2008-02-28
If you're not sure which nvidia card you have, run this command from a terminal or prompt.

```
lspci | grep VGA
```

---

### Post by White_Sabre on 2008-02-28
VGA compatible controller : nVidia Corporation Unknown Device 0422 (rev a 1)


(also I would like to point out that it cant connect to the internet, just incase you didnt realise)

---

### Post by oedha on 2008-02-28
you have to find out this unknown nvidia......
do you have manual book or something....
what is **sudo lshw -short -C display** output ?

---

### Post by White_Sabre on 2008-02-28
Ok,I have no idea as it is the default one heres the output

H/W path                 Device      Class       Description
============================================================
/0/100/1/0                           display     nVidia Corporation

also I have vista, if we could use that to find out?

---

### Post by oedha on 2008-02-28
yes...you can check the exact type there.....:)

---

### Post by overdrank on 2008-02-28
> **White_Sabre said:**
> VGA compatible controller : nVidia Corporation Unknown Device 0422 (rev a 1)


(also I would like to point out that it cant connect to the internet, just incase you didnt realise)

Hi and you can also update pci ids
```
sudo update-pciids
```

---

### Post by White_Sabre on 2008-02-28
Ok how? Ill log onto Vista

---

### Post by White_Sabre on 2008-02-28
ok its a Nvidia GeForce 8400 GS

---

### Post by overdrank on 2008-02-28
> **White_Sabre said:**
> ok its a Nvidia GeForce 8400 GS

Ok have you enabled the restricted drivers located under system, administration. Or you may look at Envy to install the drivers 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by White_Sabre on 2008-02-28
> **overdrank said:**
> Ok have you enabled the restricted drivers located under system, administration. Or you may look at Envy to install the drivers 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

which one is safer? is this system on vista o ubuntu?

---

### Post by overdrank on 2008-02-28
> **White_Sabre said:**
> which one is safer? is this system on vista o ubuntu?

The restricted drivers. :KS

---

### Post by White_Sabre on 2008-02-28
Ok so how do I do this thingy about restricted drivers

---

### Post by overdrank on 2008-02-28
> **White_Sabre said:**
> Ok so how do I do this thingy about restricted drivers

Quote
you enabled the restricted drivers located under system, administration

---

### Post by White_Sabre on 2008-02-28
My hardware doesnt need any restricted drivers
thats what it says

---

### Post by overdrank on 2008-02-28
> **White_Sabre said:**
> My hardware doesnt need any restricted drivers
thats what it says

Ok then I would recommend using Envy that I linked previously. As it has helped other users with that graphics card.

---

### Post by White_Sabre on 2008-02-28
> **overdrank said:**
> Ok then I would recommend using Envy that I linked previously. As it has helped other users with that graphics card.

Do i need a connection on the Ubuntu computer b/c Ubuntu wont connect to my internet :(

---

### Post by overdrank on 2008-02-28
> **White_Sabre said:**
> Do i need a connection on the Ubuntu computer b/c Ubuntu wont connect to my internet :(

Yes you will need a internet connection.

---

### Post by White_Sabre on 2008-02-29
yeah well ubuntu wont connect to it :\ 
anyway sorrry wont be able to access my computer for today and tommorrow

---

### Post by stchman on 2008-02-29
> **White_Sabre said:**
> Is there a commad for 1440x990 resolution?

edit your /etc/fstab and put "1440x900" in the line of resolutions of your xorg.conf, make sure it is the first in the line.

---

### Post by White_Sabre on 2008-03-05
Haha I did it.!!! Thank you all!

---

