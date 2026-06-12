---
title: "Ubuntu loading bar freezes when I use graphic card... Need help"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by zth on 2007-09-02
This is my first time using linux... I installed everything perfectly, and in fact I'm using it right now. But my problem is when I try to enable the nvidia graphics driver. I have an nvidia geforce fx5500 graphics card. Usually, I will attempt to enable the driver, reboot and press f1 to get to the bios, select the pci card as my graphics card, reboot again, and everything works how it's supposed to up until the loading screen. When the ubuntu graphic comes up and the little bar below it starts filling up, it stops at the exact same point EVERY TIME. I've tried everything the forums have to offer but none of it is working and I have no clue what's going on. So then I have to go back into my bios and reset it to use the onboard graphics card and go through the whole "sudo dpkg-reconfigure -phi xserver-xorg" thing and everything works fine. I want to know why ubuntu's not working with my graphics card. Any help anyone can give me is greatly appreciated.

---

### Post by goatflyer on 2007-09-02
It sounds to me like you haven't told ubuntu to use the pci card.


First open up a terminal window and type
```

lspci

```

You should see a line looking similar to mine...

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 02e1 (rev a2)

Except maybe your card model name will be detected.  The important thing here is the PCI address of the card you want ubuntu to use.  In my case it is 01.00  (just ignore the first 4 digits)

Then when you do the sudo dpkg-reconfigure xserver-xorg command, where it says PCI address of your card, type 01.00 (or wherever yours is located).  Then finish answering all the questions.  This should get you up and running with the generic 'nv' driver.   Later, if you want to change to the proprietary nvidia driver, I suggest letting 'envy' do it for you.

You can find envy here at:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by zth on 2007-09-02
ok so i tried that and still the same thing is happening. it always freezes on the 3rd little tick in the orange bar. I must have typed something wrong though cause now I can't even get ubuntu going like i could before. Is there some other problem that could be causing this to happen?

---

### Post by ev5unleash1 on 2007-09-02
I'm having the same problem with a friends computer running the same graphics card.

---

### Post by zth on 2007-09-02
alright well at least I know I'm not alone... usually i manage to mess something up by being stupid lol. So is there compatibility issues with this card and ubuntu? I'll check and see if other people on other forums are having trouble with this card and get back here...

---

### Post by ev5unleash1 on 2007-09-02
Yea, this is a house hold and a big step to get familys into Ubuntu.

---

