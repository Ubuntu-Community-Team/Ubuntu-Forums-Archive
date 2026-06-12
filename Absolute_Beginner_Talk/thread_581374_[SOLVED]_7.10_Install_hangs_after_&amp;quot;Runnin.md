---
title: "[SOLVED] 7.10 Install hangs after &amp;quot;Running local boot scripts (/etc/rc.local)&amp;quot;"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by bashir on 2007-10-19
Hi all,

My first post since I was waiting for 7.10 to come out.
Downloaded the 64bit desktop iso and started my install.
I ran into the video driver issue, so I removed the splash and quiet parametets and tried the install again.
Now, my problem lies during the install when it gets to "Running local boot scripts (/etc/rc.local)    [OK]".  It just stops.  No drive activity.  My ethernet is unplugged, just incase.
I can hit enter and it takes me to a prompt.  I can switch consoles (ALT-F2 etc) and get another prompt.
But the install just stops there ... I'm not too sure what to do next ?

I have all new hardware and had to wait for 7.10 since my motherboard uses the VT8237S chip.
During the boot, I see it recognise the chip and my sata drives, my ide dvd drive ... it looks all ok but just stops.  The box has 2GB of RAM with shared on-board video of 64MB.  The CPU is an Intel Core2Duo 1.6Ghz E2140.

If anyone can help out, it would be greatly appreciated.
I'm not sure what to do next .....  :(

Thanks,
Bashir.

---

### Post by twiceasworn on 2007-10-19
Hey there,

Sorry to hear you are having some difficulties.  Are you getting any sort of error on the console or it just boots to a terminal?  if it just boots to a terminal then there is probably just an issue with your graphics card not playing nice with the xserver.  if you can get to a normal terminal and log in, try doing a:

```
sudo dpkg-reconfigure xserver-xorg
```

When it asks you for the driver, pick vesa.  This is not a very good driver but it will at least get you to a gui so you can find out how to install the driver for your onboard video.

---

### Post by bashir on 2007-10-19
thanks for the quickly reply twiceasworn.

i ran the code stated and picked vesa.
after a run through of questions, including keyboard and mouse, it then goes back to the ubuntu prompt.

how do i get the install back up and running ?
or am i totally missing something ..... (sorry about the lack of experience)

thanks.

---

### Post by Caffeine_Junky on 2007-10-19
try 

sudo reboot

it will ask for your password, type it and press enter (note: password will be invisable) but it is there.
***************
EDIT: sorry for any confusion my answer caused.  I was just providing an easy way for a beginner to get out of the F1 command line after reconfiguring Xorg and then being stuck at a prompt not knowing how to proceed.
I have been stuck there myself and "startx" would only produce error messages. So rebooting would at least get me "back in the game" so too speak.

---

### Post by bashir on 2007-10-19
> **Caffeine_Junky said:**
> try 

sudo reboot

it will ask for your password, type it and press enter (note: password will be invisable) but it is there.

Thanks Caffeine_Junky for the tip.
It does look like it is the video card.

i tried sudo reboot, but unfortunately it's just a never ending circle ....
couldn't install and back at the prompt again - argh ...

unfortunately, the only OS I have successfully installed is XP and i'd prefer to stay away completely.

---

### Post by pointone on 2007-10-19
Why would you have them reboot and undo the changes made to X.Org?

Try this:

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

Even better, try booting the CD in "safe graphics mode."

If all else fails, you can also try the alternate install CD.

---

### Post by bcasanov on 2007-10-19
I am having the same problem as the orginal poster, except I have a Dell 1420n and instead of using a live CD, I just upgraded from my vanilla Feisty installation.

---

### Post by bcasanov on 2007-10-19
I tried pointone's advice and it worked for me!  Thanks!

---

### Post by Bliepo32 on 2007-10-19
From what I understand, your installation stalls. My suggestion is, that you try the alternate install cd. It could be however, that the installation will succeed, but Ubuntu will still not work.

---

### Post by bashir on 2007-10-19
thanks for the tips so far guys ...

i tried your suggestion pointone, but the GNOME display manager failed to start ....

so i'm downloading the alternate cd and will give that a go.

will keep you posted ...

thanks again,
bashir.

---

### Post by bashir on 2007-10-20
I've found the details for my video card and was wondering where i can confirm if it is actually supported with ubuntu 7.10 ...

it is a VIA Chrome9 HC IGP (rev 01) - VGA compatible PCI 01:00.0 (details from lspci)

thanks ...
bashir.

---

### Post by bashir on 2007-10-20
> **pointone said:**
> Why would you have them reboot and undo the changes made to X.Org?

Try this:

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

Even better, try booting the CD in "safe graphics mode."

If all else fails, you can also try the alternate install CD.

pointone, i successfully got it to run the gui after running gdm restart.
alot of trial and error with reconfiguring xserver-xorg
but after i do the gdm restart and click continue, it goes back to the ubuntu prompt ...

is there anyway to continue with the installation (ie keep going where it left off?)

thanks.
bashir.

---

### Post by bashir on 2007-10-20
all sorted now.

downloaded and installed using the alternate CD and worked first go !!

thanks everyone for getting my first ever Ubuntu pc up and running ... :)

cheers,
bashir.

---

### Post by ghsfr33d0m on 2008-07-22
> **pointone said:**
> Why would you have them reboot and undo the changes made to X.Org?

Try this:

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

Even better, try booting the CD in "safe graphics mode."

If all else fails, you can also try the alternate install CD.

Thanks man, that worked perfect. I was having the same trouble as the other guys.

---

