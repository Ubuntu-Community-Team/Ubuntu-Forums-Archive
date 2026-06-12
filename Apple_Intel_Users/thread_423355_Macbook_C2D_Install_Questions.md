---
title: "Macbook C2D Install Questions"
date: 2007-04-25
forum: Apple Intel Users
---

### Post by xiambax on 2007-04-25
Hello,
I have kinda fallen off the wagon as of late because i stopped using linux about a year or so ago. Computers have made such a great advancement i just kind of got bored of waiting and bough a mac.
But thats besides the point.

I'm downloading Fawn now and will begin to install it when the ISO is done downloading.

What i want to know is:

1: can i safely resized my HFS partition from ubuntu install disk.
2: Do i have to worry about anything after that as far as getting hardware to work. I see some people have had problems, do these issues generally occur?

Gpartd [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) should work for resizing that partition if i can from the cd.

Anyway any feedback would be great.

-Nathan

---

### Post by ronocdh on 2007-04-25
> **xiambax said:**
> Hello,
I have kinda fallen off the wagon as of late because i stopped using linux about a year or so ago. Computers have made such a great advancement i just kind of got bored of waiting and bough a mac.
But thats besides the point.

I'm downloading Fawn now and will begin to install it when the ISO is done downloading.

What i want to know is:

1: can i safely resized my HFS partition from ubuntu install disk.
2: Do i have to worry about anything after that as far as getting hardware to work. I see some people have had problems, do these issues generally occur?

Gpartd [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) should work for resizing that partition if i can from the cd.

Anyway any feedback would be great.

-Nathan
Actually, if you're just dual booting, I would partition from OS X! You could do this using the Boot Camp utility if you want a GUI, but if you're comfortable with CLI, just use the **diskutil** command and partition. That way when you boot the live CD you'll have a partition present for you, and you can format it as ext3 (make sure it's the right one! ;)).

As for trouble, the MacBooks have it fairly good. The Core Duos seem to have a bit of sleep trouble, but as I understand it this largely went away with the C2Ds. You have Intel graphics, so no problem there (open hardware). You might want to grab the 915resolution package from the repos, but other than that, you're set!

Wireless shouldn't be too difficult, for some it works OOB, for others it's a simple madwifi or ndiswrapper process.

Post back letting us know how it goes!

---

### Post by xiambax on 2007-04-28
> **ronocdh said:**
> Actually, if you're just dual booting, I would partition from OS X! You could do this using the Boot Camp utility if you want a GUI, but if you're comfortable with CLI, just use the **diskutil** command and partition. That way when you boot the live CD you'll have a partition present for you, and you can format it as ext3 (make sure it's the right one! ;)).

As for trouble, the MacBooks have it fairly good. The Core Duos seem to have a bit of sleep trouble, but as I understand it this largely went away with the C2Ds. You have Intel graphics, so no problem there (open hardware). You might want to grab the 915resolution package from the repos, but other than that, you're set!

Wireless shouldn't be too difficult, for some it works OOB, for others it's a simple madwifi or ndiswrapper process.

Post back letting us know how it goes!

I got it up and running and everything went smoothly. I used your trick with bootcamp and everything worked great. i just need to get the madwifi thingy working now so i can fix everything and get it working great. i just need to get the internet working now so i can use it.

update:
[http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/](http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/)

currently walking threw this tutorial hope everything goes ok

---

### Post by ronocdh on 2007-04-29
> **xiambax said:**
> I got it up and running and everything went smoothly. I used your trick with bootcamp and everything worked great. i just need to get the madwifi thingy working now so i can fix everything and get it working great. i just need to get the internet working now so i can use it.

update:
[http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/](http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/)

currently walking threw this tutorial hope everything goes ok
Please post back with results. I have not yet been able to get encrypted wireless working, neither with madwifi nor ndiswrapper.

---

### Post by Romu on 2007-04-29
I don't know if the Macbook & Macbook Pro use the same wifi chipset but on my Macbook Pro, ndiswrapper makes my computer unbootable, with a "soft lockup CPU#0" or something similar.

The bug has already been reported in Launchpad.

Madwifi works well but doesn't support WPA.

---

### Post by ronocdh on 2007-04-29
> **Romu said:**
> I don't know if the Macbook & Macbook Pro use the same wifi chipset but on my Macbook Pro, ndiswrapper makes my computer unbootable, with a "soft lockup CPU#0" or something similar.

The bug has already been reported in Launchpad.

Madwifi works well but doesn't support WPA.
I haven't even gotten Madwifi working with WEP, despite its documentation indicating otherwise. I have never heard of your ndiswrapper error. Which version of ndiswrapper were you using and what's your processor?

---

### Post by xiambax on 2007-04-29
> **ronocdh said:**
> Please post back with results. I have not yet been able to get encrypted wireless working, neither with madwifi nor ndiswrapper.

Everything worked fine to be honest. The only thing i really noticed is on first attempt to connect to my wpa 2 apple airport express i get kicked off after a couple minutes then when i connect the second time it stays connected... 
you may want to note i have my 11n enabled too.

Download the display driver. works good.
Beryl works fine.

Also applyed the SynapticMouse drivers and applyed them to my xorg.conf and the track pad now acts as if i were using it within macosx...

Flawless install all the way threw.

I was surprised to be honest. but maybe i underestimate my l33t nerd skillzah :D

---

### Post by Romu on 2007-04-30
> **ronocdh said:**
> I haven't even gotten Madwifi working with WEP, despite its documentation indicating otherwise. I have never heard of your ndiswrapper error. Which version of ndiswrapper were you using and what's your processor?

I tested with the Synaptic ndsiwrapper version (1.38) and I even downloaded, recompiled and installed the last ndiswrapper (1.42) with the DLink driver. This driver worked perfectly with Edgy.

The bug is reported here :
[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/83224]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/83224")

---

### Post by ronocdh on 2007-04-30
> **Romu said:**
> I tested with the Synaptic ndsiwrapper version (1.38) and I even downloaded, recompiled and installed the last ndiswrapper (1.42) with the DLink driver. This driver worked perfectly with Edgy.

The bug is reported here :
[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/83224]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/83224")
Sweet, thanks. As per Azathoth's post above, I'm going to give ndiswrapper 1.43 a spin tonight. Hopefully this will resolve the problem! I've been using the net5416 driver Apple provides for WinXP. Nice to hear you've had success with the DLink, though.

---

