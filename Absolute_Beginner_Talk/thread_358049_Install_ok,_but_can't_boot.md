---
title: "Install ok, but can't boot"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by hppyfngy on 2007-02-10
Installing 6.10 on this system:


> Mainboard : EPoX COMPUTER CO., LTD nForce4-SLI DDR: 9NPA+SLI / 9NPAJSLI / 9NPASLI Series

> Chipset : nVidia nForce4

> Processor : AMD Athlon 64 3500+ @ 2200 MHz

> Physical Memory : 1024 MB (2 x 512 DDR-SDRAM )

> Video Card : Nvidia Corp GeForce 7600 GT

> Hard Disk : WDC (160 GB)

> Hard Disk : WDC (500 GB)

> DVD-Rom Drive : _NEC DVD_RW ND-3550A

> Monitor Type : Samsung SyncMaster - 20 inchs (dvi)

I could only boot the cd by setting the resolution to 1024x768, 16bit.  After that worked I was able to install although I was a little suspicious that the final restart hung up (and I tried it twice.)  

Now I get past GRUB and the system starts to boot but there's a point where it seems to be going to the login screen, but the graphics are off the screen so I can't log in.  I try recovery boot and everything looks okay but then I get to a point where it stops and I don't know the commands to continue.  

I can still boot the cd as before so I was wondering if I can modify the installed files, while running off the cd to allow me to boot.  

Be nice, I'm a real linux noob...

---

### Post by BarfBag on 2007-02-10
Boot into recovery mode and log-in with your user name and password.  Once you're logged in, type this:

> sudo nano /etc/X11/xorg.conf

This command instructs nano (a text-based file editor) to open your XORG config file, which is the file that tells the GUI which driver to use, etc.  I believe the section you need to look for is called "Screen," but I'm not sure.  It will have a list of resolutions.  Remove all of the ones after 1024x768.  Exit the editor by hitting Ctrl-X.  Save your changes.  Then, type the command below which should start the GUI.

> startx

Hope this helps.  Good luck!

---

### Post by hppyfngy on 2007-02-10
Is that just in the default 24bit settings?  I tried that and I just get some diagonal lines (along with the Ubuntu music.)

---

### Post by BarfBag on 2007-02-10
> **hppyfngy said:**
> Is that just in the default 24bit settings?  I tried that and I just get some diagonal lines (along with the Ubuntu music.)

In that case, try this.  Again, boot into recovery mode and log-in.  Type:

> sudo nano /etc/X11/xorg.conf

Look for the "Screen" section.  Change "DefaultDepth    24" to "DefaultDepth    16" (without quotes, of course).  Then, type:

> startx

---

### Post by hppyfngy on 2007-02-10
Tried that too.  I tried changing Default Depth to 16 and that didn't help.  Then I tried Default Depth 16 and took out all but 1024x768 in the 16 bit line and that didn't help either.

I'm stumped.  If I boot the cd at 1024x768 @16bit, it boots...:confused: 

Any of these changes I try results in these diagonal dotted lines

Thanks for trying to help, btw

---

### Post by hppyfngy on 2007-02-10
Okay, since you guys seem to be out of ideas, I've installed 6.06 over top of this install.  It works fine.  

So, now I'm trying to upgrade it to 6.10.  I've made no other changes, just thought I'd keep this thread alive for the benefit of anyone else who has a similar problem.  

(Not that I know what I'm doing, but I can get pretty stubborn about these things...:lolflag: )

---

### Post by hppyfngy on 2007-02-10
Okay, so here's the update.  I did the upgrade to 6.10 from within 6.06 and Eureka! It didn't work.  

Same darned thing.  I wait for the splash screen, which looks fine but when it should go to the login screen, I get these diagonal lines.  I know it's just a video issue as I can enter my username and password and actually log in, but I never see a desktop, just those diagonal lines.  


So, unless I hear a better idea, I'm going to re-install 6.06 and try to update the video driver and then upgrade to 6.10.  

So, if you're finding this amusing or are just curious to see how far I'll blindly go into the linux blender, check back later.  :popcorn:

---

### Post by riggits on 2007-02-11
So you're able to install Ubuntu then?  
I'm able to get to the screen where you choose boot options (Start or Install Ubuntu, Start with Safe Graphics Mode, etc) but nothing works.  Every resolution is bogus, getting either black screen ("Graphics mode not supported" says the Dell monitor) or an error starting X Server, with non-selectable options to view the log or not and a screenful of junk letters.
How'd you get past the screenful of junk???

---

### Post by hppyfngy on 2007-02-11
> **riggits said:**
> So you're able to install Ubuntu then?  
I'm able to get to the screen where you choose boot options (Start or Install Ubuntu, Start with Safe Graphics Mode, etc) but nothing works.  Every resolution is bogus, getting either black screen ("Graphics mode not supported" says the Dell monitor) or an error starting X Server, with non-selectable options to view the log or not and a screenful of junk letters.
How'd you get past the screenful of junk???

I'm not sure what you mean by "screen full of junk."  

I was able to boot the cd on 6.10 by changing the resolution to 1024x768, 16bit.  Then I could install.  It was only on reboot to the installed version that I have the display problem.  

I was also able to boot and install 6.06, and I could reboot into the system, but after doing updates I once again have these diagonal lines.  Tried to run the new Nvidia driver from recovery console but it said it was unable to find the 'ld' sys util.  And that I should make sure I had binutils installed, which I had done in the update.  It also says to make sure I have 'ld' in the PATH.  I have 'ld-static' in the path.  

Anyone?:confused:

---

### Post by hppyfngy on 2007-02-11
bump?

---

### Post by shareMenaPeace on 2007-02-11
Enter the console

CTRL + ALT + F2 login and enter

```
sudo reconfigure xserver-xorg
```

---

### Post by hppyfngy on 2007-02-12
And change "Screen" to 1024?  Tried that.  Didn't work.  Did I mention I'm using a dvi connection to a 16x1200 lcd?  Would that have anything to do with it?

---

