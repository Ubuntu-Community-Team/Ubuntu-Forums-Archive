---
title: "Help me... Im having big problems!! how to acess xorg.conf"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by harrington on 2006-12-27
OK I think that I understand now that my LCD monitor does not support the resolution or refresh rate that is default for the installation. Im trying the live cd but my Samsund LCD monitor goes into standby when trying to access ubuntu for the first time. I see it load (where the orange bar goes accross. Oh by the way I downloaded the newest version, I am new to linux completly. I understand that there are alternative installations, I want this to work, Ive got it on the cd ready to go, computer boots to the cd, but I wanna see the desktop environment. I have read allot about customizing xorg.conf but how do I do this??? Any help would be great. I wanna eventually get rid of windows! I understand some of the topics in these forums, but most go over my head!

system:
pentium D 3.6ghz
windows xp media center
atix1300
wireless keyboard and mouse
samsund 19inch widescreen

Please help me get this running. I want to eventually get rid of windows and run linux

---

### Post by taurus on 2006-12-27
Boot into recovery mode from GRUB menu and at the prompt, edit your /etc/X11/xorg.conf with

```
nano -w /etc/X11/xorg.conf
```

---

### Post by harrington on 2006-12-27
Like I said I am new to this. I see the main intro screen where I get boot options, and safe graphics, mem test. Ive tried every option, but still my lcd goes into standby

---

### Post by taurus on 2006-12-27
Remove the LiveCD from the drive.  Boot with your harddrive and at the GRUB menu, you will see three options:  first for Ubuntu, second for recovery mode, and third for memtest.  Use the down arrow to highlight the second option and hit Enter.  Wait for it to finish booting and run that command to edit your /etc/X11/xorg.conf...

```
nano -w /etc/X11/xorg.conf
```

---

### Post by harrington on 2006-12-27
When I load from main drive it will just go to windows??? I am confused, Where would I do this. What Im refering to is the window that first comes up after booting from cd. Where do I go from there

---

### Post by taurus on 2006-12-27
Let's back up a little!  Do you already have Ubuntu installed on your harddrive?

---

### Post by dmartinsca on 2006-12-27
When you boot the computer from the livecd you should have a few options to choose from. At that screen you can press F4 to get a list of resolutions to use. Try picking the resolution which matches the native resolution of your monitor (the last number is bit depth (number of colours), pick 32). If this doesn't work, try pressing Ctrl+Alt+F1 after the monitor has gone blank. This should switch you to a text console where you can enter commands and edit files. If you type **nano -w /etc/X11/xorg.conf** here you can edit the xorg.conf file. (the -w simply turns off line wrapping when lines go past the edge of the display area)

---

### Post by harrington on 2006-12-27
That sounds like a logical solution, I appreciate you giving the time to post a reply so quickly, If anyone can think of any thing else that would be great also. I just wanna see linux for my first time, I was so exited when it was loading, but then from that to stand by monitor.

---

### Post by Balaam's Miracle on 2006-12-27
> **dmartinsca said:**
> When you boot the computer from the livecd you should have a few options to choose from. At that screen you can press F4 to get a list of resolutions to use. Try picking the resolution which matches the native resolution of your monitor (the last number is bit depth (number of colours), pick 32). If this doesn't work, try pressing Ctrl+Alt+F1 after the monitor has gone blank. This should switch you to a text console where you can enter commands and edit files. If you type **nano -w /etc/X11/xorg.conf** here you can edit the xorg.conf file. (the -w simply turns off line wrapping when lines go past the edge of the display area)

From what i read and assuming that the info that Harrington gave is accurate, i would guess that at the selection screen, the monitor goes in stand-by mode when he is booting from the Live CD.

I'm pretty fresh at using 'buntu myself, so i'm wondering if there is a way to boot the Live CD witout APM functions or even better, completely turn off DPMS or whatever it is that makes an LCD monitor go into standby mode.

---

### Post by harrington on 2006-12-27
I think it has to do with the native resolution, but you would think that it would automatically choose the proper one would it not?

---

### Post by harrington on 2006-12-27
There is a Linux ATI driver... would this help????

 ATI Proprietary Linux x86 Display Driver 8.32.5

---

### Post by riven0 on 2006-12-27
Okay, I'm not understanding this completely. Are you able to get to this screen? (Check attached image)...

---

### Post by Balaam's Miracle on 2006-12-27
> **harrington said:**
> I think it has to do with the native resolution, but you would think that it would automatically choose the proper one would it not?

If by "it" you mean the monitor, then yes, one would think so. However, in my experience many monitors and especially LCD monitors go into stand-by mode when they encounter a refresh rate that they don't know in order to protect them from damage caused by incorrect refresh rates. (i've my own thoughts about that, but let's not get into that now).
So my guess is that your monitor is presented with a different refresh rate than what it expects.

> There is a Linux ATI driver... would this help????
 ATI Proprietary Linux x86 Display Driver 8.32.5

Yes it would, but only after you've installed a working Ubuntu system. But since you are stuck at the initial selection screen and you are booting from the Live CD, any changes you make will be not very useful since they will be gone after you've shut down the PC.

I'd say that this is a problem for more advanced users than me (been using Ubuntu since only a few weeks).

---

### Post by harrington on 2006-12-27
I think the last post is exactly correct. I belive that it is the refresh rate. I am going to try the alt-clrl-F4 option and try through the terminal when it does go into the standby mode. I am not sure what the native resolution is, I will have to find that out too. And I understand that I dont actually have it installed so drivers would not really be a resolution. Is there any way to change the refresh rate? All answers are helping allot thanks

---

### Post by harrington on 2006-12-27
Anyone else know a quick fix for this or step by step?

---

### Post by dmartinsca on 2006-12-28
You can turn off acpi (the new version of apm) although i doubt that will fix the problem. It sounds to me, as Balaam's Miracle said, that the monitor is getting a refresh rate it doesn't like.
Something I didn't think of before: You can change the resolution that the graphical display is at by pressing Ctrl+Alt+plus (or minus). Plus and Minus have to be the ones on your number pad! When you the monitor goes into standby, try pressing these keys. (More than once if the first time doesn't work)
If that doesn't work, you'll need to define the refresh rates for your monitor. There are two ranges, Horizontal and Vertical, dig out the manual for your monitor or look it up on the net. The first thing to check is that you can get to a console by pressing Ctrl+Alt+F1 (F1-F6 all take you to different consoles, F7 has the graphical display). If you see a black screen with white text then we're in business! You'll need to run a couple of commands from here and edit your xorg.conf file to define the refresh rates your monitor can handle. Type the following:
```
/etc/init.d/gdm stop
nano -w /etc/X11/xorg.conf
```
Now you should have an editor open with the contents of your xorg.conf file showing. There will be a line which says **Section "Monitor"**, look for it, you may need to scroll down with the arrow keys. A few lines down there will be a line which says **EndSection**. In between these two lines there _may_ be a couple of lines which look something like this:
```
        HorizSync       15-80
        VertRefresh     50-90
```
If not, you'll have to type them in. Either way, replace the numbers with the horizontal and vertical refresh rates for your monitor. Now close the editor and save the file by pressing Ctrl+X, Y, Enter. Now run the following command:```
 /etc/init.d/gdm start
```
Now you may need to switch back to the graphical display by pressing Ctrl+Alt+F7 or it may switch on it's own. Hopefully this will fix your problem! If not you could try the following but i'm doubtful it will help.


 To turn off acpi, you need to tell the kernel (the core of the linux) not to use acpi. When you boot from the CD, press F6 at the screen riven0 posted a picture of. This will allow you to pass parameters to the kernel at boot time. Pressing F6 should open a little box with some text in it already. Append the following to that text then press enter.
```
acpi=off
```

---

### Post by viper2299 on 2007-02-16
I'm having the same problem with the install, and I've gotten all the way into the xorg.conf file and found out which lines to edit, the only problem is I cannot edit and save the file, because it's still on the CD.  How do I get the file edited?  Thanks.

---

