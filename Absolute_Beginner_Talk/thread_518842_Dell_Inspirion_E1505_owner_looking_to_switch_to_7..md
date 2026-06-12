---
title: "Dell Inspirion E1505 owner looking to switch to 7.04"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Eriks_Knor on 2007-08-06
Greetings folks.
I have a Dell Inspirion E1505 laptop and have been contemplating making it an Ubuntu machine. I have Ubuntu on my PC as a dual boot, separate hard dive. I like what I'm seeing so far, but before I take the next step and install 7.04 on the laptop, I wanted to get some opinions, advice, experiences, etc from any other E1505 owners out there who have taken the plunge.
Thanks for your help in advance.

---

### Post by wolfen69 on 2007-08-06
instead of "maybe" finding someone with the same machine, just post the laptops specs. people here will let you know if it will fly. plus, if you've been using the live cd without incident, it will be fine to install.

---

### Post by tgm4883 on 2007-08-06
E1505, C2D, intell 3945 wireless.  64-bit feisty

Feisty works out of box with this computer.  Install the 915resolution packages from synaptic to get widescreen support (otherwise everything is stretched)

Not a single problem with the system, it runs cool and quiet.  Works like a charm.  I did disable touchpad tapping though as my hands like to play with the touchpad while im typing.

Install was easy and straight forward.  No extra work required here.

:EDIT:

Forgot to mention that I have then intel video card and compiz fusion looks nice with it

---

### Post by dasunst3r on 2007-08-06
The first thing I did when I took my E1505 out of the box was to blow Vista off and install my combination of Ubuntu and Windows XP Pro.  It is a great laptop to run Linux on, especially if you opted for the Intel PRO/Wireless 3945 (abbreviated *ipw3945*) and an nVidia graphics card.  Here's my blog entry about it: [http://www.cyeungrun.com/2007/03/14/new-platform-dell-inspiron-e1505/](http://www.cyeungrun.com/2007/03/14/new-platform-dell-inspiron-e1505/)  Pay particular attention to the *Working with Linux* section because it took me a lot of time to figure that out.

A quick search of e1505 in the forum turned up this link.  You should look at it: [http://ubuntuforums.org/showthread.php?t=297092&highlight=e1505](http://ubuntuforums.org/showthread.php?t=297092&highlight=e1505)

---

### Post by testube_babies on 2007-08-06
The only extra work you might have is if you have the ATi x1300 or x1400 video card, one of the Dell Broadcom 1390 or 1490 wireless cards, or the Intel 4965 wireless card.

But, that being said, there are how-to's on how to make all of the above hardware work, and I don't think many people have run into problems with them.

---

### Post by Eriks_Knor on 2007-08-06
> **wolfen69 said:**
> instead of "maybe" finding someone with the same machine, just post the laptops specs. people here will let you know if it will fly. plus, if you've been using the live cd without incident, it will be fine to install.

You're right of course. Here are my specs:

Inspiron E1505, Intel Core Duoprocessor T2350 (2MB/1.86GHz/ 533MHz)

1GB, DDR2, 533MHz 2 Dimm for Inspiron 6400/E1505

256MB ATI MOBILITY RADEON X1400 HyperMemory, for Inspiron 6400/E1505

Microsoft Windows XP Professional, Service Pack 2, English, for Inspiron

Integrated Broadcom 440x 10/100 Network Cardand Modem, for Inspiron

8X DVD+/-RW Drive for Inspiron 6400/E1505

Dell Wireless 1390 802.11b/g Mini Card (54Mbps), for Inspiron 6400/E1505

---

### Post by Ek0nomik on 2007-08-06
I have a Dell Inspiron E1505 as well.

For your video card:  [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

For your wireless card:  [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Checkmate.

---

### Post by Eriks_Knor on 2007-08-06
Ok, I burned my 7.04 cd, changed the boot order to where the machine boots from the sd\dvd first. I booted from the CD and I checked the CD integrity first. No errors found. I reboot and I choose the start or intall option. Machine reads the disk, then goes to a black screen and will not go any further.
I have a DVD of 6.10, Edgy Eft. that came with a book I bought. Slapped that in, and I can run Ubuntu from it, no problem. My first thought would be to try and burn another CD. My second thought is to install 6.10. In the long run, is it going to matter which I install?

Thoughts?

---

### Post by tgm4883 on 2007-08-06
> **Eriks_Knor said:**
> Ok, I burned my 7.04 cd, changed the boot order to where the machine boots from the sd\dvd first. I booted from the CD and I checked the CD integrity first. No errors found. I reboot and I choose the start or intall option. Machine reads the disk, then goes to a black screen and will not go any further.
I have a DVD of 6.10, Edgy Eft. that came with a book I bought. Slapped that in, and I can run Ubuntu from it, no problem. My first thought would be to try and burn another CD. My second thought is to install 6.10. In the long run, is it going to matter which I install?

Thoughts?

Its your ATI card.  You could get the feisty DVD and it would probably work.  Or do an alternate install

---

### Post by Eriks_Knor on 2007-08-06
> **tgm4883 said:**
> Its your ATI card.  You could get the feisty DVD and it would probably work.  Or do an alternate install

Alternate install?

I am a noob after all....

---

### Post by Ek0nomik on 2007-08-06
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Under the green 'Start Download' button you can check a box to get the Alternate CD instead of the Live CD.

I had to use the Alternate CD to install Ubuntu with my laptop as well.  I prefer the Alternate CD though anyways.  :)

---

### Post by Eriks_Knor on 2007-08-06
Wow...
I've been really impressed with these forums so far. Everyone here has been very helpful. I'm downloading my alternate version of Feisty right now.

---

### Post by Ek0nomik on 2007-08-06
> **Eriks_Knor said:**
> Wow...
I've been really impressed with these forums so far. Everyone here has been very helpful. I'm downloading my alternate version of Feisty right now.

It should install flawlessly.  But, once the installation is over, you will want to look at the thread I pointed out earlier for your ATI X series card.

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by Eriks_Knor on 2007-08-06
Ok,

I ran the alternate install., didn't mess with configuring the network, so I skipped that. Ejected the disk to boot up. The Ubuntu splash came up, progress bar finished, then i have a black screen telling me to log in, then a blue screen with a gray area that says:

Failed to start the X server (your graphical interface) it is likely that it is not set op correctly. Would you like to view the X server output to diagnose the problem.

There also appears to be something similar to a DOS screen that is breaking through in areas of the screen that have the following scrolling down
Error: Microcode "bcm43xx_microcode5.fw" not available or failed to load.
[ 70.908000] bcm43xx: Error: Micrcode "bcm43xx_microcode5.fw not available or load failed.


Uh....help?

---

### Post by Eriks_Knor on 2007-08-06
Just found the thread for this error and am going through the solutions there. Thanks, dudes!

---

