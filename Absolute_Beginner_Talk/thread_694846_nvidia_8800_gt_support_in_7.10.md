---
title: "nvidia 8800 gt support in 7.10?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by spaceknight019283 on 2008-02-12
My friend recently got an 8800gt card for his computer cause he really loves "company of heroes" and the other few enjoyable w*ndows games out there. Anyway, I was wondering how I should help him to get his ubuntu installation supported this new card (we have not booted up yet, trying to research this stuff before I dive in). Anyway, I know nvidia has the drivers on their site, but I was wondering if Ubuntu normally gets fussy if its not involved with the installation of drivers. Wasnt really sure where to put this, but there wasnt really an obvious multimedia/hardware sub forum.

---

### Post by neurostu on 2008-02-12
Its really easy, all you have to do is install using "SAFE GRAPHICS MODE" then when the install is complete reboot. Ubuntu will detect the NVidia card and tell you that it needs to download the proprietary driver.  Let it do that and it will all work wonderfully!

---

### Post by neurostu on 2008-02-12
Sorry, when I said install I meant install UBUNTU in safe graphics mode
If ubuntu is already installed then just put the card in and boot up. Ubuntu will detect the new video card and fetch the drivers.

---

### Post by FuturePilot on 2008-02-12
I'm not sure but I don't think Ubuntu 7.10 has the drivers in the repos for the 8800. You may need to install a program called [Envy]("http://albertomilone.com/nvidia_scripts1.html") to get the driver that supports your card. Just be warned that when a kernel update comes through you may need to run Envy again to reinstall the driver because X may break.

---

### Post by Therion on 2008-02-12
> **FuturePilot said:**
> 

I'm not sure but I don't think Ubuntu 7.10 has the drivers in the repos for the 8800. You may need to install a program called [Envy]("http://albertomilone.com/nvidia_scripts1.html") to get the driver that supports your card.
Correct.  Envy sets up my 8800GTS just fine though.  What a lifesaver!

> **FuturePilot said:**
> 

Just be warned that when a kernel update comes through you may need to run Envy again to reinstall the driver because X may break.
Because X ***will***  break -- Oh yes, yes it will.  Annoying, but not the end of the world I suppose.

---

### Post by pedro_orange on 2008-02-12
I have an nVidia 8800GTS & I installed my drivers using Restricted Drivers management. 
Works fine and if I have to run stuff in Wine it works fine.

I have in the past used Envy & it is really good. Check it out.

---

### Post by Sammi on 2008-02-12
The Nvidia driver found with Restricted Drivers Management is relatively old and will not work that well with the 8xxx line. It's good for 7xxx and 6xxx though.

Use Envy to get good drivers for 8xxx cards.

But you will need to learn and remember this line "sudo envy -t". You'll need it when the kernel gets an upgrade and the graphical user environment (X, Gnome) won't boot, because the Nvidia drivers have to be reinstalled to work with a new kernel. That command will launch Envy in a command prompt from where you will be able to uninstall the Nvidia driver and reinstall it again.

---

### Post by Therion on 2008-02-12
> **Sammi said:**
> 

But you will need to learn and remember this line: "sudo envy -t". 
You'll need it when the kernel gets an upgrade ...

Where were you with this information a couple weeks ago or so, eh??  You know, when I ***needed*** it??!  Ugh... Talk about a painful, annoying, work-around.

Seriously though ... Writing this one down.  Thanks for that tip!!

---

### Post by Sammi on 2008-02-12
> **Therion said:**
> Where were you with this information a couple weeks ago or so, eh??  You know, when I ***needed*** it??!  Ugh... Talk about a painful, annoying, work-around.

Seriously though ... Writing this one down.  Thanks for that tip!!
NP :D

But how do you think I figured it out? Took me at least an hour forum reading and searching on my other computer. I'm just glad I have two:lolflag:

---

