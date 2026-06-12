---
title: "Live CD Boot Problem From A Newbee"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by EdInHouston on 2006-11-05
Hello, this is my first time using Ubuntu.  I have limited Linux experience having used Puppy a few times but there are a lot of simple things I don't know concerning linux.

I downloaded Ubuntu6.10i386iso and burned it to a DVD then verified it after checking it with HashTab.  I inserted the LiveDVD, rebooted, and the Start Screen came up.  I tested my memory (768M) and it was fine.  I rebooted to start enjoying my LiveDVD before installing it to my hard drive.  

The DVD started loading but then stopped and a screen popped up telling me XORG needed to be configured and then I could restart GDM.  I pressed enter and a flashing prompt came up.  I think it was the console however after typing some commands nothing happened so I pulled the plug and came here.

I have an ATI Radeon VisionTek PCI card for my monitor and I think I need to boot in VESA mode to load Ubuntu with this card because this is what I did to make Puppy work.

Could someone walk me through the process of how to do this?  Please remember I am new and I will need to know all the minor steps involved as well.

Thanks
Ed

BTW, my system is a HP Pavilion A310N, DMA hard drive, 768M DDR SDRAM, BIOS set to plug and play.

---

### Post by DanSchnell on 2006-11-05
To change it to vesa, you need to get into the terminal first (ctrl+alt+f1)

Then type```
sudo dpkg-reconfigure xserver-xorg
```

You should get a blueish diplay screen that will help you reconfigure

If your not sure if you want to change, you should probably just leave it at the default choice.  One of the screens will have a long list of drivers you can use.  Simply use the arrow keys to scroll your way down to 'vesa'.  Finish the setup.  After this you should get a terminal feed at the bottom of you screen (or it could take up the whole screen)

use ctrl+alt+backspace to restart x 

or type ```
sudo /etc/init.d/gdm restart
``` 
Note, If your installing kubuntu, it would be kdm,instead of gdm

---

### Post by EdInHouston on 2006-11-05
I'll give it a try again.  I tried this before my earlier post after reading other post concerning ati driver problems and I couldn't get the terminal to come up using the buttons ctrl+alt+f1  or as someone mentioned ctrl+alt+f2.  I typed it in while the boot up option screen was in view.  Nothing happened.

I tried again while the prompt was flashing that occurred after the screen that told me to reconfigure xorg and restart GDM and nothing happened.  

I don't know if that prompt is the terminal but just in case it was I tried typing sudo dpkg-reconfigure xserver-xorg and punching the enter button but nothing happened other that the prompt moving down a space.

I'll be back in a minute.

---

### Post by EdInHouston on 2006-11-05
The same thing happened.  I just cant get the terminal to come up and if that black screen with the flashing prompt is the terminal then that wont do anything.  If I type something in and press enter the prompt just moves down a space and I have to do a hard reboot.  I tried ctrl+alt+backspace and sudo /etc/init.d/dgm restart to reboot but nothing happened so I shut the power off.  

At the top of that black screen it says this:

*Activating swap...                [ok]
mount: Function not implemented
*Checking file systems
fsck 1.39                           [ok]

Just for the heck of it I checked the DVD for errors again.  It was ok.

It says it's loading 100 percent of the linux kernel and casper if that matters.

---

