---
title: "Lock-up after install"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Praga on 2008-03-12
I managed to get the latest version of Ubuntu installed last night, but I'm having a big problem. It goes thru the boot process but locks up just after the circular mouse pointer shows up on the screen. It flashes a couple times then goes to a screen full of vertical colorful stripes. 

I read elsewhere about how to reconfigure the video drivers from the command line and I did that. The default seemed to be correct.

I can get to the command line, but the gui locks up every time.

---

### Post by neurostu on 2008-03-12
Have you tried booting in recovery mode? or safe graphics mode?

---

### Post by gobbles414 on 2008-03-12
> **Praga said:**
> I managed to get the latest version of Ubuntu installed last night, but I'm having a big problem. It goes thru the boot process but locks up just after the circular mouse pointer shows up on the screen. It flashes a couple times then goes to a screen full of vertical colorful stripes. 

I read elsewhere about how to reconfigure the video drivers from the command line and I did that. The default seemed to be correct.

I can get to the command line, but the gui locks up every time.

Try reconfiguring in the command line again. But this time, choose the VESA (generic) option. Then reboot and log into Ubuntu. If you're able to boot into Ubuntu using the VESA option and you're only going to use your PC for surfing the internet etc., you can stop here. But if you'd like to get 3D acceleration and other advanced features of your graphics card working on your PC, go *System => Administration => Restricted Drivers Manager*. Look for a graphics driver in the list. By the way, what is the brand and model number of your PC? Your answer will help us to help you.

---

