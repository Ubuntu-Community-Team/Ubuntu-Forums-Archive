---
title: "Gutsy on Dell 1521 - No Sound"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by will_ship on 2007-10-19
~ Hi

I am brand new to Ubuntu and would like to get some help.

I am dual booting with Windows Vista on a:

 Dell Inspiron 1521

   Processor: AMD Turion 64 X2 Mobile Technology TL-50
   RAM: 2 GB
   Video Card: ATI Radeon X1270
   Sound: SigmaTel HD Audio CODEC


I installed 7.10 Gutsy Gibson on my hard drive and am able to get into it but my sound doesn't work. I guess that I don't have the driver for SigmaTel HD Audio CODEC but i don't know how or where to install it.

Can anyone help me? Please keep in mind that I don't know much about Ubuntu at all.

Thanks   :  )

---

### Post by roderikk on 2007-10-19
If your sound does work in Windows it might just be the case that it is muted. If you press Alt-F2 you go into the 'run' window.

If you then type:    gnome-volume-control

You go to the volume control. Go to Edit -> Preferences and add all the things listed there. See if any of them are muted or on a very low level, also try switching on/off the External Amplifier switch (on the switches tab), that sometimes does the trick.

Good luck!

---

### Post by will_ship on 2007-10-19
Thanks _alot_ for your help.

I made sure it is not on mute on windows but still doesn't work.

When I try to go to volume control from anywhere it says:

------------------------------------------------------------------------------------------------
I_____________________________________________________________X_I
I
I
I    No Volume Control GStreamer plugins and/or devices found
I 
I
I
I
-----------------------------------------------------------------------------------------------

The Volume monitor displays an error message too.

I think that Sigma Tel sound may not be supported or something...

---

### Post by linitrofe on 2007-10-19
I had the same problem, the only way I resolved it was downloading the new alsa drivers, recompile them and install.

---

### Post by arpeggi on 2007-10-19
i've got the same problem. i'm on a dell vostro 1500.
the problem is i don't know how to download and install the new drivers :(

---

### Post by linitrofe on 2007-10-19
Sorry, I didn't read the newbie part. I don't have the EXACT step, but here's my info... anything else just ask.

Download the new alsa drivers from:
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2")

