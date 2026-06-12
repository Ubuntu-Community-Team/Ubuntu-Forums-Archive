---
title: "Intel 945GM Chipset"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by all4als on 2007-05-24
OK, so I have loaded Fiesty and all is working brilliantly. I have an express intel chipset 945gm, and the highest resoltion in the screen resolution preferences is 1024x768. The only monitor i am using is the one on my laptop. The monitor mfg is Seiko Epson. I was wondering if there was anyway (other than buying a new video card) to set my resolution at a higher rate?

Signed, 
New to Ubuntu

---

### Post by Simran on 2007-05-24
I have the same chipset, found 915resolution

Open the terminal and type:

sudo apt-get install 915resolution

once installed then type: 

915resoultion mode X Y              *X being Xaxis resolution Y being yaxis resolution* 

Simran

---

### Post by all4als on 2007-05-24
How do I know what the best resolution will be? Thank you for the quick response.

---

### Post by .adma on 2007-05-24
your rez is 1440 x 900.  

You can try 915resolution...didnt work for me.  However, I did get it working with this:

sudo apt-get install xserver-xorg-video-intel



This will install the xserver intel driver....instead of using the i810 driver, which is what you are probably using now.  Not sure if this is necessary, but I also uninstalled the i810 with:

sudo apt-get rm xserver-xorg-video-i810

Everything is beautiful and clear now.


here is a link to the thread that helped me:
[http://ubuntuforums.org/showthread.php?t=443782](http://ubuntuforums.org/showthread.php?t=443782)

---

### Post by all4als on 2007-05-24
I have now done the intel and the i810 video drivers suggested, and my highest screen resolution is still 1024x768. I thought my laptop could do a better screen res than that. Is this right?

As a side note on the widows side, that is all my screen res can get to also, but I thought it was something that windows or dell had locked down. 

Thank you all for your help.

---

### Post by .adma on 2007-05-24
well if thats your windows rez...thats probably the best you can do.  Is your screen distorted?

---

### Post by ramjet_1953 on 2007-05-24
If you are using Feisty 7.04, a better option is to use the new Intel driver.

It is also MUCH easier to set up;

In a console, just copy and paste this command:

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

When it has finished, just re-boot your system and you should now have a selection of resolutions available in your [COLOR="Blue"]System>Preferences>Screen Resolution[/COLOR] menu.

Regards,
Roger :cool:

---

### Post by all4als on 2007-05-26
Thanks Roger. Does that mean the best Resolution after I load the Intel drivers is found in that location? If so, the best Res I can get is 1024x768. Which is a real bummer. I appreciate all of the help. So far, this OS is great.

---

### Post by ramjet_1953 on 2007-05-27
If 1024 X 768 was the best that you could get under Windows, I guess that is all that your screen can do.

I guess it isn't a widescreen laptop, then? So at 1024 X 768 the aspect ratio is correct and circles on the screen are round and not squashed?

It seems a bit stange, though.

When you go into  the System>Preferences>Screen Resolution menu is 1024 X 768 the highest resolution available?

Regards,
Roger :cool:

---

### Post by all4als on 2007-05-29
Sorry for taking so long to get back to you, but yes is the answer to your question. 1024x768 is the highest resolution under System>Pref>Screen Res. However I only have two other options. Those options being 800x600 and 640x480.  I really thought that the laptop would do better, but maybe I am crazy.

---

### Post by SoulinEther on 2007-05-29
> **ramjet_1953 said:**
> If 1024 X 768 was the best that you could get under Windows, I guess that is all that your screen can do.

I guess it isn't a widescreen laptop, then? So at 1024 X 768 the aspect ratio is correct and circles on the screen are round and not squashed?

It seems a bit stange, though.

When you go into  the System>Preferences>Screen Resolution menu is 1024 X 768 the highest resolution available?

Regards,
Roger :cool:
Well, not all laptops are widescreen. 8) Honestly a widescreen monitor or laptop has a bunch of pixels missing. :S

---

### Post by ramjet_1953 on 2007-05-29
If you read carefully the whole series of posts here, you might undestand that my comment was that it was strange that his resolution couldn't go past 1024 X 768, not that I was surprised that it was not a widescreen.

Roger :cool:

---

