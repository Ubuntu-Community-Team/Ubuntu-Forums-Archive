---
title: "wireless internet not detected on ubuntu live disk"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by sleeper414 on 2008-01-13
hi there,

i have an acer laptop thats pretty new, form 06. i decided to run ubuntus live disk, as i allready have it on a desktop and it runs fine.
however, when the lap top ran it. the graphics were bad...it just wasnt as sharp and looked "off"
more importantly, it didnt see my wireless card.
ie no internet.

didnt make any sense.

any thoughts?
:confused:

---

### Post by SOULRiDER on 2008-01-13
You will have to install the wireless drivers. The screen looking bad could be due to a bad resolution. Once video drivers are installed you can select a correct resolution so all will look OK.

What video card and what wireless card do you have?

---

### Post by p_quarles on 2008-01-13
A lot of wireless cards only have drivers available for Windows. In almost all cases, you can get the Windows driver to work by using a program called NDISwrapper. 

So, the fact that it doesn't work in the live disk doesn't mean that you won't be able to get it to work after installing.

Probably a similar issue with the graphics: you'll need to install or configure a different driver.

Can you tell us what kinds of video and wifi cards you have on this machine?

---

### Post by sleeper414 on 2008-01-13
its a broadcom..which i just learned isnt supported "out of the box"

the graphics are SiS (i think) i am not sure where to look, this is all i get from the device manager.
i have a feeling this isnt a big deal. i have been running ubuntu on two desktops with no issues.
in fact the drivers are probably in the synaptic list.
i think i just need to know what they are.

any ideas?

---

### Post by SOULRiDER on 2008-01-13
Here are the wireless docs [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
Find the exact mdel of your card and simply follow hte instructions on how to install the drivers. As for the video drivers, we need more info on what your video card is or at least what the laptop model is so we can help you out.

---

### Post by sleeper414 on 2008-01-13
thank you for the link.
the make is an 

acer 2434 WLCi travel mate....and i cant find anything on it. its bizzare really.

:confused:

---

### Post by anewguy on 2008-01-13
Type this in a terminal window and post back the results:

lspci


That way we should be able to see the exact info for both the wireless and the video.

Thanks!:)

---

### Post by sleeper414 on 2008-01-13
ok thanks for the tip

the wireless is ::::
BCM 4318 [airforce one 54g]

video is:::::::
SiS 661/ 741/760/
PCI/AGP or 662/761gx PCIE VGA display adaptor.

it appears that  multiple VGA's can be drivin?

---

### Post by SOULRiDER on 2008-01-13
Check this thread out for your wireless:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

For video, im still searching ;)

---

### Post by SOULRiDER on 2008-01-13
The only thing I can find about your video is that it kinda sucks.
Apparently theres a driver at [http://www.winischhofer.eu/linuxsispart1.shtml#22](http://www.winischhofer.eu/linuxsispart1.shtml#22) although to be honest, i think its better if you leave it alone and stick with 2d only =/

---

### Post by anewguy on 2008-01-13
> **sleeper414 said:**
> ok thanks for the tip

the wireless is ::::
BCM 4318 [airforce one 54g]

video is:::::::
SiS 661/ 741/760/
PCI/AGP or 662/761gx PCIE VGA display adaptor.

it appears that  multiple VGA's can be drivin?

The wireless is easy to get working, but you may need a wired connection depending on what you have already on your system.  Basically it involves installing ndiswrapper and its' utilities and then loading your Windows driver with it.  I created a how-to for a laptop I used to have that includes the wireless in the first section.  Don't worry that the laptop is a different brand - all that's important is the wireless.  Try using this how-to:

[http://ubuntuforums.org/showthread.php?t=507505]("http://ubuntuforums.org/showthread.php?t=507505")


It looks like some others have done research on your video, but I'll take a look around and let you know if something shows up.

:)

---

### Post by anewguy on 2008-01-13
I think, as previously mentioned by someone else, your video is going to be a little bit picky.  I did find some posts for you to research:

[http://ubuntuforums.org/showthread.php?t=488185&highlight=Silicon+Integrated+Systems]("http://ubuntuforums.org/showthread.php?t=488185&highlight=Silicon+Integrated+Systems")

[http://www.linuxforums.org/forum/ubuntu-help/104790-sis-graphics-drivers-ubuntu-7-04-a.html]("http://www.linuxforums.org/forum/ubuntu-help/104790-sis-graphics-drivers-ubuntu-7-04-a.html")

[http://www.winischhofer.eu/linuxsispart4.shtml]("http://www.winischhofer.eu/linuxsispart4.shtml")

[http://ithacafreesoftware.org/forum/viewtopic.php?t=251]("http://ithacafreesoftware.org/forum/viewtopic.php?t=251")

These are just a few of the posts I found by searching Yahoo with your Sis chipset.  Perhaps one or more of them can be of some help.

Good luck!:)

---

### Post by sleeper414 on 2008-01-14
bummer.

i love the idea of kicking windows and apple to the curb.

but if the scree is gonna look like an over head projecter...nope.

what about xubuntu?

i dont get it...... i have two OLD towers and ubuntu and xbuntu runs fine.....this is a laptop and its from less than 2 yrs ago...grapghics or not...XP looks flawless...what gives???:mad::evil:

---

