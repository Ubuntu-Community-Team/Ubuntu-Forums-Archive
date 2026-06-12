---
title: "Dell Laditude CPI sound card setup"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by malt^ on 2007-02-28
Me once again,  :)
  This time needing a little clarification on setting up the sound card to work on my Dell Laditude CPI. I found this post on setting it up... [http://www.ubuntuforums.org/showthread.php?t=90869](http://www.ubuntuforums.org/showthread.php?t=90869)
but it seems it glossed over a few things for us Noob's on just what to type in the terminal screen (remember we can't even do DOS let alone Linux). O.o

In the post it has this:

1.) Edit /boot/grub/menu.lst and add acpi=off to the end of the options for the kernel.
2.) Install libsdl.2debian-alsa via Synaptic.
3.) Removed /etc/modprobe.d/alsa-base.
4.) Created /etc/modprobe.d/alsa.
    and put this code in it:
alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236
options snd-cs4236 port=0×530 cport=0×210 isapnp=0 dma1=1 dma2=0 irq=5
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1
 
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
 
alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss
 
options snd cards_limit=1

5.) Added snd-cs4236 to the bottom of /etc/modules

Now my questions are....
For number 1,) Should this read: "Sudo nano /boot/grub/menu.lst" ??? Or What??
For number 2.) Seems straight forward on what to do.
For number 3.) Remove?? How is this done? Noob's like me need a tad more info.
For numer 4.) Create?? Ditto...Little more info on what to type in to "create".
For number 5.) Seems straight forward to do.

---

### Post by benfindlay on 2007-03-01
I have an old dell latitude CPi laptop, and found this thread really useful: [http://www.ubuntuforums.org/showthread.php?t=90336]("http://www.ubuntuforums.org/showthread.php?t=90336")

Also, I couldn't get any version newer than 5.10 to work properly, tried both upgrade from 5.10 to 6.06 and fresh install of 6.06 but no joy!

But with reference to your questions:

1. yeah, its ```
sudo nano /boot/grub/menu.lst
```
2. can do it via synaptic, or in terminal just type ```
sudo apt-get install libsdl.2debian-alsa
```
3. Not sure about this, but if its a file, just type ```
sudo rm /etc/modprobe.d/alsa-base
``` to delete it
4. Again, if its refering to a file, then type ```
sudo touch /etc/modprobe.d/alsa
```
5. Just type ```
sudo nano /etc/modules
``` then scroll to the end and add ```
snd-cs4236
```

---

### Post by malt^ on 2007-03-01
Well regarding getting Ubuntu mounted, I added the max ram it could handle first, did a total wipe of the hard drive and used the 5.10 CD, it installed great-fixed the screen resolution first (couldn't see hardly anything, let alone fix the sound card)....anywho so far its running 100% than it did under Win88SE :D

---

### Post by gliberatore on 2007-12-03
I'm tyring to install 7.1 Feisty on my Dell CPi D266XT (CS4237b sound chip).  I tried the above and still have no sound.  One minor difference I encountered is the version number of 1.2 for the library package.  I even added a "sudo moprobe -v snd-cs4236" into the process.  However, my volume control icon still has a red cross out overlay on it and when I open it, I get a message saying "the volume control did not find any elements and/or devices to control.  This means either you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."  Harware Information does show the Crystal Semiconductor CS-423x sound - SB/WSS/OPL3 emulation and control entries.  
Any ideas?
-Gaetano

---

