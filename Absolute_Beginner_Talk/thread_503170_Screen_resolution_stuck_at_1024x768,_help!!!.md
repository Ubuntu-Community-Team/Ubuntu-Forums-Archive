---
title: "Screen resolution stuck at 1024x768, help!!!"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by jannen on 2007-07-17
Hi there. I know this has been dealt few times here, but so far nothing seems to help to me.

I want a 1400 x 1050 resolution I have used on XP, Ubuntu only gives the option up tp 1024 x 768. 

I have tried the commands found in the forum in the terminal (sudo dpkg-reconfigure -phigh xserver-xorg), but none seems to help... :(

 I have an Acer laptop with Nvidia Geforce 2. I can find the driver at: System--->Administration--->Restricted Driver, and I have tried to enable the Nividia driver, but its not helping... im all stuck in 1024x768...

Any help would be appreciated!!! Thanks.

---

### Post by S15_88 on 2007-07-17
open terminal and type: 

sudo dpkg-reconfigure xserver-xorg 

you will get a chance to enter your desired resolution, for anything your not sure of just use the default settings.

Thanks, Alain

---

### Post by jannen on 2007-07-17
Hi, thanks for the reply, isnt that the same as: sudo dpkg-reconfigure -phigh xserver-xorg - I tried that dozen of times! Thanks again.

---

### Post by scott_g on 2007-07-17
After you try enabling the restricted drivers, does it show that they are working?  (ie: if you go back to the restricted drivers menu after you restart, is the graphics card still checked?)

If they are working, go to the terminal, and type:

```

nvidia-settings

```

This will open up a friendly dialogue box that lets you configure everything from multiple displays to temperature settings, to screen resolutions.  The resolutions displayed will be limited by your refresh rate.  If the resolution you want is not there, post back here, or see: [http://ubuntuforums.org/showpost.php?p=2844601&postcount=3]("http://ubuntuforums.org/showpost.php?p=2844601&postcount=3")
(skip to step # 2, and pick a resonable refresh rate; likely in the 60-80Hz range).

Once you have it working, you can create a menu entry in gnome to open up the dialogue automatically.

Hopefully it helps,
Scott

---

### Post by S15_88 on 2007-07-17
sorry about that i read the title and threw that down, sorry i didn't read the full message.

---

### Post by jannen on 2007-07-17
Tried with the nvidia-settings. Got to the settings window, tried to apply but received error messages (wanted a screenshot here, but dont know yet how to do it in Ubuntu...). Anyway tried and third time i have it!!! 1400x 1050, 66. Looks great, just hope it will stay like this when i start Ubuntu next time.

Thanks, that was great help from you!!!

:)

---

### Post by scott_g on 2007-07-17
> **jannen said:**
>  (wanted a screenshot here, but dont know yet how to do it in Ubuntu...). 

Press the Print Screen key on the keyboard, or go to Applications>Accessories>Take Screen Shot (in Gnome).

Scott

---

### Post by jannen on 2007-07-18
Hi, I had to come back here! When restarting the computer the screen remains black, only by clicking ctrl alt backspace I can now get to the desktop, but again its 1024x768!!!!

I typed again to terminal: nvidia-settings, changed the resolution to 1400x1050, looks good but when saving it I get this error:

ERROR: Unable to create backup file '/etc/X11/xorg.conf.backup'.

Arghhhhh!!!! Any help guys? I just want to keep the 1400 resolution and not change it every time I start Ubuntu...

Thanks... :confused:

---

### Post by jannen on 2007-07-18
Bit more information: 

When Ubuntu starts after logo I just get a black screen and nothing happens. Just before that I see a quick message telling: "Failed to allocate mem resource.... " and a bunch of numbers.

I can only start Ubuntu by Ctrl Alt Backspace, but it just goes back to the wrong resolution and I loose all my settings such as destkop image.

Help.... anyone???

---

### Post by sad_iq on 2007-07-18
Have you tried manually changing resolutions in xorg.conf??? ```
sudo nano /etc/X11/xorg.conf
``` and add your resolution there...or replace 1024x768 with your desired resolution.If things fail replace the new res with the old one!!!

---

### Post by Snitz on 2007-07-18
Try this one, it helped me.
[http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by sad_iq on 2007-07-18
> **Snitz said:**
> Try this one, it helped me.
[http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)
Won't work...he's using nvidia ...your guide is for intel only!!! :)

---

### Post by jannen on 2007-07-18
Thanks. 

Tried the: sudo nano /etc/X11/xorg.conf. But how do I change the values? The cursor does not move to the numbers, cant delete or add any new values?

Sorry never used the terminal before, dont know how to edit it!

---

### Post by sad_iq on 2007-07-18
Ok...let's try this then...```
gksudo gedit /etc/X11/xorg.conf
``` Then edit to your needs. In the terminal you can use the arrows to move...then to save CTRL+X then Enter(twice)!!!

---

### Post by scott_g on 2007-07-18
If just adding the desired resolution to the Mode line in the Screen section of your xorg.conf file doesn't work, try the steps mentioned [here]("http://ubuntuforums.org/showpost.php?p=2844601&postcount=3") (skip to step 2).

Good luck,
Scott

---

### Post by jannen on 2007-07-18
I have tried the steps you have given me above several times. I can get the resolution work fine now at 1400x1050, however when restarting / starting Ubuntu I get stuck in a black screen. The only way out is Ctrl Alt Backspace which brings me back to the 1024x768. Could something be wrong with the Nvidia drivers? Something else goes wrong at startup?

Im using Nvidia accelereated graphics driver which is enabled in the Restricted Drivers (In use). 

Appreciate your patience with me!!! Thanks.

---

### Post by scott_g on 2007-07-18
So you have modified your xorg.conf file's Mode's section and monitor section?

Did you try using the gtf tool?

Do you get an Nvidia splash screen when it starts up?

Is it a pure black screen?  Or are there lines on it?

Can you post your xorg.conf file (as an attachment)?

Thanks,
Scott

---

### Post by Hobo Joe on 2007-07-18
All you need is root permissions.

```

sudo nvidia-settings

```

Then change everything how you want it, then save it to Xorg config file, and quick reboot.

---

### Post by scott_g on 2007-07-18
Woops, I should have known that....lol, my mistake

---

### Post by jannen on 2007-07-18
Yes I tried that as well... wont help. It actually changed max resolution to 800x600...

---

### Post by jannen on 2007-07-18
Thanks Scott,

Sorry couldnt see all the latest comments. The screen is black with no lines or anything, pressing enter can the Ubuntu drum sound, so something is running in the back. Cant see any Nvidia splash screen at start up either.

I tried what I could of your advice above... problem is restarting the computer now.

<<< Can you post your xorg.conf file (as an attachment)?

Sorry dont know how to do that?

Thanks.,
Janne








So you have modified your xorg.conf file's Mode's section and monitor section?

Did you try using the gtf tool?

Do you get an Nvidia splash screen when it starts up?

Is it a pure black screen? Or are there lines on it?

Can you post your xorg.conf file (as an attachment)?

Thanks,
Scott

---

### Post by Hobo Joe on 2007-07-18
To post your xorg.conf, type:

```

gksudo /etc/X11/xorg.conf

```
Then just paste it here.

---

### Post by jannen on 2007-07-18
Wrote: gksudo /etc/X11/xorg.conf. It asked for password - but after that nothing!?

Played around with all above advice. Now Ubuntu starts with black screen as before, I press Ctrl Alt  Backspace - and get Nvidia splash screen and desktop comes up with 1400x1050. Weird eh? 

DOes it matter if I choose in the boot menu Ubuntu with the 16 or 15? (dont know what the difference is).

Thanks a million!

---

### Post by xc3RnbFO8P on 2007-07-18
I added "1680x1050" "1280x800" in /etc/x11/xorg.conf, be sure that your monitor support it.
You can try to add "1400x1050"

---

### Post by jannen on 2007-07-19
The resolution of my screen is 1400x1050. It works now but only after pressing Ctrl Alt Backspace after startup, as I still get the black screen.

---

### Post by user1397 on 2007-07-19
By the way, (I know that you are getting a blank screen, but this is for future reference) when executing the **sudo dpkg-reconfigure xserver-xorg** command in a terminal, it takes you into a text-mode interface, where you need to first select the correct driver for your video card, and then follow most of the defaults, until you come to the screen resolution settings screen.  The ones that will be used have a little asterisk next to them; if you want to select more, just use the up and down arrow keys to go to a particular one, and press the spacebar to select it. then accept some more defaults, and you're done.

as for your blank screen issue, I recommend running this command again, and selecting the right options, but don't do both this command *and * the restricted drivers manager.  it's one or the other.

---

### Post by scott_g on 2007-07-22
> **jannen said:**
> Wrote: gksudo /etc/X11/xorg.conf. It asked for password - but after that nothing!?

Can you try:

```

gksudo **gedit** /etc/X11/xorg.conf

```

Or,

Go to the advanced post editing, and click on "Manage Attachments" (at the bottom).  It should let you upload a file; just select the /etc/X11/xorg.conf file.

----------------------

> **jannen said:**
> Yes I tried that as well... wont help. It actually changed max resolution to 800x600...
Is that the maximum resolution you can choose from the nvidia-settings dialogue, or the System->Preferences->Screen Resolution?



Thanks,
Scott

---

