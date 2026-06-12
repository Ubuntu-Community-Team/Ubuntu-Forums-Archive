---
title: "ubuntu studio boot problem please help"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by LinuxSoundMan on 2007-11-10
ubuntu studio provides the best linux audio set up ive ever seen. however i have been having some boot issues. I upgraded from gutsy and 9 times out of 10 it gets past the GRUB loader and just as it seems like the welcome screen will pop up instead i get this rainbow colored stripe down the left side of my screen and sometimes no stripe at all, sometimes it just freezes before getting to the welcome screen. I have figured out that  it only happens when it boots using the rt kernel(?)  for some reason i can boot successfully every time using the "generic" kernel(?) which i have to manually choose by escaping into the GRUB menu and selecting it. This is the only major issue i am having with ubuntu studio. this started happening after i upgraded from gutsy. my laptop specs can be found here..

[http://support.gateway.com/s/Mobile/Gateway/200ARC/3501609sp83.shtml](http://support.gateway.com/s/Mobile/Gateway/200ARC/3501609sp83.shtml)

and here is a pic of that lovely rainbow colored anomaly.

[IMG]http://xs.to/xs.php?h=xs121&d=07456&f=PICT0156.JPG[/IMG]

if u cant see it above try this link...

[http://xs.to/xs.php?h=xs121&d=07456&f=PICT0156.JPG](http://xs.to/xs.php?h=xs121&d=07456&f=PICT0156.JPG)


any help with this issue is greatly appreciated. thank you in advance for your support.

---

### Post by matthewcraig on 2007-11-10
This rainbow stripe looks like a problem with the monitor hardware.  Have you called Gateway about this issue?

---

### Post by LinuxSoundMan on 2007-11-10
no i have not called them. i was hoping that i would not have to go that route. the thing is it does boot in to the rt kernel (when it wants to) it very fickle about it. but like i said for the most part it freezes into that color bar. i dont know if gateway will even have any idea how to help me here. but eventually i may break down and give them a call. thanks for the reply.

---

### Post by overdrank on 2007-11-10
> **LinuxSoundMan said:**
> no i have not called them. i was hoping that i would not have to go that route. the thing is it does boot in to the rt kernel (when it wants to) it very fickle about it. but like i said for the most part it freezes into that color bar. i dont know if gateway will even have any idea how to help me here. but eventually i may break down and give them a call. thanks for the reply.

Hi and you may try and reconfigure you xorg from the recovery mode.Using this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by LinuxSoundMan on 2007-11-10
> Hi and you may try and reconfigure you xorg from the recovery mode.Using this command
Code:

sudo dpkg-reconfigure -phigh xserver-xorg


What exactly will this do. pardon my ignorance as i am brand new to linux. thanks for the help.

---

### Post by overdrank on 2007-11-10
> **LinuxSoundMan said:**
> What exactly will this do. pardon my ignorance as i am brand new to linux. thanks for the help.

No problem, this will reconfigure you xorg automatically and hopefully correct the resolution issue.

---

### Post by LinuxSoundMan on 2007-11-10
ahh i see. i wil give that a try. brb

---

### Post by LinuxSoundMan on 2007-11-10
which kernel should i boot into to do this? "rt" or "generic" or does it matter? thanks again

---

### Post by overdrank on 2007-11-10
> **LinuxSoundMan said:**
> which kernel should i boot into to do this? "rt" or "generic" or does it matter? thanks again

I would recommend the recovery mode which should be the next selection down on the list.

---

### Post by LinuxSoundMan on 2007-11-10
ok i  went ahead and did that command in recovery mode and it brought me to the configuration screen and from there i was lost as to what to do. all i saw as a list of resolutions which where quite a few and quite high, am i to delete the ones that my graphics cannot handle? if so do i simply hit delete for the ones i want to get rid of. thanks a lot for your help.

---

### Post by LinuxSoundMan on 2007-11-10
im not sure if anything was "automatically" done. i could be wrong though. all i got was a screen with the list of resolutions. thanks

---

### Post by LinuxSoundMan on 2007-11-10
i just noticed that the highest resolution i can set within ubuntu is 1024-768 which is much lower than the resolutions listed on the configuration screen.

---

### Post by LinuxSoundMan on 2007-11-10
hey where did u go?? HEEELP!!!! please excuse my noobness.:(:confused: i am desperate.

---

### Post by LinuxSoundMan on 2007-11-10
i went ahead and checked the proper resolutions within the xorg configure window. but it seems that is wont stick because it still gave me the same boot rainbow screen and when i get back into the xorg reconfig the resolutions i checked are unchecked. perhaps i will install the driver from gateway. hopefully this will work. thanks anyways for all your help. ive learned a lot from this.

---

### Post by LinuxSoundMan on 2007-11-10
well i found a driver for my graphics card now to install it. is there any proper procedure for this? i will also check to see how much ram graphics is allowed to use. thanks

---

### Post by overdrank on 2007-11-10
> **LinuxSoundMan said:**
> well i found a driver for my graphics card now to install it. is there any proper procedure for this? i will also check to see how much ram graphics is allowed to use. thanks

HI you need not install the drivers for the  intel chipset. You may boot into recovery mode and use the command startx then open synaptic manager and search for the 915 resolution and that may help. Check your xorg also with this command   cat /etc/X11/xorg.conf    and make sure you are using the i810 driver  under the devices section.

---

### Post by LinuxSoundMan on 2007-11-10
i will try that. does it matter if from within ubuntu the archive manager says "archive type not supported" for the graphics driver i downloaded. it is an archive. thanks again.

---

### Post by LinuxSoundMan on 2007-11-10
ok i couldnt install the 915 resolution package from "startx" because i could not connect to the internet but i was lucky enough to be able to boot into rt in normal mode not recovery mode. (sometimes it just boots normally without the rainbow stripe.once logged in i was able to connect to the internet and install the 915 resolution package. however i noticed this in the description. this is quoted directly from the description 

> resolution modification tool for Intel graphic chipset
915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server.

915resolution's modifications of the BIOS are transient.
There is no risk of permanent modification of the BIOS.
This also means that 915resolution must be run every time the
computer boots in order for its changes to take effect.
If you want to automatically set the resolution on each boot
and before X is launched, see /usr/share/doc/915resolution/README.Debian
for information about configuring the provided initscript.

The 915resolution package becomes obsolete with the newer xorg,
especially if you have the xserver-xorg-video-intel package installed.
Newer xorg brings modesetting support by default.

the problem is i cannot find that readme file. 
and nothing seems to have ahppened after installing 915 resolution. 

last...how exactly do i open up the xorg config from cat/etc.x11/xorg.conf  

i cannot find it anywhere. thanks again.

---

### Post by LinuxSoundMan on 2007-11-10
nothing seems to be working. i typed that command from recovery mode (cat etc/x11/xorg.conf) and it said no such file or directory. wierd. it seems as if this will be impossible to overcome. i may have to migrate to another distro but i was hoping i wouldnt have to. also the 915resolution package after downloading and installing is nowhere to be found. i dont know what to do. but thanks a lot for your help. i really appreciate you taking the time to help me. cheers.

---

### Post by LinuxSoundMan on 2007-11-10
is it possible to install ubuntu studio from a usb key drive?

---

### Post by LinuxSoundMan on 2007-11-11
after a fresh install from the dvd everythings working without a glitch. thanks ubuntu and thanks to all who helped me.

---

