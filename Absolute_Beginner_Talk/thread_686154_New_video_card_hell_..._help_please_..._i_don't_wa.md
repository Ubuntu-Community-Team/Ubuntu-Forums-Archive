---
title: "New video card hell ... help please ... i don't want to re-install"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by ACuriousGuy on 2008-02-02
OK.  I've got an old e-machines computer that had a 64 MG onboard video card.  I installed and Ubuntu ran great except *.avi playback (and other video formats but that was the most common) were in black and white.  I bought a nvidia card (256 MG, GeForce 5500. I installed that today then booted up. Initially I had a balck screen.  OK.  Reboot then change BIOS settings to use PCI card instead of integrated (default choice). Then I reboot.  Upon restart, I see my normal screen, then after a couple of seconds I see the 2 second Loading GRUB screen. After that, it says "starting" (or something like that). then for like 1 second I see something about not being able to configure region 0 for device XXX (some number I can never get). Then it shows the Ubuntu progress bar that normally leads to login screen but all I get is a black screen.

So I go back into BIOS and back to integrated, swap the cable, then it starts but I get a message about proprietary drivers?  I install them, then reboot, BIOS, chagne settings, etc. ... still nothing.  Go back to Integrated, then I get a "running in low display settings" (or something like that).  Now, regardless of which card I use, I can't see the screen.  With the new PCI card, I get five lines of asterisk (the last something about loading from etc/local?).  If I take that card out and use the Integrated card, something has been changed because my screan is just "mush".  I can't see anthying but static.  I hear the login screen and can log-in (althought I can't see my typing). 

I have about 150 gigs of vidoe and music on the computer.  Please tell me there is a way to fix this.  I can return this video card and buy another one if necessary but how do I go back to my old settings?  the PCI type video card is necessary because it's the only slot I have in this machine.

Please .... any help?  Anything I can do to NOT have to re-install Ubuntu?  I've got the CD so if that is required cool.

Oh, sorry.  I'm running 7.1.  As you can tell, hardware is SOOOOO not something I know about.  Any and all help is grearly appreciated.  And thank you in advance.

---

### Post by JoshuaRL on 2008-02-02
Here you go man:

[http://ubuntuforums.org/showthread.php?t=680567](http://ubuntuforums.org/showthread.php?t=680567)
and my last post on page three:
[http://ubuntuforums.org/showthread.php?t=680567&page=3](http://ubuntuforums.org/showthread.php?t=680567&page=3)

Read through to the end and the other thread linked there.  From what I've seen Linux doesn't pay any attention to BIOS settings.  It does it's own hardware detection, and so you'll need to blacklist the onboard video.

---

### Post by overdrank on 2008-02-02
> **ACuriousGuy said:**
> OK.  I've got an old e-machines computer that had a 64 MG onboard video card.  I installed and Ubuntu ran great except *.avi playback (and other video formats but that was the most common) were in black and white.  I bought a nvidia card (256 MG, GeForce 5500. I installed that today then booted up. Initially I had a balck screen.  OK.  Reboot then change BIOS settings to use PCI card instead of integrated (default choice). Then I reboot.  Upon restart, I see my normal screen, then after a couple of seconds I see the 2 second Loading GRUB screen. After that, it says "starting" (or something like that). then for like 1 second I see something about not being able to configure region 0 for device XXX (some number I can never get). Then it shows the Ubuntu progress bar that normally leads to login screen but all I get is a black screen.

So I go back into BIOS and back to integrated, swap the cable, then it starts but I get a message about proprietary drivers?  I install them, then reboot, BIOS, chagne settings, etc. ... still nothing.  Go back to Integrated, then I get a "running in low display settings" (or something like that).  Now, regardless of which card I use, I can't see the screen.  With the new PCI card, I get five lines of asterisk (the last something about loading from etc/local?).  If I take that card out and use the Integrated card, something has been changed because my screan is just "mush".  I can't see anthying but static.  I hear the login screen and can log-in (althought I can't see my typing). 

I have about 150 gigs of vidoe and music on the computer.  Please tell me there is a way to fix this.  I can return this video card and buy another one if necessary but how do I go back to my old settings?  the PCI type video card is necessary because it's the only slot I have in this machine.

Please .... any help?  Anything I can do to NOT have to re-install Ubuntu?  I've got the CD so if that is required cool.

Oh, sorry.  I'm running 7.1.  As you can tell, hardware is SOOOOO not something I know about.  Any and all help is grearly appreciated.  And thank you in advance.

HI and welcome, you can try and boot into recovery mode which is usually the second choice in the grub. The reconfigure your xorg with the nvidia graphics care installed with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` hopefully this will get you to a GUI, Desktop. Good luck.

---

### Post by JoshuaRL on 2008-02-02
> **overdrank said:**
> HI and welcome, you can try and boot into recovery mode which is usually the second choice in the grub. The reconfigure your xorg with the nvidia graphics care installed with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` hopefully this will get you to a GUI, Desktop. Good luck.

That's a good idea, but I'm almost sure that the issue is that Ubuntu is reading the onboard video card instead of the new one.  Not sure if this is considered a bug or not, but I think that if you install on an onboard and then upgrade afterword, it won't realize that and it'll have issues.  You need to blacklist that onboard card to get it to work.

---

### Post by dcstar on 2008-02-02
> **JoshuaRL said:**
> That's a good idea, but I'm almost sure that the issue is that Ubuntu is reading the onboard video card instead of the new one.  Not sure if this is considered a bug or not, but I think that if you install on an onboard and then upgrade afterword, it won't realize that and it'll have issues.  **You need to blacklist that onboard card to get it to work.**

No, you simply disable the onboad in the BIOS (virtually all BIOSs have this option).

Just use the Nvidia card, follow the previous instructions about using dpkg-reconfigure and select the "VESA" driver - that will work with **all** video cards.

Once the system boots up install the appropriate Nvidia restricted driver (use the "Envy" third-party software if you like) and then things should work.

---

### Post by JoshuaRL on 2008-02-03
He already tried that.  It didn't work, it's all up there in the OP.  I'm sure I'm right.  Have you read all those links?  They're talking about his card too.

---

### Post by dcstar on 2008-02-03
> **JoshuaRL said:**
> He already tried that.  It didn't work, it's all up there in the OP.  I'm sure I'm right.  Have you read all those links?  They're talking about his card too.

**He** has not mentioned using the VESA drivers (or reading those links), the OP has not responded to the various mix of useful replies and the not so useful ones.

---

### Post by JoshuaRL on 2008-02-03
Alright man, all I know is it ain't worth arguing over.  We'll see what helps him.

Peace.

---

### Post by ACuriousGuy on 2008-02-03
Just for a quick update. When I posted last night it was through the bootable CD (because I didn't have a screen using the hard disk). I wasn't able to try anything (couldn't see the web if I was trying the solutions). I've borrowed a laptop today so I'll be able to work on it today (probably in a hour or so).

thanks again for the help guys. I'll let you know what happens and which method works to get me back up and running.  Thanks again.

---

