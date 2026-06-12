---
title: "Newb, loving Ubuntu -&gt; but dilemma with google earth"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by mogojoel on 2007-04-29
so a few years back i had a go at mandrake, and quite enjoyed it.
following this i quietly slipped back in to windoze machines, and now after having 3 operating pc's in my house i decided to have another go at the linux-type OS.
Ubuntu has been simply brilliant on this old antique PC i have put it on.
p4 2.2, 1g ram, 3 x 40g hdd (one of which is still bootable to windows) and all the other things that go with a nice home system of 5 (or maybe less) years ago.
i love the new speed it has introduced to this pc and have found myself spending all day messing with it, doing the terminal commands etc. and just getting the feel for things.

the _ONLY_ issue i have had though, is upon firing up google earth, the computer goes to a black screen with text that i am too drunk to read in time and reboots telling me that nautilus has failed (or similar)

im certainly not a complete newb at computers, but as far as linux goes, lets pretend its a language. i speak enough to order a coffee and buy the paper, but not enough to hold a conversation.

can anybody give me any ideas as to what would cause this to happen? or is there a command for error reporting that i could use to give you guys more info to help me troubleshoot?

any help appreciated.

joel 

note- i have a habit of becoming adventurous with my pc's when under the influence of alcohol :lolflag:

---

### Post by madmetal on 2007-04-29
well if you dont have vga drivers installed then google earth wont properly work..
do you have vga drivers installed? and which vga do you have? maybe its too old for google earth..

UAresolved.

---

### Post by mogojoel on 2007-04-29
i assume i have vga installed.
i look at the /system/preferences/hardware and it states that i have the SiS AGP VGA there in the device manager, however it would only be the drivers installed as default by the Ubuntu install CD. Do i need to get a better?! driver for this device? if so, how?

edit- google earth works fine when using it in XP, so the card must be able to support it.

---

### Post by madmetal on 2007-04-29
open a terminal and give
glxinfo | grep render
if ther return is yes then you are ok with 3d rendering..
how have you installed googleearth?

---

### Post by mogojoel on 2007-04-29
google earth was installed using automatix2. it is there.

when i put that command in to terminal, it made the system do the "black screen-text thing" again and rebooted ubuntu.
i clearly have a problem with the vga driver/3d rendering.
i am not entirely sure what the vga card is, but i know it is of the sis 65x_650_740 family.
is there a driver easily available for this? my googling and searching here has only led me to become confused.

---

### Post by madmetal on 2007-04-29
yeap its a problem caused by your vga card/drivers..
searched a while and found this one

> I have a sis card. Xorg is configured to use sis. If I enter glxinfo in a terminal, X crashes and I have to logon again....

ls /usr/lib/xorg/modules/drivers/sis_drv.so --> this drivers comes default with edgy

and in /etc/X11/xorg.conf, section device, driver "sis"
here [http://ubuntuforums.org/showpost.php?p=2095314&postcount=3](http://ubuntuforums.org/showpost.php?p=2095314&postcount=3)

---

### Post by madmetal on 2007-04-29
yeap its a problem caused by your vga card/drivers..
searched a while and found this one

> I have a sis card. Xorg is configured to use sis. If I enter glxinfo in a terminal, X crashes and I have to logon again....

ls /usr/lib/xorg/modules/drivers/sis_drv.so --> this drivers comes default with edgy

and in /etc/X11/xorg.conf, section device, driver "sis"
here [http://ubuntuforums.org/showpost.php?p=2095314&postcount=3](http://ubuntuforums.org/showpost.php?p=2095314&postcount=3)

i hope this would help more..
SiS surely has a linux driver problem..

---

### Post by tommawat on 2007-05-06
Hello everyone!

I am a newbie and am having this problem of GoogleEarth crashing my session.  I had it installed under Edgy but after updating to Feisty, I cannot get it to work.  I assume it has something to do with the 3D issues.  When I upgraded to Feisty, I wanted to try the 3D desktop and clicked the box under the 'preferences' 'desktop effects' but nothing has happened.  I have tried to install through synaptic, automatix2, and from the googleearth website, but all do the same thing.  Under Wine, there are several errors in installation but it eventually loads, but is not function properly.  Anyway, I prefer not to use wine for GoogleEarth.  

So, I guess I want to make sure I have fully uninstalled it 100%.  Then I want to reinstall it and make it work.

Any Ideas?

Here is some info about my computer if it helps:

Dell Inspiron 1000 Notebook
1GB + 256MB RAM
Intel Celeron R 2.20GHZ
SIS 65x/M650/740 PCI/AGP VGA Display
SIS SiS961/2 SMBus Controller

I have ADSL internet and run Feisty.

Thanks in advance!

---

### Post by battleshipterry on 2007-05-26
tommawat you may no longer viewing this thread but google earth running on my fiesty pc crashes I turned off desktop effects under (system prefences desktop effects) and rebooted it works ok now.

---

### Post by tommawat on 2007-06-01
thanks for that battleshipterry!  i dont think i have enabled the desktop effects, but when i go there, there is only a button that says 'click to enable desktop effects' and the two options below are greyed out...but the windows wobble is checked and the window cube is unchecked.  do you know how to turn this off?  i want to but dont know how...

---

