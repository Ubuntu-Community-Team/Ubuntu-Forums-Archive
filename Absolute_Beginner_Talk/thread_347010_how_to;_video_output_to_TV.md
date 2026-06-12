---
title: "how to; video output to TV"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by tordan on 2007-01-26
This my second attempt at getting this question answered. 
I have a radeon video card with VGA/SVIDEO/RCA output capability. I cannot get the video to output through the SVIDEO or RCA connectors.
In windows the card was detected and functioned  automatically. I did nothing to get Ubuntu to recognize the VGA output, but the other to do not seem to be configured right or something.
It was recommended that I download Kommander Editor to work on this problem, but I don't have the slightest clue as to where to go from there. 
Please help me...
Anyone...

Peace.

---

### Post by aPello on 2007-01-26
What model is your card? The older cards arnt fully supported by the driver. (I have a Radeon 7000 VE, and it fell into that category).

And to enable the TV out function youll need to do some editing of /etc/X11/xorg.conf
if you search the forums for "dual monitor" or something, youll find some help.

You might try this as a start tho: [http://www.ubuntuforums.org/showthread.php?t=221174&highlight=howto+dual+monitors](http://www.ubuntuforums.org/showthread.php?t=221174&highlight=howto+dual+monitors)

---

### Post by tordan on 2007-01-26
The card reads:
Radeon VE 32M DDR VO

It was given to me with no other information.

Do you know what my best option might be?

---

### Post by rmartz on 2007-01-26
Have you checked the manufaturer's site for any linux drivers that may need to be installed?

Isn't Radeon at ati.com?

---

### Post by cstatman on 2007-01-27
i don;t know if this helps, but I had an ATI Radeon card.  All my techs at work said "ATI means - painful in Linux"

so I just bought a Nvidia GeForce 7600 AGP card.  it seems to work better, have more drivers available, and my Ubuntu guru tells me he likes it better

I am still learning to setup the drivers and change resolutions.  By learning, I mean fighting.

Anyhow, good luck.  I dumped ATI just like I dumped Windows

---

### Post by rmartz on 2007-01-27
I have a Radeon card in my laptop that I run Ubuntu 6.10 on with no problems. Might  just be the older card not having the riht drivers. Glad things are working better.

Peace.

---

### Post by DrMega on 2007-01-27
Radeon cards use ATI chipsets (in fact they are effectively another badge for ATI). I have a Radeon 7000 in my older machine and it isn't very well supported by either the default open source driver, and is not supported at all by the proprietary ATI driver.

An my newer machine I have an ASUS 9550 (same deal, all ATI). I installed the proprietary driver from ATI to get it going properly. That machine is ONLY connected to the TV, I.e. no monitor is every connected. I found it fairly straight forward to set up. There is a config tool (command line) that comes with the ATI driver (can't remember its name off the top of my head but I can find out if you're still stuck). One command basically configures you're whole TV out and everything.

If your card is pre ATI 8000 series, there is another option. I saw a link to a site that explained how to connect directly from the VGA port to your TVs SCART (something I might try at some point to see if I get a better picture quality).

Sorry I've been a bit vague, give me a shout if you're still stuck and I'll dig out all the necessary details.

---

### Post by tordan on 2007-01-31
I just learned that the ATI Radeon VE series is also known as Radeon 7000 series.
Thats good information, but there doesn't seem to be any driver at the AMD/ATI site to support the 7000 series for Linux. 

Any clues?

---

### Post by DrMega on 2007-02-01
There is a compatibility issue with Radeon 7000 series cards in Linux it would seem. Nowt to do with TV Out, but it goes to show that it is not a well supported card. Have a look at the following link.

[https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/16873]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/16873")

You could get an ATI 9250 or 9550 for next to nothing, and the ATI proprietary drivers (which in my experience work well) support those cards.

---

### Post by tordan on 2007-02-01
I have no idea what those people are talking about, but I get the feeling that getting the 7000 series to work is hopeless.
Is that right?

---

### Post by DrMega on 2007-02-01
> **tordan said:**
> I have no idea what those people are talking about, but I get the feeling that getting the 7000 series to work is hopeless.
Is that right?

Never give up (says the man that is giving up). I am currently trying researching whether or not to buy a nVidia XFX6200 to replace my Radeon 7000. I have had to go back to Windoze for the time being because I'm sick of Ubuntu freezing at random.

On that note, does anyone know if the nVidia XFX6200 has any issues in Ubuntu?

---

