---
title: "no sound"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by jer92 on 2008-01-05
i have a gateway laptop and the sound does not work and the grafix won't work

---

### Post by aktiwers on 2008-01-05
What sound card and what video card does it have?

---

### Post by ubuntu-freak on 2008-01-05
Is it an old laptop? Graphics don't work in what way? Post the specs of your laptop to get real help. 
 
Nathan

---

### Post by jer92 on 2008-01-05
gateway 4530gz
Intel® with 32 MB UMA Video Memory (chipset integrated)

    * 2D hardware acceleration
    * 3D rendering acceleration 

PC2001 compliant AC' 97 audio

is this what u need if not visit here [http://assets.gateway.com/s/Mobile/Gateway/4536GZ/4095sp3.shtml]("http://assets.gateway.com/s/Mobile/Gateway/4536GZ/4095sp3.shtml")

i can't enable visual effects

---

### Post by jer92 on 2008-01-05
here is my spect on my laptop 
[http://assets.gateway.com/s/Mobile/Gateway/4536GZ/4095sp3.shtml]("http://assets.gateway.com/s/Mobile/Gateway/4536GZ/4095sp3.shtml")[http://assets.gateway.com/s/Mobile/Gateway/4536GZ/4095sp3.shtml](http://assets.gateway.com/s/Mobile/Gateway/4536GZ/4095sp3.shtml)
:confused::confused::confused::confused:

---

### Post by ubuntu-freak on 2008-01-05
Has the sound never worked or did it stop working? Did the visual effects ever work before?
 
Nathan
 
P.S. You should rename this thread to 'No sound or visual effects' as some will ignore posts with crappy titles.

---

### Post by jaz.spb on 2008-01-05
**sound** : may be it's ALSA trouble. does ubuntu estimated your card?
**video** : I'm sure that your video card supports special video effects...

---

### Post by jer92 on 2008-01-05
the sound  never worked 
visual effects have never worked 





jeremy

---

### Post by ayenack on 2008-01-05
Try this jeremy. For sound card.

In terminal.
**gksu gedit /etc/modprobe.d/alsa-base**

Add this to the end of the file and reboot.

**options snd-hda-intel position_fix=1 model=3stack**

Reboot. If that does not work you may need to download alsa drivers.

BTW. You can edit your sound card settings using **alsamixer** in terminal.

---

### Post by jer92 on 2008-01-05
i will try it i am on ms right now and may not reload to linex today but i will try it and say how it truned out

---

### Post by ubuntu-freak on 2008-01-05
I agree with ayenack. For whatever reason Ubuntu may not have detected your onboard sound so search synaptic for 'alsa' and make sure the drivers are installed. 
 
Regarding your visual effects problem, are you completely sure they don't work? What do you see when you minimize a window? Have you gone to System>Preferences>Appearances>Desktop Effects and enabled the Extra Effects option? Then move a window around and see if it wobbles.
 
Also, you should sudo apt-get install compizconfig-settings-manager 
 
Then open it in System>Preferences and make sure the cube plugin and rotate cube plugin are ticked. You can also make it semi transparent while rotating by clicking on the cube plugin and going to the Opacity tab.
 
To use the cube plugin hold ctrl alt and the left mouse button, keep them pressed and move your mouse left and right. Or you can  press the left or right keyboard buttons while holding down ctrl alt. 
 
You will see that some plugins ask you to press the 'super' key. That is the key with the windows logo on it near the alt key. 
 
Hope that helps. 
 
Nathan

---

### Post by jer92 on 2008-01-07
when i try to enable effects it says can't enable effects

---

### Post by ubuntu-freak on 2008-01-07
Try running the next Ubuntu release from the CD and see if your sound and desktop effects work. 
 
[http://cdimage.ubuntu.com/releases/hardy/alpha-2/hardy-desktop-i386.iso](http://cdimage.ubuntu.com/releases/hardy/alpha-2/hardy-desktop-i386.iso)
 
Remember it's alpha and will be buggy. If it works better though you should install it.
 
Nathan

---

### Post by jer92 on 2008-01-07
if it works i mite install it

---

### Post by ubuntu-freak on 2008-01-07
I still don't know why you're having so much trouble. I have a similar spec to you, alsa sound and 855gm graphics.
 
Did sound work with the gutsy live cd? Put it in again and check.
 
Nathan

---

### Post by jer92 on 2008-01-08
no it did not

---

### Post by ubuntu-freak on 2008-01-08
Try the next ubuntu release. If that doesn't work give fedora a try. 
 
Nathan

---

### Post by ayenack on 2008-01-08
Probably a silly question. Have you checked your settings in **System>Preferences>Sound** to make sure that the correct sound driver is selected etc.

Also can you paste the outcome of this command. In terminal.

**lspci -v**

This will list the hardware on your PCI bus in your computer so I can get a better idea of the exact model of sound card and video card that you have.

BTW. lspci stands for List PCI and the -v stands for verbose.

---

### Post by barbedsaber on 2008-01-08
and not to be offensive, but sheck if your sound is turned up, if ther is a physical switch on your computer, that it is turned on. you would be amazed how often that helps.

---

### Post by ayenack on 2008-01-09
> **barbedsaber said:**
> and not to be offensive, but sheck if your sound is turned up, if ther is a physical switch on your computer, that it is turned on. you would be amazed how often that helps.

LOL.

Very true. Once went through a whole bunch of attempted fixes only to remember that I had unplugged the cable from the sound card. Had been scratching my head for a good two hours before I remembered.

---

### Post by jer92 on 2008-01-09
the sound is turned up

---

### Post by ubuntu-freak on 2008-01-09
Did you try hardy heron? If your laptop is fairly new the next ubuntu release might work.
 
Nathan

---

### Post by jer92 on 2008-01-09
i have not had time to download it  it tskes about 2 hours

---

### Post by ayenack on 2008-01-10
lspci -v

---

### Post by ubuntu-freak on 2008-01-11
Try this thread
 
[http://ubuntuforums.org/showthread.php?t=443233](http://ubuntuforums.org/showthread.php?t=443233) 
 
And this thread

[http://ubuntuforums.org/showthread.php?t=205449&highlight=ac97](http://ubuntuforums.org/showthread.php?t=205449&highlight=ac97)

There is a link to the bug report site in the 2nd thread. Give them your exact hardware details. 

Nathan

---

### Post by ubuntu-freak on 2008-01-12
Also, try
 
sudo apt-get install gnome-alsamixer
 
Could be muted by default. It's installed into the sound and video menu.
 
Nathan

---

### Post by jer92 on 2008-01-14
i got the graphics working by installing hardy
but the sound won't work

---

### Post by jer92 on 2008-01-17
i found this in the sound
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Rioworks Unknown device 203a
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
	Memory at e0100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

---

### Post by ubuntu-freak on 2008-01-17
Try finding a how-to for compiling your sound driver. Search ac97

---

### Post by ubuntu-freak on 2008-01-18
Anyone know what this guy has to do?

---

### Post by jer92 on 2008-01-18
help is wanted

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
Subsystem: Rioworks Unknown device 203a
Flags: bus master, medium devsel, latency 0, IRQ 10
I/O ports at 1c00 [size=256]
I/O ports at 18c0 [size=64]
Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
Memory at e0100800 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>

---

### Post by ubuntu-freak on 2008-01-18
Try this thread
 
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)
 
Nathan

---

### Post by jer92 on 2008-01-18
it won't install the mixer

---

### Post by ubuntu-freak on 2008-01-18
Type alsamixer in your terminal. You might have to unmute the sound that way.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-20
Try the above solution first. I've not done it it myself but I think you just navigate in the terminal and try to unmute the sound. If that doesn't work, try this thread as one of the forum staff (Sef) posted a possible solution
 
[http://ubuntuforums.org/showthread.php?p=4170211#post4170211](http://ubuntuforums.org/showthread.php?p=4170211#post4170211)
 
Nathan

---

### Post by jer92 on 2008-01-25
i have not recieved any upades for hardy 

help on sound any one

---

### Post by ubuntu-freak on 2008-01-25
You probably need to compile your sound driver. Already posted links concerning that on page 1 or 2. Go to my how-to first and install the essential packages. Some people got sound after installing them. 
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

