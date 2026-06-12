---
title: "Cant install - Monitor switches off"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by CTR_Chris on 2007-10-01
OK so I make my bootable CD, boot from it and get my first Ubuntu menu up. WOOP WOOP!

So I click install and it starts loading, after a while my monitor stops recieving signal from video card and it switches into power saving mode.

Ok so I reboot back to the menu, and this time i try option 2, the one with safe graphics mode...but again this does the same thing.

All though the moitor goes off, when the Cd has finished running I cant what I assume is Ubuntu loading music.

HELP! Ive searched the forum but cant find this problem.

Ive tried both DVI ports on my video card and neither seem to work

What am I doing wrong ?

---

### Post by SpiritIsReality on 2007-10-01
howdy
edit:don't listen to the bull about the live cd workin.I'm fairly sure you need to try the alternate cd. from here.
[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/) or you could try the gutsy release here
[http://cdimage.ubuntu.com/gobuntu/daily/current/](http://cdimage.ubuntu.com/gobuntu/daily/current/)
(I'm about the last one to listen to. but ...
If you figure the install went ahead, you could try using the live cd and choose the recover broken system. If you get to a login prompt, log in and try running this )
```
sudo dpkg-reconfigure xserver-xorg
```then answer the questions the best you can. Most times choosing the default,
the one it has chosen already, will work. To be safe you could use the vesa driver.
It would help to know your monitor's vertical and horizontal refresh rates, and choose the ...not the simple, or the medium, but the last option, for resolution.
expert or something like that. The name eludes me right now.
then after that you can run (type in and then press enter) ```
sudo shutdown -r now
``` to restart your computer.sudo shutdown -h now, to shut down.
If that doesn't get you a graphics user interface (gui) you could try installing with
the alternate cd and then probably have to run the sudo dpkg-reconfigure xserver-xorg  
Some links that might be helpful:
[https://help.ubuntu.com/community/HelpOnInstalling/TroubleShooting?action=fullsearch&context=180&value=video&titlesearch=Titles](https://help.ubuntu.com/community/HelpOnInstalling/TroubleShooting?action=fullsearch&context=180&value=video&titlesearch=Titles)
[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28video%29]("https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28video%29")
[https://help.ubuntu.com/community/Video?highlight=%28video%29](https://help.ubuntu.com/community/Video?highlight=%28video%29)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=trouble&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=trouble&titlesearch=Titles)
you can either go to your monitor's manufacturer web page, or google the name and model number of your monitor, and horiz vert.
buds

---

### Post by Hospadar on 2007-10-01
Also, try making sure that the power-saver modes arn't set wierd, this seems unlikely but you never know.  go to Preferences->Power Options and Preferences->Screensaver.

Probably something above will be more helpful, but you never know

---

### Post by jordanmthomas on 2007-10-01
One last dumb suggestion:  If your video card has two outputs, try using the other.  I've had certain other operating systems fail to start their display if I wasn't using a particular output on my video card.

Like Hospadar said, it's more likely to be something like above.

---

### Post by CTR_Chris on 2007-10-02
> **jordanmthomas said:**
> One last dumb suggestion:  If your video card has two outputs, try using the other.  I've had certain other operating systems fail to start their display if I wasn't using a particular output on my video card.

Like Hospadar said, it's more likely to be something like above.

I did say I have tried both already


Bit of a pain because I cant get into anything to change anything

---

### Post by rjs82vette on 2007-10-02
When you get to the boot menu look at the bottom of the screen and press the key for VGA.... I think it is F4, that will use the vesa driver and your monitor will stay on. 

I have to do this everytime I load Ubuntu........

---

### Post by CTR_Chris on 2007-10-02
Ive already tried F4 and selecting a few VGA screen modes and this dosnt have any effect.

I click start or install, I get the orange bar sliding left to right for a while, then after a minute or 2 the screen says it is no longer recieving a signal.

A minute or 2 later i can then hear the starup music for Ubuntu, but nothing on the screen.

Am I to assume Lynux only works with Video cards that have a normal VGA output?

---

### Post by CTR_Chris on 2007-10-02
Ok I have now pluged in another DVI cable to the other port on my graphics card, on the other end of that is a VGA plug, and I have put this into my old monitor, and this now wokrs.

but still cant get other monitor to work

---

### Post by SpiritIsReality on 2007-10-02
howdy
As far as I know, if the live cd does not work, then try the alternate install cd.
scroll down this page to alternate cd. click to download.
[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/) you will see the files and md5sum further down the page. 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
then if you have to change your graphics/resolution use the command
$ sudo dpkg-reconfigure xserver-xorg
press enter and it will allow you to change things so they will work better.
any help?
buds

---