### Post by Praga on 2008-03-12
Its a Dell GX260 using onboard video.
[http://support.dell.com/support/topics/global.aspx/support/my_systems_info/details?c=us&l=en&s=gen&~tab=2&servicetag=3w9h021](http://support.dell.com/support/topics/global.aspx/support/my_systems_info/details?c=us&l=en&s=gen&~tab=2&servicetag=3w9h021)

I'll try using VESA now and update this in a min.

---

### Post by Praga on 2008-03-12
Ok, I set it to VESA and it seemed to get a little bit further. 

The resolution changed to 640x480, it went to a command line login prompt and logged in for me I assume. Then a screen filled with weird chracters and colored boxes popped up for a sec and then a dialog box saying that I was running a low res or something popped up. I clicked 'ok' then the funny looking screen with weird crap popped up again, then a black screen. No command line or mouse...just black. The keylock button on the keyboard still works, so I assume it isnt locked up.

---

### Post by Praga on 2008-03-12
> **neurostu said:**
> Have you tried booting in recovery mode? or safe graphics mode?

How do I get to "safe graphics mode" are you reffering to the command line?

---

### Post by gobbles414 on 2008-03-12
> **Praga said:**
> How do I get to "safe graphics mode" are you reffering to the command line?

**According to my research, you may want to use the Intel 845 graphics driver.** Try selecting that using the command line in "Rescue Mode". If you have multiple operating systems on your PC, the appropriate menu for going into rescue mode should appear as your computer is booting. If you only have Ubuntu installed on your PC, you'll need to press the escape button on your keyboard when GRUB starts to load -- GRUB should give you a short countdown prior to loading your defaults. Once your in the correct menu, choose the highest version of your kernel with the (Recovery Mode) option. Once this loads, you'll get a command line interface.

---

### Post by Praga on 2008-03-12
Here's exactly what I'm doing, but it's no differant than what I was doing before...

Hit esc to bring up menu, pick safe mode.

root@desktop2 dpkg-reconfigure xserver-xorg

It asks if I want it to autodetect the video card, and I don't see where it does much differant either way.

I pick intel from the list of manufacturers, then I get a screen telling me that the "Identifier for my video card" is:

Corporation 82845G/GL (Brookdale-G)/GE Chipset Integrated Graphics Device

I pick that and I'm right back where I started, locking up at a colorful stripy screen.

---

### Post by gobbles414 on 2008-03-12
Try manually choosing some similarly named Intel chipsets. Is there an option for the 845 chipset without the 82 in front? Also, you say that you're using your PC's integrated video. Do you have a graphics card installed in your PC too? That could make a difference in your procedures.

---

### Post by Praga on 2008-03-12
I don't understand how to pick another intel card. It gives a long list of manufacturers and I picked intel. The next screen tells me the 'Identifier for my video card'. There doesn't seem to be an option to pick any other intel card. It does let me backspace and delete the given entry...but what then?

Maybe I'm using the wrong command...

dpkg-reconfigure xserver-xorg

Is that correct? I'm a total linux noob.

---

### Post by Praga on 2008-03-12
Oh btw...earlier when I switched to VESA, it gave me the same "Identifier". I'm guessing that I'm just not getting to the right thing to change my vid driver.

---

### Post by gobbles414 on 2008-03-12
> **Praga said:**
> I don't understand how to pick another intel card. It gives a long list of manufacturers and I picked intel. The next screen tells me the 'Identifier for my video card'. There doesn't seem to be an option to pick any other intel card. It does let me backspace and delete the given entry...but what then?

Maybe I'm using the wrong command...

dpkg-reconfigure xserver-xorg

Is that correct? I'm a total linux noob.

You're using the correct command. But try this variation:

1. Use the *dpkg-reconfigure xserver-xorg* command in Rescue Mode and select the VESA driver.
2. Reboot
3. The low resolution warning should appear. There should be two options accompanying the warning.
4. Choose the option that will allow you to reconfigure your graphics (I forget the exact button).
5. This should show a more user-friendly menu for selecting different Intel chipsets. Try 845 first.
6. If you can log into Ubuntu, you've finished!

Did this help?

---

### Post by Praga on 2008-03-12
No Mr Gobbles....that didn't work. It does look a little more promising though.

I was able to get to the config screen that you were talking about. I tried the Intel 845 driver, hit test, and the screen went black. Hitting random keys on the keyboard produced an occasional noise, but no video. I hard booted it and tried again, this time picking the 745 driver and got the same result. All the 8xx drivers seemed to be the same driver which is why I tried the 745.

---

### Post by gobbles414 on 2008-03-13
Praga,

Well. since you managed to install Ubuntu I'm going to guess that the LiveCD chooses the correct display driver. Put your LiveCD into your computer and restart. When the LiveCD has completely loaded, go *System => Administration => Screens and Graphics*. On a piece of paper, write down all of the settings from this utility (there are tabs). Reboot and remove the LiveCD. Now, use the *dpkg-reconfigure xserver-xorg* command to enter these settings into your Ubuntu installation. Restart again.

What monitor are you using? Are you sure that it's working properly? For instance, does it work in Windows? Also, do you have a graphics card installed in your computer in addition to the integrated graphics?

---

### Post by Praga on 2008-03-13
I'm guessing that I have bigger problems than I thought...maybe a bad HDD? Is the LiveCD dependant at all on the HDD? 
While booting to the CD I noticed the following errors:

On the black screen...

Buffer I/O error on dev SR0
SquashFS errors reading stuff (3 of these)

Then on the tan screen...

Int Error
Failed to initialize HAL

I then clicked ok and nothing else happened. I'm stuck at the tan screen.

The CDROM drive I'm using is some old POS from 2000. It wouldn't suprise me if it didnt work right. The CDROM in the computer didnt work at all and wouldn't read a CD.

This is just an extra PC I had laying around that I was trying to get running for my son. I may just give up on getting this one working. In a week or so I'm picking up another PC from my mom, maybe I'll have better luck with it. What do you think? Lost cause?

**edit**  The monitor is a Samsung SyncMaster 910MP. It worked fine in XP. No, I'm only using the onboard video. The other card broke.

---

### Post by luvit on 2008-03-13
I skimmed over this pretty fast... I have a GX260

Are you using the Alternate ISO image? -- it solved install problems for me.
I also updated my BIOS, the BIOS image is in my blog.

I have posted about my GX260 on some other threads around  here and don't want to be spammy about how awesome my GX260 is working on v7.10.
I'm a new member so I'll watch this thread (I just subscribed).

---

### Post by Praga on 2008-03-13
Thanks luvit. I just read your blog and the problems you had sound just like what I'm going thru. I'm downloading the alternate CD now and I'll give that a try. Is a bios update totally neccesary? lol....I dont have any floppys.

---

### Post by gobbles414 on 2008-03-13
> **Praga said:**
> Thanks luvit. I just read your blog and the problems you had sound just like what I'm going thru. I'm downloading the alternate CD now and I'll give that a try. Is a bios update totally neccesary? lol....I dont have any floppys.

It sounds to me like your LiveCD is either defective or incompatible with your computer. Please run the *Check CD for Defects* option as you LiveCD is loading, and post the results. If your CD passes the test, I agree with luvit that the alternate CD is probably your best option.

I'm sure that luvit is trustworthy. But I would still recommend that you download the BIOS update from a more official source if possible. BTW, some computers will allow you to use a USB flash drive instead of a floppy to update the BIOS.

---

### Post by luvit on 2008-03-13
My blog has a link to Dell's link (check link properties).
I very much recommend the BIOS update.
I do agree to check the CD for errors, but the Alternate CD does not use th GUI install... but it's still easy and detects the video :)

---

### Post by Praga on 2008-03-14
Hey thanks guys. I downloaded Hiren's boot cd and used it to flash my bios. My original install is working and it seems to be flawless. I appreciate your time!

---

### Post by gobbles414 on 2008-03-14
> **Praga said:**
> Hey thanks guys. I downloaded Hiren's boot cd and used it to flash my bios. My original install is working and it seems to be flawless. I appreciate your time!

I'm really glad that your PC is working now. Congratulations!

---

### Post by luvit on 2008-03-14
> **Praga said:**
> Hey thanks guys. I downloaded Hiren's boot cd and used it to flash my bios. My original install is working and it seems to be flawless. I appreciate your time!Glad to be of help!

---