Get the necessary stuff to build the modules:
> sudo apt-get install build-essential linux-source
(I don't really remember if the kernel sources are necessary)

Untar the kernel source at /usr/src
```
sudo tar xjf linux-source-2.6.22.tar.bz2
```

Untar the alsa drivers on... anywhere.... say /tmp
and just:
```
make
sudo make install
```

The drivers will be installed on the wrong directory (/lib/modules/2.6.22-14/update) just move all the contents to the correct one (/lib/modules/2.6.22-14/kernel/sound)

PLEASE! I need feedback with the procedures in order to improve them.
Good Luck!

---

### Post by linitrofe on 2007-10-19
ctpaterson reports similar issues with Inspiron 1520 on:
[http://ubuntuforums.org/showthread.php?t=577469&highlight=1521+gutsy]("http://ubuntuforums.org/showthread.php?t=577469&highlight=1521+gutsy")

And had the needed steps to get the sound working, try that ones too and if the ctpaterson steps works with the Inspiron 1521 please report it directly with him to update the fix list.

(I don't see anything about moving the files, so I prefer his metod)

Oh! after the <sudo make install> you must reboot your machine.

---

### Post by qbox on 2007-10-19
> **linitrofe said:**
> ctpaterson reports similar issues with Inspiron 1520 on:
[http://ubuntuforums.org/showthread.php?t=577469&highlight=1521+gutsy]("http://ubuntuforums.org/showthread.php?t=577469&highlight=1521+gutsy")

And had the needed steps to get the sound working, try that ones too and if the ctpaterson steps works with the Inspiron 1521 please report it directly with him to update the fix list.

(I don't see anything about moving the files, so I prefer his metod)

Oh! after the <sudo make install> you must reboot your machine.

Not working for me.
I have inspiron 1520 
any help?

---

### Post by will_ship on 2007-10-21
I still don't know what to do. * tear* :(

---

### Post by qbox on 2007-10-22
will_ship
Install and uninstall drivers. that worked for me

---

### Post by Luis Macias on 2007-10-23
Hi there, im new to ubuntu, and i have the same pc that u have, and.... i have the solution, please read this page and try the solutions it has, last one worked for me, rememerb to reboot and see if worked after trying everyone, please dont give up, try all of them im sure they will fix ur problem.  Here is teh link [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

by the way, that page is not mine, i founded googling, so good luck! and thanks to the guy who posted that

---

### Post by will_ship on 2007-10-23
Thanks Luis. My sound is now working perfectly. I used the last method like you said.

---

### Post by miguelm on 2007-11-02
Hello, thanks to you the sound is working. It was difficult but it worked.

I have a Inspiron 1721 ( same as 1521 but with a 17' screen )

first i tried the Intel solution for the 1520. Didn't work. What i did:
[I]sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa[/I]

Then I entered this post and realized that the alsa folder in kerenl was in updates and not in sound:

[I]The drivers will be installed on the wrong directory (/lib/modules/2.6.22-14/update) just move all the contents to the correct one (/lib/modules/2.6.22-14/kernel/sound)
[/I]

After restarting the pips of the system works, but still i didn't have sound. so I downloaded the alsa tar:
[I]Download the new alsa drivers from:
[ftp://ftp.alsa-project.org/pub/drive...1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.15.tar.bz2)[/I]
1)untar
2)in the folder: ./configure
3)make
4) sudo make install

reboot

SOUND WORKING.:lolflag::lolflag:

Thankss

I don't know if these are the correct steps, but they worked for me.

---

### Post by Luis Macias on 2007-11-19
Found this in another forum, now i have louder sound!!

sudo apt-get install alsamixergui alsa-tools alsa-tools-gui alsa-oss alsaplayer-alsa

Thanks to huck416, he posted that.

Hope this helps you to improve your oS

---

### Post by madfella on 2007-11-21
Do you mean Method G?? Is that the one everyone's using?

---

### Post by Luis Macias on 2007-11-22
Yes, if u have dell 1520 or 1521 use method g, this last post is after u install method g, and this will give u higher sound.

---

### Post by huck416 on 2007-11-29
Try my tips on my post. Same machine, had same problems. Now it works like a dream.

Huck416

[http://ubuntuforums.org/showthread.php?t=607378&highlight=dell+inspiron+1521](http://ubuntuforums.org/showthread.php?t=607378&highlight=dell+inspiron+1521)

---

### Post by Aximilli on 2008-04-09
I followed the directions here:

> **linitrofe said:**
> Sorry, I didn't read the newbie part. I don't have the EXACT step, but here's my info... anything else just ask.

Download the new alsa drivers from:
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2")

Get the necessary stuff to build the modules:

(I don't really remember if the kernel sources are necessary)

Untar the kernel source at /usr/src
```
sudo tar xjf linux-source-2.6.22.tar.bz2
```

Untar the alsa drivers on... anywhere.... say /tmp
and just:
```
make
sudo make install
```

The drivers will be installed on the wrong directory (/lib/modules/2.6.22-14/update) just move all the contents to the correct one (/lib/modules/2.6.22-14/kernel/sound)

PLEASE! I need feedback with the procedures in order to improve them.
Good Luck!

After rebooting, I have sound, but now my wired network has disappeared, Ubuntu only recognizes that I have wireless. Could moving the contents from /lib/modules/2.6.22-14/update to /kernel/sound have caused this? Please help, this is my girlfriends laptop and I've totally wiped vista, so I gotta make Ubuntu work right for her.

---

### Post by Aximilli on 2008-04-09
I hate to bump like this but I really need help to get this working.

---

