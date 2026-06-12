---
title: "Max resolution with Fiesty is 1024x768"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by samadams on 2007-06-06
I just upgraded to Fiesty last night and now my max resolution available is 1024x768.  I have already edited my xorg.conf file to add the desired resolutions but the resolution setting in preferences will not display higher options.  Any ideas?

---

### Post by Inxsible on 2007-06-06
have you tried removing all the other resolutions except the one you want in the xorg?

I have read that helps sometimes !

---

### Post by Hobo Joe on 2007-06-06
What is your video card and driver?

---

### Post by NeoLithium on 2007-06-06
It could be the video card that was selected for your install as well though.  You might want to reconfigure it to select a more proper card.
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak   (This makes a backup just in case)

sudo dpkg-reconfigure xserver-xorg

```
Answer all the questions you know the answers to, leave the rest as defaults
Then restart your x server and hopefully it will give you what you need.

If one of the options causes problems and the X-Server won't work, you can just return it to the pre-reconfigure state with the following command:
```

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

```

Hope this helps

---

### Post by jerrylamos on 2007-06-06
I had to find out what driver my Intel graphics chip used, namely i810, video memory 65536 KB, and what resolution my Hanns-G LCD would take, 1280x1024, and what refresh rate, 75.
Then I did Ctrl-Alt-F1
sudo dpkg-reconfigure -phigh xserver-xorg
(note no blanks before the hyphen - except on -phigh)
(enter password)
then got some menus so I could set the parameters above.  Then
sudo killall gdm
startx
Worked fine.  I have better luck with the sudo dpkg than with editing xorg.conf directly.

Do note early Gutsy Gibbon 7.10 worked O.K. as booted, however it's early Alpha code and likely lots of bugs.  It releases in October but the adventuresome with nothing to lose can try it.

Cheers, Jerry;)

---

### Post by Ek0nomik on 2007-06-06
> **Inxsible said:**
> have you tried removing all the other resolutions except the one you want in the xorg?

I have read that helps sometimes !

As long as he has the desired resolution in his xorg, he is fine.  If he has lesser values it won't make a difference.

What jerrylamos said could work.  Running dpkg-reconfigure -phigh xserver-xorg is what did the trick for me with an Nvidia graphics card.

Otherwise you will want to do as Hobo Joe said and post us your video card and drivers that you are using.

---

### Post by samadams on 2007-06-06
Well, if linux would bother to put this info somewhere I could easily find it, I might be able to tell ya.  I think, if I remember correctly that the card or the driver is ATI, I didn't know they could be separate, so right now I can't tell you more than that.  The monitor is a Gateway EV700.  (note - I bought this machine used - so I don't have any info other than what an OS can tell me as to what hardware I have)  If you could be so kind as to tell me where to find this - I'll report the result back here.
Thanks.

(and I don't mean to sound bitchy - but it really irks me when such needed and basic info is buried where you have to 'guess' where you might find it - I used the hardware info option under preferences but it's not very clear.)

---

### Post by samadams on 2007-06-06
I tried this and now the x-server is toast.  But now how do I get to a command line to restore the backup .conf file?  All I get is a 'dos' screen with no prompt that lets me type anything I want and the ENTER key just works as a carriage return - it doesn't execute anything.

FYI - the x-server told me that there was a fatal error - no screens found.  It also told me "no devices found"

Where to next?

---

### Post by NeoLithium on 2007-06-06
You can boot yourself into recovery mode that will give you the terminal to type the 
```

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

