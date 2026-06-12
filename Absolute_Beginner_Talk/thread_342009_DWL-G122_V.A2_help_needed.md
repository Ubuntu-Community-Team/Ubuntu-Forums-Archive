---
title: "DWL-G122 V.A2 help needed"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by AmandaKerik on 2007-01-19
I've looked for the instructions on how to get my wireless to work, but they're either for a different version (C3, for an example) or so full of jargon that my eyes glazed over.

I am a relative Ubuntu newbie when it comes to stuff like this, and my install of Ubuntu is only hours long. On the other hand, I've updated Ubuntu's files, installed a few programs through apt and automatix2. Google has helped a lot with those things, but has failed me with this task.

Can someone write out (or point to) a easily understood how-to on setting this specific one up?

I'm dual-booting XP and Ubuntu 6.06, I have the drivers for the wireless on CD.

When I plug it in it does get warm, so there is power, but the lights don't come on (they do in XP) and there's no access. I can reset the router if needed, but for some reason the router doesn't like my nic card. The nic card works fine - I'm using it right now to directly connect to my modem. The router does, however, like the wireless, and I can (in XP) change the settings through that.

I have another computer that I might be able to steal the nic card from, but I'd rather not as I want to get that one running as well.

So, can anyone help me with this?

[Edit]
I found a clue here - [http://ubuntuforums.org/showthread.php?t=341455](http://ubuntuforums.org/showthread.php?t=341455)
That showed where to look for devices (System > Administration > Device Manager) and my wireless is listed!
It's Computer > USB 2.0 > EHCI Host Controller > DWL-G122 802.11g rev.A2
So it is seeing it and understanding what it is...

What do I do now?

---

### Post by AmandaKerik on 2007-01-20
Anyone?

---

### Post by AmandaKerik on 2007-01-25
One last bump.

All I'm asking for is a good tutorial and maybe a link to an Ubuntu glossary, so I can decypher what the jargon means?

---

### Post by dbd on 2007-01-25
OK, according to the list [**here**]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") it should work fine with ndiswrapper (which is a way to use windows drivers in linux), and there is info on how to use ndiswrapper [**here**]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

Also it looks like [**this driver**]("http://jbnote.free.fr/prism54usb/") should work too. 

And if you want a more general guide then [**this**]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") may be of use to you.

Good luck! And feel free to post again if you have any problems.

---

### Post by AmandaKerik on 2007-01-25
Thank you for your response....

I'm currently stuck without any internet access in Ubuntu - the file at /etc/network/interface (and /interfaces and /interfaces~) are blank. There's no connection even with the ethernet directly connected to the router.

I'm currently in XP (which I kept as a game playing OS), trying to find the default settings for this / these files. I'll get there, I'm sure... it just takes time.

Once again, thanks for taking the time to respond. :)

---

### Post by dbd on 2007-01-26
So you can't even get on the net when using a wired connection? Strange, problems with wired networking a pretty rare.

I'd never heard of the /etc/network/interface file before, so I'm not sure what it being blank means, sorry.

Since you most want wireless I'll ignore the wired problem for now and concentrate on getting your wireless to work. I had a look on the forums and found someone who had some luck with driver loader, which you can download from [here]("http://www.linuxant.com/driverloader/wlan/full/downloads-ubuntu-x86.php")
Then install it with the command:
> sudo dpkg -i driverloader_{version}_{arch}.deb
And then point your browser to DriverLoader's web configurator at [http://127.0.0.1:18020/](http://127.0.0.1:18020/) and login as "root" to complete the installation.

For more info look around [here]("http://www.linuxant.com/driverloader/").

Good luck :)

---

### Post by AmandaKerik on 2007-01-26
I actually fixed the "no internet through ethernet" problem by using my Ubuntu CD to get the settings I needed:

# beginning
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan inet dhcp
# end

And that's what the default for the /etc/network/interfaces file is, so hopefull if someone's searching for it now, they'll find it.

And I'll be going the ndiswrapper route until I can find a driver that'll do the same thing natively in Ubuntu.:D

---

### Post by AmandaKerik on 2007-02-02
I'm not sure if I should start another thread on this, but I'm STILL having some serious issues...

I have 
ndiswrapper installed
the right driver installed 
wireless assistant installed
windows wireless drivers installed (ndisgtk)
and lots of other wireless, usb, etc etc stuff installed.

I've set the info in /etc/network/interfaces
I've set the info in the command line
I can see my AP when I scan
I can set and see the info in ndisgtk 

I've changed the settings on my AP to open key,
I've gone through over 15 walk-throughs on setting this up...

I've even managed to get it associated with my AP once - which still didn't connect to the net, and was lost at reboot... even when I did the same set up again it didn't associate ever again.

And still no net connection :(

My question is - my wireless uses a Prism 2 chipset, will the native Prism54 driver work?

Because I'm about ready to just buy a Linux-compatible toggle off of ebay at this point
(I've been fighting with this for over a week)

---

### Post by dbd on 2007-02-06
Sorry, I've run out of ideas I'm afraid. I'm not really a wireless networking expert, so if you want to keep trying it may be worth starting a new thread over in the networking help forum where there may be people who know more about wireless than over here. But after everything you've tried I wouldn't be that hopeful of a solution. :(

---

