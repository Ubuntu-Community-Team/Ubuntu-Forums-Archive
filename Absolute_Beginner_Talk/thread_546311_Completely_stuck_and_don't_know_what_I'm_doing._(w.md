---
title: "Completely stuck and don't know what I'm doing. (windows/wine)"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by ains on 2007-09-08
Hi all.
Firstly let me just say I don't have a clue what I'm doing or what I've done. Looking back, it probably wasn't the best idea. 

Here's my problem anyway. 
I bought a Philips fwm589 mini hifi today, and there is a USB connection ability for me to play music from my computer. Only snag is that the software required to do this only runs on windows.
Now, I've tried running the setup under wine but it seems to think that the usb cable is not connected, and won't continue with the installation process. I know that there is no problem with my ports and the lights on my hifi light up when I stick the cable in so something's happening there. Maybe some problem with wine?
Is there any way of installing this software from the CD? 
Also if I wanted to switch back to windows XP, and it's not recognizing my hard drive on setup, what can I do if I don't have a floppy drive? I have two CD drives if that's of any relevance. 
I know nothing about computers so feel free to laugh.
Thanks in advance for any help...

ains

---

### Post by mlentink on 2007-09-08
I'm not quite certain what your question is. Do you want help wit getting that Philips thingy to worK (I know I won't be much help)?
Or do you want to get back to Windows? If so, what does your system currently look like? Do you have a dual boot setup?

---

### Post by ains on 2007-09-08
Well I don't think I can get the phillips thing to work.... just won't recognise the connection.
So I guess I want to install windows xp again. I don't have a dual boot setup just a ubuntu installation. 
I can't just go back to windows due to the can't find hard drive / no floppy drive combination. 
Is it possible to setup a dual boot for windows from Ubuntu? 


ty much for response

---

### Post by mlentink on 2007-09-08
Could you explain what you mean with the 'can't find hard drive / no floppy drive combination'? 
Have you tried simply inserting your Windows installation-cd and then rebooting?

---

### Post by ains on 2007-09-08
Yeah that's what I tried to do to start off with.
It told me it couldn't find a hard drive and exited setup.
I read around and people said that you need a floppy drive (i.e.  this topic [http://ubuntuforums.org/showthread.php?t=536041](http://ubuntuforums.org/showthread.php?t=536041)).
As I say I really don't know what I'm doing here..

thankyou

---

### Post by rtr86 on 2007-09-08
> **ains said:**
> Well I don't think I can get the phillips thing to work.... just won't recognise the connection.
So I guess I want to install windows xp again. I don't have a dual boot setup just a ubuntu installation. 
I can't just go back to windows due to the can't find hard drive / no floppy drive combination. 
Is it possible to setup a dual boot for windows from Ubuntu? 


ty much for response

If you want to reinstall windows from scratch and you have a Windows XP CD (must be full not upgrade)  then enter BIOS (usually hit the DEL key on starup) and select CD-ROM as first drive to load in boot priority. Then just reset with CD in drive and reinstall.

---

### Post by HermanAB on 2007-09-08
Hmm, if your Ubuntu is working properly, then don't destroy it to install Windows.  Rather install Virtualbox/VMware and install Windows in that, then Windows can run concurrently in a window.  This way you can experiment with systems in the virtual machine without breaking your base system.

Regarding the Philips:
Display the system log and then plug the USB cable in, to see whether Linux udev detects it:
$ sudo tail -f /var/log/messages
then plug in.

If you see a message about the USB, then there is hope.  If you see nothing, then there is pretty much no hope.

Cheers,

Herman

---

### Post by JohnCub on 2007-09-08
The hard drive you have, is it SATA?  If so, that's why Windows doesn't see it, it will need drivers loaded at boot time.  Otherwise I got nothing.  :P

---

### Post by ains on 2007-09-08
> **HermanAB said:**
> Hmm, if your Ubuntu is working properly, then don't destroy it to install Windows.  Rather install Virtualbox/VMware and install Windows in that, then Windows can run concurrently in a window.  This way you can experiment with systems in the virtual machine without breaking your base system.

Regarding the Philips:
Display the system log and then plug the USB cable in, to see whether Linux udev detects it:
$ sudo tail -f /var/log/messages
then plug in.

If you see a message about the USB, then there is hope.  If you see nothing, then there is pretty much no hope.

Cheers,

Herman

How slow would the virtual windows be? I have a decent amount of RAM and high end CPU (is that correct terminology? heh). Maybe this could be a possible solution :)
The USB is detected in my logs 100%. 
It's just on the Philips installation CD it tells me that I need to plug it in - maybe a problem because I'm going through wine?

Thanks to all replies.

---

### Post by ains on 2007-09-08
> **JohnCub said:**
> The hard drive you have, is it SATA?  If so, that's why Windows doesn't see it, it will need drivers loaded at boot time.  Otherwise I got nothing.  :P

Yeah it is. If I don't have a floppy drive or a USB floppy is there any other way to apply the drivers?

Thankyou!

---

### Post by mlentink on 2007-09-08
> **ains said:**
> It's just on the Philips installation CD it tells me that I need to plug it in - maybe a problem because I'm going through wine?
Heck, yeah!
Please be aware that even though the Wine-people do a terrific job, they're not all-powerful. Linux is a completely different animal from windows, so I'm not at all amazed something doesn't work.

---

### Post by ains on 2007-09-08
Okay so basically I need an install of windows on my computer :D
Hopefully someone will be able to help RE the invisible HD. 
Thanks to all replies as always!

---

### Post by graigsmith on 2007-09-08
do what i do.   When i find a piece of hardware that doesn't work in linux i take it back to the store, and tell them it diddn't work with linux.  

My guess is that the software lets you play music on the speakers without using any of the sound hardware on the computer, so it would be like the sound system could have the entire pc music catalog on your computer without using the computer's own speakers. so you could use the speakers for something else.   If it's like most windows software i know, it's bloated, crappy, and buggy.   and i mean, if this is all it does, why bother? just buy a nice set of speakers for your ubuntu box. and mabey upgrade to a well supported sound card like an audigy or something.  < anyone know of a better sound card for it?

---

### Post by rtr86 on 2007-09-08
> **ains said:**
> Okay so basically I need an install of windows on my computer :D
Hopefully someone will be able to help RE the invisible HD. 
Thanks to all replies as always!

You could actually make your own windows install using nLite and intergrate the drivers on cd, although this can be complicated and you would need to be in windows really to do this. Search for nilite for more info.

Do you have the drivers on a floppy for the SATA drive? I think it would be best to just buy a cheap floppy drive to be honest. Make sure you hit 'f6' on CD load to install 'third party or raid drivers' from the drive.

---

### Post by graigsmith on 2007-09-08
> Yeah it is. If I don't have a floppy drive or a USB floppy is there any other way to apply the drivers?

Thankyou!

No.  Unfortunately. back when Microsoft released xp.  floppy drives were totally obselete, and they totally didn't even care. so when you need to install something like windows xp on a sata drive, you pretty much are forced to go out and buy a floppy disk drive that has NO use today other than installing a driver for sata drives. or possibly updating your bios.  The really bad thing is, that some of the sata drivers cant even fit on a floppy anymore.  (im sorry for your sake that microsoft has NO ability to look into the future)

HMM, there is a possibility that you could burn a new xp cd.  I know some people do a slipstreaming type of thing where they can include special drivers on a copy of xp that they made.  it's called slipstreaming.

---