```

---

### Post by samadams on 2007-06-06
okay - before I go (the live cd takes about 20 minutes to boot up)  this recovery mode WILL be on the list when the CD menu pops up?  I never noticed it before.  Or is there a hot key I have to press to access this mode?

---

### Post by NeoLithium on 2007-06-06
You should be able to boot into your computer as normal, and select the kernel with the (Recovery Mode) option in the grub menu. You might need to hit ESC as grub is loading, if the menu doesn't show up normally when you boot your computer.

---

### Post by samadams on 2007-06-06
okay - thanks - I'm back now with a 1024x768 screen.  Any ideas on where the reconfig went wrong and how I can fix it so I can get these other resolutions?

*note* I'm gonna be out for a few hours so I won't get to this till tomorrow - so there's no hurry, this isn't exactly a critical issue but it would be nice to resolve it.

Thanks in advance,
Sam

---

### Post by ramjet_1953 on 2007-06-06
You need to install the Intel video driver, as it only had legacy drivers on-board.

Copy and paste this command into a terminal:

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

After this, re-boot and you should now automatically be in the optimum video mode for your system.

Also if you have a look in [COLOR="Blue"]System>Preferences>Screen Resolution[/COLOR] , you should now have quite a few options.

Regards,
Roger :cool:

---

### Post by samadams on 2007-06-07
Thanks, I'll give that Intel driver a try.  But I'm curious.  If I could successfully edit xorg.conf in Dapper to get the resolution I want, why does Fiesty not give me those extra options in setting my resolution? (the file still has those changes I made - they just don't show up when I go to set it)

---

### Post by samadams on 2007-06-15
Okay - tried the intel driver.  ubuntu tells me it will install one package and remove another - but not which one.  It also doesn't give me the option to just install and not remove anything.  Which may be a problem, because ubuntu tells me there is a dependency issue, that video-all depends on video-i810 which will be removed.  It proceeded to remove i810 and install intel.  I rebooted and .....  no change.  Still stuck in 1024x768 with no additional options in preferences>screen resolution.  So I thought, maybe since I had to manually update xorg.conf in dapper, I should do so here. (I have in the meantime done a clean Fiesty install, so those changes were erased)  I've done so and restarted X - still nothing.

Why would Dapper give me higher resolutions and not Fiesty?  How can I find the info for my hardware so I can configure xorg as suggested higher in the thread?

---

### Post by samadams on 2007-06-15
Okay - a little more info.

I did some more digging and found that I have an Intel chipset for sure.  82810E DC-133 to be exact.

I noticed that the driver for the chipset is still i810_smbus but the driver for the controller is agpgart-intel.  Could this discrepancy be the problem?  Why, when I installed the intel driver, did it only work for the controller and not the chipset?  How do I fix this or do I even need to?

---

### Post by samadams on 2007-09-18
Okay - I've been really busy - but I'd like to get cracking on this again.

I went through all the steps all over again.

I edited the xorg.conf file including the higher resolutions I wanted and even took out the lower ones.  I added: 1280x1024 1280x960 1152x864.

When I rebooted the x-server I saw the new resolutions except that any vertical number higher than 800 was changed to 800 and all of the old lower resolutions remained.  (e.g. 1280x1024 was listed as 1280x800 and so on)

So I tried to reconfigure the x-server next.  This seemed to go smoothly and this time, when choosing available video modes I selected only those at 1280 x1024 and higher.  I also set this as my 'regular' mode.

Upon re starting X, there is absolutely no change at all.  My best resolution is still 1280x800.

What is so strange is that before under Dapper, I could get all the resolutions I wanted.  Only after a clean Fiesty install, did I begin to have this problem.

Any guesses, or should I just wait it out for Gutsy so I don't have to do this all over again?

Thanks

---

### Post by samadams on 2007-09-18
I just thought of something.  Does Fiesty think I'm using a Laptop and thus is limiting my vertical resolution?  or is there some other reason my Vertical would be limited to 800?  (note, both XP and Dapper had no trouble giving me 1280x1024 with all the same hardware)

---

### Post by alienexplorers on 2007-09-19
Use a modeline in your monitor section of xorg-conf file.
Example:
> # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

---

### Post by skyjacker on 2007-09-19
> **samadams said:**
>   I think, if I remember correctly that the card or the driver is ATI,

I just went through this. Go to [http://albertomilone.com/nvidia_scrips1.html](http://albertomilone.com/nvidia_scrips1.html), and read his info. This works for ATI cards also.Applications add/remove and install Envy. Install, run once to remove old driver. Run a second time to install new driver. Then sudo ati-settings (i think as i ran sudo nvidia for mine). Good luck

---

